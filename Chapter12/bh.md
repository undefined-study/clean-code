### 단순한 설계 규칙 1: 모든 테스트를 실행하라

무엇보다 의도한 대로 돌아가는 시스템을 내놓아야 한다. 하지만, [나쁜코드](https://github.com/undefined-study/clean-code/blob/main/Chapter01/bh.md#%EB%82%98%EC%81%9C-%EC%BD%94%EB%93%9C)
에서 언급했듯, '안 돌아가는 프로그램보다 돌아가는 쓰레기가 좋다고..' 다시 돌아와 정리하겠다고 다짐했지만, 나중은 결코 오지 않는다는 것을 명심하고
클린한 코드를 생산하기 위해 노력해야 한다.

_여기서, '의도한 대로 돌아가는 시스템' 에서 의도한 대로 돌아간다는 증명은 무엇이 할까?_
시스템이 의도한 대로 돌아가는 지 검증할 간단한 방법이 없다면, 문서 작성을 위해 투자한 노력에
대한 가치는 인정받기 힘들고, 테스트가 불가능한 시스템은 검증도 불가능하니 검증이 불가능한 시스템은
절대 출시하면 안된다.

테스트 가능한 시스템을 만들려고 애쓰면 설계 품질이 더욱 높아진다.
SRP(단일 책임 원칙)을 지켜 크기가 작고 목적 하나만 수행하는 클래스가 나오도록
코드를 작성하면 테스트 하기가 훨씬 쉽다. 

_외람된 이야기일 수 있지만, 리엑트에서 여러 분기를 걸쳐 결과값을 랜더링하는 로직들이 있다면
(아래 예시보다 훨씬 복잡할 것) 같은 결과를 테스트하고자 하지만, 작은 분기를 담당하는 로직이라도
함수로 단일 책임 원칙으로 함수로 분리해서 작성하면 테스트 자원을 오히려 아낄 수 있지 않을까..?_

### 리엑트 컴포넌트 테스팅

```tsx
//PaymentHistoryCard.tsx
const PaymentHistoryCard = ({paymentHistory}: PaymentHistoryProps) => {
  return (
    <div data-testid="payment-method">
      {paymentHistory.paymentMethod === PaymentMethodEnum.BankTransfer ? '계좌 이체' : '카드 결제'}
    </div>
  );
}
```

```tsx
//PaymentHistoryCard.test.tsx

const mockPaymentHistory = {
  paymentMethod: PaymentMethodEnum.BankTransfer,
}

render(<PaymentHistoryCard paymentHistory={mockPaymentHistory}/>)

it('결제 내역의 결제 방식을 확인할 수 있다.', () => {
  const paymentMethodElement = screen.getByTestId('payment-method');
  expect(paymentHistoryElement).toHaveTextContent('계좌 이체');
})
```

#### 함수 테스팅

```ts
//paymentHistoryRenderHelper.ts

const renderPaymentMethod = (paymentMethod) => {
  return paymentMethod === PaymentMethodEnum.BankTransfer ? '계좌 이체' : '카드 결제';
}
```

```tsx
//PaymentHistoryCard.tsx
const PaymentHistoryCard = ({paymentHistory}: PaymentHistoryProps) => {
  return (
    <div data-testid="payment-method">
      {renderPaymentMethod(paymentHistory.paymentMethod)}
    </div>
  );
}
```

```ts
//PaymentHistoryRenderHelper.test.ts

const mockPaymentHistory = {
  paymentMethod: PaymentMethodEnum.BankTransfer,
  ...
}

expect(renderPaymentMethod(mockPaymentHistory.paymentMethod)).toEqual('계좌 이체');
```

테스트 케이스가 많을수록 개발자는 쉽게 코드를 작성할 수 있다. 따라서 철저한 테스트가 가능한
시스템을 만들기 위한 설계를 해야한다. 

결합도가 높으면 테스트 케이스를 작성하기 어렵다. 앞서 마찬가지로 테스트 케이스를 많이 작성할수록
개발자는 DIP 같은 원칙을 적용 (의존성 주입, 인터페이스, 추상화 등)과 같은 도구를 통해
의존성을 낮춘다. 

_리엑트 컴포넌트에서 커스텀 훅을 사용하는 이유..가 props를 최소화하면서도
의존성을 주입할 수 있어서가 아닐까? 예시로 컴포넌트의 props가 많으면 의존성이
높고, 테스트하기도 어려워진다...이건 [chapter03/함수 인수](https://github.com/undefined-study/clean-code/blob/main/Chapter03/jisu.md#-%ED%95%A8%EC%88%98-%EC%9D%B8%EC%88%98)를 최소화하는 것이 중요하다는 것과
같은 맥락이 아닐까 싶다._

```tsx
//PaymentHistoryCard.test.tsx

const mockA = {...}
const mockB = {...} 
const mockC = {...}

render(
  <Component
    A={mockA}
    B={mockB}
    C={mockC}
    ...
  )
```

### 단순한 설계 규칙 2~4: 리팩터링

테스트 케이스를 모두 작성했다면 이제 코드와 클래스를 정리해도 좋다.
만약 만약 add() 함수가 있다고 해보자.

```js
function add(a, b) {
  if (!isNumber(a) || !isNumber(b)) return 0;
  return Math.sqrt(Math.pow(a, 2)) + Math.sqrt(Math.pow(a, 2)); // ?
}
```

_add() 함수에 대한 테스트 케이스를 작성해두고, 테스트 케이스가 실패되면
PR이 클로즈된다던지, CI 레벨에서 머지가 불가능하게 만들어두었다고 가정한다면,
테스트 케이스가 있기 때문에 부담없이 보다 간편한 함수로 리팩토링하기 편해진다._

```js
expect(add(1, 2)).toBe(3);
expect(add(5, 5)).toBe(10);
expect(add(1, '3')).toBe(0);
expect(add(1, undefined)).toBe(0);
expect(add('1', '3')).toBe(0);
```

```js
function add(a, b) {
  if (!isNumber(a) || !isNumber(b)) return 0;
  return a + b;
}
```

코드 정리하면서 시스템이 깨질까 걱정할 필요가 없다. 테스트 케이스가 있으니까!

- 응집도를 높이고
- 결합도를 낮추고
- 관심사를 분리하고
- 시스템 관심사를 모듈로 나누고
- 함수와 클래스 크기를 줄이고
- 시스템 관심사를 모듈로 나누고
- 중복을 제거하고
- 프로그래머의 의도를 표현하고
- 클래스와 메서드 수를 최소로 줄이고

마음껏 리팩토링할 수 있다.

_최근 테스트 코드를 작성하면서, 테스트하기 쉬운 코드를 생산하고 테스트 케이스를
많이 만들어두면 신나는 리팩토링이 가능하지 않을까 생각이 많이 든다._

