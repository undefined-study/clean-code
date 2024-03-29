<div align="center">
  <h1>Chapter10 : 클래스</h1>
</div>

**[독서 포인트]**
<br />
📌 클래스 잘 만드는 방법

<br />

## 클래스 체계

- 클래스를 정의하는 표준 자바 "관례"가 있다.

- 순서

  - 정적 공개 상수

  - 정적 비공개 상수

  - 비공개 인스턴스 변수

  - 공개 함수 (비공개 함수는 자신을 호출한 공개 함수 바로 뒤에 온다.)

- 변수, 유틸리티 함수는 가능한 비공개로 두는 게 좋지만, 테스트 등을 위해서 protected로 선언해서 테스트 코드에는 접근을 허용하기도 한다.

  - 단, 이렇게 캡슐화를 풀어주는 결정은 언제나 최후의 수단!

## 클래스는 작야아 한다!

- (앞장에서 등장했던) 함수와 마찬가지로, 클래스도 작게 만들어야 한다.

- 메서드 수가 기준이 아니라, 클래스의 "책임"을 기준으로 분리하는 게 좋다.

- 클래스의 이름은 그 클래스의 책임을 기술해야 한다. 반대로 말하면, 간결한 이름이 떠오르지 않을 땐 그 클래스의 책임이 너무 많다는 것이다.

- 단일 책임 원칙(SRP)

  - 클래스/모듈을 변경할 이유가 단 하나뿐이어야 한다는 원칙

  - 관심사를 분리하는 작업은 프로그래밍에서뿐만 아니라 프로그래밍 활동에서도 중요하다. ('돌아가는 소프트웨어'라는 관심사에서 '깨끗하고 체계적인 소프트웨어'라는 다음 관심사로 넘어가야 한다.)

  - 단일 책임을 기준으로 쪼개고 쪼개다가 클래스 개수가 너무 많아지면 이 클래스 저 클래스 돌아다녀야 해서 큰 그림을 이해하기 어려워진다!?

    - 작은 클래스가 여럿인 시스템이든, 큰 클래스가 소수인 시스템이든, 결국 익혀야 하는 양은 비슷하다.

    - 큼직한 다목적 클래스들을 가진 시스템의 경우에는, 어느 한 부분을 변경해야 할 때 당장 알 필요 없는 부분들도 파악하게 만들어서 비효율적이다.

    - 결론: 작은 클래스를 여럿 가진 시스템이 더 바람직하다.

- 응집도(Cohesion)

  - 각 클래스 메서드는 클래스 인스턴스 변수를 하나 이상 사용해야 한다.

  - 메서드가 변수를 많이 사용할수록 메서드-클래스 응집도가 더 높다.

  - "응집도가 높다." = 클래스에 속한 메서드와 변수가 서로 의존하며 논리적인 단위로 묶인다는 의미

  - 클래스가 응집력을 잃으면 쪼개라!

  - 여기서 잠깐, 안전한 리팩토링 방법

    1. 기존 프로그램의 동작을 검증하는 테스트 슈트 작성

    2. 한 번에 하나씩, 수 차례에 걸쳐 조금씩 코드 변경

    3. 코드를 변경할 때마다 테스트를 수행 -> 기존 프로그램과 동일하게 동작하는지 확인

## 변경하기 쉬운 클래스

- 뭔가 변경할 때마다 시스템이 의도대로 동작하지 않을 위험이 있다.

- 깨끗한 시스템을 만드는 것이 중요한 이유: 변경에 수반하는 위험을 낮춤.

- 요구사항은 변하기 마련 -> 코드도 변하기 마련

  - concrete 클래스: 상세한 구현을 포함한다.

  - abstract 클래스: 개념만 포함한다.

- 상세한 구현에 의존하는 클래스의 단점

  - 구현이 바뀌면 위험

  - 테스트가 어려움.

- 시스템의 "결합도"를 낮추면 유연성과 재사용성이 높아진다.

  - "결합도가 낮다." = 각 시스템의 요소가 다른 요소와 변경으로부터 잘 격리되어 있다는 의미

  - 결합도를 최소로 낮추면 DIP(Dependency Inversion Principle)를 따르는 클래스를 구현할 수 있다. DIP는 클래스 설계 원칙 중 하나로, 클래스가 상세한 구현이 아니라 **추상화에 의존해야 한다**는 원칙이다.
