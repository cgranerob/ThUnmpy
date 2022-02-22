# ThUnmpy : Thermal Unmixing library for python.

All the sharpening methods of **Thunmpy** rely on the base that the fine-scale information in the shortwave optical domain (VNIR-SWIR) can be used to improve the resolution of the Land Surface Temperature (LST) images. To this end, these methods express the LST as a function of a given VNIR-SWIR feature (I): 

<img src="https://render.githubusercontent.com/render/math?math=LST=f(I)">

These features (I) can be reflectance or radiance measures at a given wavelength or indices mixing measures at different wavelengths.

Thus these methods rely on two main hypotheses: 

- we can find a parametric function describing the relationship between the LST and VNIR-SWIR features
- this relationship is scale invariant

In other words, based on these hypotheses, it is possible to obtain high resolution LST images by modelling the relationship between LST and VNIR-SWIR features at a coarse scale, and applying the model
to high resolution VNIR-SWIR features to retrieve the LST images at this finer scale. Finally, in order to enhance the high resolution result, a residual estimation is applied to correct fine-scale LST values.

Three main steps can be considered:

- Fit of <img src="https://render.githubusercontent.com/render/math?math=LST_c = f(I_c)"> at coarse scale c.
- Unmixing with the obtained fit parameters, <img src="https://render.githubusercontent.com/render/math?math=LST_f = f(I_f)">, where f indicates fine scale
- Residual correction

# Contents of Thunmpy package
This repository contains four main files with functions. Each function contains its description. 

1) **ThunmFit**: contains several functions to perform fits of LST vs VNIR-SWIR indices.

	- linear_fit
	- bilinear_fit
	- huts_fit
	- linear_fit_window
	- fit_byclass: a prior classification is needed

2) **Thunmixing**: contains several functions to generate a first (non-corrected) version of the fine scale LST by applying the same equations than in Thunmfit but to VNIR-SWIR indices at fine scale.

	- linear_unmixing
	- bilinear_unmixing
	- linear_unmixing_byclass
	- huts_unmixing
	- aatprk_unmixing

3) **Thunmcorr**: contains several functions to provide a residual corrected fine scale LST.

	- correction_avrg
	- correction_linreg
	- quality_correction
	- correction_ATPRK
	- correction_AATPRK

4) **Methods**: contains 4 second-layer functions directly performing sharpening methods.

	- TsHARP
	- HUTS
	- ATPRK
	- AATPRK

In order to illustrate how to use Thunmpy, this repository also contains two notebooks and some small images in the "tests" folder:

1) **Pre-defined_functions.ipynb**: contains 4 scripts showing how to use the 4 functions of Method.py, i.e. TsHARP, HUTS, ATPRK and AATPRK sharpening methodologies.

2) **Custom_functions.ipynb**: contains 1 script showing how to call functions from ThunmFit, Thunmixing and Thunmcorr in order to perform a bilinear sharpening.

3) **Small images**: LST, Albedo and NDBI images at 20m and 100m are obtained from downscaling initial images from Madrid (Spain) obtained during the <a href="https://earth.esa.int/eogateway/campaigns/desirex-2008"> DESIREX</a> campaign in 2008 at 4m of spatial resolution. Here we provide only small images to illustrate the use of Thunmpy. 

# Installation

Required packages:

- numpy
- matplotlib
- gdal
- scipy
- cv2

In order to install Thunmpy follow instructions below:

- Install required packages
- Download the full repository
- From your terminal, go to the downloaded Thunmpy repository <code>cd ~/Downloads/Thunmpy/ </code> and, once on it, type <code>pip install .</code>

# References
Granero-Belinchon, C.; Michel, A.; Lagouarde, J.-P.; Sobrino, J.A.; Briottet, X. **Multi-Resolution Study of Thermal Unmixing Techniques over Madrid Urban Area: Case Study of TRISHNA Mission**. Remote Sens. 2019, 11, 1251. <a href="https://doi.org/10.3390/rs11101251" > https://doi.org/10.3390/rs11101251 </a> and references therein.

# Contact

Carlos Granero-Belinchon <br />
Mathematical and Electrical Engineering Department <br />
IMT Atlantique <br />
Brest, France <br />
e: carlos.granero-belinchon [at] imt-atlantique.fr <br />
w: https://cgranerob.github.io/ <br />
w: https://www.imt-atlantique.fr/en/person/carlos-granero-belinchon <br />

