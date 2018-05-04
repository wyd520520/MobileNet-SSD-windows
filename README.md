# Windows Caffe

**This is an experimental, fixed some bugs from https://github.com/runhang/caffe-ssd-windows
and I add following items into project 
1. add opencv imshow 
2. add MobileNet 
3. Support MobileNetV2 (source from [MobileNetv2-SSDLite](https://github.com/chuanqi305/MobileNetv2-SSDLite) )

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
```

### For Visual 2013

Edit build_win.cmd and set varible MSVC_VERSION=12

### For GPU

config build_win.cmd and set CPU_Only flag to 0

### Running Caffe 

Download SSD_300x300 [deploy model](https://drive.google.com/file/d/0BzKzrI_SkD1_WVVTSmQxU0dVRzA/view) and save at 

$caffe_root\models\VGGNet\VOC0712\SSD_300x300\

Download deploy weights from original [web](https://github.com/chuanqi305/MobileNet-SSD) and save at 

$caffe_root\models\\MobileNet\

```
> cd $caffe_root/
> dectect.cmd
```

#### Python Usage

```
> cd $caffe_root
> python examples\ssd\test_ssd.py data\VOC0712\000166.jpg models\MobileNet\MobileNetSSD_deploy.prototxt models\MobileNet\MobileNetSSD_deploy.caffemodel
```

If load success , you can see the image window like this 

![alt tag](2017-12-13_141522.png)

### Optional detector

Set detect.cmd varible "detector" (0,1) to switch VGG or MobileNet

### Trainning Prepare

Download [lmdb](https://drive.google.com/open?id=19pBP1NwomDvm43xxgDaRuj_X4KubwuCZ)

Unzip into $caffe_root/ 

Please check the path exist "$caffe_root\examples\VOC0712\VOC0712_trainval_lmdb"

### Trainning VGG_SSD Caffe 

Download SSD_300x300 [pretrain weights](http://cs.unc.edu/~wliu/projects/ParseNet/VGG_ILSVRC_16_layers_fc_reduced.caffemodel) and save at

$caffe_root\models\VGGNet\

```
> cd $caffe_root/
> train.cmd
```

### Trainning MobilentSSD_V1  

Download pre-train weights from original [web](https://github.com/chuanqi305/MobileNet-SSD) and save at 

$caffe_root\models\\MobileNet\

```
> cd $caffe_root/
> train_mobilenet.cmd
```

### Trainning MobilnetSSD_V2
  
```
> cd $caffe_root/
> train_mobilenet_v2.cmd
```

#### Trainning own dataset and deploy MobilentSSD_V1

follow this [project](https://github.com/chuanqi305/MobileNet-SSD) step

### Video Demo

```
> cd $caffe_root/
> demo.cmd or demov2.cmd (MobilenetSSD_V2)
```

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/9REYv5H3WMw/0.jpg)](https://www.youtube.com/watch?v=9REYv5H3WMw)

### Webcam Demo

```
> cd $caffe_root/
> demo_webcam.cmd
```

#### Vehicle deploy model 

##### CLASS NAME

```
char* CLASSES2[6] = { "__background__","bicycle", "car", "motorbike", "person","cones" };
```
##### Model and Weights MobilnetSSD_V1

[weights](https://drive.google.com/open?id=1LbLSTPFSlHML5qAUYN-kt1bw2HxvvNWS)

[model](https://drive.google.com/open?id=1KOE5r-71FFWU0LZbpo9HMEUwM_RE1LHR)

##### Vehicle detection using MobilnetSSD_V2

```
> cd $caffe_root/
> demo.cmd or demov2_custom.cmd 
```

##### Demo Video MobilnetSSD_V1

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/jn6SOzT_wPA/0.jpg)](https://www.youtube.com/watch?v=jn6SOzT_wPA)

##### Demo Video MobilnetSSD_V2

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/oc3tXxOoSH4/0.jpg)](https://www.youtube.com/watch?v=oc3tXxOoSH4)

### See also

#### Labeling tool with MobileNet-SSD

[AutoLabelImg](https://github.com/eric612/AutoLabelImg)

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/PnFCTBvq3OI/0.jpg)](https://www.youtube.com/watch?v=PnFCTBvq3OI)

