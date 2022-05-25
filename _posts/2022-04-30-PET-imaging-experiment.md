---
title: Positron Emission Tomography (PET)
layout: post
post-image: "https://raw.githubusercontent.com/levikeay/Project_Site/d3e30ba88913de760b18a511d7e9013c9304f40c/assets/images/PET_diagram_offcenter_filtered.png"
description: I performed this imaging experiment as a part of Physics 409.

---

### INTRODUCTION ###

This experiment was a component of Physics 409, experimental physics. The purpose of the experiment was to understand and characterize a positron emmission tomography (PET) imaging system. I began by taking scans along a single dimension with a single radiation source which allowed for me to understand the effects of imaging parameters on the resolution of the system. I then progressed to imaging two radiation sources with an additional rotational degree of freedom, which allows for a 2 dimensional image ot be reconstructed.

### BACKGROUND

Positron Emission tomography (PET) is an imaging modality which uses [beta-positive decay](https://www.britannica.com/science/beta-plus-decay) of a radiation sample as its imaging energy source. This decay is well suited to its purpose because it produces two photons which are emitted in opposing directions, due to the conservation of energy when a positron and electron annihilate inside the radiation source. This characteristics along-axis emission provides the geometric information which is used in image reconstruction from the scanning device. Two opposing detectors are used and when they detect photons simultaneously, it is known that the source of emission lies somewhere along the line between them. By detecting at many angles, an image of the radiation source distribution can be made by using an [inverse radon transform](https://www.mathworks.com/help/images/the-inverse-radon-transformation.html).
 
In medical PET systems, the multiple angles of detection is usually achieved by having a ring of detectors surrounding the imaging area. In the present experiment, the set-up consitutes just two detectors, directly opposing each other as shown in . Radioactive samples can then be placed in the staging area and moved along the track in one dimension, as well as rotatiing. These 2 degrees of freedom can then be combined to form a 2 dimensional image via the inverse radon transform.


| ![][setup1] |
|:--:|
| The 2 photomultiplier tube detector setup |


|![][setup_close]|
|:--:|
| Close up of the imaging area. The arm can hold one or two radiation sources and can move both linearly along the track and rotate on its axis.|

### 1 dimensional scan
![][setup]

Figure 1


![][setup_close]
 
To begin, a single radiation source was imaged by simply moving it in 1 dimension: along track. Rotation with a single source would have little effect because the source is small and spherical. This allows for us to gain insight into the parameter response of the imaing profile with different apertures.

![3 gaussians fit to data from different aperture tests](https://raw.githubusercontent.com/levikeay/Project_Site/master/assets/images/PET/3gaussians_title.jpeg)

Profiles of two source imaging at eifferent angles look like this: 

![scan profiles for 9 angles](https://raw.githubusercontent.com/levikeay/Project_Site/d3e30ba88913de760b18a511d7e9013c9304f40c/assets/images/rotation_subplots.jpeg)

![showing PMT setup][setup]
![showing closeup of copper aperture][setup_close]


![][scan_profile]
![][3gaussians]
![][9angles]
![][3scans]
![][diagram_center]
![][diagram_offcenter]
![][hardware]
![][iradon_crescent]
![][iradon_centered]
![][iradon_backprojection]
![][iradon_SART]
![][results_fig]
![][signal_correction]


[setup]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/setup_picture.png?raw=true
[setup1]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/setup_picture.png?raw=true 
{height="36px" width="36px"}

[setup_close]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/setup_closeup.jpg?raw=true
[scan_profile]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/single_source_errorbars.jpeg?raw=true
[3gaussians]: https://raw.githubusercontent.com/levikeay/Project_Site/master/assets/images/PET/3gaussians_title.jpeg
[9angles]: https://raw.githubusercontent.com/levikeay/Project_Site/d3e30ba88913de760b18a511d7e9013c9304f40c/assets/images/rotation_subplots.jpeg
[3scans]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/3apts_rawdata.jpeg?raw=true
[diagram_center]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/PET_diagram.png?raw=true
[diagram_offcenter]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/PET_diagram_offcenter.png?raw=true
[hardware]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/hardware.jpg?raw=true
[iradon_crescent]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/nice_radon_fig.png?raw=true
[iradon_centered]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/nice_radon_fig1.png?raw=true
[iradon_backprojection]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/nice_radon_fig66.png?raw=true
[iradon_SART]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/nice_radon_fig99.png?raw=true
[results_fig]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/primaryvsnoise_params2.jpeg?raw=true
[signal_correction]: https://github.com/levikeay/Project_Site/blob/master/assets/images/PET/signal_correction.jpeg?raw=true
