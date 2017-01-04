---
layout: single
title: "Introduction to lidar raster data products"
excerpt: "This lesson reviews how a lidar data point cloud is converted to a raster."
authors: ['Leah Wasser', 'NEON Data Skills']
lastModified: 2017-01-03
category: [course-materials]
class-lesson: ['class-lidar-r']
permalink: /course-materials/earth-analytics/week-3/lidar-raster-data/
nav-title: 'LiDAR Raster Data'
week: 3
sidebar:
  nav:
author_profile: false
comments: false
order: 3
---
{% include toc title="In This Lesson" icon="file-text" %}


<div class='notice--success' markdown="1">

## <i class="fa fa-graduation-cap" aria-hidden="true"></i> Learning Objectives

After completing this tutorial, you will be able to:

* Describe the basic process of how a lidar point cloud is converted into a raster.
*

## <i class="fa fa-check-square-o fa-2" aria-hidden="true"></i> What You Need

You will need a computer with internet access to complete this lesson.

</div>

In the last lesson, we learned about lidar points clouds. In this lesson, we
will learn how a point cloud is converted into a gridded or raster data format.

## create a graphic of lidar points and then a raster version??

<figure>
   <a href="{{ site.url }}/images/course-materials/earth-analytics/week-3/#">
   <img src="#" alt="Lidar data collected by NEON AOP"></a>
   <figcaption>Caption here.
   </figcaption>
</figure>


### How A Lidar system records points

Remember that lidar is an active remote sensing system that records reflected
or returned light energy. A discrete return lidar system, records the strongest
reflections of light as discrete or individual points. Each point has an associated
X, Y and Z value associated with it. It also has an intensity which represents
the amount of reflected light energy that returned to the sensor.

<figure>
   <a href="{{ site.url }}/images/course-materials/earth-analytics/week-3/waveform.png" target="_blank">
   <img src="{{ site.url }}/images/course-materials/earth-analytics/week-3/waveform.png" alt="Example of a lidar waveform"></a>
   <figcaption>An example LiDAR waveform. Source: NEON.
   </figcaption>
</figure>


## Gridded or Raster LiDAR Data Products
Point clouds provide a lot of information, scientifically. However they can be
difficult to work with given the size of the data and tools that are available
to handle large volumns of points. LiDAR data products are often
created and stored in a gridded or raster data format. The raster format can be
easier for many people to work with and also is supported by many different
commonly used software packages.

A raster file is a composed of regular grid of cells, all of which are the same
size. You've looked at and used rasters before if you've looked at photographs
or imagery in a tool like Google Earth. However, the raster files that we will
work with are different from photographs in that they are spatially referenced.
Each pixel represents an area of land on the ground. That area is defined by
the **resolution** of the raster.


<figure>
   <a href="{{ site.url }}/images/course-materials/earth-analytics/week-3/raster-concept.png" target="_blank">
   <img src="{{ site.url }}/images/course-materials/earth-analytics/week-3/raster-concept.png" alt="Raster data concept diagram."></a>
   <figcaption>A raster is composed of a regular grid of cells. Each cell is the same
   size in the x and y direction. Source: Colin Williams, NEON.
   </figcaption>
</figure>

A few notes about rasters:

-  Each cell is called a pixel.
-  And each pixel represents an area on the ground.
-  The resolution of the raster represents the area that each pixel represents
the area it represents on the ground. So, a 1 meter resolution raster, means that each pixel represents  a 1 m by 1m area on the ground.

A raster dataset can have attributes associated with it as well. For instance in a
LiDAR derived digital elevation model (DEM), each cell represents an elevation
value for that location on the earth. In a LIDAR derived intensity image, each cell
represents a LIDAR intensity value or the amount of light energy returned to and
recorded by the sensor.

<figure>
   <a href="{{ site.url }}/images/course-materials/earth-analytics/week-3/raster-resolution.png" target="_blank">
   <img src="{{ site.url }}/images/course-materials/earth-analytics/week-3/raster-resolution.png" alt="Raster data resolution concept diagram."></a>
   <figcaption>Raster can be stored at different resolutions. The resolution simply
   represents the size of each pixel cell. Source: Colin Williams, NEON.
   </figcaption>
</figure>

## Creating A Raster From LiDAR Point Clouds

There are different ways to create a raster from LiDAR point clouds. Let's look
at one of the most basic ways to create a raster file points - gridding.
When you grid raster data, you calculate a value for each pixel or cell in your
raster dataset using the points that are spatially located within that cell. To
do this:

1. A grid is placed on top of the LiDAR data in geographic space. Each cell in
the grid has the same spatial dimensions. These dimensions represent that
particular area on the ground. If we want to derive a 1 m resolution raster
from the lidar data, we overlay a 1m by 1m grid over the LiDAR data points.
2. Within each 1 m x 1 m cell, we calculate a value to be applied to that cell,
using the LiDAR points found within that cell. The simplest method of doing this
is to take the max, min or mean height value of all lidar points found within
the 1 m cell. If we use this approach, we might have cells in the raster that
don't contains any lidar points. These cells will have a "no data" value if we
process our raster in this way.

### Point to Raster Methods - Interpolation

A different approach is to interpolate the value for each cell. Interpolation
considers the values of points outside of the cell in addition to points within
the cell to calculate a value. Interpolation also often uses statistical operations
(math) to calculate the cell value. Interpolation is useful because it can provide us
with some ability to predict or calculate cell values in areas where there are
no data (or no points). And to quantify the error associated with those predictions
which is useful to know, if you are doing research.

We will not be talking about interpolation in today's class.

<figure>
  <a href="{{ site.url }}/images/course-materials/earth-analytics/week-3/gridding.gif">
  <img src="{{ site.url }}/images/course-materials/earth-analytics/week-3/gridding.gif" alt="Animation Showing the general process of taking lidar point clouds and converting them to a Raster Format"></a>
  <figcaption>
  Animation Showing the general process of taking lidar point clouds and
  converting them to a Raster Format. Source: Tristan Goulden, NEON.
  </figcaption>
</figure>

## Open Raster Data in R

To work with raster data in `R`, we can use the `raster` and `rgdal` packages.


```r

# load libraries
library(raster)
library(rgdal)

# set working directory to ensure R can find the file we wish to import
# setwd("working-dir-path-here")
```

We can use the `raster("path-to-raster-here")` function to open a raster in R.

## NOTE SWITCH THIS TO USE THE DEM INSTEAD.


```r

# open raster data
lidar_dem <- raster(x="data/week3/lidar/post-flood/postDSM3.tif")

# plot raster data
plot(lidar_dem)
```

![digital surface model raster plot]({{ site.baseurl }}/images/rfigs/course-materials/earth-analytics/week-3/lidar-intro/2016-12-06-raster03-lidar-raster-data/open-plot-raster-1.png)


If we zoom in on a small section of the raster, we can see the individual pixels
that make up the raster. Each pixel has one value associated with it. In this
case that value represents the elevation of ground.


```r
plot(lidar_dem, xlim=c(473000, 473050), ylim=c(4434000, 4434050),
     main="Lidar Raster - Zoomed into to one small region")
```

![zoom in on a small part of a raster - see the pixels?]({{ site.baseurl }}/images/rfigs/course-materials/earth-analytics/week-3/lidar-intro/2016-12-06-raster03-lidar-raster-data/plot-zoomed-in-raster-1.png)

## Raster Resolution

A raster has horizontal (x and y) resolution. This resolution represents the
area on the ground that each pixel covers. The units for our data are in meters.
Given our data resolution is 1 x 1, this means that each pixel represents a 1 x 1 meter area on the ground.


```r

# what is the x and y resolution for our raster data?
xres(lidar_dem)
## [1] 1
yres(lidar_dem)
## [1] 1
```

### Resolution units

Resolution as a number doesn't mean anything unless we know the units. We can
figure out the horizontal (x and y) units from the coordinate reference system
string.


```r

# view coordinate refence system
crs(lidar_dem)
## CRS arguments:
##  +proj=utm +zone=13 +datum=WGS84 +units=m +no_defs +ellps=WGS84
## +towgs84=0,0,0
```

Notice this string contains an element called **units=m**. This means the units
are in meters. We won't get into too much detail about coordinate refence strings
in this class but they are important to be familiar with when working with spatial
data.

## Distribution of elevation values

We can view the distribution of elevation values in our data too. This is useful
for identifying outlier data values.


```r
# plot histogram
hist(lidar_dem,
     main="Distribution of elevation values",
     xlab="elevation (meters)", ylab="frequency",
     col="springgreen")
## Warning in .hist1(x, maxpixels = maxpixels, main = main, plot = plot, ...):
## 2% of the raster cells were used. 100000 values used.
```

![histogram of DEM elevation values]({{ site.baseurl }}/images/rfigs/course-materials/earth-analytics/week-3/lidar-intro/2016-12-06-raster03-lidar-raster-data/view-hist-1.png)