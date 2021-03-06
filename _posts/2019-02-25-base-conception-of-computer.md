---
layout: post
title: 1. 컴퓨터 동작의 기본 개념
category: computer architecture 
---
>목차
- 계산기 모델
- 문서관리원 모델
	- 스토어 프로그램 컴퓨터
	- 문서관리원 모델 다시 보기
- 레지스터 파일
- RAM: 레지스터만으로는 부족할 때
	- 문서관리원 모델의 확장
	- 예: 두 수 더하기
- 코드 스트림 살펴 보기: 프로그램
	- 명령어의 종류
	- DLW-1 기본 아키텍처 및 산술 명령어 포맷
- 메모리 접근 자세히 보기: 레지스터와 직접값 비교
	- 직접값
	- 상대 레지스터 주소 지정

---
- 현대 컴퓨터의 핵심 기술은 **마이크로프로세서**(중앙 처리 장치(CPU, Central Processing Unit))이다. 마이크로프로세서는 작은 정방형의 은빛 실리콘 물체로, 수많은 초소형 논리게이트와 전기가 흐르는 채널로 이루어져 있다.

- 마이크로프로세서에 들어있는 게이트(트랜지스터)와 채널(전선)은 기본적으로 TV 리모콘이나 고물 라디오에도 들어있는 것과 같은 것이지만 훨씬 작다.

---

## 1. 계산기 모델
- 컴퓨터는 ++명령어(코드) 스트림++, ++데이터 스트림++, ++결과 스트림++으로 이루어져 있다.  

- code stream은 여러 연산을 순차적으로 나열한 것이며, data stream은 코드 스트림의 연산을 적용할 데이터(피연산자)이며, 마지막 result stream은 코드 스트림을 데이터 스트림에 적용한 연산 결과다.

- 예를 들어, 덧셈을 해야하는 경우 ALU는 코드 스트림에서 덧셈 연산을 받고, 데이터 스트림에서 피연산자인 2와 3을 받아서 5라는 결과를 결과 스트림으로 출력한다. 

## 2. 문서관리원 모델
- 계산기 모델도 여러모로 유용하기는 하지만, 컴퓨터를 나타내는 더 좋은 모델도 있다.
> 컴퓨터는 숫자를 다루는 기기이다. 컴퓨터의 동작은 3가지 요소(입력된 숫자(입력), 숫자를 다루는 법칙(수정), 컴퓨터 동작 후 지금까지의 수행 결과(쓰기))에 기반한다. 

--- 
- 문서관리원 모델은 연산 결과에 중점을 둔다. 결국 컴퓨터의 목적은 연산 자체가 아니라, 주어진 데이터에서 유용한 결과를 뽑아내는 것이기 때문이다. ++**다시 한번 강조하지만, 컴퓨터에서 중요한 것은 연산 제차가 아니라 입력된 데이터에 일련의 연산을 적용하고 그 결과를 저장하는 것이다.**++

- 컴퓨터의 일은 읽기, 수정, 쓰기가 전부이다. 결국 컴퓨터로 게임을 하건 음악을 듣건, 컴퓨터 내부에서 일어나는 모든 일은 문서관리원 모델로 설명이 가능하다.

### 2.1 스토어 프로그램 컴퓨터
- 컴퓨터 읽기-수정-쓰기를 수행하기 위해서는 다음 3가지 기본요소가 필요하다.


> #### 1. 저장소
> #### 2. 산술 연산 장치
> #### 3. 버스

|  | 내용 |
| ------ | ----------- |
| 저장소   | 컴퓨터가 데이터를 '읽고', '쓴다'고 할 때, 이는 데이터를 저장하는 저장소가 최소 하나 이상 있다는 것을 가정한다. |
| 산술 연산 장치(ALU) | ALU는 저장소에서 읽어온 데이터에 대해 산술 연산(덧셈, 뺄셈 등)을 수행한다. 연산 수행을 위해 컴퓨터는 우선 저장소에서 읽어온 데이터를 ALU의 데이터 포트에 쓴다. 데이터는 ALU 내부에서 연산을 통해 가공된 후, ALU 출력 포트를 통해 저장소에 쓰여진다. |
| 버스    | ALU와 저장소 사이에 데이터를 옮기려면 데이터를 전송하는 방법이 필요하다. 실제 ALU는 여러 전선으로 이루어진 데이터 버스(data bus)를 사용해서 데이터를 읽고 쓴다. 명령어는 명령어 버스(instruction bus)를 통해 ALU로 전송된다. |