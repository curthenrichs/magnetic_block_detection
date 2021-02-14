# block_detector
Provides the 2D to 3D mapping code, simple computer vision block detector, and calibration code.

## Nodes

General ROS nodes:

- block_pose ~ Converts from 2D BlockPose coordinates to 3D BlockPose coordinates.
- block_vision ~ Provides block_detector with ability to capture blocks from a vision.
- data_sampler ~ Prints training data format for the vision model based on valid blocks.
- plot_2d_points ~ Plot 2D AR points found to image.
- robot_camera_align ~ Uses an AR tag on the robot gripper to calibrate relationship between camera, base_link, and end_effector TFs.
- static_camera ~ Provides a static image source from file provided.

Multi-camera ROS nodes:

- tf_bridge ~ TF Bridge maps from internal tf space for vision pipeline into the global tf tree.
- two_camerea_agreement ~ Generates the final environment sense from multiple cameras.

## Install
Make sure to install the necessary camera ROS drivers. For instance if using a USB webcam then install [usb_cam](http://wiki.ros.org/usb_cam).

Then install the following python modules:
- [scikit-learn](https://pypi.org/project/scikit-learn/)
  - [numpy](https://pypi.org/project/numpy/)
  - [matplotlib](https://pypi.org/project/matplotlib/)
- [cv2](https://pypi.org/project/opencv-python/)
- [shapely](https://pypi.org/project/Shapely/)
- [yaml](https://pypi.org/project/PyYAML/)

Note, block_detector already has the following python modules within the package:
- [christophhagen/averaging-quaternions](https://github.com/christophhagen/averaging-quaternions) ~ Please see the [README](./block_detector/src/averaging_quaternions/README.md).

## Run
Enter following into terminal:

```
roslaunch block_detector main.launch video_src:=<video-device e.g., /dev/video0>
```

## Calibrate
To calibrate, you will need to move the robot's end-effector into the camera's field of view. The end-effector should have an AR tag attached (make note of which one for calibration). Then you can start the calibration procedure with the `robot_camera_align` node. This node will capture the current TFs of the robot and camera to work out the relationship using the AR marker. I recommend moving the robot slowly in the scene to get better averaging during this process. Once complete, the configuration file will be saved for future use.
