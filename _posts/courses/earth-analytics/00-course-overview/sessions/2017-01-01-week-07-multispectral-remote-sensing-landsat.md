---
layout: single
category: courses
title: "Landsat Data in R - Fire Ecology & Remote Sensing"
permalink: /courses/earth-analytics/spectral-remote-sensing-landsat/
modified: '2017-10-10'
week-landing: 7
week: 7
sidebar:
  nav:
comments: false
author_profile: false
course: "earth-analytics"
module-type: 'session'
redirect_from:
  - "/courses/earth-analytics/week-7/"
---

{% include toc title="This Week" icon="file-text" %}


<div class="notice--info" markdown="1">

## <i class="fa fa-ship" aria-hidden="true"></i> Welcome to Week {{ page.week }}!

Welcome to week {{ page.week }} of Earth Analytics!

At the end of this week you will be able to

* Describe what a spectral band is related to remote sensing data.
* Create maps of spectral remote sensing data using different band combinations including CIR, and RGB.
* Calculate NDVI in `R` using efficient raster processing approaches including rasterbricks and the overlay function.
* Use the Landsat file naming convention to determine correct band combinations for plotting and to  calculate NDVI.
* Define additive color model.

{% include/data_subsets/course_earth_analytics/_data-week6-7.md %}


</div>


|  Time | Topic   | Speaker   |
|---|---|---|---|---|
| 9:30 - 9:45  | Review last week's assignment / questions |   |
| 9:45 - 10:00  | Introduction to multispectral remote sensing  |  |
| 10:00 - 11:00  | Coding Session: Multispectral data in R - rasterstacks and bricks & Band combinations |  Leah  |
|===
| 11:10 - 12:20  | Vegetation indices and NDVI in R |  Leah  |

### 1a. Remote Sensing Readings

* <a href="https://landsat.gsfc.nasa.gov/landsat-data-continuity-mission/" target="_blank">NASA overview of Landsat 8</a>
* <a href="https://www.e-education.psu.edu/natureofgeoinfo/c8_p12.html" target="_blank">Penn State e-Education post on multi-spectral data. Note they discuss AVHRR at the top which we aren't using but be sure to read about Landsat.</a>


### 2. Complete the Assignment Below (5 points)

<div class="notice--warning" markdown="1">

## <i class="fa fa-pencil-square-o" aria-hidden="true"></i> Homework Submission

### Produce a .pdf Report

Create a new `R markdown `document. Name it: **lastName-firstInitial-week6.Rmd**
Within your `.Rmd` document, include the plots listed below. When you are done
with your report, use `knitr` to convert it to `PDF` format. Submit both the
`.Rmd` file and the `.pdf` file. Be sure to name your files as instructed above!

#### Use knitr Code Chunk Arguments
In your final report, use the following knitr code chunk arguments to hide messages
and warnings and code as you see fit.

* `message = FALSE`, `warning = FALSE` Hide warnings and messages in a code chunk
* `echo = FALSE` Hide code and just show code output
* `results = 'hide'` Hide the verbose output from some functions like `readOGR()`.

#### Answer the Questions Below in Your Report

1. What is the key difference between active and passive remote sensing system?
2. Describe *atleast* 3 differences between lidar vs landsat remote sensing data.
2. Explain what a vegetation index is.

#### Include the Plots Below.
For all plots:

1. Be sure to describe what each plot shows in your final report using a figure
caption argument in your code chunks: `fig.cap="caption here".
2. Add appropriate titles that tells someone reading your report what the map shows

#### Plots 1 & 2: RGB & CIR images
Create a 1) RGB and 2) Color Infrared (CIR) image of the study site using NAIP data : `naip/m_3910505_nw_13_1_20150919/crop/m_3910505_nw_13_1_20150919_crop.tif`

[Use this lesson on stacking plots in base R]({{ site.url }} /courses/earth-analytics/spectral-remote-sensing-modis/grid-of-plots-report/)
to stack the plots on top of each other.


#### Plot 3: Create a plot of NDVI

Using the same NAIP image above, calculate NDVI and plot it. Use a function to
perform the NDVI math and the overlay() function to implement the
actual NDVI calculation. Your code should look something like this: `overlay(b1, b2, fun = normalized_diff)`. Be sure that your function is included in your code when you submit your assignment!

#### Plot 4 & 5: NDVI

Create  map of NDVI pre and post fire.

#### Plot 6 & 7: CIR image with Landsat

Plot a RGB and CIR image using Landsat data collected pre-fire. What do you notice
in the data that may cause problems when analyzing it?


HINTS:

If you see the error below when you plot your RGB images, try to apply a
stretch argument to your `plotRGB()` function.

```r
## Error in grDevices::rgb(RGB[, 1], RGB[, 2], RGB[, 3], alpha = alpha, max = scale) :
##  color intensity -0.00010005, not in [0,1]
```

Try to add the code chunk below after any plots where you change the columns
using the `par()` function. This will "clean" your plot parameters so the next
plot renders correctly.


```html
{r, echo = FALSE, results = 'hide'}
# the function below clears our your plot render space removing any margins or
# other changes to `par()` settings.
dev.off()

```

****

## Homework Due: Monday October 16 2017 @ 8AM.
Submit your report in both `.Rmd` and `.html` format to the D2L dropbox.

</div>

## Grading

#### R Markdown Report Structure & Code: 10%

| Full Credit | No Credit  |
|:----|----|
| PDF and RMD submitted |  |
| Code is written using "clean" code practices following the Hadley Wickham style guide|  |
| Code chunk contains code and runs  |  |
| All required R packages are listed at the top of the document in a code chunk. | |
| Lines of code are broken up at commas to make the code more readable  |  |


####  Knitr pdf Output: 20%

| Full Credit | No Credit  |
|:----|----|
| Code chunk arguments are used to hide warnings |  |
| Code chunk arguments are used to hide code and just show output |  |
| PDf report emphasizes the write up and the code outputs rather than showing each step of the code | |

####  Report Questions: 20%

| Full Credit | No Credit  |
|:----|----|
| What is the key difference between active and passive remote sensing system is answered correctly. |  |  | | |
| Describe atleast 3 differences between how lidar vs landsat remote sensing data is answered correctly.|  |  | | |
| Explain what a vegetation index is answered correctly. |||||


### Plots are Worth 50% of the Assignment Grade

#### Create a MAP of the Difference Between NDVI Pre vs Post Fire (Post fire - Pre-fire NDVI).

| Full Credit | No Credit  |
|:----|----|
| Pre and post fire NDVI are created |  |  | | |
| Plot renders on the pdf. |  |  | | |
| Plot contains a meaningful title. |  |  | | |
| Plot has a 2-3 sentence figure caption that clearly describes plot contents. |  |  | | |

#### Plot 2 Create a MAP of the difference between NBR pre vs post fire (Post fire - pre-fire NBR).

| Full Credit | No Credit  |
|:----|----|
| Pre and post fire NBR are created |  |  | | |
| Plot renders on the pdf. |  |  | | |
| Plot contains a meaningful title. |  |  | | |
| Plot has a 2-3 sentence figure caption that clearly describes plot contents. |  |  | | |
| Plot includes a clear legend with each "level" of burn severity labeled clearly. |  |  | | |

#### Plots 3 - Create a classified map of post fire NDVI using classification values that you think make sense based upon exploring the data.

| Full Credit | No Credit  |
|:----|----|
| A classified map has been created and renders in the report. |  |  | | |
| The values chosen to create the classified plot clearly show differences in NDVI values. |  |  | | |
| The colors chosen to create the classified plot clearly show differences in NDVI values. |  |  | | |
| Plot has a clear title that describes the data being shown. |  |  | | |
| Plot has a clear legend that shows the classes chosen and associated colors rendered on the map. |  |  | | |
| Plots have a 2-3 sentence caption that clearly describes plot contents. |  |  | | |

#### Plots 4 Create a classified map of post fire NBR using the classification thresholds.

| Full Credit | No Credit  |
|:----|----|
| Plot renders on the pdf. |  |
| Plot contains a meaningful title. |  |
| Plot has a 2-3 sentence figure caption that clearly describes plot contents. |  |
| Plot data are classified using the thresholds specified. |  |
| Plot data colors clearly show areas of most intense burn compared to areas of no or less burn severity. |  |
| Plot has a clear legend that shows the classes chosen and associated colors rendered on the map. | |


### Example report plots



<img src="{{ site.url }}/images/rfigs/courses/earth-analytics/00-course-overview/sessions/2017-01-01-week-07-multispectral-remote-sensing-landsat/load-packages-1.png" title="NAIP CIR" alt="NAIP CIR" width="90%" />






<img src="{{ site.url }}/images/rfigs/courses/earth-analytics/00-course-overview/sessions/2017-01-01-week-07-multispectral-remote-sensing-landsat/unnamed-chunk-3-1.png" title="Landsat NDVI pre and post fire" alt="Landsat NDVI pre and post fire" width="90%" />



<img src="{{ site.url }}/images/rfigs/courses/earth-analytics/00-course-overview/sessions/2017-01-01-week-07-multispectral-remote-sensing-landsat/unnamed-chunk-5-1.png" title=" " alt=" " width="90%" />





<!--
#### Plot 2
Create a MAP of the **difference between NBR pre vs post fire** with Landsat data  (Pre fire - post-fire NBR). Classify that data using the classification thresholds below. Be sure to include a legend on your map that helps someone looking at it
understand differences.

| SEVERITY LEVEL  | NBR RANGE |
|------------------------------|
| Enhanced Regrowth | -700 to  -100  |
| Unburned       |  -100 to +100  |
| Low Severity     | +100 to +270  |
| Moderate Severity  | +270 to +660  |
| High Severity     |  +660 to +1300 |

Note: if your min and max NBR values are outside of the range above, you can adjust
-700 to be your smallest raster value and for high severity you can adjust 1300 to
be your largest NBR raster value.

#### Plot 3
Create a classified map of **post fire NDVI** with Landsat data using classification values that you
think make sense based upon exploring the data.

#### Plot 4
Create a map of **post fire NBR** with Landsat data.
-->