---
title: Automated Forest Harvest Detection Using a CubeSat Imagery Timeseries
layout: post
usemathjax: true
post-image: "https://user-images.githubusercontent.com/63168148/186097612-0c4c06d0-09df-4e83-b4fe-889eccd94588.gif"
description: a method of pixel-wise change detection leveraging spectral signature trajectories

---

Here I present an algorithm developed in order to automatically detect forest harvest from CubeSat constellation imagery. A paper is submitted for review which further details the method and results found. The Python scripts which implement this method can be found [in this repository](https://github.com/levikeay/CubeSat_Change_Detection).

### CubeSat Imagery 


CubeSats are small (10 cm^3) satellites in low earth orbit which can work as a constellation to provide high spatial resolution imagery at a high revisit rate, thus overcoming the traditional spatial-temporal resolution tradeoff of traditional imaging platforms. My research focussed on utilizing CubeSat imagery from the company [Planet](https://www.planet.com/), leveraging its high spatial and temporal resolution to map the activity of forest harvesting through time of managed forests in Ontario, Canada.

<p align="center">
  <img src="https://user-images.githubusercontent.com/63168148/191145016-998f92f0-9660-4305-9024-f56889ed768e.png"><br>
  One of Planet's "Dove" Cubesats - image credit: Planet
</p>

### Detecting harvest using Satellite imagery

To track forest harvest, we utilized the Normalized Difference Vegetation Index, which is commonly used to track plant health. It works by combining the red and near-infrared (NIR) as follows:

$$ NDVI =  \frac{(NIR - Red)}{(NIR + Red)} $$

In this way, healthy vegetation appears bright, and all else is relatively dark. We compute NDVI for each image we havae available of the study site, giving a timeseries that looks like this:

<p align="center">
  <img src="https://user-images.githubusercontent.com/63168148/187098691-02ffde3d-48d4-48a8-8a34-87b320a3fda4.gif" width="400">
  <br>
  An NDVI timeseries showing harvest activity in the study area.
</p>

See more about data smoothing in [my other post on spectral trajectory despiking](https://levikeay.github.io/Project_Site/blog/Spectral_despike).

---


![siteA_prediction_legend](https://user-images.githubusercontent.com/63168148/191173807-6c6655a2-3b85-4b41-adc0-1a9e9975642b.png)


### Breakpoint detection
Taking an individual pixel's NDVI value through time as the input signal, Kernalized Changepoint Detection using the Pruned Exact Linear Time (PELT) search method is applied, and the breakpoint most likely to represent harvest is selected using attributes of the signal and its subsignals. This process is applied to each pixel-timeseries in the area of interest, and each pixel's predicted date of harvest is recorded onto a harvest map at the same resolution of the input imagery:

<p align="center">
  <img src="https://user-images.githubusercontent.com/63168148/187100170-094ba6de-961a-491d-bbd2-30ada9c12918.png" width="400">  
</p>

The color map shows the day of year of predicted harvest, with yellow being earliest dates, and red being the latest dates. This date in cell format is the output of the method. 

---
### post-processing
False positives are of concern in many applications. Accuracy of result can improved through spatial filtering:

|![image](https://user-images.githubusercontent.com/63168148/187100562-cb81f4c6-c1f9-4f3b-89b3-347c5827e26f.png)| ![image](https://user-images.githubusercontent.com/63168148/187100590-83ffa26e-8780-4cc5-a4a1-e18bd06298d5.png) |
|:--:|:--:|
|many false positives are present before filtering | spatial accuracy is improved after filtering |

Recommended filters for post processing are sieve and modal filters.

