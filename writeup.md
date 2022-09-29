# Writeup: Track 3D-Objects Over Time

This is the final project of sensor fusion and object tracking. There are four main steps: Step 1: Implement an extended Kalman filter. Step 2: Implement track management including track state and track score, track initialization and deletion. Step 3: Implement single nearest neighbour data association and gating. Step 4: Apply sensor fusion by implementing the nonlinear camera measurement model and a sensor visibility check.

RMSE is used to quantify the performance of the object detection and tracking performance. The plots of RMSE and tracking video are in /student/Figures_Videos

### 1. Write a short recap of the four tracking steps and what you implemented there (filter, track management, association, camera fusion). Which results did you achieve? Which part of the project was most difficult for you to complete, and why?

## Step 1: Extended Kalman Filter

EKF is implemented and applied to a simple single-target scenario with lidar only. The constant velocity model is used to develop the system matrix and process matrix F and process nosie Q. A linear measurement model is used for lidar. A nonlinear measurement model is used for camera. The following figures are tracking and RMSE measurement RMSE results. 

![image](student/Figures_Videos/EKF1.png)
![image](student/Figures_Videos/RMSE_Measurement.png)



### 2. Do you see any benefits in camera-lidar fusion compared to lidar-only tracking (in theory and in your concrete results)? 


### 3. Which challenges will a sensor fusion system face in real-life scenarios? Did you see any of these challenges in the project?


### 4. Can you think of ways to improve your tracking results in the future?

