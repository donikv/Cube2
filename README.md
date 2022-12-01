# Cube2
Cube2: A large multi-illuminant dataset

The whole dataset can be found [here](https://ferhr.sharepoint.com/:f:/s/imageprocessinggroup/EqiYusGI8x9Gp40B0iDAaaIBwpU1oSv5FbU5ESs33lMQFQ), alongside a loader written in python for loading images.

## Description
Cube2 is a large multi illuminant dataset composed of 2500 outdoor and indoor images. 
These images were collected using 5 different DSLR camera models and in different times during the day and in different times of the year. 
Images were mostly collected in Croatia, and feature mostly urban scenes. 
Outdoor images were annotated manually. In addition to the spatial map of illuminants for each image, the groundtruth color of the illuminants is provided.
The color of the illuminants was retrieved from the SpyderCube calibration objects that were placed in each scene. The dataset is GDPR compliant, whcih means all faces have been masked out. 

***OUTDATED TABLE***
|Camera | N. images|
|-------|----------|
|Canon 550D|  X    |
|Canon EOS 5D| X   |
|Nikon D7000|  X   |


## Usage
Images in the dataset are divided into folders.
Each image folder contains the following files:

- **img.png** - minimally processed image, only simply debayering was performed
                additional preprocessing steps are required
- **gt_mask.png** - segmentation max where 1 represents pixels in the ambient light and 2 represents pixels point light
- **cubes.txt** - contains the coordinates of rectangles that cover the SpyderCubes (x0,y0,x1,y1) that need to be set to 0 so the model doesn't overfit on the cube
- **GDPR_cubes.txt** - contains coordinate of rectangels that cover the sensitive data (x0,y0,x1,y1)
- **gt.txt** - the shadow and sun illumination used as ground-truth for model training. The first row is the shadow illuminant and the second is the sun illuminant


## Examples
