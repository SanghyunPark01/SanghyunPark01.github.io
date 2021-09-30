---
title:  "[Sig&Sys-study]Ch02-1"
excerpt: "Ch02 Linear Time-Invariant (LTI) Systems(1)"

categories:
  - SigSys_study
tags:
  - [Signals&Systems]

toc: true
toc_sticky: true

use_math: true

date: 2021-09-28
last_modified_at: 2021-09-28
---

# Ch02 Linear Time-Invariant (LTI) Systems  
**LTI 시스템이란 선형성 시불변성 성질을 가지는 시스템이다**  
# 2.1 DT LTI Systems: The convolution sum  
## DT신호의 표현  
Linear combination으로 풀어쓰면,  
$x[n]=$
$\cdots +x[-3]\delta[n+3]+x[-2]\delta[n+2]+x[-1]\delta[n+1]$  
$\quad\qquad +x[0]\delta[n]+x[1]\delta[n-1]+x[2]\delta[n-2]+\cdots$  
이다.  
따라서, **$x[n]$을 convolution sum으로 나타낼 수 있다.**  

**중요!**  $x[n]=\Sigma_{k=-\infty}^{k=\infty}x[k]\delta[n-k]=x[n]*\delta[n]$  
  
## DT 임펄스 응답과 LTI의 Convolution합으로 표현  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135128054-c0a3a952-d857-4af1-a1d3-0b84d3169756.png" width="70%" height="50%"></p>  

선형성을 이용해보면,  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135128345-d985a704-aafd-4222-9138-c1f6a220cb03.png" width="70%" height="50%"></p>  

$\qquad\qquad\qquad\qquad\qquad\qquad\Downarrow$  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135128833-2315b0c5-4a12-4056-8bd6-2f8efc621b0d.png" width="70%" height="50%"></p>  

**예제**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135129911-5a30397e-5a59-4906-80db-ca77332e0336.png" width="70%" height="50%"></p>  

---

# 2.2 CT LTI Systems: The convolution Integral  
전반적인 내용은 2.1과 유사하다.
## CT신호의 표현  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135132067-72635e66-a1f4-4706-b8ae-ba25cbbcc15a.png" width="70%" height="50%"></p>  

추가적으로 sampling property를 생각해보면,  
$x(t)=\int_{-\infty}^{\infty}x(\tau)\delta(t-\tau)d\tau$  
$\qquad =\int_{-\infty}^{\infty}x(t)\delta(t-\tau)d\tau$  
$\qquad =x(t)\int_{-\infty}^{\infty}\delta(t-\tau)d\tau$  
$\qquad =x(t)$  

## CT 임펄스 응답과 LTI의 Convolution Integral로 표현  
2.1 에서 했던 내용과 유사하다.
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135133315-23e0ffa4-d406-45ca-b34b-39bc4d02e2d4.png" width="70%" height="50%"></p>  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135133752-ddc2399f-fd2d-4f36-80e5-67e2ed4cc02f.png" width="70%" height="50%"></p>  

**문제풀때 팁**  
$y(t)=x(t)*h(t)=\int _{-\infty}^{\infty}x(\tau)h(t-\tau)d\tau$  

$\quad$ or  

$y(t)=h(t)*x(t)=\int _{-\infty}^{\infty}h(\tau)x(t-\tau)d\tau$  

문제풀때 둘중에 계산이 쉬운것을 택하면 된다.  

---

# 2.3 Properties of LTI Systems  
**출력이 $X(t)$ 와 $h(t)$ 의 convolution으로 나타낼 수 있는건 LTI시스템 에서만 성립**  
## Commutative(교환), Distributive(분배), Associative(결합) Property  
**교환법칙**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135301495-1a3c9bc1-fa03-4e94-934e-ced8d42ce6ce.png" width="70%" height="50%"></p>  

**분배법칙**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135303879-7a2ebefc-ca12-4469-be92-b25d2ca26eb3.png" width="70%" height="50%"></p>  

**결합법칙**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135304119-50b85f6c-a712-444f-bbb3-704bf1385892.png" width="70%" height="50%"></p>  

## (중요!) Specific Properties of LTI System  
LTI 시스템의 경우 지난 포스트에서 다루었던 시스템의 특성보다 구체적인 특성을 갖는다. 어떤특성이 있는지 알아보자.  

## LTI Systems with and without Memory(LTI에서의 메모리)  
**Memoryless의 조건(DT에서)**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135452223-a6a27aef-781f-49d1-b532-6947d9b844bd.png" width="70%" height="50%"></p>  

위 조건을 만족하기 위해선,  
* $n\neq 0$일때, $h[n]=0$ 이어야 한다.  
* $\Rightarrow h[n]=K\delta[n]\;(K=h[0])$  

$\therefore y[n]=x[n]*h[n]=x[n]*K\delta[n]=Kx[n]$  

**CT에서 위 조건이 성립하는지 보자**  
$h(t)=K\delta(t)$  
$y(t)=x(t)*h(t)=\int_{-\infty}^{\infty}x(\tau)h(t-\tau)d\tau=\int_{-\infty}^{\infty}x(\tau)K\delta(t-\tau)d\tau$  

$\qquad\qquad\qquad\qquad K\int_{-\infty}^{\infty}x(\tau)\delta(t-\tau)d\tau = kx(t)*\delta(t)=Kx(t)$  
$\therefore y(t)=Kx(t)$  
  
**Therefore**  
LTI 시스템이 메모리가 없을조건은 아래와 같고, 나머지는 메모리가 있다.  
* $h[n]=K\delta[n]$  
* $h(t)=K\delta(t)$  

## Invertibility of LTI Systems(LTI에서의 가역성)  
undo가 가능해야 한다.  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135457247-b96a75a3-2447-45f6-9138-50b0ba3c6c72.png" width="50%" height="50%"></p>  

$(h_1(t)=h^{-1}(t))$  

$x(t) * (h(t)*h_1(t))=x(t)$  

$\therefore h(t)*h_1(t)=\delta(t)$  

DT도 마찬가지이다.  
$\therefore h[n]*h_1[n]=\delta[n]$  

## Causality for LTI Systems(LTI에서의 인과성)  
* $k>n$에 대해 $y[n]$는 $x[k]$에 의존하면 안된다.  
* <p align=""><img src="https://user-images.githubusercontent.com/77342519/135462057-86f70632-3e81-4488-8441-9babea1cc82f.png" width="50%" height="50%"></p>  

$\Rightarrow h[n-k]=0 (k>n)$  
$\therefore h[n]=0 (n<0)$  
$\Rightarrow$ Initial rest : 과거부터 그 시점의 입력이 다 0이었으면 출력도 0이된다.  
**CT일때도 조건이 같다.**
$h(t)=0 (t<0)$  
  
**LTI System이 Causal하면,**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135463957-87370113-2fce-4310-acb3-8eab993615c8.png" width="50%" height="50%"></p>  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135464052-88320d26-a136-41bf-960b-2c1510e4d343.png" width="70%" height="50%"></p>  

## Stability for LTI Systems(LTI에서의 안정성)  
**BIBO**  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135465043-7d664d6d-452f-4e9c-9771-114ac46509a0.png" width="70%" height="50%"></p>  
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135465204-2ce79b56-5b46-4673-a35d-5a4283cffa3c.png" width="70%" height="50%"></p>  

## Unit Step Response of LTI Systems(LTI에서의 유닛스탭 응답)  
아래는 임펄스응답과 유닛스텝 응답이다.
<p align=""><img src="https://user-images.githubusercontent.com/77342519/135465397-370d99d9-8526-438e-987f-272118ea8da1.png" width="40%" height="50%"></p>  

**DT**  
$s[n]=u[n]*h[n]=\sum_{k=-\infty}^{k=\infty}h[k]u[n-k] =\sum_{k=-\infty}^{k=n}h[k]$  
$\Rightarrow h[n]=s[n]-s[n-1]$  
**CT**  
$s(t)=\int_{-\infty}^{t}h(\tau)d\tau$  
$\Rightarrow h(t)=\frac{ds(t)}{dt}=s'(t)$  

---

**다음 포스트에 이어서**