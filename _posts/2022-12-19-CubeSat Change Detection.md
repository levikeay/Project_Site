---
title: Automated Forest Harvest Detection Using a CubeSat Imagery Timeseries
layout: post
usemathjax: true
post-image: "https://user-images.githubusercontent.com/63168148/218497443-b78344da-fb75-4674-8e5e-ce01060f53a6.png"
description: My first publication, a study of methods for automated change detection 

---

CubeSats are an exciting new remote sensing technology, but require new approaches to fully leverage the data they produce. The aim of this research was to develop and test such a method with applications to the field of forest management and monitoring. Below you will find a brief introduction to cubesat technology, by no means complete, meant to serve as context for those who need it which may help to understand the research presented in the research article, which can be found here :

[Canadian Journal of Remote Sensing: https://doi.org/10.1080/07038992.2022.2154598](https://doi.org/10.1080/07038992.2022.2154598)

Please feel free to [contact me](https://levikeay.github.io/Project_Site/#contact) with any questions regarding the research.

## The problem that cubsats solve: ##
Amongst all satellite based imaging systems it is true that for a single satellite/sensor, there is a geometrically imposed tradeoff between spatial resolution, and swath width (the area imaged in a single sensor passover), and thus also in the revisit time of the satellite (ie, the temporal resolution). Designing satellite imaging platforms has always involved managing this dilemna: place a satellite in lower orbit, or with more "zoomed in" optics, and you can acquire high spatial resolution, but with a lower revisit time. This is the approach of the Landsat mission which acheives 30m ground resolution at a 16 day revisit time*. Compare this to the MODIS sensor, which has a daily revisit time, but a spatial resolution ranging from 250 - 1000m depending on the the spectral band. Different applications of satellite imagery would benefit from different spatio-temporal resolution characteristics. 

\* Landsat now uses 2 platforms in opposing orbits, giving an effective revisit time of 8 days.

## How they do it: ##

CubeSats overcome the tradeoff of spatial and temporal resolution by operating as a fleet, or constellation, of many sensors. Although a given sensor will have a very long revisit time, together the constellation of many satellites will image the earth at high cadence. In the case of [Planet](https://www.planet.com/?gclid=CjwKCAiA_6yfBhBNEiwAkmXy5zvDOOXAsXSt2ZXu7fRcgthVc9xMXyTxuMchtyu7-QutRTwaQqiAtBoCurwQAvD_BwE), the CubeSat company used in my research, the earth is imaged near-daily, with a 3m ground resolution, by using a constellation of approximately 200 CubeSats

## New challenges: ##

Though CubeSats are an exciting revolution in remote sensing in their potential to monitor Earth systems at unprecendent detail in space and time, there are certain obstacles that must be overcome in order to access their full potential. CubeSats produce so much data, that it becomes impractical to manually assess it over large areas. So, automated, computer vision change detection and classification algorithms are needed. There are existing algorithms that are commonly used in remote sensing using "conventional" datasets, such as Landsat. However, the data quality of CubeSat constellations is found to be somewhat inferior to their single platform ancestors, particularily in terms of radiometric consistency. Because images of one study area are acquired by many different sensors, the slight variations of properties of those sensors, as well as changing lighting conditions and phenology, are present in the timeseries data as noise, which presents an issue for automated methods. 

While CubeSat providers are aware of this limitation and are working towards improving data quality, further work is still needed before CubeSat imagery can be utilized to its full potential.

## CubeSats and Forestry: ##

Now, with some background having been presented, please read my publication (link below), where my coauthors and I propose a method for detecting forest harvest automatically using the Planet CubeSat archive. Follow the link below to the Canadian Journal of Remote Sensing where you can find the article (open source).

[https://doi.org/10.1080/07038992.2022.2154598](https://doi.org/10.1080/07038992.2022.2154598)

#### Abstract ####

The advent of CubeSat constellations is revolutionizing the ability to observe Earth systems through time. The improved spatial and temporal resolutions from these data could assist in tracking forest harvesting by forest management companies or government organizations interested in monitoring the sustainable management of forest resources. However, differing characteristics of individual satellites in each constellation requires study into geometric and radiometric normalization of the imagery and tuning parameters for change detection algorithms. In this study, a method for the spatial and temporal detection of forest harvest operations using images from the PlanetScope constellation was developed and implemented for a managed forest in Ontario, Canada. Temporal smoothing was applied on Landsat-normalized PlanetScope values of the Normalized Differential Vegetation Index (NDVI), and change points were detected based on the first derivative of the NDVI trend. Detected changes were compared to known locations of harvesting machines. Results indicate that 80–90% of harvested areas were detected, with temporal errors of approximately 9–10 days for two sites. Overall, this study demonstrated that forest harvesting can be detected with relative accuracy, deriving previously unavailable levels of spatial and temporal detail and enhancing the ability of forest stakeholders to monitor the sustainable use of forest resources.


Please feel free to [contact me](https://levikeay.github.io/Project_Site/#contact) with any questions regarding the research or future collaborations.

## **To cite this article:** ##

Levi Keay, Christopher Mulverhill, Nicholas C. Coops & Grant McCartney (2022) Automated Forest Harvest Detection With a Normalized PlanetScope Imagery Time Series, Canadian Journal of Remote Sensing, DOI: 10.1080/07038992.2022.2154598

