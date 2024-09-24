# 혼자 공부하는 컴퓨터구조 & 운영체제
## Chpater1. 컴퓨터 구조 시작하기
### 1. 컴퓨터 구조를 알아야하는 이유
- 컴퓨터 구조를 알고 있다면 문제 상황 발생 시 빠르게 진단& 해결이 가능함.
- 성능 / 용량 / 비용을 고려할 수 있게 됨 (RAM, core에 대해서 알게 된 후에 노트북을 비교해볼 수 있게 된 것처럼...)

### 2. 컴퓨터 구조의 큰 그림
 #### 1) 컴퓨터가 이해하는 정보
- 데이터 : 컴퓨터와 주고받는 정보나 컴퓨터에 저장된 정보, 숫자, 문자, 이미지, 동영상 등의 형태
- 명령어 : 데이터를 움직이고 컴퓨터를 실질적으로 동작 시키는 정보

 #### 2) 컴퓨터의 4가지 핵심 부품 
- CPU(중앙처리장치)  
- 메모리(주기억장치)
- 보조기억장치
- 입출력장치

### 3. 컴퓨터의 핵심 부품
![컴퓨터_핵심_부품](https://github.com/user-attachments/assets/3a204d73-b3c7-4440-abc1-635cf099b5c1)

#### 1) 메모리(주기억장치, Main Memory)

- 프로그램이 실행되기 위해서는 반드시 메모리에 저장되어 있어야 함
- 메모리는 **현재 실행되는 프로그램의 명령어와 데이터를 저장**함
- 메모리에 저장된 값의 위치는 주소로 알 수 있음

#### 2) CPU(중앙처리장치, Central Processing Unit)
- 메모리에 저장된 명령어를 읽어 들이고, 읽어 들인 명령어를 해석하고 실행하는 부품

- CPU 내부 구성 요소
  - 산술논리연산장치 （ALU：Arithmetic Logic Unit）
     - 계산을 위한 부품

  - 레지스터 (register)
     - 프로그램을 실행하는데 필요한 값들을 임시로 저장함
     - CPU 안에 여러 개가 존재하고 각기 다른 이름과 역할을 가지고 있음

   - 제어장치 (CU； Control Unit)
     - 제어 신호 (Control Signal) 이라는 전기 신호를 내보내고 명령어를 해석하는 장치
     - 메모리에 저장된 값을 읽거나 저장하고 싶을 땐 메모리를 향해 메모리 읽기/ 메모리 쓰기라는 제어 신호를 보냄

#### 3) 보조기억장치(Secondary Storage)
- 메모리보다 크기가 크고 전원이 꺼져도 저장된 내용을 잃지 않는 메모리 보조 저장장치
- 종류 : RAM(Random Access Memory), ROM(Read Only Memory). 주로 RAM을 말함

#### 4) 입출력장치(Input/Output device)
- 컴퓨터 외부에 연결되어 컴퓨터 내부와 정보를 교환하는 장치
- 마이크, 스피커, 프린터. 마우스, 키보드 등

#### 5) 메인보드(마더보드)와 시스템 버스
   - 메인보드(main board)
     - 컴퓨터의 핵심 부품들은 모두 메인보드라는 판에 슬롯과 연결단자로 부착됨
     - 메인보드 내부의 버스(bus)라는 내부 통로를 통해서 부품끼리 서로 정보를 주고 받을 수 있음
       
   - 시스템 버스(system bus)
     - 컴퓨터의 4가지 핵심 부품을 연결하는 가장 중요한 버스
     - 시스템 버스의 종류
       - 주소 버스( address bus ) : 주소를 주고받는 통로
       - 데이터 버스( data bus ) : 명령어와 데이터를 주고받는 통로
       - 제어 버스( control bus ) : 제어 신호를 주고받는 통로

----
## Chapter2. 데이터
### 1. 0과 1로 숫자를 표현하는 방법

#### 1) 정보 단위 
- 비트 (bit) : 0과 1을 나타내는 가장 작은 정보 단위, n 비트는 2^n 가지 정보를 나타냄.

|비트 개수 | 표현|
| --- | --- |
| 1비트(2개) | 0   1 |
| 2비트(4개) | 00   01   10   11 |
| 3비트(8개) | 000  100   010   001   110   101   011   111 |

- 비트 외의 정보 단위들
  
| 단위 | 크기 |  
| --- | --- |
| 1 byte | 8 bit |
| 1 KB | 1000 byte |
| 1 MB | 1000 KB |
| 1 GB | 1000 MB |
| 1 TB | 1000 GB |

- 워드 : CPU가 한번에 처리할 수 있는 data 크기
→ CPU가 한번에 32비트를 처리할 수 있다면 1워드 = 32비트

  - 하프 워드( 1/2 크기) - 풀 워드(1배 크기) - 더블 워드(2개 크기)
  - CPU는 대부분 32비트 또는 64비트
    

#### 2) 이진법 (binary)
##### (1) 이진법이란? 
- 0과 1만으로 숫자를 나타내는 방법
- 표기법
  - (예) 이진수 8 표현법 : 1000*(₂)* 또는 *0b*1000
##### (2) 이진법의 음수 표기
- 2의 보수 (two’s complement)
  - 사전적 의미는 ‘어떤 수를 그보다 큰 2ⁿ에서 뺀 값을 의미
  - 예) 11(₂)의 2의 보수는 11(₂)보다 큰 2ⁿ, 즉 100(₂)에서 11(₂)을 뺀 01(₂)이 되는 것
  - ‘모든 0과 1을 뒤집고, 거기에 1을 더한 값’으로 이해하면 됨.
  - 2의 보수 한계 : 양수와 음수의 표기법이 동일함
  - 컴퓨터 내부에서 어떤 수를 다룰 때는 이 수가 양수인지 음수인지를 구분하기 위해 플래그(부가정보)를 사용하기 때문에 컴퓨터는 양수와 음수의 표기법이 동일하더라도 헷갈리지 않음!
  - [참고_JAVA의 2의 보수법](https://yermi.tistory.com/entry/JAVA-2%EC%9D%98-%EB%B3%B4%EC%88%98%EB%B2%95-%EC%9D%8C%EC%88%98%EC%9D%98-2%EC%A7%84-%ED%91%9C%ED%98%84-1%EC%9D%98-%EB%B3%B4%EC%88%98%EF%BC%8B1)
 

  
#### 3) 십육진법 (hexademical)
##### (1) 십육진법이란? 
- 이진법은 숫자 크기가 커질 수록 변환 시 길이가 길어진다는 한계가 있음. 이를 보완하기 위해서 십육진법을 사용함 (이진법 <-> 십육진법)
- 한 글자당 열여섯 종류(0~9, A~F)의 숫자를 표현할 수 있음
- 표기법
  - (예) 십육진수 15 표기 : 15*(16)*또는 *0x*15
 
##### (2) 십육진수를 이진수로 변환하기
 ![image](https://github.com/user-attachments/assets/143b14b7-7d70-497f-b490-89f69c974696)

##### (3) 이진수를 십육진수로 변환하기
![image](https://github.com/user-attachments/assets/3ad6fc1f-ff25-470c-8318-4f1e83488c77)


### 2. 0과 1로 문자를 표현하는 방법

#### 1) 주요 개념

- 문자 집합(character set)
  - 컴퓨터가 인식하고 표현할 수 있는 문자의 모음

- 문자 인코딩(character encoding)
   - 컴퓨터가 이해하는 데이터(0 또는 1)로 문자코드를 변환

- 문자 디코딩(character decoding)
   - 0과 1로 이루어진 문자 코드를 사람이 이해할 수 있는 문자로 변환하는 과정

#### 2) 표현 방법
   - 아스키 코드 ASCII (American Standard Code for Information Interchange)
      - 초창기 문자 집합 중 하나로 영어 알파벳과 아라비아 숫자 그리고 일부 특수 문자를 포함함
      - 7비트로 표현됨. 정보의 가짓수는 2^7 = 128개

   - EUC-KR
     - 완성형 인코딩
     - 한글자를 표현하려면 16비트(2바이트) 필요함
     - 2350개 정도 표현 가능함
     - 한국어 외의 다른 외국어와 함께 쓰면 인코딩이 잘 안됨. (한계)

   - 유니코드와 UTF-8
     - 유니코드 : 여러나라 문자를 광범위하게 표현할 수 있는 통일된 문자 집합
     - UTF-8
        - 유니코드를 위한 가변 길이 문자 인코딩 방식 
        - 1~4바이트로 인코딩 됨

  ---
  

  ## Chapter3. 명령어
### 1. 소스코드와 명령어

#### 1) 언어의 종류
| 분류 | 목적 | 종류 |
| --- | --- | --- |
| 고급 언어 | for 사람 | java, C, C++, phython…  |
| 저급 언어 | for 기계(이해&실행) | 기계어(machine code), 어셈블리어(assembly langauge) |

[참고]
- 기계어(machine code) :  0과 1의 명령어 비트
- 어셈블리어(assembly langauge) :  기계어를 읽기 편한 형태로 번역하기 위한 언어 (고급언어X)

#### 2) 고급 언어의 종류  
  ##### (1) 컴파일 언어 
   - 대표적인 언어 : C
   - 소스 코드 전체가 저급 언어로 변환(컴파일)됨
  
  ##### (2) 인터프리터 언어 
  - 대표적인 언어 :  phython
  
  - 인터프리터에  의해 소스 코드가 한 줄씩  실행, 저급 언어로 변환됨 
    ⇒ 소스 코드 전체가 변환되길 기다리는 시간이 필요 없음
    ⇒ N번째 줄에 오류가 있어도 N-1번째까지 실행 가능
    (컴파일 언어는 소스 코드에 하나라도 오류 있으면 컴파일 불가)

  - 한 줄씩 실행, 변환 되기 때문에 컴파일 언어보다 느림

    ![image](https://github.com/user-attachments/assets/21a8018b-476d-4753-bf3a-f02f9a0e465a)



### 2. 명령어의 구조

#### 1) 연산코드와 오퍼랜드
![image](https://github.com/user-attachments/assets/90f82445-5f69-46c8-a8f1-7975f2af1b73)
![image](https://github.com/user-attachments/assets/27495020-5fea-46f2-b2ef-7d66fddf7c5e)

##### (1) 연산코드 (operation code) 
 - 명령어가 수행할 연산, 연산자
 - 기본적인 연산 코드 유형
   ![image](https://github.com/user-attachments/assets/bcda0f6d-9d39-4933-88b0-e43af3a16081)
   ![image](https://github.com/user-attachments/assets/6e8d1d1c-1559-4198-b058-4696fd083616)


##### (2) 오퍼랜드 (operand) 

- 연산에 사용될 데이터 또는 연산에 사용할 데이터가 저장된 위치, 피연산자
- 오퍼랜드 필드 = 주소 필드
    - why? 연산에 사용할 데이터가 저장될 위치인 메모리 주소나 레지스터 이름이 담기므로
- 예시
![image](https://github.com/user-attachments/assets/228333ef-b799-4fa9-8f6c-fbe1cfe81644)
![image](https://github.com/user-attachments/assets/b0c0d863-1cfc-4791-9d58-fc399424330f)


#### 1) 주소 지정 방식(addressing mode)

- 오퍼랜드 필드에  연산에 사용할 데이터 위치를 찾는 방식, (=유효 주소 찾는 방식)
    - why? 한정된 메모리에서 좀 더 효율적으로 데이터를 표시하기 위해서
    - 
 ##### (1) 즉시 주소 지정 방식

- 연산에 사용할 데이터 명시
- 표현할 데이터의 크기는 작아지나 연산에 필요한 데이터를 찾는 과정이 없어 빠름

![image](https://github.com/user-attachments/assets/369d2456-5188-47c2-9fc0-bc0f0b7071ee)


##### (2) 직접 주소 지정 방식

- 유효 주소(메모리 주소) 명시
- 즉시 주소 지정 방식보다는 표현 가능 데이터 크기가 커졌지만, 
유효 주소를 표현할 수 있는 범위가 연산 코드의 비트 수만큼 줄어들었음

![image](https://github.com/user-attachments/assets/f9d7f2f9-05b6-42dc-b0f1-dd6f894760fe)


##### (3) 간접 주소 지정 방식

- 유효 주소의 주소 명시
- 직접 주소 지정 방식보다 표현 할 수 있는 유효 주소 범위가 넓어짐
- 메모리에 두 번 접근해야 해서 다른 방식들보다 다소 느림

![image](https://github.com/user-attachments/assets/745b53f2-dba0-4c2c-a4ea-2dc99ef205eb)


##### (4) 레지스터 주소 지정 방식

- 유효 주소(레지스터 이름) 명시
- CPU 외부에 있는 메모리보다 CPU 내부에 있는 레지스터에 접근하는 것이 더 빠름. 따라서 직접 주소 지정 방식보다 빠르게 데이터에 접근이 가능함
- But, 직접 주소 지정 방식처럼 표현 가능한 데이터 크기에 한계가 있음

![image](https://github.com/user-attachments/assets/f143e000-2c76-4728-8c55-098f290bcb51)


##### (5) 레지스터 간접 주소 지정 방식

- 연산에 필요한 데이터는 메모리에 저장하고, 그 주소(유효 주소)를 저장한 레지스터를 명시
- 메모리에 접근하는 방식이 한번으로 줄어들어 간접 주소 지정 방식보다 빠름
![image](https://github.com/user-attachments/assets/b8d0d71d-0b03-4b93-b338-441871345e58)


---
## Chapter4. CPU의 작동 원리  

### 1. ALU와 제어 장치

#### 1) ALU
![image](https://github.com/user-attachments/assets/812996b4-93cf-4a31-870e-4ee88047948d)
- 레지스터와 제어 장치로부터 받아들인 피연산자와 제어 신호로 산술 연산, 논리 연산 등 다양한 연산을 수행함
- ALU는 메모리가 아닌 레지스터에 우선 저장함
    - why? CPU가 메모리에 접근하는 속도가 레지스터에 접근하는 속도보다 느리기 때문에
- ALU는 계산 결과와 **플래그**를 내보냄
    - 플래그( flag ) : 연산 결과에 대한 추가적인 상태 정보
    - 플래그는 플래그 레지스터에 저장됨
  ![image](https://github.com/user-attachments/assets/2f61edcf-f9c5-4402-b0fe-20022345f6b9)
[참고] 오버 플로우(overflow) : 연산 결과가 연산을 담을 레지스터보다 큰 상황


#### 2) 제어 장치
- 제어 장치 : 제어 신호를 내보내고 명령어를 해석하는 부품
- 제어 신호 : 컴퓨터 부품들을 관리하고 작동 시키기 위한 일종의 전기 신호
![image](https://github.com/user-attachments/assets/936388fc-1c6d-472e-963b-7ebca9724135)

- 제어 장치가 받아들이는 정보
    - 클럭 신호(clock signal) : 컴퓨터의 모든 부품을 움직일 수 있게 하는 시간
    - 해석해야 할 명령어 (명령 레지스터로 부터)
    - 플래그 레지스터 속 플래그 값
    - 시스템 버스, 그중에서 제어 버스로 전달된 제어 신호
- 제어 장치가 내보내는 정보
    - 제어 신호
 

 ### 2. 레지스터
 #### 1) 알아야 하는 레지스터
  ##### (1) 프로그램 카운터(PC, Program Counter)
   - 메모리에서 읽어 들일 명령어의 주소를 저장함
   - 명령어 포인터 (IP, Instrunction Pointer) 라고 부르기도 함

  ##### (2) 명령어 레지스터(IR, Instrunction Register)
   - 메모리에서 읽어 들인 명령어를 저장하는 레지스터
   - 제어 장치는 명령어 레지스터 속 명령어를 받아들이고 이를 해석한 뒤 제어 신호를 내보냄

  ##### (3) 메모리 주소 레지스터(MAR, Memory Address Register)
   - 메모리의 주소를 저장하는 레지스터
   - CPU가 주소 값을 주소 버스로 보낼 때 거치게 됨

  ##### (4) 메모리 버퍼 레지스터(MBR, Memory Buffer Register)
   - 메모리와 주고받을 값(데이터와 명령어)를 저장하는 레지스터
   - 데이터 버스로 주고받을 값이 거쳐 지나감
   - 메모리 데이터 레지스터(MDR, Memory Data Register) 라고도 부름

  ##### (5) 범용 레지스터(general purpose register)
   - 다양하고 일반적인 상황에서 사용하는 레지스터
   - 데이터와 주소를 모두 저장할 수 있음
   - CPU 안에 여러 개 존재함

  ##### (6) 플래그 레지스터(flag register) 
   - 연산 결과 또는 CPU 상태에 대한 부가적인 정보를 저장하는 레지스터
   - 특정 레지스터를 이용한 주소 지정 방식
    
   ###### ㄱ. 스택 주소 지정 방식
       - 스택과 스택 포인터를 이용한 주소 지정 방식
       - 스택 포인터( stack pointer ) : 스택의 꼭대기를 가리키는 레지스터(=마지막으로 저장한 값)
       
![image](https://github.com/user-attachments/assets/b59f604e-0ff1-44ba-acfc-570327095f36)
![image](https://github.com/user-attachments/assets/9d81470f-1d5a-4e5b-9982-f78de19ac420)

   ###### ㄴ. 변위 주소 지정 방식(displacement addressing mode)
      - 오퍼랜드 필드의 값(변위)과 특정 레지스터의 값을 더하여 유효 주소를 얻어내는 주소 지정 방식
       
     a. 상대 주소 지정 방식(relative addressing mode)
         - 오퍼랜드와 프로그램 카운터의 값을 더하여 유효 주소를 얻는 방식
  ![image](https://github.com/user-attachments/assets/c36a6d73-0546-472f-80c2-93144e1b9218)
  ![image](https://github.com/user-attachments/assets/89068611-19e1-40f6-81c8-c31c2636d13c)

      b. 베이스 레지스터 주소 지정 방식
         - 오퍼랜드와 베이스 레지스터의 값을 더하여 유효 주소를 얻는 방식
         - 베이스 레지스터는 ‘기준 주소’, 오퍼랜드는 ‘기준 주소로부터 떨어진 거리’로서의 역할
           즉,  베이스 레지스터 속 기준 주소로부터 얼마나 떨어져 있는 주소에 접근할 것인지를 연산하여 유효 주소를 얻어내는 방식
  ![image](https://github.com/user-attachments/assets/511a4537-f771-4c11-b06a-2eda4935ef37)

#### [참고] 레지스터 더 알아보기
     https://github.com/kangtegong/self-learning-cs/blob/main/registers/registers.md  

### 3. 명령어 사이클과 인터럽트
![image](https://github.com/user-attachments/assets/a2a07d1d-9721-4f2a-b5c7-96b58d0ada9e)

 #### 1) 명령어 사이클(instruction cycle)
     : 프로그램 속 각각의 명령어들이 반복되며 실행되는 일정한 주기
##### (1) 인출 사이클(fetch cycle) : 메모리에 있는 명령어를 CPU로 가지고 오는 단계
##### (2) 실행 사이클(execution cycle) 
- CPU로 가지고 온 명령어를 실행함.
- 제어 장치가 명령어 레지스터에 담긴 값을 해석하고 제어 신호를 발생 시키는 단계
##### (3) 간접 사이클(indirect cycle)
- 간접 주소 지정 방식 think, 명령어를 실행하기 위해 메모리 접근을 한 번 더 함
![image](https://github.com/user-attachments/assets/d6333a2b-fd36-4f21-b249-f64af5277c30)


#### 2) 인터럽트(interrupt)
    : CPU의 정상적인 작업을 방해하는 신호
    
- 동기 인터럽트(synchronous interrupts)
    - CPU에 의해 발생하는 인터럽트
    - 프로그래밍 상의 오류와 같은 예외적인 상황에 마주쳤을 때 발생함
    - 예외 exception 이라고도 부름

- 비동기 인터럽트(asynchronous interrupts)
   - 입출력 장치에 의해서 발생하는 인터럽트
![image](https://github.com/user-attachments/assets/a674761b-97c1-4703-971d-4420432442be)
![image](https://github.com/user-attachments/assets/8370b57a-8fd2-4773-9472-5a208ced506c)

##### (1) 하드웨어 인터럽트
- 알림과 같은 인터럽트
- CPU는 입출력 작업 도중에도 효율적으로 명령어를 처리하기 위해 하드웨어 인터럽트를 사용
- 하드웨어 인터럽트 처리 순서
![image](https://github.com/user-attachments/assets/f2956728-d551-4e62-8227-cefb1172d3f7)

- 인터럽트 요청 신호
  - 인터럽트 하기 전에 CPU에게 확인 받는 과정
    ![image](https://github.com/user-attachments/assets/ea781923-11d6-41ba-8853-f644709e34a9)

- 인터럽트 플래그
   - 하드웨어 인터럽트를 받아들일지, 무시할지 결정하는 플래그
   - 인터럽트 플래그가 불가능으로 되어 있으면 CPU는 인터럽트 요청이 와도 무시함
(단, 모든걸 무시할 순 없음. 막을 수 있는 플래그와 막을 수 없는 플래그가 있음)
![image](https://github.com/user-attachments/assets/26329e1f-9526-4c76-b960-d10a6ddd5c1c)
![image](https://github.com/user-attachments/assets/d3248783-6278-42ab-8534-c1d59a40fcbc)

- 인터럽트 서비스 루틴(ISR, Interrupt Service Routine)
  - CPU가 인터럽트 요청을 받아들이기 위해 실행시키는 프로그램
  - 인터럽트 핸들러(interrupt handler) 라고도 부름
  - ‘CPU가  인터럽트를 처리한다’는 말은  ‘인터럽트 서비스 루틴을 실행하고, 
    본래  수행하던 작업으로  다시 되돌아온다’ 라는  말과  동일함
![Untitled (4)](https://github.com/user-attachments/assets/be5f488c-31f8-4771-9129-adb343cd3feb)

- 인터럽트 벡터 (Interrupt Vector)
  - 인터럽트 서비스 루틴을 식별하기 위한 정보
![Untitled (5)](https://github.com/user-attachments/assets/16dce855-77c9-4699-8ab7-b7b80f3281b1)

##### [하드웨어 인터럽트 정리]

정리하면, ‘CPU가 인터럽트를 처리한다’는 말은 ‘인터럽트 서비스 루틴을 실행하고, 본래 수행하던 작업으로 다시 되돌아온다’는 말과 같습니다. 그리고 CPU가 인터럽트 서비스 루틴을 실행하려면 인터럽트 서비스 루틴의 시작 주소를 알아야 하는데, 이는 인터럽트 벡터를 통해 알 수 있습니다.

CPU는 인터럽트 서비스 루틴을 실행하기 전에 프로그램 카운터 값 등 현재 프로그램을 재개하기 위해 필요한 모든 내용을 스택에 백업합니다. 그러고 나서 인터럽트 서비스 루틴의 시작 주소가 위치한 곳으로 프로그램 카운터 값을 갱신하고 인터럽트 서비스 루틴을 실행합니다.

![image](https://github.com/user-attachments/assets/380620a2-f9c5-434e-9240-c45930b880f4)
![image](https://github.com/user-attachments/assets/5d944e0b-83c5-4e18-9b0d-944ba8886535)

##### [명령어 사이클 정리]
![image](https://github.com/user-attachments/assets/bed406b5-c649-41b2-ad45-3d7bf1831bac)

  ## Chapter5. CPU 성능 향상 기법
### 1. 빠른 CPU를 위한 설계 기법

#### 1) 클럭
- 클럭 속도가 높은 CPU는 일반적으로 성능이 좋다
- 클럭 속도 : 헤르츠(Hz) 단위로 측정함 1초에 클럭이 몇번 반복되는지 나타냄.
(예) 1초에 클럭이 100번 반복 → 100Hz
- 오버클럭킹(overclocking) : 최대 클럭 속도를 강제로 끌어올리는 일
- 클럭 속도를 무조건 올린다고 CPU 성능이 향상 되는 것은 아니다. 발열이슈가 있음!
  

#### 2) 코어와 멀티 코어
- CPU의 코어와 스레드 수를 늘리면 성능이 향상됨
- 코어(Core) : 명령어를 실행하는 부품    (예) 8 코어 → 명령어 실행하는 부품 8개
- CPU : 명령어를 실행하는 부품을 여러개 포함하는 부품 (코어가 여러 개 모인 것!)
    
    ⇒ 멀티 코어(multi-core) CPU 또는 멀티코어 프로세서라고 부름
  ![image](https://github.com/user-attachments/assets/fc92b72a-0495-414f-a151-96da76c574d4)
  ![image](https://github.com/user-attachments/assets/c2f870cc-12a7-447d-b737-04071932e00b)


#### 3) 스레드
- 스레드(thread) : 실행 흐름의 단위(사전적)
    - 하드웨어적 스레드
        - 하나의 코어가 동시에 처리하는 명령어 단위
        - 1코어 1스레드 CPU
          ![image](https://github.com/user-attachments/assets/94b9ed0c-f26f-4166-bac5-8adace8de122)
        - 2코어 4스레드 CPU
          ![image](https://github.com/user-attachments/assets/9f2aeb21-8c42-49e7-8044-d407a708694c)
