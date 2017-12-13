# Windows Caffe

**This is an experimental, fixed some bugs from https://github.com/runhang/caffe-ssd-windows
and I add following item into project 
1. add opencv imshow windows to ssd_dectect
2. add MobileNet to detector

## Windows Setup

### Requirements

 - Visual Studio 2013 or 2015
 - [CMake](https://cmake.org/) 3.4 or higher (Visual Studio and [Ninja](https://ninja-build.org/) generators are supported)
 - Anaconda 

### Optional Dependencies

 - Python for the pycaffe interface. Anaconda Python 2.7 or 3.5 x64 (or Miniconda)
 - Matlab for the matcaffe interface.
 - CUDA 7.5 or 8.0 (use CUDA 8 if using Visual Studio 2015)
 - cuDNN v5

 We assume that `cmake.exe` and `python.exe` are on your `PATH`.

### Configuring and Building Caffe (CPU Only)
Create a python2.7 env from Anaconda and activate
```
> cd $caffe_root/script
> build_win.cmd
> cd build
> Caffe.sln
> select release
> build solutions
> build install
```
Now you can see ssd_detect.exe at $caffe_root/script/install/bin

### For Visual 2013
Edit build_win.cmd and set varible MSVC_VERSION=12

### For GPU

config build_wind.cmd and cmakelist and set CPU_Only flag to 0

### Running Caffe (CPU Only)
download pre-train model and voc0712 lmdb from [model](https://drive.google.com/file/d/1Wwx6616HRk2eNI7eDZsr3Ijuv2dokCks/view?usp=sharing)
unzip into install/bin
```
> cd $caffe_root/script/install/bin
> dectect.cmd
```
If load success , you can see the image window like this [result](https://drive.google.com/file/d/15dmQVO0i0wOD28wXQOrLhjg7-UvS7K9O/view?usp=sharing)

### Optional detector

Set detect.cmd varible "detector" to switch VGG or MobileNet

### Trainning Caffe (CPU Only)
```
> cd $caffe_root/script/install/bin
> caffe train -solver models\VGGNet\VOC0712\SSD_300x300\solver.prototxt --weights=models\VGGNet\VGG_ILSVRC_16_layers_fc_reduced.caffemodel
```

