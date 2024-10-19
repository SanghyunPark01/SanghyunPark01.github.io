---
title:  "Ubuntu에 ROS2 설치하기"
excerpt: "Ubuntu 22.04에 ROS2 Iron 설치하기"

categories:
  - Development/Robotics
tags:
  - [Ubuntu, ROS, ROS2]

toc: true
toc_sticky: true
use_math: true

date: 2024-01-20
last_modified_at: 2024-01-20
---  
ROS2 Install  
Ubuntu ROS2 Install  
ROS2 설치  
Ubuntu ROS2 설치  

# Ubuntu 22.04에 ROS2 설치하기  
현재 Ubuntu 22.04버전에서 ROS2 Humble과 Iron을 지원한다.  
현재 최신 버전인 Iron을 설치할 것이다.  

## 설정  
터미널에 입력한다.  
```bash
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
```
터미널에 아래 명령어를 입력하면 사진과 같이 나타난다.  
```bash
locale
```
<p align="center"><img src="/Post_img/Development/Robotics/ros_install0.png" width="50%" height="100%"></p> 

아래 명령어를 통해 시스템에 추가한다.  
```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

```bash
sudo apt update && sudo apt install ros-dev-tools
sudo apt update
sudo apt upgrade
```

## 설치  
아래 명령어를 입력해 바로 설치가 가능하다.  
```bash
sudo apt install ros-iron-desktop
```  
아래 명령어를 입력해 `.bashrc`에 추가하고 업데이트 한다.  
```bash
echo "source /opt/ros/iron/setup.bash" >> ~/.bashrc
source ~/.bashrc
```  

## 실행
ROS2는 ROS와 달리 `roscore`가 없이 실행된다.  
간단히 동작을 확인하기 위해 2개의 터미널을 준비해준다.  

```bash
ros2 run demo_nodes_py listener
```

```bash
ros2 run demo_nodes_cpp talker
```  

각각 위 명령어를 입력해주고 아래와 같이 데이터 송/수신이 된다면, 잘 동작하는 것이다.  

<p align="center"><img src="/Post_img/Development/Robotics/ros_install1.png" width="100%" height="100%"></p> 

---
**Reference**  
[0] [ROS2 Documentation](https://docs.ros.org/en/iron/Installation/Ubuntu-Install-Debians.html)