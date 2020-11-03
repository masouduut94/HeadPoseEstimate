# HeadPoseEstimate
## Introduce
This is a head pose estimation system based on 3d facial landmarks. Please realize it's not the most advanced method in this field. Util I created this repository, there have been some end-to-end solutions.

## Usage
<!-- TODO -->

## How does it work
### 1. Get the 3d facial landmarks
Thanks for 1adrianb's [excellent work](https://github.com/1adrianb/face-alignment), we can easily get the 3d facial landmarks.
### 2. Determine direction of face
The horizontal direction `hd` and vertical direction `vd` of face can be determined by PCA. Let's notate facial orientation with `fd`, then `fd = hd x vd`. Note: `x` is cross products.  
Here is an example. The origin image:
![origin image](figures/origin_frame.png)

The following image shows 68 landmarks.  
Red axis: X  
Green axis: Y  
Blue axis: Z  
The three yellow arrows are `hd`, `vd` and `fd`.
![landmarks](figures/landmarks.png)
### 3. Estimate rotation
Normalize `hd`, `vd` and `fd`, make them as unit vectors. 
Rotation transform from  
   | 1  0  0 |  
   | 0  1  0 |  
   | 0  0  1 |  
   to  
   | hd |  
   | vd |  
   | fd |  
can be estimated with Kabsch algorithm.
## Get head pose directly from a network 
I highly recommend you to take a look at [Hopenet](https://github.com/natanielruiz/deep-head-pose).
