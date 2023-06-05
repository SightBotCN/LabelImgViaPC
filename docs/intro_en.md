# Usage

## Introduction

LabelImgViaPC is a tool for labeling images using lidar point cloud. The main principle is to label three-dimensional objects (cubes) on the point cloud, and obtain the target information on the images through the mapping relationship between the point cloud and the images. This software supports adjusting 3D targets through perspective views. Due to the frequent mismatch between point clouds and images, this software supports adjusting the mapping points on the image (3D targets remain unchanged)


## Config

To simplify the software interface, all configuration is in the config.ini file， see bin/config.ini

About the camera model, we use the omnidirectional camera CMei model (refer to the Single View Point Omnidirectional Camera Calibration from Planar Grids) 

as the omnidirectional model has better universality and support for regular camera, wide-angle camera, and fisheye camera

About camera intrinsic parameter calibration, it is recommended that one camera corresponds to one set of intrinsic parameters

as even the same camera may have errors in internal parameter consistency due to manufacturing processes


## Label

### Label Steps：

Please pay attention to the license status in the upper left corner before labeling. If it is invalid, the label file cannot be saved

1.  Double click in the File List box to select a PCD file

2.  Click on the point cloud view with the left and right mouse buttons, and use the scroll wheel to adjust the viewing angle

3.  Enter the new mode with the w key on the keyboard, click the left mouse button in the point cloud view, move the mouse and click the left mouse button again to obtain the complete target

4.  The "Current Class" dropdown box can be used to set the target type

5.  Adjust the 3D target pose through the keyboard, commonly used (q, w, e, a, s, d, z, x), not commonly used (c, v, b, n), and not commonly used shortcut keys to adjust pitch and roll (configuration. ini ->z_rotation_only needs to be set to false)

3D targets can also be adjusted through point cloud projection images (top view, front view, side view)

6.  Adjust the 2D projection of the 3D target on the image. You can select one or more items in the Labels tab "P0~P7" and adjust the position through the keyboard (w, a, s, d). Manually adjusting the box of the 2D target will change the target color. If you need to delete the manual adjustment result, use the delete key to delete it; Please note that after manually adjusting the 2D target, the 3D target will no longer automatically project to the corresponding image in 2D

7.  Set whether the target is visible. Double click the left button on the small image to switch the visible status of the two-dimensional target

8.  Save, double clicking on the File List box will automatically save the PCD file when switching files; You can also save using the Ctrl+s shortcut key. When saving with the shortcut key, do not select any target. Double clicking on a non target location in the point cloud or clicking the Deselect button can deselect it


## Label File

A PCD file corresponds to a JSON tag file, which contains the following fields:

'folder': PCD folder

'filename': PCD file name

'path': PCD full path

'Objects': 3D targets

'name': Target type

'centroid': 3D target center

'dimensions': 3D target length, width, height

'rotations': 3D target rotation angle, [0, 360)

'visible': whether the mapping target from the 3D target to each image is visible

'img_bboxes': Mapping targets from 3D targets to various images. If left blank, it is automatically mapped, and if there is a value, it is manually adjusted



## FAQ

1.  The shortcut button is not responding

The main logic of software shortcut keys is to first activate the relevant window with a mouse click, and then use the shortcut key operation, which can reduce the number of shortcut keys


