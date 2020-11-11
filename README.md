# NDCV-Landmark-detection-and-tracking-SLAM

In this project, we'll implement SLAM (Simultaneous Localization and Mapping) for a 2 dimensional world!
We’ll combine what you know about robot sensor measurements and movement to create a map of an environment from only sensor 
and motion data gathered by a robot, over time. 
SLAM gives you a way to track the location of a robot in the world in real-time and identify the locations of landmarks 
such as buildings, trees, rocks, and other world features. 

## Omega and Xi Constraints
Graph SLAM is done by creating and modifying the constraint matrix and vector: **omega** and **xi**. 
In this project, we'll try to implementing constraints for a 2D world. 
We are referring to robot poses as Px, Py and landmark positions as Lx, Ly, 
and one way to approach this challenge is to add both x and y locations in the constraint matrices.

The solution to these matrices (which holds all values for robot poses P and landmark locations L) is the vector, `mu`, 
which can be computed at the end of the construction of omega and xi as the inverse of omega times xi:  **𝜇=Ω−1𝜉**

<p align="center"> 
<img src=https://github.com/Oktafsurya/NDCV-Landmark-detection-and-tracking-SLAM/blob/master/images/constraints2D.png height="400" width="480">
</p>

## SLAM
Using the setting like this:
```
num_landmarks      = 5        # number of landmarks
N                  = 20       # time steps
world_size         = 100.0    # size of world (square)

```
the omega matrix and Xi vector after performing SLAM is look like:
<p align="center"> 
<img src=https://github.com/Oktafsurya/NDCV-Landmark-detection-and-tracking-SLAM/blob/master/images/omega_slam.png height="700" width="780"> <img src=https://github.com/Oktafsurya/NDCV-Landmark-detection-and-tracking-SLAM/blob/master/images/xi_slam.png>
</p>

The robot pose and landmarks location on 2D map after SLAM:
```
Last pose:  (59.168884020123784, 62.02768164132489)
landmark:  [(35.87862717049849, 28.641743499989595), (76.6536270080191, 77.70413251460167), 
(80.88935106162532, 30.516100398410625), (53.705221683595894, 6.057525837559687), (62.87493516440121, 93.38631967711054)]
```
<p align="center"> 
<img src=https://github.com/Oktafsurya/NDCV-Landmark-detection-and-tracking-SLAM/blob/master/images/robot_landmark_final.png height="800" width="800">
</p>

The groundtruth data for that result is:
```
Robot: [x=60.95318 y=63.37249]
Landmarks:  [[37, 30], [78, 78], [81, 30], [54, 6], [64, 93]]
```
So, the error between slam result and groundtruth is:
```
MSE Landmarks Pos = 0.678641560885
MSE Robot pos = 2.49611083268
```
