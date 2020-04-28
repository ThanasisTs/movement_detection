# A human movement detection ROS package

Given an input of 3D human joint positions (e.g. as recorded by [openpose_utils](https://github.com/thanasists/openpose_utils), this package offers the following functionalities:

* Detection of the beginning and end of the human movement.
* Check for invalid positions or movements.

Furthermore, it is possible to remove points which correspond to the rest state from the beginning and the end of the movement and to smooth the recorded motion(check [this repo](https://github.com/thanasists/trajectory_point_process)).

## Functionality
* It accepts 3D cartesian positions points expressed in the `base_link` frame in the form of `Keypoint3d_list` ROS message (check [this](https://github.com/ThanasisTs/openpose_utils/tree/master/keypoint_3d_matching_msgs) for the definition of the custom message)
* To detect the beginning and end of the movement, the standard deviation of N cosnecutive points is checked.
* Invalid points (outliers), whose distance from previous points is bigger than a threshold are removed. If more than XX consecutive points satisfy the condition the movement is considered invalid.

## Launch files
To check the functionality realtime:
* Launch `roslaunch openpose_utils_launch openpose_sole.launch sim:=false live_camera:=true manos_tf:=true` (check the [openpose_utils](https://github.com/ThanasisTs/openpose_utils) repo).

* Launch the movement_detection tool: `roslaunch movement_detection movement_detection.launch`. (NOTEWARNING: the participant must remain for a few seconds in rest at the beginning and end of the movement).

The arguments of the launch file are the following:
* `smooth`: True if you want to smooth the trajectory (default FALSE)
* `filter`: True if you want to remove redundant points (default FALSE)
