# 7. 오류 처리

오류는 프로그램에 반드시 필요한 요소 중 하나이며 잘못될 가능성을 바로잡을 책임을 위해 오류 처리를 한다.

## 오류 코드보다 예외를 사용하라

호출자 코드를 깔끔하게 유지하기 위해서, 오류가 발생하면 오류 코드를 출력하는 것보단 예외를 던지는 것이 낫다. 

## Try-Catch-Finally 문부터 작성하라

try 블록에서 무슨 일이 생기든 catch 블록은 프로그램 상태를
일관성있게 유지해야 하기 때문에 예외가 발생할 여지가 있는 코드를 짤 때는
try-catch-finally 문으로 코드의 틀을 잡고 가는것이 낫다.

## 미확인 예외를 사용하라

확인된 예외를 사용하여 메서드가 반환할 예외를 모두 열거하는 것이
멋진 아이디어로 여겨졌지만, 예외를 지원하지 않는 언어 또한
안정적인 소프트웨어를 제작하는 데 문제 없기 때문에 
미확인 예외를 사용하자.

## 예외에 의미를 제공하라

예외를 던질 때는 전후 상황을 충분히 덫붙이며,
오류 메세지에 정보를 담아 예외와 함께 던진다.

## 호출자를 고려해 예외 클래스를 정의하라

오류를 분류하는 것보다 더 중요한 것은 오류를 잡아내는 방법이다.
대다수 상황에서 우리가 오류를 처리하는 방식은 비교적
일정하고, 오류를 기록하고, 계속 수행해도 되는지 확인하는 과정이다.
즉, 예외 대응 방식은 예외 유형과 무관하게 거의 동일하다.

## 정상 흐름을 정의하라

## null을 반환하지 마라

null을 반환하는 코드는 일거리를 늘리고 호출자에게 문제를 떠넘긴다.

## null을 전달하지 마라

메서드에서 null을 반환, 전달하는 것 모두 다 나쁘다.

## 결론

