```python
import yaml
from osgeo import gdal, ogr, osr
import datetime
import os, time
from pygeometa.core import render_template

path = "C:/Path/to/your/Raster/or/Vector/file.extensionOfChoice"
(fileRoot, fileExt) = os.path.splitext(path)
outFileName = fileRoot + "_mod" + fileExt

rstr = [".tif", ".asc", ".vrt", ".hdf4", ".hdf5", ".gpkg", ".img", ".grib", ".sdat", ".xyz"]
vctr = [".geojson", ".shp", ".vct", ".mvt", ".gdb", ".kml", ".gpx"]

# Look at the geospatial data to grab pertinent information to update the .yml file with

fName = str(os.path.basename(path))
crDate = str(time.ctime(os.path.getctime(path)))

if fileExt in rstr:                             # for raster files
    ds = gdal.Open(path)
    dataType = 'grid'
    geomType = 'surface'
    crs = osr.SpatialReference(wkt=ds.GetProjection())
    fct = str(crs.GetAttrValue('AUTHORITY',0))
    code = str(crs.GetAttrValue('AUTHORITY',1))
    crs = fct+":"+code
    ulx, xres, xskew, uly, yskew, yres  = ds.GetGeoTransform()
    lrx = ulx + (ds.RasterXSize * xres)
    lry = uly + (ds.RasterYSize * yres)
    geogExtent = str(ulx)+","+str(uly)+","+str(lrx)+","+str(lry)
    
else:                                           # for vector files
    ds = ogr.Open(path)
    layer = ds.GetLayer()
    prj=ds.GetLayer().GetSpatialRef()
    geogExtent = str(ds.GetLayer().GetExtent())
    geogExtent = str(geogExtent.translate({ord(i): None for i in '()'}))
    feature = layer.GetNextFeature()
    geometry = feature.GetGeometryRef()
    geomType = str(geometry.GetGeometryName())
    dataType = 'vector'
    crs = str(prj.GetAttrValue('geogcs'))

# Open Base .yml file to edit with updated information

with open("test_new.yml") as f:
    d = yaml.load(f)

    d["metadata"]["identifier"] = fName
    d["metadata"]["dataseturi"] = path
    d["spatial"]["datatype"] = dataType
    d["spatial"]["geomtype"] = geomType
    d["spatial"]["crs"] = crs
    d["spatial"]["bbox"] = geogExtent
    d["identification"]["title_en"] = fName
    d["identification"]["abstract_en"] = 'This is a test abstract'
    d["identification"]["dates"]["creation"] = crDate
    d["distribution"]['local']["url"] = path
    
    # You can uncomment the next line if you want to verify the xml output that is created
    #print(render_template(d, schema='iso19139'))
    
    # Render the yml file to the xml file format matching the ISO19139 Schema
    xml_string = render_template(d, schema='iso19139')
    
    # Split the filename to remove the extension so it can be used in the Metadata file name
    (fileRt, fileEx) = os.path.splitext(fName)
    xmlf = 'MD_'+fileRt+'.xml'
    
    # Write rendered xml to the Metadata file
    with open (xmlf, 'w') as x:
        x.write(xml_string)

```
