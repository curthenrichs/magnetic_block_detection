# block_detector
Provides the 2D to 3D mapping code, simple computer vision block detector, and calibration code.

##  Overview


## Calibrate


## Install
Make sure to install the necessary camera ROS drivers. For instance if using a USB webcam then install [usb_cam](http://wiki.ros.org/usb_cam).

Then install the following python modules:
- [christophhagen/averaging-quaternions](https://github.com/christophhagen/averaging-quaternions)
- [scikit-learn](https://pypi.org/project/scikit-learn/)
  - [numpy](https://pypi.org/project/numpy/)
  - [matplotlib](https://pypi.org/project/matplotlib/)
- [cv2](https://pypi.org/project/opencv-python/
- [shapely](https://pypi.org/project/Shapely/)
- [yaml](https://pypi.org/project/PyYAML/)

## Run
Enter following into terminal:

```
roslaunch block_detector main.launch video_src:=<video-device e.g., /dev/video0>
```
