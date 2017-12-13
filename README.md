# Windows Caffe

**This is an experimental, fixed some bugs from https://github.com/eric612/caffe-ssd-windows 
and I add below item into project 
1. add opencv imshow windows to ssd_dectect
2. add MobileNet to detector

**Update**: this branch is not actively maintained. Please checkout [this](https://github.com/BVLC/caffe/tree/windows) for more active Windows support.
If you want to read the Chines version of READMER, please click on it please click [README-Chinese](https://github.com/runhang/caffe-ssd/blob/master/README-Chinese.md)


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
>cd caffe_ssd_windows root/script
>build_win.cmd
>cd build
>Caffe.sln
>select release
>build solutions
>build install

### For GPU
config build_wind.cmd and cmakelist CPU_Only flag to 0

Now you can see ssd_detect.ext at install/bin

### Running Caffe (CPU Only)
download pre-train model and voc0712 lmdb from [model](https://drive.google.com/file/d/1Wwx6616HRk2eNI7eDZsr3Ijuv2dokCks/view?usp=sharing)
unzip into install/bin

>cd install/bin
>dectect.cmd
If load sucess , you can see the image window like this [result](https://drive.google.com/file/d/15dmQVO0i0wOD28wXQOrLhjg7-UvS7K9O/view?usp=sharing)

### Optional detector
Edit detect.cmd varible "detector" to switch type (VGG or MobileNet)

### Trainning Caffe (CPU Only)

>cd install/bin
>train.cmd


