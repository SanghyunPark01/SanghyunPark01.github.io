---
title:  "Ubuntu에 Nvidia Driver 설치하기"
excerpt: "Ubuntu 22.04에 Nvidia Graphic Driver 설치하기"

categories:
  - Ubuntu/Tips
tags:
  - [Ubuntu, CUDA, NVIDIA Driver]

toc: true
toc_sticky: true
use_math: true

date: 2024-01-14
last_modified_at: 2024-01-14
---

# Problem
우분투에서 NVIDIA Graphic Driver를 확인 하는 명령어인  
```bash
nvidia-smi
```  
를 입력하였을 때 제대로 나오지 않는다면, 아직 Driver가 설치되지 않은 것이다.  
아래 과정을 통해 NVIDIA Graphic Driver를 설치할 수 있다.  
**설치하기에 앞서, 내 컴퓨터에 GPU가 NVIDIA 것인지 확인!**  

# NVIDIA Driver 설치  
## A. 설치 가능 버전 확인하기
우선, 내 컴퓨터의 NVIDIA GPU가 달려있다면, 우분투를 설치 후에 GPU와 맞는 Driver버전을 확인해야 한다. 터미널에 아래 명령어를 입력해 확인한다.  
```bash
ubuntu-drivers devices
```
그러면 아래와 같이 나타날 것이다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_ndriver0.png" width="100%" height="100%"></p>  

보면, nvidia-driver-(version)이 있고, 이 뒤에 server또는 open이 붙어있는 것들이 있다. 여기서 recommended를 보면, 버전이 535인 것을 확인할 수 있다.  
버전을 확인하였으면, 그냥 설치할지 open을 설치할지 server를 설치할지 정하여야한다.  
**보통 일반적으로 그냥 설치한다.**  

## B. 설치하기
위에서 어떤 버전을 설치할지 정하였으면, 아래 명령어처럼 입력해 설치할 수 있다. 내 것의 경우는 535이기 때문에 535로 설치한다.  
**각자 맞는 버전이 다르니, 잘 확인하고 아래 명령어 수정해서 입력!!**  
```bash
sudo apt-get install nvidia-driver-535
```  
설치가 잘 되었다면, 재부팅 후 아래 명령어를 입력해 확인한  
(사실 로그오프하고 로그인 해도 됨)  
```bash
nvidia-smi
```  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_ndriver1.png" width="100%" height="100%"></p>  

**사진과 같이 잘 나온다면 성공이다!**  
다음으로 [CUDA를 설치할 것이다.](https://sanghyunpark01.github.io/ubuntu/tips/Uubntu_Cuda/)