# deepdespeckling for Synthetic Aperture Radar (SAR) images


Based on the work of Emanuele Dalsasso, post-doctoral researcher at CNAM and Telecom Paris.

Speckle fluctuations seriously limit the interpretability of synthetic aperture radar (SAR) images. This package provides despeckling methods that can highly improve the quality and interpretability of SAR images.

The package contains both test and train parts, wether you wish to despeckle a single pic (test) or use our model to build or improve your own.

To know more about the researcher's work : https://arxiv.org/abs/2110.13148

To get a test function using Tensorflow's framework : https://gitlab.telecom-paris.fr/ring/MERLIN/-/blob/master/README.md


[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
<img src="icons/pypi.svg" class="center">
<img src="icons/doc.svg" class="center">
<img src="icons/build.svg" class="center">

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

# Installation

Install merlin by running in the command prompt :

```console
pip install -i https://test.pypi.org/simple/ deepdespeckling
```

# Initialization for merlin package.

```python
import deepdespeckling
```




# Authors


* [Emanuele Dalsasso](https://perso.telecom-paristech.fr/dalsasso/) (Researcher at Telecom Paris)
* [Youcef Kemiche](https://engineeringteam.hi-paris.fr/about-us-2/) (Hi! PARIS engineer)
* [Pierre Blanchard](https://engineeringteam.hi-paris.fr/about-us-2/) (Hi! PARIS engineer)


# Use cases

The package offers you 3 different methods for despeckling your SAR images: the fullsize method, the coordinates based method and the crop method.

1) I have a high-resolution SAR image and I want to apply the despeckling function to the whole of it::

```python
from merlinsar.test.spotlight import despeckle

image_path="path/to/cosar/image"
destination_directory="path/where/to/save/results"
model_weights_path="path/to/model/weights"

despeckle(image_path,destination_directory,model_weights_path=model_weights_path)
```

2) I have a high-resolution SAR image but I only want to apply the despeckling function to a specific area for which I know the coordinates::
```python
from merlinsar.test.spotlight import despeckle_from_coordinates

image_path="path/to/cosar/image"
destination_directory="path/where/to/save/results"
model_weights_path="path/to/model/weights"
coordinates_dictionnary = {'x_start':2600,'y_start':1000,'x_end':3000,'y_end':1200}

despeckle_from_coordinates(image_path, coordinates_dict, destination_directory, model_weights_path)
````

Noisy image             |  Denoised image
:----------------------:|:-------------------------:
![](img/coordinates/noisy_test_image_data.png)  |  ![](img/coordinates/denoised_test_image_data.png)

3) I have a high-resolution SAR image but I want to apply the despeckling function to an area I want to select with a crop::
```python
from merlinsar.test.spotlight import despeckle_from_crop

image_path="path/to/cosar/image"
destination_directory="path/where/to/save/results"
model_weights_path="path/to/model/weights"
fixed = True "(it will crop a 256*256 image from the position of your click)" or False "(you will draw free-handly the area of your interest)"

despeckle_from_crop(image_path, destination_directory, model_weights_path, fixed=False)
```
* The cropping tool:

<p align="center">
  <img src="img/crop/crop_example.png" width="66%" class="center">
</p>

* The results:

Noisy cropped image                     |           Denoised cropped image
:-----------------------------------------------------------:|:------------------------------------------:
 <img src="img/crop/noisy_test_image_data.png" width="100%"> | <img src="img/crop/denoised_test_image_data.png" width="1000%">



# Contribute


- Source Code: https://github.com/hi-paris/deepdespeckling.git

# License

* Free software: CeCILL-B

# FAQ

* Please contact us at [engineer@hi-paris.fr](engineer@hi-paris.fr)
