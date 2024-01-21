---
title:  "Ubuntu에 OpenCV 설치하기"
excerpt: "Ubuntu 22.04에 OpenCV 4.4.0 설치하기"

categories:
  - Ubuntu/Tips
tags:
  - [Ubuntu, OpenCV]

toc: true
toc_sticky: true
use_math: true

date: 2024-01-19
last_modified_at: 2024-01-19
---

# 기존 버전 확인
기존에 OpenCV를 설치하였다면 제거해 주고 진행한다.  
```bash
pkg-config --modversion opencv4
```
또는
```bash
pkg-config --modversion opencv
```
를 입력해 버전이 뜨면, 이미 설치 되어 있는 것이므로 제거해주고 설치를 진행해야한다.

# OpenCV 설치
## 패키지 설치
터미널에서,  
```bash
sudo apt-get update
sudo apt-get upgrade
```
를 진행한 후, 아래 명령어들을 하나씩 입력한다.  
```bash
sudo apt-get install build-essential cmake
sudo apt-get install pkg-config
sudo apt-get install libjpeg-dev libtiff5-dev libpng-dev
sudo apt-get install ffmpeg libavcodec-dev libavformat-dev libswscale-dev libxvidcore-dev libx264-dev libxine2-dev
sudo apt-get install libv4l-dev v4l-utils
sudo apt-get install libglx-dev
sudo apt-get install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
sudo apt-get install libgtk-3-dev
sudo apt-get install libgtk2.0-dev
sudo apt-get install libgtk3.0-cil-dev
sudo apt-get install mesa-utils libgl1-mesa-dri libgtkgl2.0-dev libgtkglext1-dev
sudo apt-get install libatlas-base-dev gfortran libeigen3-dev
sudo apt-get install python3-dev python3-numpy
```  
## OpenCV 빌드  
소스코드를 다운받아 압축해제 한다.  
```bash
wget -O opencv.zip https://github.com/opencv/opencv/archive/4.4.0.zip
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.4.0.zip
unzip opencv.zip
unzip opencv_contrib.zip
```  
그러면 아래와 같이 되어있을 것이다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_opencv1.png" width="100%" height="100%"></p>  

그 다음 아래 명령어를 통해 폴더 안으로 들어간다.  
```bash
cd opencv-4.4.0
```  
build폴더를 만들고 안에 들어간다.  
```bash
sudo mkdir bulid
cd bulid
```  
아래 명령어 전체를 터미널에 복사 붙여넣기를 통해, cmake를 해 Makefile을 만들 수 있다.  
```bash
cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D WITH_TBB=OFF \
-D WITH_IPP=OFF \
-D WITH_1394=OFF \
-D BUILD_WITH_DEBUG_INFO=OFF \
-D BUILD_DOCS=OFF \
-D INSTALL_C_EXAMPLES=ON \
-D INSTALL_PYTHON_EXAMPLES=ON \
-D BUILD_EXAMPLES=OFF \
-D BUILD_PACKAGE=OFF \
-D BUILD_TESTS=OFF \
-D BUILD_PERF_TESTS=OFF \
-D WITH_QT=OFF \
-D WITH_GTK=ON \
-D WITH_OPENGL=ON \
-D BUILD_opencv_python3=ON \
-D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-4.4.0/modules \
-D WITH_V4L=ON \
-D WITH_FFMPEG=ON \
-D WITH_XINE=ON \
-D OPENCV_ENABLE_NONFREE=ON \
-D BUILD_NEW_PYTHON_SUPPORT=ON \
-D OPENCV_SKIP_PYTHON_LOADER=ON \
-D OPENCV_GENERATE_PKGCONFIG=ON ../
```  
cmake가 다 되었으면 마지막에 아래 사진처럼 될 것이다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_opencv2.png" width="100%" height="100%"></p>  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_opencv3.png" width="100%" height="100%"></p>  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_opencv4.png" width="100%" height="100%"></p>  

잘 되었으면, 빌드한다.  
```bash
make -j$(nproc)
```  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_opencv5.png" width="100%" height="100%"></p>  

위 사진처럼 빌드가 잘 되면, 아래 명령어를 입력해 설치한다.
```bash
sudo make install
```  
설치가 다 되었으면, 아래 명령어를 입력한다.  
```bash
cat /etc/ld.so.conf.d/*
```  
이때, 아래 사진처럼 `/usr/local/lib`가 있어야 한다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_opencv6.png" width="100%" height="100%"></p>  

**만약 없다면**  
```bash
sudo sh -c 'echo '/usr/local/lib' > /etc/ld.so.conf.d/opencv.conf'
```  
를 입력한다. **위 사신처럼 있으면 안해도 됨.**  
  
지금까지 잘 되었으면 아래 명령어를 반드시 입력한다.  
```bash
sudo ldconfig
```  
  
설치가 끝났다. 아래 명령어를 입력해 버전이 잘 나오는지 확인한다.  
```bash
pkg-config --modversion opencv4
```  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_opencv7.png" width="100%" height="100%"></p>  

위 사진처럼 나온다면 잘 설치가 되었다는 것이다.
  
---

Reference  
[[0]OpenCV 버전 Release](https://opencv.org/releases/)  
[[1]OpenCV Github](https://github.com/opencv/opencv)  
[[2]OpenCV설치](https://velog.io/@minukiki/Ubuntu-20.04%EC%97%90-OpenCV-4.4.0-%EC%84%A4%EC%B9%98)
