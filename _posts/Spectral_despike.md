Despiking spectral trajectories is an important step of preprocessing, especially of new cubesat imagery datasets which may not have sufficient cloud masking algoirthms available.

I have made a simple modification to the prior approach of cloud despiking designed for annual best available pixel (BAP) datasets, which have regularly spaced timeseries data (1 point per year). For this approach it is fitting to take the mean of neighbouring values, as it is equivalent to interpolation when the data is evenly spaced.

However with irregularly spaced observations as is found with high cadence cubesat data, an extra few lines of code are required to calculate the linearly interpolated values of each data points' neighbours

Here is an example of my algorithm in progress, despiking some artificial data, with the large initial spike meant to represent a cloud:

![despike_envelope](https://user-images.githubusercontent.com/63168148/186032134-c36e72a8-8323-4c52-a469-1d61f7af20f5.gif)
