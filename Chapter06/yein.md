<div align="center">
  <h1>Chapter06 : 객체와 자료 구조</h1>
</div>

**[독서 포인트]**
<br />
📌 객체 vs 자료 구조

<br />

## 자료 추상화

- 구현을 감추려면 추상화가 필요하다.

- 진정한 의미의 클래스: 사용자가 구현을 모른 채 자료의 핵심을 조작할 수 있어야.

- 정보가 어디서 오는지 드러나지 않도록 작성해야

- 단순히 get, set 함수를 추가한다고 해서 추상화가 저절로 이루어지는 게 아님.

## 자료/객체 비대칭

- 자료 구조 <---> 객체

  - 객체(클래스)

    - 자료는 숨긴 채 자료를 다루는 함수만 공개함.

    - 객체 지향 코드

    - 새로운 **함수**를 추가하기 어려움.

  - 자료 구조

    - 자료를 그대로 공개하며, 별다른 함수는 제공하지 않음.

    - 절차적인 코드

    - 새로운 **자료 구조**를 추가하기 어려움.

## 디미터 법칙(또는 데메테르 법칙)

- 모듈은 자신이 조작하는 객체의 속사정을 몰라야 한다는 법칙 => 객체는 get 함수로 내부 구조를 공개하면 안 된다!

- 자료 구조에는 디미터 법칙이 적용되지 않는다.

### 기차 충돌

- (메서드 체이닝?)

- 조잡해서 비추인 건 알겠는데..

- *디미터 법칙을 위반하는 경우, 어떻게 위반한다는 것인지* 글만 봐서는 잘 모르겠다.

### 잡종 구조

- 절반은 객체, 절반은 자료 구조(~~끔찍한 혼종~~, ~~반인반수~~)

- get, set 함수로 비공개 변수를 그대로 노출하기도..

- 확신 없는 어중간한 설계~

### 구조체 감추기

- 객체에게는 **뭔가를 하라**고 말해야지, **속을 드러내라**고 말하면 안된다.

## 자료 전달 객체

- 자료 구조체의 전형적인 형태: 공개 변수만 있고, 함수는 없는 클래스 => 자료 전달 객체(Data Transfer Object)

- DTO는 db와 통신하는 경우에도 유용

  - 주로 db에 저장되어 있는 가공되지 않은 정보를 애플리케이션 코드에서 사용할 객체로 변환하는 과정에서 맨 첫 단계에서 사용하는 구조체

- bean 구조가 일반적이나, 이는 사이비 캡슐화(private 변수를 get, set으로 조작하는 것)하는 것이므로 지양할 것

### 활성 레코드

- DTO의 특수한 형태

- 여기에 비즈니스 로직을 추가해서 이 자료 구조를 객체로 취급하는 것은 지양해야 함. => 끔찍한 혼종이 되기 때문

- 활성 레코드는 자료 구조로 취급하기! => 비즈니스 로직을 담아야 한다면 이것과 별개로 객체를 생성해서 거기에 담기
