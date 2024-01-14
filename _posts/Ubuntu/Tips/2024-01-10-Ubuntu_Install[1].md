---
title:  "외장 SSD에 Ubuntu 22.04 설치하기(1)"
excerpt: "Ubuntu 22.04 설치하기"

categories:
  - Ubuntu/Tips
tags:
  - [Ubuntu]

toc: true
toc_sticky: true
use_math: true

date: 2024-01-10
last_modified_at: 2024-01-10
---

[[이전글]Ubuntu 22.04 부팅 USB만들기](https://sanghyunpark01.github.io/ubuntu/tips/Ubuntu_Install-0/)  

# 2. Ubuntu 22.04 설치하기  
본 글은 **외장 SSD**에 Ubuntu를 설치하는 과정을 설명한다. 외장 SSD를 공장 초기화 하는 영상은 아래 링크 참조.  
[https://www.youtube.com/watch?v=TDAXvOoNWQI](https://www.youtube.com/watch?v=TDAXvOoNWQI)  
## A. USB로 부팅  
이전에 만들었던 부팅 USB를 컴퓨터에 꽂고 컴퓨터를 재부팅한다.  
**반드시 USB 3.0이상을 지원하는 부분에 꽂기**  
1. 컴퓨터가 꺼졌다 켜질때, BIOS에 접속한다. (BIOS들어가는 방법은 구글 검색)  
2. 부팅순서를 바꾼다. (UEFI적혀있는 것을 제일 위로)  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_BIOS.jpg" width="50%" height="50%"></p>  
3. 그리고 저장 후 나오기(Save&Exit)를 눌러 부팅한다.  

그리고 좀 기다리면 아래와 같은 화면이 나온다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_BIOS2.jpg" width="80%" height="100%"></p>  

제일 위에줄이 선택되어 있을 것이다. 가만히 기다리거나(자동으로 넘어가짐), Enter를 누르면 된다. 잠시 기다리면 또 아래와 같은 화면이 나온다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_partition0.jpg" width="80%" height="100%"></p>  

여기서 Try Ubuntu를 클릭후 대기한다. 그러면, 우분투 기본 바탕화면이 뜰 것이다.  

## B. 파티션 나누기
바탕화면에서 터미널을 연다. (Ctrl+Alt+T 로 열 수 있다.)  
1. 터미널이 열렸으면 아래 명령어를 입력한다.  
   ```sudo gparted```  

   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_partition1.png" width="100%" height="100%"></p>  
2. 그러면 아래와 같이 화면이 뜰 것이다. 여기서 동그라미 친 부분을 누른다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_partition2.png" width="100%" height="100%"></p>  
3. 선택지에서 설치할 SSD를 클릭한다. 나의 경우는 `/dev/sda`가 SSD이다.(1.82 TiB라고 쓰여있기 때문... 용량이 2T짜리이라서) 참고로 `/dev/sdb`는 USB이다.  
   설치할 SSD를 클릭한다.
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_partition3.jpg" width="80%" height="100%"></p>  
4. 아래 화면에 나타나 있는 것이 파티션이다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_partition4.png" width="80%" height="100%"></p>  

   여기서 모두 우클릭 후, delete를 눌러서 모두 `unallocated`상태로 만든다. 그러면 아래와 같은 상태가 된다. 여기서 우클릭 후 `new`를 누른다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_partition5.png" width="80%" height="100%"></p>  
5. 아래 화면처럼 필요한 만큼 파티션을 할당한다.  
   New Size 부분에 원래 `1907728MiB`(총용량)이였는데. 나는 `1900728MiB`만큼 할당해줬다. 그리고 **File System은 ex4**로 설정해준다. 그다음 Add버튼을 누른다.
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_partition6.png" width="80%" height="100%"></p>  
6. 그러면 아래처럼 파티션이 할당이 된다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_partition7.png" width="80%" height="100%"></p>  

   다시 `unallocated` 부분을 클릭 후, `New`를 누른다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_partition8.png" width="80%" height="100%"></p>  

   아까와 같이 남은 용량을 할당한다. 이 때 **File System은 linux-swap**으로 선택하고 Add버튼을 누른다. linux-swap은 ubuntu에서 RAM메모리가 부족할 때 RAM역할을 대신할 수 있도록 해주는 공간이다.(임시로 RAM역할을 하는 곳이므로, RAM이 부족하다면 컴퓨터의 RAM용량을 늘리도록...)  
7. 그러면 아래와 같이 되고, 체크 모양을 누른다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_partition9.png" width="80%" height="100%"></p>  
   체크 모양을 누르면 아래 창이 뜨는데 Apply를 누른다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_partition10.png" width="80%" height="100%"></p>  
8. 시간이 지나면 아래처럼 되고(All operation ~~ completed) close를 누른다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_partition11.png" width="80%" height="100%"></p>  
   최종적으로 아래 사진 처럼 된다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_partition12.png" width="80%" height="100%"></p>  

모두 잘 되었으면 창을 닫는다.  

## C. Ubuntu 설치 설정  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_install0.png" width="80%" height="100%"></p>  
위 사진처럼 생긴 것을 클릭한다. 그다음 아래과정을 진행한다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_install1.png" width="80%" height="100%"></p>  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_install2.png" width="80%" height="100%"></p>  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_install3.png" width="80%" height="100%"></p>  

**이제 매우 중요하다.**  
아래 사진에서 `Something else`를 클릭 후 continue를 누른다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_install4.png" width="80%" height="100%"></p>  

1. 그러면 아래와 같이 화면이 뜰 것이다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_install5.png" width="80%" height="100%"></p>  
2. 마우스 스크롤로 내리다 보면 아까 파티션을 설정한 부분이 보일 것이다.(나의 경우 `/dev/sda`)  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_install6.png" width="80%" height="100%"></p>  

   여기서 해당 `ex4`라고 되어 있는 줄을 클릭 후, 더블 클릭을 한다.  
3. 아래 화면처럼 구성한다.(용량은 자동을 되어있어서 놔둬도 됨)  
   `Use as`를 `Ext4 journaling file system`으로 선택하고 `Mount Point`를 `/`로 하고 포멧 체크 후 OK를 누른다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_install7.png" width="80%" height="100%"></p>  
4. 그러면 아래와 같이 ex4부분에 체크가 되어있을 것이다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_install8.png" width="80%" height="100%"></p>  
5. bootloader위치를 설정해줘야 한다. **아래 처럼 설치할 SSD로 해주어야 한다.(SSD이름이 나오게)**  
   `/dev/sda`가 아닌 `/dev/sda Samsung PSSD T7 (2.0 TB)`처럼 이름이 나와야 한다.  
   <p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_install9.png" width="80%" height="100%"></p>  

다 되었으면 install now를 누른다. 아래 화면처럼 뭐가 뜰텐데 Continue를 누른다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_install10.png" width="80%" height="100%"></p>  


## D. Ubuntu 설치  
거의 다 됬다. 아래 과정을 따라가면 끝난다!  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_final0.png" width="80%" height="100%"></p>  
위치는 현제 위치로 해준다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_final1.png" width="80%" height="100%"></p>  
user설정은 하고싶은대로 한다. Continue를 누르면 아래와 같이 설치가 진행될 것이다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_final3.png" width="80%" height="100%"></p>  
설치가 끝나면 아래화면이 뜨고, Restart now를 누른다.  
<p align="center"><img src="/Post_img/Ubuntu/Tips/Ubuntu_Install1_final4.png" width="80%" height="100%"></p>  

그러면 **Please remove ~~ ENTER**어쩌고가 뜨는데 설치 USB를 제거 후 Enter를 누르면 된다.  

우분투가 잘 켜질 것이다.  기존 윈도우로 들어가고 싶을 때, BIOS에 들어가서 부팅 순서를 변경해주면 된다.  

만약 잘 안켜진다면 10분정도 대기해본다. 대기해도 안켜진다면, 아래 링크를 참고해서 해결할 수 있다.  
[Ubuntu Nouveau끄기](https://sanghyunpark01.github.io/ubuntu/troubleshooting/Nouveau/)  

**우분투 초기설정은 아래 링크에서 확인 가능하다.**  
[우분투 초기 설정](https://sanghyunpark01.github.io/ubuntu/tips/Ubuntu_setting-0/)