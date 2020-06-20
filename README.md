# tams_camera_config
A place to put tams camera calibration files

## Kinect2 calibration
- Instruction: https://github.com/code-iai/iai_kinect2/tree/master/kinect2_calibration
- Start ros core: `roscore`
- Start camera with a low fps: `rosrun kinect2_bridge kinect2_bridge _fps_limit:=2`
- Creat a directory for calibration data files: `mkdir ~/kinect_cal_data; cd ~/kinect_cal_data`
- Record images for the color camera: `rosrun kinect2_calibration kinect2_calibration chess6x8x0.05 record color`
- Calibrate the intrinsics for color camera: `rosrun kinect2_calibration kinect2_calibration chess6x8x0.05 calibrate color`
- Record images for the ir camera: `rosrun kinect2_calibration kinect2_calibration chess6x8x0.05 record ir`
- Calibrate the intrinsics of the ir camera: `rosrun kinect2_calibration kinect2_calibration chess6x8x0.05 calibrate ir`
- Record images on both cameras synchronized: `rosrun kinect2_calibration kinect2_calibration chess6x8x0.05 record sync`
- Calibrate the extrinsics: `rosrun kinect2_calibration kinect2_calibration chess6x8x0.05 calibrate sync`
- Calibrate the depth measurements: `rosrun kinect2_calibration kinect2_calibration chess6x8x0.05 calibrate depth`
- Find out the serial number of your kinect2 by looking at the first lines printed out by the kinect2_bridge. The line looks like this: `device serial: 012526541941`


## USB cameras
For USB cameras with libuvc write access has to be granted. Temporarily this can be done with:
	`sudo chmod o+w /dev/bus/usb/00X/0XX` (temporarily)
or by adding a udev rule. If an entry for your camera already exists, copy the file from `udev_rules/99-uvc.rules` to `/etc/udev/rules.d/99-uvc.rules`
