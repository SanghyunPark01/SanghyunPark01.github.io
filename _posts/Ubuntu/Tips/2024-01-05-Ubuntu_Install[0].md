---
title:  "외장 SSD에 Ubuntu 22.04 설치하기(0)"
excerpt: "Ubuntu 22.04 부팅 USB만들기"

categories:
  - Ubuntu/Tips
tags:
  - [Ubuntu]

toc: true
toc_sticky: true
use_math: true

date: 2024-01-05
last_modified_at: 2024-01-05
---

# 0. Ubuntu 설치 절차  
윈도우 노트북을 사용하면서 Ubuntu를 사용할 일이 있을 것이다. 이 때, 보통 기존 SSD의 파티션을 나누거나 외장 SSD를 사용할 것이다. 본 글은 **외장 SSD**에 Ubuntu를 설치하는 과정을 적을 것이다.  
보통 Ubuntu설치과정은 부팅 USB를 만들고 USB로 부팅을 한 다음 SSD에 Ubuntu를 설치하는 것이다.  

# 1. Ubuntu 22.04 부팅 USB만들기

## A. rufus 프로그램 설치
먼저 [링크(https://rufus.ie/ko/)](https://rufus.ie/ko/)에 들어가 rufus를 다운로드 받는다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install0_rufus.jpg" width="100%" height="100%"></p> 

표준 버전을 다운받는다.

## B. Ubuntu ISO 이미지 다운로드
우분투 설치 및 부팅 데이터를 위해 Ubuntu ISO이미지를 아래 링크로 부터 다운 받는다.  
[링크(https://ubuntu.com/download/desktop)](https://ubuntu.com/download/desktop)  

<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install0_ubuntu_img.jpg" width="100%" height="100%"></p> 

Download 버튼을 눌러 파일을 받는다.

## C. 제작
위 두 과정이 다 완료 되었으면, 충분한 용량을 가진(요즘 기본 16GB용량으로 나와서 문제가 없다...) USB를 준비해준다. 비어있는 USB가 준비되었으면 컴퓨터에 연결한다.  
  
**1) 설치한 rufus를 실행해준다.**
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install0_rufus_usb.jpg" width="50%" height="100%"></p> 

USB가 연결되었으면 자동으로 장치가 선택되어있을 것이다. 만약 선택되어있지 않다면, USB를 직접 선택해주자.  
  
**2) ISO이미지 선택**  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install0_rufus_select.jpg" width="50%" height="100%"></p> 

선택 부분을 클릭해 다운받은 ISO이미지를 선택해준다. 그러면 아래와 같이 될 것이다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install0_rufus_iso.jpg" width="50%" height="100%"></p> 
  
**3) 시작**
시작 버튼을 누르자. 그러면 아래와 같이 창이 뜬다. 'OK'를 누른다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install0_rufus_start_1.jpg" width="80%" height="100%"></p> 

아래 창이 뜬다면 '예'를 누르자. 안떠도 상관 없다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install0_rufus_start_2.jpg" width="80%" height="100%"></p> 

'확인'을 누른다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install0_rufus_start_3.jpg" width="80%" height="100%"></p> 

그러면, 상태 창이 아래와 같이 진행될 것이다. 잠시만 기다리자.
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install0_rufus_start_4.jpg" width="80%" height="100%"></p> 

아래와 같은 상태가 되면 '닫기'를 눌러 마무리 한다.
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install0_rufus_start_5.jpg" width="80%" height="100%"></p> 

이제 부팅 USB제작은 끝났다. 다음으로 외장 SSD파티션 설정과 Ubuntu 설치를 설명할 것이다.