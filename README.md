# CS-Study
CS Study (2023.12~) 

1. 오브젝트와 의존관계
   - 클래스 간 관계가 필요함
   - 낮은 결합도, 강한 응집력 -> 코드 변경시 대처가 쉬움
   - "사용" 관계 = 스프링의 IoC 컨테이너가 제공하는 DI의 속성을 이용함
     즉, 코드 상(=아키텍쳐) 으로는 클래스 간의 관계를 알 수 없음
     런타임시 (Client 요청 등) 클래스 간의 관계가 결정 됨

 2. 템플릿
    - 코드의 반복을 줄이기 위한 디자인 패턴
    - 중요 개념
      Client : 행동을 요청함
      Context : 변화하지 않는 부분을 정리함
      Strategy : 어떤 클래스와 관계를 맺을지에 대해서 정의한 부분
    - 전략패턴
      Client의 코드에서 어떤 Strategy 사용할지 결정한 후 -> Context를 요청함
      매번 클래스를 만드는 수고를 덜기 위해서, 내부 클래스 이용함 (new 인터페이스 -> 클래스 정의)

    - 템플릿/콜백 패턴
      전략패턴과 유사하나, 인터페이스를 구현하는 부분이 메소드임
      
