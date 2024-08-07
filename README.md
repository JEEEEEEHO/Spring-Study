# 토비 스프링 독서 스터디 

**1. 오브젝트와 의존관계**
   - 클래스 간 관계가 필요함
   - 낮은 결합도, 강한 응집력 -> 코드 변경시 대처가 쉬움
   - "사용" 관계 = 스프링의 IoC 컨테이너가 제공하는 DI의 속성을 이용함
     즉, 코드 상(=아키텍쳐) 으로는 클래스 간의 관계를 알 수 없음</br>
     런타임시 (Client 요청 등) 클래스 간의 관계가 결정 됨</br>
   ![의존관계](https://t1.daumcdn.net/cfile/tistory/22546A5056C4244F2A)</br>

     

 **2. 템플릿**
- 코드의 반복을 줄이기 위한 디자인 패턴
- 중요 개념</br>
      Client : 행동을 요청함</br>
      Context : 변화하지 않는 부분을 정리함</br>
      Strategy : 어떤 클래스와 관계를 맺을지에 대해서 정의한 부분
- 전략패턴
      Client의 코드에서 어떤 Strategy 사용할지 결정한 후 -> Context를 요청함</br>
      매번 클래스를 만드는 수고를 덜기 위해서, 내부 클래스 이용함 (new 인터페이스 -> 클래스 정의)
- 템플릿/콜백 패턴
      전략패턴과 유사하나, 인터페이스를 구현하는 부분이 메소드임
      
 **3. 예외**
 - RunTimeException : 프로그램 오류, catch throws를 하지 않아도 되며 런타임 에러의 보편화
 - 예외 전환 :
   ```
   try {
      예외가 발생하는 코드
   } catch(SQLExcetption e) {
      new RunTimeException(e); <- 해당 오류가 발생하더라도 RunTimeException으로 전환하여 처리함  
   }
   ```
   - DataAccessException <- 데이터 엑세스 프로그램에 상관없이 예외처리 가능한 인터페이스

  **4. 서비스 추상화**
  - 비즈니스 로직의 분리 (메소드로 따로 분리하여 처리함)
  - 트랜잭션 로직 분리
    *트랜잭션 경계 설정 중요 (커밋에 오류가 나는 경우 어떻게 할 것인가 = 전체 rollback / commit 알림)
   - 테스트를 위한 interface 생성 

  **5. AOP**
  - 트랜잭션 서비스 추상화
    
    ⚠️트랜잭션 경계 설정 + 비즈니스 로직
    
    → 특정 트랜잭션 기술에 종속됨 (기술이 바뀌면 가져다 쓰는 부분 다 고쳐야함)
    
    💡트랜잭션 추상내용 정리 + 비즈니스 로직 (구체적인 내용) 
    
    인터페이스와 DI를 통해 무엇을 하는지 남기고 
    
    (비즈니스 로직 —- 트랜잭션)
    
    어떻게 해야하는지 분리 
    
- 프록시와 데코레이터 패턴
    
    트랜잭션의 결계설정 (rollback..) 담당 코드 때문에 트랜잭션 코드 부분에 비즈니스 로직 처리 메소드 필요 
    
    ⇒ DI를 이용해 데코레이터 패턴 적용
    
    클라이언트 —- 인터페이스와 DI 를 통해 접근 `트랜잭션`  —— 타깃
    
    프록시 역할을 하는 트랜잭션 데코레이터를 거쳐서 타깃에 접근 
    
    ⇒ 독립적인 단위 테스트 가능 
    
- 다이내믹 프록시와 프록시 팩토리 빈
    
    프록시 클래스 없이도 오브젝트를 런타임시에 만들어주는 프록시 기술 
    
- 자동 프록시 생성 방법과 포인트컷
    
    스프링 컨테이너의 빈 생성 후 처리 기법
    
    → 컨테이너 초기화 시점에서 자동으로 프록시를 만들어주는 방법
    
    프록시를 적용할 대상을 일일이 지정하지 않고 패턴을 이용해 자동으로 선정해주는 확장된 포인트컷 사용 
    
- 부가기능의 모듈화
- AOP: 애스펙트 지향 프로그래밍
    - 에스펙트 : 부가기능 모듈
        
        애플리케이션의 핵심 기능을 담고 있진 않지만, 핵심기능에 부가되어 의미를 갖게 됨 
        
        부가될 기능을 정의한 코드 + 어드바이스를 어디에 적용할 것인지를 결정하는 포인트컷


 **8.스프링이란 무엇인가?**
    
 **8.1 스프링의 정의**
 
 - 애플리케이션 프레임워크
     - 프레임워크 : 애플리케이션의 특정 계층에서 주로 동작하는 한 가지 기술에 집중
     - 스프링 ⇒ 특정 계층이나 기술 업무 분야에 국한되지 않고 애플리케이션 전 영역을 포괄
     - 경량급
     - 오픈소스
     - 자바 엔터프라이즈 개발을 편하게
 
 - **8.2 스프링의 목적**
     
     8.2.1 엔터프라이즈 개발의 복잡함
     
     복잡함의 근본적인 이유
     
     - 기술적인 요구사항 늘어남
     - 비즈니스 로직의 복잡함이 증가함
     
     복잡함을 가중시키는 원인
     
     - 세부요소가 이해하기 힘든 방식으로 얽혀있음
     
     8.2.2 복잡함을 해결하려는 도전
     
     제거될 수 없는 근본적인 복잡함
     
     실패한 해결책: EJB
     
     비침투적인 방식을 통한 효과적인 해결책: 스프링
     
     8.2.3 복잡함을 상대하는 스프링의 전략
     
     기술적 복잡함을 상대하는 전략
     
     비즈니스와 애플리케이션 로직의 복잡함을 상대하는 전략
     
     핵심 도구: 객체지향과 DI
     
 - **8.3 POJO 프로그래밍**
     
     8.3.1 스프링의 핵심: POJO
     
     - IoC/DI, AOP, PSA  : application을 POJO로 개발할 수 있게 해주는 enabling technology
     
     8.3.2 POJO란 무엇인가?
     
     - Plain Old Java Object : 자바의 **단순한 오브젝트**를 이용해 비즈니스 로직을 구성
     
     8.3.3 POJO의 조건
     
     - 꼭 필요한 API에 종속되지 않아야 함
     - 특정 환경에 종속되지 않아야 함
         
         객체 지향적인 자바의 언어 기본에 충실해야함 
         
     
     💡 **잘 못된 방법**
     
     1. 책임과 역할이 다른 코드를 한 클래스에 몰아넣어 만능 클래스 만들기 
     2. 재사용이 불가능할 정도로 다른 레이어와 영역의 코드와 강한 결합
     3. 상속과 다형성으로 처리하지 않고 if/switch문이 가득한 메서드 
     
     8.3.4 POJO의 장점
     
     - 자동화된 테스트에 유리
     - 객체지향적인 설계를 자유롭게 적용할 수 있음
     
     8.3.5 POJO 프레임워크
     
     - POJO 프레임워크 : 스프링 / hibernate
     - 스프링 : POJO를 이용한 엔터프라이즈 개발을 목적으로 하는 프레임워크
     - hibernate : DB 기술에 적용
     
 - **8.4 스프링의 기술**
     
     POJO프로그래밍을 쉽게 하기 위해서 지원하는 세가지 기능 
     
     → IoC/DI, AOP, PSA 
     
     8.4.1 제어의 역전(IoC) / 의존관계 주입(DI)
     
     <aside>
     💡 왜 두개의 오브젝트를 분리 (serviceImpl)
     
     > 인터페이스를 두고 느슨하게 연결 (service - interface)
     
     > 실제 사용할 대상을 DI를 통해 외부에서 연결? (@Autowired service)
     
     (≠ new 키워드) 
     
     🔰 “유연한 확장이 가능하게 하기 위해서”
     
     </aside>
     
     ***DI의 활용 방법***
     
     - 핵심 기능의 변경
         
         DAO **←—-(주입)—** JDBC / JPA / Hibernate 
         
     - 핵심기능의 동적 변경
     - 부가기능의 추가
         
         데코레이터 패턴 
         
     - 인터페이스 변경
         
         중간에 인터페이스 어댑텨 역할을 해주는 레이어 추가 
         
     - 프록시
         
         lazy loading 을 적용하려면 프록시가 필요함 
         
     - 템플릿과 콜백
     - 싱글톤과 오브젝트 스코프
     - 테스트
     
     8.4.2 애스펙트 지향 프로그래밍(AOP)
     
     AOP의 적용 기법
     
     - 스프링이 제공하는 가장 대표적인 AOP = 트랜잭션
     - @Configurable 을 사용해서 도메인 오브젝트에 DI 자동 적용
     
     AOP의 적용 단계
     
     8.4.3 포터블 서비스 추상화(PSA)


# 혼자 공부하는 컴퓨터 구조+운영체제

1. **컴퓨터 구조**
    - 컴퓨터가 이해하는 정보
        - 데이터
        - 명령어
        
    - 컴퓨터의 **네가지 부품**
        - CPU
            - 메모리에 저장된 명령어를 읽고 → 해석하고 → 실행하는 부품
            - 산술논리연산장치, 레지스터(내부의 임시저장장치), 제어장치
            - 메모리에 명령어 > 읽고 > 레지스터에 저장한 후 > 연산 후 > 쓰기
        - 메모리
            - 주소 (0과 1로 구성되어있음)
            - 저장 용량이 작고 비쌈, 전원이 꺼지면 저장된 내용을 잃음
        - 보조기억장치
            - SSD, CD-ROM
        - 입출력장치
            - 컴퓨터 외부와 연동되어 내부와 정보를 교환하는 장치
        
    - 메인보드와 **시스템 버스**
        
        메인보드 : 핵심 부품들이 연결되어 있는 판
        
        버스 : 핵심 부품들간에 서로 정보를 주고 받을 수 있게 하는 통로 
        
        - 주소 버스
        - 데이터 버스 : 명령어와 데이터를 주고 받는 버스
        - 제어 버스 : 제어 신호를 주고 받는 버스
     

2. **데이터**
   - **0과 1로 숫자를 표현하는 법**
       - 정보 단위
           - 비트 : 0과 1을 나타내는 가장 작은 정보 단위, 2의 N승 (하나의 이진수 = 하나의 비트)
           - 바이트 : 8개의 비트를 묶은 단위
           - 킬로 바이트 → 메가 바이트 → 테라바이트
       - 이진법
   
   - **0과 1로 문자를 표현하는 법**
       - 문자 집합과 인코딩
           
           인코딩 : 문자 → 0, 1
           
           디코딩 : 0, 1 → 문자
           
       - 인코딩 방법
           - 아스키 코드 : 7비트 (=128개) 고유한 수에 문자가 1:1 대응함
           - 유니코드와 UTF-8

4. **CPU 작동원리**
    - **[CPU의 구성요소]** ALU 계산 > 제어장치 해석 > 레지스터 저장
    - **ALU와 제어장치**
        - ALU의 계산 결과를 레지스터에 저장함 (메모리보다 접근 속도 빠름)
        - 플래그 : ALU가 연산의 결과와 함께 보내는 값 → 플래그 레지스터에 저장
        - 제어장치 - 신호를 내보내고 명령어를 해석하는 부품 (전기신호)
            - clock 시간 단위
            - 해석해야하는 명령어를 받아드림 (명령어 레지스터)
            - 플래그 레지스터 안에 플래그 값을 받아드림
            - 제어 버스로 전달된 신로를 받아드림
    - **레지스터**
    - **명령어 사이클과 인터럽트**
        - 인터럽트 : 정해진 흐름에 따라 명령어를 처리해 나가지만, 간혹 흐름이 끊기는 상황 발생
        - 순서
            - 명령어 메모리에 저장
                
                > CPU로 인출 (인출사이클) 
                
                > CPU에서 명령어 실행 (실행 사이클) + 메모리 접근 한번 더 (간접 사이클) 
                
        - 인터럽트 : 이런 사이클의 순서를 방해하여 중단 시킴
            - 종류 : 동기(CPU에 의해) / 비동기(입출력 - 완료 시 CPU 인터럽팅)
            - 인터럽트 이후에 다시 돌아오기 위해서 스택 영역에 백업함
            
            ✅ function 이란 기능이 등장한 것도 동작의 반복 + 수행 후에 다시 돌아올 수 있는 기능을 구현하기 위해서 생김 
            
            ✅ 동작은 stack 영역에 쌓임 (자바 메모리, javascript stack 메모리 사용)


4.**CPU 성능 향상 기법**
 - **클럭**
     
     클럭신호에 맞추어 컴퓨터 부품들이 작동함 
     
     헤르츠 단위로 측정 
     
 - **코어와 멀티코어**
     - 코어 : 명령어를 실행하는 부품 = “코어(ALU / register/ 제어장치)”
         
         하나의 CPU에 여러개의 코어를 둘 수도 있음 
         
     - 스레드 :
         - 하드웨어적 스레드 → 명령의 단위
             
             하나의 코어가 동시에 처리하는 `명령어 단위`
             
             1개의 레지스터 - 1개의 명령어 처리하기 위한 정보 저장 
             
             ⇒ 여러개의 레지스터를 1개의 코어가 가질 수 있음 (=멀티스레드)
             
         - 소프트웨어적 스레드 (프로그래밍 관점) → 실행의 단위
             
             하나의 프로그램에서 `독립적으로 실행되는 단위` 
             
 - 명령어 병렬처리 기법
     
     CPU를 쉬지 않고 작동시키는 방법 
     
     - 명령어 파이프라인 (인출 해석 실행 저장) : 하나의 명령어가 처리되는 과정
     - 명령어 파이프라이닝 - 해당 파이프라인을 겹쳐서 처리
 
 - CISC와 RISC
        
        RISC : 고정 길이 명령어 
        
        명령어가 1클럭 내외로 실행되기 때문에 파이프라이닝에 최적화 
        
        메모리 접근을 단순화하고 최소화 추구
