# [12장] 창발성

## 📚 목차
- 창발적 설계로 깔끔한 코드를 구현하자
- 단순한 설계 규칙 1: 모든 테스트를 실행하라
- 단순한 설계 규칙 2~4: 리팩터링
- 중복을 없애라
- 표현하라
- 클래스와 메서드 수를 최소로 줄여라
- 결론
- 참고 문헌

---

### 켄트 벡이 제시한 단순한 설계 규칙 네 가지
- 모든 테스트를 실행한다.
- 중복을 없앤다.
- 프로그래머 의도를 표현한다.
- 클래스와 메서드 수를 최소로 줄인다.

### 🔍 중복을 없애라
중복은 추가 작업, 추가 위험, 불필요한 복잡도를 뜻하기 때문에 우수한 설계에서 커다란 적이다.
- #### [TEMPLATE METHOD 패턴](https://hudi.blog/template-method-pattern/)
    고차원 중복을 제거할 목적으로 자주 사용하는 기법이다.   
    어떤 작업을 처리하는 일부분을 서브 크래스로 캡슐화해 전체 일을 수행하는 구조는 바꾸지 않으면서 특정 단계에서 수행하는 내역을 바꾸는 패턴이다.   
    전체적으로는 동일하면서 부분적으로는 다른 구문으로 구성된 메서드의 코드 중복을 최소화할 때 유용하다.

### 🔍 표현하라
자신이 이해하는 코드를 짜기는 쉽지만 다른 사람이 이해하기 쉬운 코드를 짜기는 어렵다.   
개발자가 코드를 명백하게 짤수록 다른 사람이 그 코드를 이해하기 쉬워진다.
- #### 좋은 이름을 선택한다.
- #### 함수와 클래스 크기를 가능한 줄인다.
- #### 표준 명칭을 사용한다.
- #### 단위 테스트 케이스를 꼼꼼히 작성한다.
표현력을 높이는 가장 중요한 방법은 노력이다.
나중에 코드를 읽을 사람은 바로 자신일 가능성이 높다는 사실을 명심하자.