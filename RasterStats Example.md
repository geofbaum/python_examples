```python

import os
from rasterstats import zonal_stats

directory = os.path.join("c:\\","Path\\To\\Your\\Folder\\of\\Rasters")
vector = "your_shapefile_or_geojson_file"
extract_stats = ['mean', 'std', 'min', 'max', 'majority', 'minority', 'unique']

for root,dirs,files in os.walk(directory):					# Walkthrough the folder and grab only the raster files
    for file in files:									# Split the filename into it's name and extension
	if file.endswith(".tiff" or ".tif"):						# 
	    f,e = os.path.splittext(file)						# 
	    stats = zonal_stats(vector, file, stats=extract_stats, geojson_out=True)	# run zonal_stats on the file to retrieve the stats from
											# the raster file
	# [f['mean'] for f in stats] returns mean values
		   
		   
```
```python
#
# for just one file
#

from rasterstats import zonal_stats

extract_stats = ['mean', 'std', 'min', 'max', 'majority', 'minority', 'unique']

vector = "your_shapefile_or_geojson_file"
raster = "your_raster_file"

stats = zonal_stats(vector, raster, stats=extract_stats, geojson_out=True)

[f['mean'] for f in stats]  # returns mean values

```
