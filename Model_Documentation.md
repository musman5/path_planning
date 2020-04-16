# Refelection:
I followed the project Q&A video to start. I used spline library for interpolation of x,y points. 
The car trajectory is predicted by setting three targets points in future. Two previous points are also used to get previous path the car was following and the angle at which the car was moving. Spline will calculate the trajectory points based on the values for 30 meters of road ahead. Trajectory contains fifty points and remaining points, on which the car has not traveled yet,  will be used in next path calucation when predicting new trajectory.

The core functions of my implementation are defined as below:

# Lane and Car Detection
First we detect car lane from sensor fusion data. We need to determine car position so that our car can take appropriate action. 
- Detect if any car is infront of us
- Detect if any car is on left side lane
- Detect if any is on right side lane

If there is no car infront of us, we can move forward with maximum accerlation allowed. If there is car infront of us and there is no safe lane change possible, we need to decrease speed. The safety limit is set as 30 meters for the car. It means if there is any car within 30 meters of our car either in neighbouring lane, where we are trying to change lane, it is considered not safe. We will discard lane change action. 

# Take Action Based on Detection

If there is a car ahead of us then follow these actions

  1. No car present on the left lane, change lane to left lane
  2. Car present on left lane then check right lane
  3. No car present on right lane, change to right lane
  4. Car present on left and right lane, then decrease speed
  5. If cars present on left, right and ahead of us, slow down.
  6. If lane change is done, then come back to center lane after lane change
 
## Note:
Inline comments for explanation are also added in code.