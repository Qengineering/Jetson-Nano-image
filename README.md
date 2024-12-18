# Jetson Nano DNN image
![output image]( https://qengineering.eu/images/SDcard32GBJetson.webp )<br/>
## A Jetson Nano image with OpenCV, TensorFlow and Pytorch
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)<br/><br/>

------------

## Installation.

- Get a 32 GB (minimal) SD-card which will hold the image. 
- Download the `JetsonNano.img.xz` image (**7.2 GByte!**) from our [Sync](https://ln5.sync.com/dl/4bdb25370/xewd7xqz-6khtpcs2-w7zais3c-8uqi2rcj) site. 
- Flash the image on the SD card with the [Imager](https://www.raspberrypi.org/software/) or [balenaEtcher](https://www.balena.io/etcher/).
- According to [issue #17](https://github.com/Qengineering/Jetson-Nano-image/issues/17#) only flash the xz directly, not an unzipped img image.
- Insert the SD card in your Jetson Nano **4 GB RAM** and enjoy.
- Username: ***jetson***
- Password: ***jetson***
- JetsonNano.img.xz md5sum: 621F2E4E0B7775E5293E2186C96E91AA

### GDrive.
In some parts of the world, getting a good solid connection to Sync is difficult. That is why we've also provided a copy on [Google Drive](https://drive.google.com/file/d/1xSKJQX2uuLI-ewShU8LP8FROC6ozyiwo/view?usp=sharing). However, Google Drive limits the number of daily downloads. Please be considerate and use Google Drive only if necessary.

------------

## Tips.

* If you are in need of extra space, you can delete the opencv and the opencv_contrib folder from the SD card. They are no longer needed since all libraries are placed in the /usr/ directory.
* Use a tool like [GParted](https://gparted.org/) `sudo apt-get install gparted` to expand the image to larger SD cards. We recommend a minimum of 64 GB. Deep learning simply requires a lot of space.<br/><br/>

------------

## Pre-installed frameworks.

- [JetPack](https://developer.nvidia.com/embedded/jetpack) 4.6.0
- [OpenCV](https://qengineering.eu/deep-learning-with-opencv-on-raspberry-pi-4.html) 4.5.3
- [TensorFLow](https://qengineering.eu/install-tensorflow-2.4.0-on-raspberry-64-os.html) 2.4.1
- [TensorFlow Addons](https://qengineering.eu/install-tensorflow-2.4.0-on-raspberry-64-os.html) 0.13.0-dev
- [Pytorch](https://qengineering.eu/install-pytorch-on-raspberry-pi-4.html) 1.8.1
- [TorchVision](https://qengineering.eu/install-pytorch-on-raspberry-pi-4.html) 0.9.1
- [LibTorch](https://qengineering.eu/install-pytorch-on-raspberry-pi-4.html) 1.8.1 
- [ncnn](https://qengineering.eu/install-ncnn-on-jetson-nano.html) 20210720
- [MNN](https://qengineering.eu/install-mnn-on-jetson-nano.html) 1.2.1
- [JTOP](https://github.com/rbonghi/jetson_stats) 3.1.1 
- [TeamViewer aarch64](https://www.teamviewer.com/en/download/linux/) 15.24.5

Tensorflow 2.5 and above require CUDA 11. CUDA version 11 cannot be installed on a Jetson Nano due to incompatibility between the GPU and low-level software at this time, hence Tensorflow 2.4.1. Only when NVIDIA releases a JetPack with CUDA 11 will we be able to upgrade Tensorflow.

![output image]( https://qengineering.eu/images/Software_Jetson.png )<br/><br/>
![output image]( https://qengineering.eu/images/JTOP_jetson.png )

------------

## OpenCV + TensorFlow.

Importing both TensorFlow and OpenCV in Python can throw the error: _cannot allocate memory in static TLS block_.<br/>
This behaviour only occurs on an aarch64 system and is caused by the OpenMP memory requirements not being met.<br/>
For more information, see GitHub ticket [#14884](https://github.com/opencv/opencv/issues/14884).<br/>

![output image](https://qengineering.eu/images/SwapImportOpenCVJetson.webp)

There are a few solutions. The easiest is to import OpenCV at the beginning, as shown above.<br/>
The other is disabling OpenMP by setting the -DBUILD_OPENMP and -DWITH_OPENMP flags OFF.<br/>
Where possible, OpenCV will now use the default pthread or the TBB engine for parallelization.<br/>
We don't recommend it. Not all OpenCV algorithms automatically switch to pthread.<br/>
Our advice is to import OpenCV into Python first before anything else.<br/>

------------

[![paypal](https://qengineering.eu/images/TipJarSmall4.png)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=CPZTM5BB3FCYL) 


