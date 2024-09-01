---
title:  "VectorNav VN-100 IMU 사용해보기"
excerpt: "ROS에서 VectorNav VN-100 IMU 사용해보기"

categories:
  - Development/Robotics
tags:
  - [VectorNav, IMU, ROS]

toc: true
toc_sticky: true
use_math: true

date: 2024-08-30
last_modified_at: 2024-08-30
---  
# 0.VectorNav IMU
VectorNav사의 IMU중에 [VN-100](https://www.vectornav.com/products/detail/vn-100?gad_source=1&gclid=EAIaIQobChMIv6jQvoqiiAMVrS57Bx2dER97EAAYASAAEgL17fD_BwE)모델을 돌려보는 방법을 설명할 것이다.

# 1. Build
[https://github.com/dawonn/vectornav](https://github.com/dawonn/vectornav) 이 링크에 해당하는 ros package를 clone 하고 build한다.
```bash
$ cd (your_ros_workspace)/src
$ git clone https://github.com/dawonn/vectornav.git
$ cd ..
$ catkin_make
```

# 2. Run
VectorNav의 ROS package안에 SDK가 포함되어 있어 SDK를 따로 설치 할 필요는 없다.
## 1) 파라미터 수정
빌드가 잘 되었다면 실행시키기 전에 파라미터를 수정해야 한다. `params/vn100.yaml`에 들어가서 먼저 포트를 수정해야 한다. 그 다음 아래 파라미터들을 수정해준다.  
- `serial_baud`를 `921600`으로 수정한다.
- `async_output_rate`를 `200`으로 한다.  

수정을 다 하였으면 `vectornav.launch`를 수정하여야 한다.  
- `vn200`을 `vn100`으로 수정해준다.

## 2) 실행 및 디버깅
IMU를 연결하고 아래 명령어를 통해 실행할 수 있다.  
```bash
$ roslaunch vectornav vectornav.launch
```
만약, 아래와 같은 오류가 발생한다면, 포트 권한 문제이다.  
```bash
terminate called after throwing an instance of 'vn::invalid_operation'
  what():  invalid operation
```
권한을 설정해주면 문제는 해결된다.  
```bash
$ sudo chmod a+rw /dev/ttyUSB0
```
하지만, 재부팅을 하면 다시 권한을 설정해줘야 하는 문제가 생긴다. 따라서, 아래 파일에 명령어를 입력해준다.  
```bash
$ sudo gedit /etc/rc.local
```
exit 0 위에, 아래문구 입력 후 저장
```bash
chmod a+rw /dev/ttyUSB0
```
IMU를 동작시켜서 Rviz로 보면 아래와 같다.  

<p align="center">
    <img src="/Post_img/Development/Robotics/2024-08-30-VectorNav_img/01.png" width="100%" height="100%">
</p> 

