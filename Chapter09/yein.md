<div align="center">
  <h1>Chapter09 : 단위 테스트</h1>
</div>

**[독서 포인트]**
<br />
📌 테스트 코드를 작성할 때 지켜야 하는 기본적인 규칙

<br />

## TDD 법칙 세 가지

- 세 가지 법칙은 다음과 같다.

  1. 실패하는 단위 테스트를 작성할 때까지 실제 코드 작성하지 않기
  2. ‘실패하는 단위 테스트’ → 컴파일 실패 X, 실행 실패 O
  3. 현재 실패하는 테스트를 통과할 정도로만 실제 코드 작성하기

- 위 원칙에 따라 테스트 코드를 작성하면 실제 코드를 사실상 전부 테스트하는 코드를 작성하게 된다.

- 하지만 테스트 코드 양이 방대해질수록 코드를 관리하는 문제도 심각해진다.

## 깨끗한 테스트 코드 유지하기

- 테스트 코드를 ‘지저분해도 빨리’ 작성하는 것이 괜찮을까? 실제 코드를 테스트한다는 목적만 달성한다면 괜찮은 걸까?

  - 지저분한 테스트 코드는 테스트를 안하는 것만 못하다!

  - 실제 코드가 변경한다면 테스트 코드도 변경해야 하는데, 테스트 코드가 지저분한 상태에선 그렇게 변경하기가 까다롭기 때문 → 그래서 결국 시간이 더 소요된다.

> 테스트 슈트가 없으면 개발자는 자신이 수정한 코드가 제대로 도는지 확인할 방법이 없다. 테스트 슈트가 없으면 시스템 이쪽을 수정해도 저쪽이 안전하다는 사실을 검증하지 못한다. 그래서 결함율이 높아지기 시작한다.

테스트 슈트를 폐지하고 위와 같은 문제를 초래하지 않으려면 애초에 테스트 코드를 깨끗하게 작성해야 한다.

- 테스트 케이스가 있으면 변경이 두렵지 않다.

  - 테스트 케이스가 없다면 모든 변경이 잠정적인 버그다.

- 테스트 커버리지가 높을수록, 실제 코드를 변경했을 때 버그가 숨어들 여지가 줄어든다.

## 깨끗한 테스트 코드

- 그렇다면 깨끗한 테스트 코드를 작성할 때 필요한 것은 무엇일까?

  - 가독성

  - ‘진짜 필요한’ 코드만 작성하기

  - 테스크 코드는 최소의 표현으로 많은 것을 나타내야 한다.

- 도메인에 특화된 테스트 언어(DSL, Domain Specific Language)

  - 잡다하고 세세한 코드는 도메인에 특화된 언어를 활용하여 정리할 수 있다.

  - 테스트 코드를 이해하는 데 방해되는 코드들은 감싸서 숨겨놓기
- 이중 표준

  - 가용 자원이나 CPU 효율 측면에서 실제 환경과 테스트 환경은 다르므로, 그런 의미에서 이중 표준을 둘 수 있다는 이야기 (cf. 코드의 깨끗함)

## 테스트 당 assert 하나 ?

- 테스트 당 assert 문이 하나일 때의 장단점

  - 장점: assert 문이 하나면 결론도 하나이므로 코드를 이해하기가 쉽다.

  - 단점: assert 문을 하나로 병합하는 방식이 불합리한 경우도 있다.

- assert 문을 하나로 병합해야 하는 경우에는 테스트를 두 개로 나누어서, 각각이 assert를 수행하도록 하면 됨.

  - 그러나 이때의 단점은, 중복되는 코드가 많아진다는 것

  - 중복 이슈 해결 방법(`given-when-then` 관례 사용할 때)
        1. Template Method 패턴 사용하기
        
          - 중복되는 부분인 `given`, `when`을 부분을 부모 클래스에 두고, `then` 부분을 자식 클래스에 둔다.
        2. `@Before`, `@Test`
        
          - 완전히 독자적인 테스트 클래스를 만들어서, `@Before` 함수에는 `given`, `when`을 부분을 넣고, `@Test` 함수에는 `then` 부분 넣기

- 하지만 모두 배보다 배꼽이 커진다! → 걍 assert 문을 여러 개 사용하는 편이 낫다는 것..

  - 물론 assert 문의 개수는 최소로 줄이는 것이 좋다.

- ‘테스트 당 assert 하나만 두기’라는 규칙보다는, 차라리 ‘테스트 함수 당 한 개념만 테스트하기’ 규칙이 나을 수 있다.

  - 독자적인 개념들을 하나의 테스트 함수 안에서 연속적으로 테스트하는 것은 별루

- ‘테스트 당 assert 하나만 두기’ → X

  - ‘테스트 당 assert 문 개수 최소로 줄이기’

  - ‘테스트 함수 하나는 하나의 개념만 테스트하기’

## F.I.R.S.T.

1. **F**irst (빠르게): 테스트는 빨라야 한다. 테스트를 자주 돌릴 수록 좋기 때문.

2. **I**ndependent (독립적으로): 각 테스트는 서로 의존하면 안 된다. 각 테스트 간에 실행 순서가 정해져 있으면 안 된다.

3. **R**epeatable (반복가능하게): 테스트는 어떤 환경에서든 돌아가야 한다. 테스트가 실패하는 환경이 있다는 것은, 테스트가 실패한 이유에 대한 변명거리가 생긴다는 것.

4. **S**elf-Validating (자가검증하는): 테스트 결과는 성공/실패 (bool)

5. **T**imely (적시에): ‘적시’ = 테스트 하려는 실제 코드를 작성하기 직전