---
layout: single
authors: ['Software Carpentry']
category: [course-materials]
title: 'Install & Setup R and R Studio on Your Computer'
excerpt: '#.'
nav-title: 'Setup Working Directory'
sidebar:
  nav:
class-lesson: ['setup-r-rstudio']
permalink: course-materials/earth-analytics/setup-working-directory
author_profile: false
comments: false
order: 3
---


## Setup your working Directory

Project organization is integral to efficient research. In this tutorial, we will
create the working directory that we will use for all of our work. This working
directory will be carefully organized with a `data` directory that we will use
to save all of our downloaded data.

<div class='notice--success' markdown="1">

# Learning Objectives
At the end of this activity, you will:

* Be able to create an easy to use and we structured project structure.
* Know how to set a working directory in R

## What You Need

You will need the most current version of R and, preferably, RStudio loaded on
your computer to complete this tutorial.

* [How to Setup R / R Studio](/course-materials/setup-r-rstudio)

</div>


## Setup Working Directory

Now that we have the basics of good project structure out of the way, let's get
our project setup. We are going to create an `Earth Analytics` working Directory
where we will store data and files used in the class.

Follow the steps below to create a working directory space AND a data Directory
on your computer:

* Navigate to the `Documents` directory on your computer.
* In the directory, create a NEW DIRECTORY called `earth-analytics`.

> Notice that we are creating a nice easy to read directory name. The name has
no spaces and uses all lower case to support machine reading down the road.
Sometimes this format of naming using dashes is referred to as a `slug`.

* Next, open the earth-analytics directory and create a directory called `data`

> We will use the data directory to store the data that we download to use in
> this course and in the tutorials hosted on this website.



<figure>
	<a href="{{ site.url }}/images/course-materials/geog-4100-5100/setup-r-rstudio/working-dir-os.png">
	<img src="{{ site.url }}/images/course-materials/geog-4100-5100/setup-r-rstudio/working-dir-os.png"></a>
	<figcaption> Your working directory should look like this. Right now it just
	contains one directory - `data`.
	</figcaption>
</figure>

* The final step is optional but recommended - especially if you are new to `R`
and `RStudio`. Open up `RStudio` and set your default working Directory
to the `earth-analytics` directory that we just created. In RStudio go to:
`Tools--> Global Options --> Click on the General setting at the top of the global
options panel` (see screen shot below).
* Browse to the earth-analytics directory and set it as your default working directory.

<figure>
	<a href="{{ site.url }}/images/course-materials/geog-4100-5100/setup-r-rstudio/r-studio-wd-setup.png">
	<img src="{{ site.url }}/images/course-materials/geog-4100-5100/setup-r-rstudio/r-studio-wd-setup.png"></a>
	<figcaption> Set your default working directory in R studio to the Earth Analytics
  directory. That way, every time you open `RStudio` it will default to that
  directory. Image: RStudio Version 0.99.903.
	</figcaption>
</figure>

Finally, let's see what your main working directory. We use the  `getwd()` function
to find out what our current working directory is in R.


```r

# view working directory
getwd()

```


```r
[1] "/Users/lewa8222/Documents/earth-analytics"
```

If your working directory path does not match the location where you created your
`earth-analytics` directory on your computer, then we need to change it. We can
do this with code OR we can use the RStudio interface to do this.

* In the RStudio interface, look at the pane in the LOWER LEFT hand corner of your
screen. It should have a tab called `Files`. In that directory, navigate to
your earth-analytics directory which should be int he `Documents` directory.
Your window should look like the screen shot below:

<figure>
	<a href="{{ site.url }}/images/course-materials/geog-4100-5100/setup-r-rstudio/working-directory.png">
	<img src="{{ site.url }}/images/course-materials/geog-4100-5100/setup-r-rstudio/working-directory.png"></a>
	<figcaption> Your working directory should look like this. It should contain
	just a `data` directory. Image: RStudio Version 0.99.903. Source: Earth Lab.
	</figcaption>
</figure>

* Next, click on the `More`. Cho0se `Set as working directory`

<figure>
	<a href="{{ site.url }}/images/course-materials/geog-4100-5100/setup-r-rstudio/set-working-dir-rstudio.png">
	<img src="{{ site.url }}/images/course-materials/geog-4100-5100/setup-r-rstudio/set-working-dir-rstudio.png"></a>
	<figcaption> You can set your working directory in RStudio directly. Image: RStudio Version 0.99.903. Source: Earth Lab.
	</figcaption>
</figure>




## Set Working Directory Using Code

We can
use the `setwd()` function to set a new working directory as follows:



```r

# set working directory - MAC File Structure - backslashes
setwd("/Users/lewa8222/Documents/earth-analytics")

# a windows machine uses front slashes. There is normally a
# drive letter like C:\
setwd("C:\Users\lewa8222\Documents\earth-analytics")

```




<figure>
	<a href="{{ site.url }}/images/course-materials/geog-4100-5100/setup-r-rstudio/working-directory.png">
	<img src="{{ site.url }}/images/course-materials/geog-4100-5100/setup-r-rstudio/working-directory.png"></a>
	<figcaption> Your working directory should look like this. It should contain
	just a `data` directory. Image: RStudio Version 0.99.903. Source: Earth Lab.
	</figcaption>
</figure>

## All Done!
Great work! You are now read to start working with `RStudio`!