# python_examples
<h1>Examples of random python code for various different purposes.</h1>
<br>
<br>
<b><i>Converting Image Files with Pillow</i></b> 
<br>
<br>
Sometimes it maybe necessary to convert image files to a different format whether it be for print publication or web publication. This
example shows a script for converting a file or multiple files of a specific type to another type. The original file will be preserved
and a new file is created with the same file name and new file type.
<br>
<br>
<b><i>Create Metadata File</i></b> 
<br>
<br>
As geospatial data use continues to grow especially with open source data, creating metadata files for your data is becoming more and 
more important. Not only does it allow others to get a grasp of the data file or data set that they are working with but it also allows 
you to link the data to specific locations if it's being distributed on a server. Finally, it allows the creator to keep track of the 
data and allows for rights and copyright information to be based to the user to explain fair use.
<br>
In this example, I will be using the GDAL, OGR, OSR, and pygeometa libraries to show an example of how simple it can be to create 
metadata if you have a large set of files all of which share at least some similar information that can be hardcoded into the MCF/yaml 
file.
<br>
<br>
<b><i>Date to Day of Year (DOY)</i> </b>
<br>
<br>
In a lot of cases with scientific data sets, data is often sorted by dates and while most data sets will have an actual year-month-day
formatted date, not all will and will use just the day of the day of the year (ex. 1-365) to denote the date and month. In this example
I am just showing a simple way to convert the current date to the DOY with the datetime library.
<br>
<br>
<b><i>Raster Stats Example</i></b>
<br>
<br>
Using the raster stats library, shows an example how to get some of the typical spatial statistics about a raster file.
<br>
<br>
<b><i>Send an Email</i></b>
<br>
<br>
An example to show how to set up a python script to send emails. This could be expanded upon to use in other cases where you want to 
send an alert or mass email.
<br>
<br>
<b><i>WeatherLink API</i></b>
<br>
<br>
This needs updated as the WeatherLink API has changed since this was originally created.
<br>
<br>
<b><i>Windows Print Item</i></b>
<br>
<br>
An example showing how to print a file with a Python script.
<br>
<br>
<b><i>Work with similarly named files</i></b>
<br>
<br>
An example expanding upon clipping raster data, with the point of being able to search automatically through a directory for files that 
share common parts of their names say, for example I have an NDVI raster file that includes NYC titled NDVI_NYC_2019 and then a
shapefile called Outline_NYC_2019, I can use the fact that they both have NYC to know that they should go together.
<br>
<br>
<b><i>Plotly Humidity Gauge</i> </b>
<br>
<br>
A simple example of how to create a gauge image to show current humidity values. Is to be used to input and create a set of images that
update when new data from a sensor is gathered.
<br>
<br>
  <b><i>Windows Printers</i></b>
<br>
<br>
An example to show how to create a list of available printers that can be used on a MS Windows based system.
<br>
<br>
