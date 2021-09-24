---
title:  "[Sig&Sys-study]Ch01-1"
excerpt: "Ch01 Signals and Systems(1)"

categories:
  - SigSys_study
tags:
  - [Signals&Systems]

toc: true
toc_sticky: true

use_math: true

date: 2021-09-14
last_modified_at: 2021-09-14
---
# 소개  
## 교재 정보
Alan V. Oppenheim and Alan S. Willsky, Signals & Systems, 2nd
edition, Prentice-Hall, 1997
# Ch01 Signals and Systems  
# 1.1 Continuous-Time and Discrete-Time Signals
## 1 ) Signal  
### 신호 의 정의  
어떤 물리적 현상이 담고 있는 정보를 구체화 한것으로서, 한 개 또는 그 이상의 독립변수의 함수 (또는 랜덤 프로세스)로 정의  
  
**신호의 예**
* 음성 신호, 영상 신호, 회사의 월간 판매 실적  

**신호의 독립변수**  
* 음성 신호 𝒔(𝒕) : 독립변수 한 개(시간)  
* 영상 신호 𝒔(𝒙, 𝒚) : 수평 및 수직 방향의 거리를 독립변수로 사용  
* 동영상 신호 𝒔(𝒙, 𝒚, 𝒕) : 2차원 평면의 위치를 나타내는 두 개의 독립변수와 시간을 더하여 3개의 독립변수  

### Deterministic vs Stochastic(or random)  
* Deterministic : 독립변수에서 신호값이 결정(함수로 표현)  
* Stochastic(or random) : Deterministic + 확률이 같이 작용하는 형태 (예: 주사위(시간,확률))  

## 2 ) CT signal 과 DT signal  
***Continuous-Time(CT) Signal***  
**독립변수가 연속이다**  
-예시) human speech, voltage등  
**신호의 표현**  
-독립변수를 소괄호 ( ) 안에 써서 표현함  
-예시) x(t)  
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133434086-29657d7f-f9ff-4923-ade5-97ddd19486e9.png" width="50%" height="50%"></p>  

***Discrete-Time(DT) Signal (or Discrete-Time Sequence)***  
**독립변수가 이산이다**  
-예시) 물건의 가격  
**신호의 표현**  
-독립변수를 대괄호 [ ] 안에 써서 표현함  
-예시) x[n] (n∈I)  
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133434352-b0fd160a-43a1-4e91-82ef-b8dddd64c611.png" width="50%" height="50%"></p>  

## 3 ) Energy and Power of CT&DT Signal  
**I ) CT Signal**  
\- <u>x(t)는 복소수가 될 수 있으므로 절댓값을 취해주어야함!</u>  
\- <u>Average Power을 더 많이 사용함으로 중요!</u>  
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133436120-053279a6-2b17-415b-88e6-8b83299be667.png" width="50%" height="50%"></p>  

**II ) DT signal**  
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133436755-2616cd0f-00fd-4148-b024-64eabb6f57cb.png" width="50%" height="50%"></p>  

**III ) Total Energy ($𝐸_∞$)**  
* -∞<t<∞  
* -∞<n<∞  
* **에너지가 값이 존재하면 유한하다**  
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133443505-cfa4d2f9-2849-417d-b3e1-fd23d4684696.png" width="50%" height="50%"></p>  

**III ) Average Signal Power ($𝑷_∞$)**  
* -∞<t<∞  
* -∞<n<∞  
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133444048-7569cf80-4631-4125-ace6-bf9e49744091.png" width="50%" height="50%"></p>  

## 4 ) Signal의 분류  
**I ) $E_∞$ < ∞ (Signal with finite total energy)**  
<u>에너지가 유한하면 Average Signal Power = 0 이다</u>  
$\Rightarrow$ 이러한 signal을 **energy signal**이라고 함  
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133445935-7bdfc682-b3df-429e-9c35-c87e8d0a9663.png" width="50%" height="50%"></p>  

**II ) $P_∞$ < ∞ (Signal with finite average power)**  
<u>Average siganl power 가 유한하면 에너지가 무한함</u>  
$ \Rightarrow $ 이러한 signal을 **power signal**이라고함  
위 그림에서 (분모) = ∞ 이므로 $P_∞$가 값이 존재하려면 $E_∞$는 ∞이다.  
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133447535-af4def23-69b5-4ec5-9c41-3c160784ea76.png" width="50%" height="50%"></p>  

**III )  $E_∞ = ∞, P_∞ = ∞$**  
* 둘다 ∞인 경우도 있음  
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133448165-f9d7bd99-1530-49a1-8a14-b58596d0f4fa.png" width="50%" height="50%"></p>  

---  
# 1.2 Transformations of the Independent Variable  
## 1.1 )Time Shift  
**CT**  
<p align="left"><img src="https://user-images.githubusercontent.com/77342519/133544887-d3443d51-597c-41df-9537-837ddbf9dd56.png" width="40%" height="40%"></p>  

**DT**  
<p align="left"><img src="https://user-images.githubusercontent.com/77342519/133544985-8103ef4b-7e77-42e5-b22c-4082f1c24863.png" width="40%" height="40%"></p>  

## 1.2 ) Time Reversal (Reflection)  
함수의 대칭과 같음  
**x축 대칭**  
* y $\rightarrow$ -y  

**y축 대칭**  
* (CT)t $\rightarrow$ -t  
* (DT)n $\rightarrow$ -n  

## 1.3 ) Time Scaling  
y(t)=x($\alpha t$)  
y[n]=x[$\alpha n$]  
<p align="left"><img src="https://user-images.githubusercontent.com/77342519/133545803-21df2b64-ca41-4514-9a7f-36f25a97c332.png" width="40%" height="40%"></p>  

## 1.4 ) 시간축 적용 순서  
**Scaling $\rightarrow$ Reflection $\rightarrow$ Shifting**  
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133546490-a983e020-f13d-4948-9fa8-7a7c21b07a44.png" width="50%" height="50%"></p>  

## 2 ) Periodic Signals  
**CT**  
<u>x(t) = x(t+T)</u>  
* x(t)는 주기가 T이다.  
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133547711-24aa1886-68c3-4ac8-aa5b-f0dc4eea9845.png" width="40%" height="40%"></p>  

* x(t) = x(t+mT)가 성립한다.(m∈I)  
$\Rightarrow$ 2T, 3T, ... 모두 주기가 될 수 있다.  
* Fundamental period( $T_{0}$ ) : 양수이면서 가장 작은 주기  
* Aperiodic siganal : periodic signal이 아닌 신호  

**DT**  
<u>x[n] = x[n+N], N ∈ I</u>  
* x[n]은 주기가 N이다.
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133547786-8b8efd7a-0f61-4d3d-8f56-61733f4a1080.png" width="40%" height="40%"></p>  

* 나머지 특징은 CT와 같음  

### 예시  
**아래 신호는 Aperiodic siganal이다.**  
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133548295-626e54b3-1682-4168-a5e9-59304e6042cc.png" width="50%" height="50%"></p>  
  

## 3 ) Even and Odd Signals
### I ) Even and odd signals  
**Even signal**  
우함수, y축 대칭이다  
* CT  
x(-t)=x(t)  
* DT  
x[-n]=x[n]  

**Odd signal**  
기함수, 원점(0,0)대칭이다  
* CT  
x(-t)=-x(t)  
* DT  
x[-n]=-x[n]  

### II ) 참고  
**모든신호는 우함수신호와 기함수신호의 합으로 이루어져있다.**  
<p align="center"><img src="https://user-images.githubusercontent.com/77342519/133548923-a953e8e2-b1f1-4d1b-9f5a-b20395b370cc.png" width="60%" height="60%"></p>  

---  
  
# 1.3 Complex Exponential and Sinusoidal Signals  
## Review  
복소평면에 대한내용은 안적고 참고사항만 적음  
* 드무아브르 정리
<p align="left"><img src="https://user-images.githubusercontent.com/77342519/133553821-b46d861d-c3c1-4d22-80bb-7f5d7fa5aff8.png" width="40%" height="40%"></p>  

* Sine wave  
**sin(wt)에서 w=2 $\pi$ f 이다. (w의 단위: rad/s, f의 단위: Hz)**  

## 1 ) Continuous-Time Complex Exponential Siganal  
**I ) x(t)**  
x(t)= $Ce^{at}$ (C랑 a는 복소수)  
  
**II ) 주기**
**a가 pure imaginary라면**,  
x(t)= $e^{jw_{0}t}$  
**x(t)가 주기함수라면**,  
x(t)= $e^{jw_{0}t}$ = $e^{jw_{0}(t+T)}$ = $e^{jw_{0}t}$ $e^{jw_{0}T}$  
$\Rightarrow$ $e^{jw_{0}T}$ = 1  
* If $w_{0}=0, \space x(t)=1$  
* If $w_{0}\neq0, \space T=\frac{2\pi}{\vert w_{0}\vert}m, m\in I$ ( $\because e^{jw_{0}T}$의 주기는 2 $\pi$ 이므로)  
$\Rightarrow T_{0}=\frac{2\pi}{\vert w_{0}\vert}$ 이며, x(t)는 주기가 $T_{0}$인 주기신호 이다.  

**III ) 주기신호의 에너지와 파워**  
<p align="left"><img src="https://user-images.githubusercontent.com/77342519/133563891-99209fe6-779b-43c5-8a34-0e3166d07e06.png" width="60%" height="60%"></p>  

**IV ) 고조파(Harmonics)**
<p align="left"><img src="
https://user-images.githubusercontent.com/77342519/133565031-843134a8-4789-4fac-b21f-fdb5cc5d49fb.png" width="30%" height="30%"></p>  
k번째 하모닉이라고 함
<p align=""><img src="https://user-images.githubusercontent.com/77342519/133565215-bb30e828-84ef-4e5d-84a2-be18688bad60.png" width="40%" height="40%"></p>  

**V ) 일반적인 복소 지수 신호**  
**$Ce^{at}$**  
* $C =\vert C \vert e^{j\theta}$ (complex number)  
* $a=r+jw_{0}$ (complex number)  

<img src="https://user-images.githubusercontent.com/77342519/133566216-1336493d-5ae1-40fe-9613-c077434d2cea.png" width="50%" height="50%"></p>
<p align=""><img src="https://user-images.githubusercontent.com/77342519/133566428-a5c6a097-3520-48db-acf4-f7629f0fa014.png" width="50%" height="50%"></p>  

x(t)에서,  
* $\vert C\vert$는 상수(constant)  
* $e^{rt}$는 포락선 (envelope)  
* cos 부분은 정현파 (sinusoidal signal)  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/133567190-d15a6c5d-e6ed-48a0-affb-4c005991dd63.png" width="50%" height="50%"></p>  

## 2 ) Discrete-Time Complex Exponential Siganal  
**I ) x(t)**  
x[n]= $C\alpha ^{n}$ (C랑 $\alpha$ 는 복소수)  
* $\alpha=e^{\beta}$  
**II ) 정현파**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/133578794-d9a65eab-43f4-43df-a357-a916710c57e8.png" width="30%" height="30%"></p>  

* 주기함수 이려면 $w_{0}$ 은 $\pi$의 배수여야 함  
**III ) 일반적인 복소 지수 신호**  
**$x[n]=C\alpha ^{n}$** 
* $C =\vert C \vert e^{j\theta}$  
* $\alpha=\vert \alpha \vert e^{jw_{0}}$  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/133583792-308d749e-3077-4c4d-a28d-579320866eaa.png" width="45%" height="45%"></p>  
cos부분은 실수부 sin부분은 허수부  

실수부만 그려보면,  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/133584080-197b9179-ac59-492b-ae0b-599fff521d98.png" width="45%" height="45%"></p>  

**IV ) 주기**  
x[t]= $e^{jw_{0}n}$의 주기를 N이라 하면,  
$e^{jw_{0}n}=e^{jw_{0}(n+N)}$  
$\Rightarrow e^{jw_{0}N}=1$  
* $w_{0}N=2\pi m\;(m\in I)$  
* $\frac{w_{0}}{2\pi}=\frac mN$  
* **$N=\frac{2\pi}{w_{0}}m$**  
* 예시는 아래와 같다.  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/133587134-010cc367-de2b-41aa-9c39-3faf2f50f1c0.png" width="50%" height="50%"></p>  

## 3 ) 고조파의 특징 (중요!!)  
**CT의 경우 하모닉이 높아지면서 무한하지만, DT의 경우 하모닉이 유한함**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/133588344-bc030bfa-fd00-4ead-8d53-986f9de5b8bb.png" width="30%" height="30%"></p>  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/133588512-a84b3e05-5053-4e3b-8cce-5e8329095656.png" width="50%" height="45%"></p>  


* 예시  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/133588790-582ba14e-96b2-45a5-8bc8-afd155bae565.png" width="50%" height="45%"></p>  

---  
**다음 포스트에 이어서**