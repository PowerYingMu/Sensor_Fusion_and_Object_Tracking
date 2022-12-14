# Writeup: Track 3D-Objects Over Time

This is the final project of sensor fusion and object tracking. There are four main steps: Step 1: Implement an extended Kalman filter. Step 2: Implement track management including track state and track score, track initialization and deletion. Step 3: Implement single nearest neighbour data association and gating. Step 4: Apply sensor fusion by implementing the nonlinear camera measurement model and a sensor visibility check.

RMSE is used to quantify the performance of the object detection and tracking performance. The plots of RMSE and tracking video are in /student/Figures_Videos

### 1. Write a short recap of the four tracking steps and what you implemented there (filter, track management, association, camera fusion). Which results did you achieve? Which part of the project was most difficult for you to complete, and why?

## Step 1: Extended Kalman Filter

EKF is implemented and applied to a simple single-target scenario with lidar only. The constant velocity model is used to develop the system matrix and process matrix F and process nosie Q. EKF is applied to a simple single-target scenario with lidar only. The following figures are tracking and RMSE measurement RMSE results. 

![image](student/Figures_Videos/EKF1.png)
![image](student/Figures_Videos/RMSE_Measurement.png)

## Step 2: Track Management
The track management is implemented, which includings initializing and deleting the tracks and setting a track state and a track score for the track object. The track state is initialized with 'initialized' and the score with 1./params.window. The track scores ire decreased for the unassigned tracks. The track is deleted if the score is too low or P is too big. After implementing the track management, a new track is initialized automatically where unassigned measurements occur, the true track is confirmed quickly, and the track is deleted after it has vanished from the visible range. The following plot is the RMSE results.

![image](student/Figures_Videos/RMSE_TrackManagement.png)

## Step 3: Data Association
A single nearest neighbor data association is implemented to associate measurements to tracks, which is based on minimizing Mahalanobis distance of detected objects to tracks. Gating is used to check if a measurement falls inside a track's gate. Multiple tracks are updated with multiple measurements. Each measurement is used at most once and each track is updated at most once. The following plot is RMSE results. The 

![image](student/Figures_Videos/RMSE_Association.png)

## Step 4: Association
A nonlinear camera measurement model and a linear lidar model is implemented.A method that checks whether an object can be seen by the camera or is outside the field of view is implemented. There are no confirmed ghosts or lost tracks. The following figure is the RMSE results

![image](student/Figures_Videos/RMSE_Fusion.png)

https://user-images.githubusercontent.com/13784216/193142571-57a4ccff-5f9e-43b3-8813-389cda636d83.mp4

The data association is the most challenge part during the implementation. When there are many measurements and detected objects, the situation can become very complex. 

### 2. Do you see any benefits in camera-lidar fusion compared to lidar-only tracking (in theory and in your concrete results)? 

The 3D LiDAR sensor works well for measuring spatial information and providing accurate distance inforamtion, and it can work in both daytime and nighttime. However, LiDAR can not provide the inforamtion like object color, textture information, etc. The camera is a perfect sensor to obtaion the information like color and texture inforamtion, which is needed for traffic signal recognitions. By combining the 3D LiDAR and camera sensors, we can take the advantages of the both sensors and overcome the weaknesses. The fused information is also more accurate than single sensor detection. 

### 3. Which challenges will a sensor fusion system face in real-life scenarios? Did you see any of these challenges in the project?
As stated in the challenge section, in the real-world scenarios, precisely handle all measurements and tracks will be challenging. Careful selection of the gating thresholld is critical.

In the real-world, weahter conditions will be another challenges to sensor fusion, like extreme weathers (heaving snow/rain).


### 4. Can you think of ways to improve your tracking results in the future?

1. Use nonlinear motion model
2. Adding more sensors, like surrounding view cameras, which can be used for 360 fusion to capture all targets near the car.

