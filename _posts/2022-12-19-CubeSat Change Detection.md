---
title: Automated Forest Harvest Detection Using a CubeSat Imagery Timeseries
layout: post
usemathjax: true
post-image: "https://user-images.githubusercontent.com/63168148/218497443-b78344da-fb75-4674-8e5e-ce01060f53a6.png"
description: My first publication, a study of methods for automated change detection 

---

CubeSats are an exciting new remote sensing technology, but require new approaches to fully leverage the data they produce. I've written a brief introduction to cubesat technology, by no means complete, which may help to understand the research presented in the article.

## The problem that cubsats solve: ##
Amongst all satellite based imaging systems it is true that for a single satellite/sensor, there is a geometrically imposed tradeoff between spatial resolution, and swath width (the area imaged in a single sensor passover), and thus also in the revisit time of the satellite (ie, the temporal resolution). Designing satellite imaging platforms has always involved managing this dilemna: place a satellite in lower orbit, or with more "zoomed in" optics, and you can acquire high spatial resolution, but with a lower revisit time. This is the approach of the Landsat mission which acheives 30m ground resolution at a 16 day revisit time^1^. Compare this to the MODIS sensor, which has a daily revisit time, but a spatial resolution ranging from 250 - 1000m depending on the the spectral band. Different applications of satellite imagery would benefit from different spatio-temporal resolution characteristics. 

## How they do it: ##

CubeSats overcome the tradeoff of spatial and temporal resolution by operating as a fleet, or constellation, of many sensors. Although a given sensor will have a ery long revisit time, together the constellation of many satellites will image the earth very often. In the case of [Planet](https://www.planet.com/?gclid=CjwKCAiA_6yfBhBNEiwAkmXy5zvDOOXAsXSt2ZXu7fRcgthVc9xMXyTxuMchtyu7-QutRTwaQqiAtBoCurwQAvD_BwE), the CubeSat company used in my research, the earth is imaged near-daily, with a 3m ground resolution.

## New challenges: ##


their ability to achieve simultaneously high temporal, and spatial resolutions. 
Follow the link below to the Canadian Journal of Remote Sensing where you can find my published article (open source), where methods and results are detailed for an algorithm to perform automated detection of harvest from a CubeSat imagery timeseries. 

[https://doi.org/10.1080/07038992.2022.2154598](https://doi.org/10.1080/07038992.2022.2154598)

Please feel free to [contact me](https://levikeay.github.io/Project_Site/#contact) with any questions regarding the research or future collaborations.

## **To cite this article:** ##

Levi Keay, Christopher Mulverhill, Nicholas C. Coops & Grant McCartney (2022) Automated Forest Harvest Detection With a Normalized PlanetScope Imagery Time Series, Canadian Journal of Remote Sensing, DOI: 10.1080/07038992.2022.2154598

## Abstract ##

The advent of CubeSat constellations is revolutionizing the ability to observe Earth systems through time. The improved spatial and temporal resolutions from these data could assist in tracking forest harvesting by forest management companies or government organizations interested in monitoring the sustainable management of forest resources. However, differing characteristics of individual satellites in each constellation requires study into geometric and radiometric normalization of the imagery and tuning parameters for change detection algorithms. In this study, a method for the spatial and temporal detection of forest harvest operations using images from the PlanetScope constellation was developed and implemented for a managed forest in Ontario, Canada. Temporal smoothing was applied on Landsat-normalized PlanetScope values of the Normalized Differential Vegetation Index (NDVI), and change points were detected based on the first derivative of the NDVI trend. Detected changes were compared to known locations of harvesting machines. Results indicate that 80–90% of harvested areas were detected, with temporal errors of approximately 9–10 days for two sites. Overall, this study demonstrated that forest harvesting can be detected with relative accuracy, deriving previously unavailable levels of spatial and temporal detail and enhancing the ability of forest stakeholders to monitor the sustainable use of forest resources.
