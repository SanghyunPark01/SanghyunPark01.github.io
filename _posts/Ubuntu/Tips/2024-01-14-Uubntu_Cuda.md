---
title:  "Ubuntu에 CUDA 설치하기"
excerpt: "Ubuntu 22.04에 CUDA 12.2 설치하기"

categories:
  - Ubuntu/Tips
tags:
  - [Ubuntu, CUDA, NVidia Driver]

toc: true
toc_sticky: true
use_math: true

date: 2024-01-14
last_modified_at: 2024-01-14
---
# 소개  
CUDA는 NVIDIA에서 만든 병렬 컴퓨팅 플랫폼 및 API모델이다.  
아주 많은 Deep Learning을 비롯한 A.I.모델들이 PyTorch, TensorFlow, TensorRT등 프레임워크를 사용하는데, 모두 CUDA가 많이 사용되서 Ubuntu에 필수적으로 설치해야 한다.  
  
CUDA를 설치하기에 앞서 [NVIDIA Driver 설치](https://sanghyunpark01.github.io/ubuntu/tips/Ubuntu_GDriver/)를 권한다.(안해도 CUDA설치하면서 해도 됨)
# CUDA 설치하기
## A. 버전확인
CUDA도 여러 버전이 존재하고 설치하기에 앞서 호환 가능한 버전을 확인해야한다.  
**CUDA는 NVIDIA Driver와 호환버전을 맞춰야한다. Driver설치를 먼저 권했던 이유이기도 한다.**  
`nvidia-smi`를 터미널에 입력해보면 아래왁 같이 확인할 수 있다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_cuda0.png" width="100%" height="100%"></p>  

오른쪽 위에 보면 CUDA에 대해 버전정보가 나와있는데, 이는 **설치된 NVIDIA Driver가 호환가능한 최대 CUDA버전** 이라는 뜻이다. 특정 버전을 다운받아도 되고, 적혀있는 버전을 다운받아도 된다. 나는 적혀있는 버전을 다운받을 것이다.  
## B. 설치
나는 12.2버전을 다운 받을 것이다. 아래 링크에 들어가 원하는 버전을 클릭하면 된다.  
[http://developer.nvidia.com/cuda-toolkit-archive](http://developer.nvidia.com/cuda-toolkit-archive)  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_cuda1.png" width="100%" height="100%"></p>  

해당 버전을 클릭하는데, 나의 경우 12.2.2를 다운받을 것이다.  
xx.x까지가 버전이고 뒤에 붙어있는 것들은 업데이트가 된 버전이다.  
클릭하면 아래 화면이 뜰 것이다. 여기서 해당 하는 것들을 선택해주면 된다.  
**OS는 Linux**이고, 보통 컴퓨터들(CPU가 Intel, AMD)은 Architecture가 x86이므로(보통 64비트) **x86_64**를 선택한다.  
나는 **Ubuntu 22.04에 설치**하므로 선택해주고, 마지막으로 **runfile (local)**를 클릭한다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_cuda2.png" width="100%" height="100%"></p>   
클릭을 하면 아래와 같이 명령어가 뜨는데, 한줄 한줄씩 **터미널**에 입력해준다.
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_cuda3.png" width="100%" height="100%"></p>  

첫번째 명령어을 입력하면, 설치파일을 다운받는 것이다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_cuda4.png" width="100%" height="100%"></p>  

두번째 명령어를 입력하고 잠시 대기하면, 아래처럼 실행될 것이다. **마우스가 아닌, 키보드 화살표 위아래**로 움직여 **Continue**로 진행한다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_cuda5.png" width="100%" height="100%"></p>  

그러면 아래창이 뜨는데, `accept`를 입력 후 **엔터**
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_cuda6.png" width="100%" height="100%"></p>  

여기서 **매우 중요!!**하다. 만약 [NVIDIA Driver를 설치](https://sanghyunpark01.github.io/ubuntu/tips/Ubuntu_GDriver/)했다면, Driver에서 **스페이스 바**를 눌러 X를 해제 해주어야 한다. NVIDIA Driver가 설치되지 않았다면 그대로 진행해도 좋다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_cuda7.png" width="100%" height="100%"></p>  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_cuda8.png" width="100%" height="100%"></p>  

**위 사진처럼 Driver부분에 X가 해제되었다면** 아래 Install로 넘어가 엔터를 누른다.
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_cuda9.png" width="100%" height="100%"></p>  

설치가 끝나면 아래처럼 된다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_cuda10.png" width="100%" height="100%"></p>  

설치가 끝났다면, .bashrc를 열어 환경변수를 입력해주어야 한다.
```bash
gedit ~/.bashrc
```
위 명령어를 입력해 .bashrc를 연 후, 마지막줄에 아래 명령어 두줄 추가**(만약, 다른 CUDA버전이면 아래 12.2대신에 자신이 살치한 쿠다 버전을 입력한다.)**
```bash
export PATH=/usr/local/cuda-12.2/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-12.2/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```
.bashrc파일에 잘 입력하였다면, 아래 명령어를 통해 터미널 상에 .bashrc업데이트 및 적용  
```bash
source ~/.bashrc
```  
그 다음, 아래 명령어를 터미널에 입력해 설치가 잘 됬는지 확인한다.
```bash
nvcc -V
```
<p align="center"><img src="/Post_img/Ubuntu/Tips/ubuntu_cuda11.png" width="100%" height="100%"></p>  

위 사진처럼 버전이 잘 뜨면 성공한 것이다!.