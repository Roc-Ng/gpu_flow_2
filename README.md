An Amended version of gpu_flow, the orginial version is in: https://github.com/feichtenhofer/gpu_flow
GPU based optical flow extraction in OpenCV

====================
### Changes:
Move all features to options

### Features:
* OpenCV wrapper for Real-Time optical flow extraction on GPU
* Automatic directory handling using Qt
* Allows saving of optical flow to disk, 
** either with clipping large displacements 
** or by adaptively scaling the displacements to the radiometric resolution of the output image

### Dependencies
* [OpenCV 2.4] (http://opencv.org/downloads.html)
* [Qt 5.4] (https://www.qt.io/qt5-4/)
* [cmake] (https://cmake.org/)

### Installation
1. `mkdir -p build`
2. `cd build`
3. `cmake ..`
4. `make`

if meet some troubles, please refer to this `https://blog.csdn.net/windows_peng/article/details/80568114`. Hope to help you.
### Usage:
```
./compute_flow [OPTION]...
```

Available options:
* `start_video`: start with video number in `vid_path` directory structure [1]
* `gpuID`: use this GPU ID [0]
* `type`: use this flow method Brox = 0, TVL1 = 1 [1] 
* `skip`: the number of frames that are skipped between flow calcuation [1]
* `vid_path`: the input directory 
* `out_path`: the output directory 
* `is_out_jpeg`: whether to save the jpeg images [true]
* `MIN_SZ`: defines the smallest side of the frame for optical flow computation [256]
* `OUT_SZ`: defines the smallest side of the frame for saving as .jpeg 
* `clipFlow`:  defines whether to clip the optical flow larger than [-20 20] pixels and maps the interval [-20 20] to  [0 255] in grayscale image space. 		       If no clipping is performed the mapping to the image space is achieved by finding the frame-wise minimum and maximum displacement and 		       mapping to [0 255] via an adaptive scaling, where the scale factors are saved as a binary file to `out_path`.
* `resize_img`: whether to resize images [true]


### Example:
```
./compute_flow gpuID=1 type=1 vid_path=/media/admin/Dataset/Videos/ out_path=/media/admin/gpu_flow/out_path_test/ out_path_jpeg=/media/admin/gpu_flow/out_path_jpeg_test/ is_out_jpeg=false
```


