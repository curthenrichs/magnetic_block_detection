# magnetic_block_detection
This system was developed to detect and locate wooden magnetic blocks within a
region bounded by at least three Alvar AR tags.

Composed of two packages:
- [block_detector](./block_detector/README.md): Block detection algorithm
- [ar_track_alvar](./ar_track_alvar/README.md): Forked (and modified) Alvar AR package

## System
The Alvar subsystem is a modified verison of the official package. The only change made is that this version also outputs the 2D image coordinates of the markers on a separate topic. This, in turn, allows for our code to produce a 2D to 3D mapping with the only assumption being the markers are placed on a flat surface. This version of the package should be drop-in compatible with other uses. Please refer to the package's [README](./ar_track_alvar/README.md) for more details.

Our package (block_detector) provides the 2D to 3D mapping code, simple computer vision block detector, and calibration code. We also have an experimental multi-camera pipeline (though it is still in development). Please refer to the package's [README](./block_detector/README.md) for more details.

Note, block_detector already has the following python modules within the package:
- [christophhagen/averaging-quaternions](https://github.com/christophhagen/averaging-quaternions) ~ Please see the [README](./block_detector/src/averaging_quaternions/README.md).

## Install
Make sure to install the necessary camera ROS drivers. For instance if using a USB webcam then install [usb_cam](http://wiki.ros.org/usb_cam).

Then install the following python modules:
- [scikit-learn](https://pypi.org/project/scikit-learn/)
  - [numpy](https://pypi.org/project/numpy/)
  - [matplotlib](https://pypi.org/project/matplotlib/)
- [cv2](https://pypi.org/project/opencv-python/)
- [shapely](https://pypi.org/project/Shapely/)
- [yaml](https://pypi.org/project/PyYAML/)

## Run
Enter following into terminal:

```
roslaunch block_detector main.launch video_src:=<video-device e.g., /dev/video0>
```
