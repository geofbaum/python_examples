```python
import os
from osgeo import gdal, gdalnumeric, ogr
from PIL import Image, ImageDraw
import numpy as np

def clip_raster(rast, features_path, output_file, gt=None, nodata=-9999):
    #
    # This is a place holder for the real clip raster routine from the
    # link that I shared yesterday. I wrote this one just to show that
    # the correct file names are being connected to each other.
    #
    
    
    #
    # Please remove what is below this until my next comment when you copy and paste in the other routine.
    raster = rast
    shp_f = features_path
    out_f = output_file
    print("Clipping the "+raster+" file with the "+shp_f+" mask file.")
    print("Output file named : "+out_f)
    # Remove until here.
    
# Example Filenames are formatted like so: NDVI_98_2018.tif and LST_98_2018.shp
ndviF = []
lstF = []
path = 'Path\\To_Your\\Folder\\' # Change this to the path of your folder with the files.
directory = os.path.join("C:\\",path) 

# Walk through your folder and put your NDVI and LST files in their own lists
# after splitting the file names to extract the part of the name that will
# be compared.

for root,dirs,files in os.walk(directory):
    for file in files:
        if file.endswith(".tif"):                           # Please change the file types in this section according to what you are using
            f = file                                        # for your raster and vector files.
            if f.startswith("NDVI"):
                n1 = f.split('NDVI')[1].split('.tif')[0]
                ndviF.append(n1)
        if file.endswith(".shp"):
            f = file
            if f.startswith("LST"):
                l1 = f.split('LST')[1].split('.shp')[0]
                lstF.append(l1)


for i in range(len(ndviF)):
    for j in range(len(ndviF)):
        if ndviF[i] == lstF[j]:
            input_r = "NDVI"+ndviF[i]+".tif"  # You will need to change these file types as well if your inputs
            input_sh = "LST"+lstF[j]+.".shp"  # are not Tiff files and shapefiles.
            output_f = "Output_File"+lstf[j]+".tif"
            clip_raster(input_r, input_sh, output_f)
```            
