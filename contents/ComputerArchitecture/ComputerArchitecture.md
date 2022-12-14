# 윈도우즈 시스템 프로그래밍(시스템 프로그래밍 + 컴퓨터 구조 + 운영체제)

## 시스템 프로그램이란?
- 컴퓨터 시스템을 동작시키는 프로그램(운영체제)
- 운영체제에서 제공하는 라이브러리를 사용하여 개발한 프로그램
<br>
<br>

## 컴퓨터 시스템의 주요 구성요소
- CPU
- 캐쉬(Cache) - 보통 CPU 내부에 존재
- 메인 메모리
- 하드디스크
<br>
<br>

## 컴퓨터 하드웨어 구성
||역할|구성|
:--:|:--:|:--:
CPU|중앙처리장치, 연산을 담당|ALU, 레지스터, 컨트롤 유닛, 버스 인터페이스
메인 메모리|컴파일이 완료된 프로그램 코드가 실행|-
입·출력 버스|컴퓨터 구성요소 사이 데이터를 주고 받는 경로|어드레스 버스, 데이터 버스, 컨트롤 버스

<br>
<br>

> **CPU**
<br>

||역할|
:--:|:--:|
ALU|실제 연산을 담당, 크게 산술 연산, 논리 연산으로 나뉨(연산만 가능)
컨트롤 유닛|명령어를 해석해 CPU의 다른 블록으로 신호를 보냄
레지스터|임시적으로 데이터를 저장하는 메모리 공간
버스 인터페이스|다른 구성요소로부터 데이터를 주고 받기 위한 프로토콜 혹은 통신방식을 담당

<br>
<br>

## 프로그램 실행 과정

<br>

**실행파일의 생성 과정**

1. 전처리기에 의한 치환 작업
   - #으로 시작하는 지시에 따라 소스코드를 변경하는 작업

<br>

2. 컴파일러에 의한 번역
   - 컴파일러에 의해 소스코드(ex.C, python)를 어셈블리 코드(기계어와 C의 중간쯤)로 번역

<br>

3. 어셈블러에 의한 바이너리 코드 생성
   - 어셈블러에 의해 어셈블리 코드를 바이너리 코드(기계어)로 번역
  
<br>

4. 링커에 의한 연결과 결합
   - 실제로 실행 가능한 실행파일을 생성하는 작업

<br>

**실행파일의 실행 과정**

- 실행 파일은 Fetch, Decode, Execution의 3단계로 실행
      
    ||역할|
    :--:|:--:|
    Fetch|메모리상의 명령어를 CPU로 가져오는 작업
    Decode|명령어를 CPU가 해석하는 단계
    Execution|명령어를 CPU가 실행하는 단계

<br>
<br>

## 폰 노이만 컴퓨터 구조
- 프로그램이 컴퓨터 내부에 저장되어 순차적으로 실행되는 구조
- "CPU - 메모리 - 프로그램"의 형태로 구성

> 다음의 질문을 통해 폰 노이만 컴퓨터 구조와 오늘날의 구조가 일치함을 알 수 있다
>> 1. Fetch는 어떤 경로를 통해 진행되는가
>><details>
>><summary>정답</summary>
>>
>>**버스 시스템**
>></details>
>>
>> 2. CPU 내부에서 명령어는 어디에 저장되는가
>><details>
>><summary>정답</summary>
>>
>>**레지스터(그 중에서도 IR)**
>></details>
>>
>> 3. Decode 단계는 누구에 의해 진행되는가
>><details>
>><summary>정답</summary>
>>
>>**컨트롤 유닛**
>></details>
>>
>> 4. Execution 단계는 누구에 의해 진행되는가
>><details>
>><summary>정답</summary>
>>
>>**ALU**
>></details>

<br>
<br>

> **버스시스템**
<br>

||역할|예시|
:--:|:--:|:--:
데이터 버스|데이터를 이동하기 위해 필요한 버스|명령어, 피연산자
어드레스 버스|주소값을 이동하기 위해 필요한 버스|데이터가 저장된 주소
컨트롤 버스|CPU가 원하는 바를 메모리에 전달할 때 사용|데이터 송신, 수신 여부