---
title:  "Ubuntu 초기 설정"
excerpt: "Ubuntu 초기 설정"

categories:
  - Ubuntu/Tips
tags:
  - [Ubuntu]

toc: true
toc_sticky: true
use_math: true

date: 2024-01-12
last_modified_at: 2024-01-12
---

# 1. Ubuntu 소프트웨어 업데이트  
터미널을 열어 아래 명령어를 입력한다.
```
sudo apt-get update
sudo apt-get upgrade
```
다 끝났다면, 메뉴에서 아래 아이콘처럼 생긴 것을 클릭한다.  
Ubuntu가 처음인 사람을 위해 메뉴는 바탕화면에서 왼쪽 아래에 있다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_0.png" width="30%" height="100%"></p>  
그러면 아래와 같은 창이 뜨는데, Install Now를 누른다.
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_1.png" width="50%" height="100%"></p>  

번외로, **현재 Ubuntu 버전은 22.04이다.** 혹시라도 나중에 24.04가 출시된다면, 분명히 24.04로 업데이트를 하시겠습니까라고 뜰텐데 **절대 누르면 안된다.**  

# 2. Ubuntu 한글 키보드 설정  
Ubuntu를 처음 설치를 하면, 한글 입력이 되지 않을 것이다. 한글입력을 하기 위해선 키보드를 추가해 주어야한다. 과정은 아래와 같다.  

1. 설정(Settings)에서 Region & Language를 클릭 후 Manage Installed Languages클릭  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_2.png" width="80%" height="100%"></p>  
   설치를 진행한다. 그 다음 아래 사진에 보이는 것처럼 Install/Remove Language를 클릭한다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_3.png" width="80%" height="100%"></p>  
   아래 사진처럼 Korean이 체크되어있는지 확인한다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_4.png" width="80%" height="100%"></p>  
   잘 체크 되어 있으면 재부팅 한다.  

2. **재부팅 후**, 설정에서 Keyboard에 들어가고 Input source에 +를 클릭한다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_5.png" width="80%" height="100%"></p>  
   Korean을 누르고, Hangul을 추가한다.
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_6.png" width="80%" height="100%"></p>  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_7.png" width="80%" height="100%"></p>  

3. 이제 한글/영문 키를 설정할 것이다. Hanugl에서 Preference를 클릭한다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_8.png" width="80%" height="100%"></p>  
   Add를 누른다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_9.png" width="80%" height="100%"></p>  
   그러면, 아래 창처럼 뜨는데 이 상태에서 한영변환키를 누른다.
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_10.png" width="80%" height="100%"></p>  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_11.png" width="80%" height="100%"></p>  
   OK를 누른 후, 방금 누른 한영 변환키를 제외한 나머지 것들을 삭제한다.
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_12.png" width="80%" height="100%"></p>  
   아래처럼 하나만 남겨놓고, Apply후 OK를 눌러 창을 닫는다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_13.png" width="50%" height="100%"></p>  

한글 입력과 영어입력 모두 잘 될것이다.  

# 3. 기타 소프트 웨어 설치  
## .deb 파일로 설치  
Google Chrome을 설치할 것이다. 아래 링크로 들어가 `.deb`파일을 다운 받는다.    
[https://www.google.com/intl/ko_kr/chrome/](https://www.google.com/intl/ko_kr/chrome/)  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_14.png" width="50%" height="100%"></p>  

다운로드 폴더에 들어가 `.deb`파일을 설치한다.  
```
cd ~/Downloads
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

그리고 메뉴에 들어가면, 아래와 같은 아이콘이 생길 것이다!
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_15.png" width="30%" height="100%"></p>  
우클릭 후, Add to Favorites를 클릭해 사이드바에 추가하자!
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_setting_16.png" width="50%" height="100%"></p>  

위와 같은 방식으로 `.deb`파일을 설치 할 수 있다. vscode와 같은 필요한 소프트웨어를 설치하면 된다.
