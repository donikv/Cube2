# Cube2
Cube2: A large multi-illuminant dataset

The whole dataset can be found [here](https://fersharepoint.add_link).

## Description

Cube2 is a large multi illuminant dataset composed of XXX outdoor and indoor images. 
These images were collected using 3 different DSLR camera models and in different times during the day and in different times of the year. 
Images were mostly collected in Croatia, and feature mostly urban scenes. 
Indoor images were collected and annotated using a variation of method for dataset collection described in the paper by [Beigpour et al.](http://www.cat.uab.cat/Public/Publications/2014/BRV2014/TIP_2014.pdf)
Outdoor images were annotated manually. In addition to the spatial map of illuminants for each image, the groundtruth color of the illuminants is provided.
The color of the illuminants was retrieved from the SpyderCube calibration objects that were placed in each scene. 

|Camera | N. images|
|-------|----------|
|Canon 550D|  X    |
|Canon EOS 5D| X   |
|Nikon D7000|  X   |

## Usage

Images in the dataset are divided into folders.
Folder indexing starts at 1
Each image folder contains the foloving files:

- img.png - minimaly proccessed image, only simply debayering was performed. 
  - To properly use this file the blacklevel (2048) needs to be reduced and all oversaturated pixels (pixel value greater or even to _max_image_value_ - 2) need to be set to 0
- img.CR2/.NEF - the raw image provided by the camera
- gt_mask.png - segmentation max where 1 represents pixels in the shadows and 2 represents pixles under direct sunlight
- cubes.txt - contains coordinate of rectangels that cover the SpyderCubes *(x0,y0,x1,y1)* that need to be set to 0 so the model doesn't overfit on the cube
- sun.txt - contains the values read from the cube in the direct sunlight. Format: left gray, right gray, left white, right white face
- shadow.txt - constains the values read from the cubes in the shadows. Format the same as in sun.txt. When there are more cubes 
                   they are stored from the most right cube in the image to the most left. If the cubes are on the same x coordinate the top one is saved first.
- face_endpoints.txt - the pixel coordinates used to extract values from the spydercubes. Same format as for shadow.txt only the final four lines are for the cube in the sunlight. Each line has 6 values which represent the three triangle endpoints as: *(x0 y0 x1 y1 x2 y2)*
- gt.txt - the shadow and sun illumination used as groundtruth for model training. The first row is the shadow illuminatant and the second is the sun illuminant

The values in sun.txt, shadow.txt, and gt.txt are l2 normalized.


## Examples
