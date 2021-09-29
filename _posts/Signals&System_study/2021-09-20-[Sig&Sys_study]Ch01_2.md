---
title:  "[Sig&Sys-study]Ch01-2"
excerpt: "Ch01 Signals and Systems(2)"

categories:
  - SigSys_study
tags:
  - [Signals&Systems]

toc: true
toc_sticky: true

use_math: true

date: 2021-09-20
last_modified_at: 2021-09-20
---
# Ch01 Signals and Systems  
저번 포스트와 이어지는 내용이다.
# 1.4 The Unit Impulse and Unit Step Functions  
## \<DT>  
**$\delta[n]$ : Unit Impulse (sample)**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/134183397-a4ba3acd-790e-440a-808b-d8e0c1b79589.png" width="50%" height="50%"></p>  

**$u[n]$ : Unit Step (sample)**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/134183515-5fb4ca61-ec3f-48ba-b7be-0c70ec1f4381.png" width="50%" height="50%"></p>  

**Relationship between $\delta[n]$ and $u[n]$**  
* $\delta[n]=u[n]-u[n-1]$  
* $u[n]=\sum_{m=-\infty}^{m=n}{\delta[m]}$  
$u[n]=\delta[-\infty]+\cdots+\delta[-1]+\delta[0]+\delta[1]+\delta[n]$  
* $u[n]=\sum_{k=\infty}^{k=0}{\delta[n-k]}=\sum_{k=0}^{k=\infty}{\delta[n-k]}$  

**Sampling Property of $\delta[n]$**  
* $x[n]\delta[n]=x[0]\delta[n]$  

**아래 그림은 위 식의 일반화 (중요!)**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/134202593-d126ae06-a2e5-4f1c-8e10-283303d32b8e.png" width="50%" height="50%"></p>  

## \<CT>  
**$u(t)$ : Unit Step**  
$t=0$에서 불연속, $t^{0+}=1,\,t^{0-}=0$ 
<p align=""><img src="https://user-images.githubusercontent.com/77342519/134203800-b42af544-7ec8-4021-b0bd-245926eb005d.png" width="30%" height="50%"></p>  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/134204047-dad4bebd-44e9-4e69-8eaa-086771b0d9bd.png" width="45%" height="50%"></p>  

**$\delta(t)$ : Unit Impulse**  
DT와 비교해서 생각해보면 아래와 같다.  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/134209542-e6f77ea0-f653-4ddd-91fb-0f85d64c9b46.png" width="70%" height="50%"></p>  

* 문제점 : $u(t)$는 $t=0$에서 불연속 이므로, 미분 불가능  
* 아래와 같이 매우 작은 $\Delta$에 대하여, $u_{\Delta}(t)$를 정의  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/134210661-67ea6387-af6d-4c81-85b5-4d29547bcefd.png" width="80%" height="50%"></p>  

**Unit Impulse와 Unit Step의 관계**  
$u(t)=\int_{-\infty}^{t}{\delta(\tau)}d\tau$  
$\downarrow$ (치환적분)  
$u(t)=\int_{\infty}^{0}{\delta(t-\sigma)}(-d\sigma)$  
=$\int_{0}^{\infty}{\delta(t-\sigma)}d\sigma\quad \Leftarrow$  
=$\int_{0}^{\infty}{\delta(\sigma-t)}d\sigma\quad \Leftarrow$  
그래프로 보면,  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/134216541-5e833579-8159-4bdf-aa0f-5d09977a05ff.png" width="50%" height="50%"></p>

**성질**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/134216902-b1bc342c-60a2-4ec3-8581-cc312ca8fca5.png" width="70%" height="50%"></p>

---
# 1.5 CT and DT Systems  
## System의 정의  
**시스템의 정의**  
* <u>신호의 형태나 속성을 변화시켜서 다른 신호를 만들어내는 개체</u>  
* Input 신호를 처리하여 output 신호(또는 response)를 만들어냄  

**시스템의 예**  
* 자동차 운전 :  
입력신호 $\rightarrow$ 핸들의 조작, 가속기에 가하는 압력 등  
출력 $\rightarrow$ 자동차의 주행 궤적, 속도 등  
* 전기 회로 :  
입력신호 $\rightarrow$ 전원  
출력 $\rightarrow$ 소자의 전류 또는 전압  
* 전기 통신 : 선로가 시스템이 됨  
입력신호 $\rightarrow$ 송신신호  
출력 $\rightarrow$ 수신신호  

## CT and DT Systems  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/134514004-335ddca2-ebdd-4436-a0de-4d3ff7c8c42d.png" width="60%" height="50%"></p>  

**예시**  
* $x[n] :$ Net deposit(원금, n달째의 입금액)  
* $y[n] :$ 총액 (원리금)  
* 1%의 매달 이자  
* $\Rightarrow y[n]=x[n]+1.01y[n-1]$  

## Interconnections of Systems  
**위에서부터 <u>series interconnection</u>, <u>parallel interconnection</u>, <u>series-parallel interconnection</u>이다.**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/134515711-ba359bdf-b958-41b0-a46f-fbfcc8c7b6d5.png" width="60%" height="50%"></p>  

**아래는 Feedback interconnection과 그것의 예시이다**
<p align=""><img src="https://user-images.githubusercontent.com/77342519/134516951-3be5e62e-7112-45ad-9c00-ef1f918794fb.png" width="60%" height="50%"></p>  

---

# 1.6 Basic System Properties  
## 1 ) Systems with and without Memory  
**without memory**  
A system is memoryless  
* 출력이 현재의 입력에 의해서만 결정이됨  
* 예시  
$\cdot\,y[n]=(2x[n]-x^2[n])^2$  
$\cdot\,y(t)=Rx(t)$  
$\cdot\,y(t)=x(t)\,\Rightarrow$ Identity system(입력과출력이 같은 시스템)  
$\cdot\,y[n]=x[n]\,\Rightarrow$  

**with memory**  
A system with memory (memory system)  
* Memoryless 시스템이 아닌 시스템 (과거나 미래값에 의해 영향을 받음)  
* 예시  
$\cdot\, y[n]=x[n-1]$  
$\cdot\,$미래값에 영향을 받는다는 것은 이미지에서 픽셀에 index를 부여했을때를 생각해 보면 된다.  

## 2 ) Invertibility and Inverse Systems (가역성)  
A system is invertible  
* 특정한 입력에 대해서 특정한 출력을 내주는 시스템인경우 가역성이 있다고 한다. (undo exist)  
* 함수로 생각하면 역함수 존재 이다.  
* 예시  
피아노 건반 : 건반누르면 소리남-> 소리를듣고 건반 맞출수 있음->가역성 / **but** 여러건반에서 같은소리가 나면 못맞춤-> 비가역성  

## 3 ) (중요!) Causality (인과성)  
**Causal**  
A system is causal (= non-anticipative)  
* 어떤 특정시점에서의 출력이 현재와 과거에 의해서만 결정이 되는 시스템  
* 예시  
$\cdot\,$ memoryless system은 causal이다.  
$\cdot\,$ Adder, delay, capacitors  
$\cdot\, y[n]=x[n-1]$  

**Noncausal**  
A system is noncausal (= anticipative)  
* 미래값에 의해서 영향을 받는 시스템  
* 예시  
$\cdot\,y[n]=x[n]-x[n+1]$  
$\cdot\,y(t)=x(t+1)$  
$\cdot\,$ 독립변수가 time이 아닌경우, noncausal system이 많이 존재함  

## 4 ) Stability (안정성)  
안정성은 여러 타입으로 정의될 수 있다.  
**BIBO (Bounded Input Bounded Output) Stability**  
* 유한한 입력, 유한한 출력  
* 모든 t에 대해,  
$|x(t)|<B_1<\infty\,\rightarrow\,|y(t)|<B_2<\infty$  
* 예시  
* <p align=""><img src="https://user-images.githubusercontent.com/77342519/134659410-b9936cdf-f2c0-4720-b5ad-4b3d8066e5f8.png" width="60%" height="50%"></p>  

## 5 ) Time Invariance (시불변성)  
A system is time invariant  
* 시스템의 출력,특성,행동 등이 시간에 따라 바뀌지 않는것을 시불변성이라 한다.  
* $x(t)\rightarrow y(t),\, x(t-t_0)\rightarrow y(t-t_0)$  
* $x[n]\rightarrow y[n],\,x[n-n_0]\rightarrow y[n-n_0]$  
* 예시 : 회로에서 소자들의 값이 일정하면 동일한 source에 대해 동일한 결과가 나옴  
* 이해를 돕기 위한 다른예시는 아래 참고  
* <p align=""><img src="https://user-images.githubusercontent.com/77342519/134664691-427e1d81-f418-4a6d-b679-14352b2e5c48.png" width="70%" height="50%"></p>  
* <p align=""><img src="https://user-images.githubusercontent.com/77342519/134664970-feae8785-a8b3-4c7b-bafe-c1750270eae5.png" width="70%" height="50%"></p>  

## 6 ) Linearity (선형성)  
A Linear system is a system that possesses the 
important property of superposition.  
* 회로이론에서 했던, Additivity와 Homogenity와 같다.  
* <p align=""><img src="https://user-images.githubusercontent.com/77342519/134665324-60b4daf1-a0a7-4c0f-844f-fefa194a53da.png" width="50%" height="50%"></p>  

* 일반적으로,  
* <p align=""><img src="https://user-images.githubusercontent.com/77342519/134665514-679efad5-26dd-459d-aa50-5e1d5aae975d.png" width="60%" height="50%"></p>  

* 예시  
$y(t)=tx(t)$  
$y_1(t)=tx_1(t)$  
$y_2(t)=tx_2(t)$  
$ax_1(t)+bx_2(t)$를 입력으로 주면,  
$y_3(t)=t(ax_1(t)+bx_2(t))$  
$\qquad =ay_1(t)+by_2(t)$  
$ax_1(t)+bx_2(t)\rightarrow ay_1(t)+by_2(t)$  
$\Rightarrow$ Linear System  

---

Ch01 정리 끝!