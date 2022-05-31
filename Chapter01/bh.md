# 1장. 깨끗한 코드

`'코드 품질을 측정하는 유일한 첫도 = 분 당 내지르는 WTF! 횟수'`,

프로그래머라서, 더 나은 프로그래머가 되려고 이 책을 읽는다. 이 책은 온통 코드들이고, 코드를 최대한 다양한 각도에서 살펴본다.
사방을 돌리고 안팎으로 뒤집으며 꼼꼼히 따져본다. 좋은 코드와 나쁜 코드를 구분하는 능력도 생긴다.
또한, 좋은 코드를 작성하는 방법도 익히며, `나쁜 코드를 좋은 코드로 바꾸는 실력도 쌓인다.`

### 코드가 존재하리라

`'코드는 요구사항을 상세히 표현하는 수단이다.'`, 코드를 자동으로 생성하는 시대가 다가오면, 프로그래머는 필요가 없다?
어떤 언어를 사용하든, 우리 프로그래밍 언어에서 추상화 수준은 점차 높아질 것이고, 고도로 추상화된 언어나
특정 응용 분야 언어로 기술을 명세하는 것 역시 코드다. 어떤 언어를 사용하든 코드는 기계가 이해하고 실행할 정도로
엄밀하고 정확하고 상세하게 정형화되어야 한다.

`'요구 사항을 모호하게 줘도 우리 의도를 정확히 꿰뚫어 프로그램을 완벽하게 실행하는 기계가 나오리라 기대한다.'`,
절대로 불가능한 기대이다. 코드는 요구사항을 표현하는 언어라는 사실을 명심하자. 창의력과 직관을 보유한 우리 인간조차도 고객의 막연한
감정만 갖고는 성공적인 시스템을 구현하지 못하며, 제대로 명시한 요구사항은 코드만큼 정형적이며 테스트 케이스로 삼기 좋다.

### 나쁜 코드

`'좋은 코드는 중요하다'`, 나쁜 코드에 시달려온 우리는 좋은 코드가 중요하며 가장 든든하고, 지지 받고 강조되어 온 전제라는 것을 경험한다.

`'출시에 바빠 코드를 마구 짰다'`, 커다란 인기를 끌었고 수많은 전문가가 구매해 사용했던 앱이 제품 출시 주기가 늘어지고,
프로그램 시동 시간이 길어지고, 죽는 횟수 또한 늘어났다. 원인은 엉망이 된 나쁜 코드 탓에 회사가 망해버린 것이 아닌가.

`'안 돌아가는 프로그램보다 돌아가는 쓰레기가 좋다고'`, 프로그래머는 누구나 나쁜 코드를 경험한다.
어째서 나쁜 코드를 짰는가! 급해서 서둘러 작업을 마무리 하며, 다시 돌아와 정리하겠다고 다짐했지만, 나중은 결코 오지 않는다.

### 나쁜 코드로 치르는 대가

`'간단한 변경이 없다'`, 코드를 고치면 엉뚱한 곳에서 문제가 생긴다. 그러니 해독 작업은 덤이며,
나쁜 코드는 개발 속도를 크게 저하시킨다는 것을 알면서 문제는 청소할 시간도 없이 다시 해독을 해야 한다.

#### 1. 원대한 재설계의 꿈

`'새 시스템이 기존 시스템을 따라잡을 즈음이면 초창기 타이거 팀원들은 모두 팀을 떠났고''''`,
원대한 재설계보단, 시간을 들여 깨끗한 코드를 만드는 노력이 비용을 절감하는 방법일 뿐만 아니라
전문가로서 살아남는 길이라는 사실을 인정하자.

#### 2. 태도

`'우리는 프로젝트를 계획하는 과정에 깊숙히 관여한다'`, 나쁜 코드로 전락하게 된 이유는 전적으로 우리 프로그래머에게 있다.
요구사항, 일정은 약속된 것이고, 약속은 일방적이지 않은 자문 형태로 진행되었다. 그러므로 프로젝트 실패는 우리에게도
커다란 책임이 있다.

`'좋은 코드를 사수하는 일은 바로 우리 프로그래머들의 책임이다'`, 나쁜 코드의 위험을 이해하지 못하는 관리자 말을
그대로 따르는 행동은 전문가답지 못하다.

#### 3. 원초적 난제

`'빨리 가는 유일한 방법은 언제나 코드를 최대한 깨끗히 유지하는 습관이다'`, 빨리 가려 양산한 나쁜 코드가 절대 빠른 것이 아니란 걸
잘 알고 있다.

#### 4. 깨끗한 코드라는 예술?

`'깨끗한 코드, 나쁜 코드를 구분할 줄 안다고 깨끗한 코드를 작성할 줄 안다는 뜻은 아니다'`,
'청결'이라는 힘겹게 얻은 감각을 활용해 자잘한 기법들을 적용하는 절제와 규율이 필요하다.
'코드 감각'을 통해 최고의 방안을 선택한 후 이동 경로를 계획하며, 나쁜 모듈을 구분짓고 이에 대한 개선 방안을 떠올린다.

#### 5. 깨끗한 코드란?

`'우아한, 교묘하고 단순해 보기에 즐거운'`, 깨끗한 코드는 보는 사람에게 즐거움을 선사해야 한다는 뜻이다.
우아하지 않은 코드는 바람직하지 않은 결과를 초래하며, 나쁜 코드는 나쁜 코드를 '유혹'한다고 치환된다.

`'깨끗한 코드는 세세한 사항까지 꼼꼼하게 처리하는 코드다'`, 프로그래머들이 대충 넘어가는 부분 중 하나가 오류 처리이며 이 또한
세세하게 처리하는 코드가 깨끗한 코드이다.

`'깨끗한 코드란 한 가지를 잘 한다고 단언한다'`, 너무 많은 일을 하려 애쓰다가 의도가 뒤섞이고 목적이 흐려지는 나쁜 코드, 반면
깨끗한 코드는 한 가지에 '집중'한다.

`'잘 쓴 문장처럼 읽혀야 한다는 시각을 특히 좋아한다'`, 해결할 문제의 긴장을 명확히 드러내야 하며, 명백한 해법을 제시하여
긴장과 문제를 풀어주어야 한다. 이것이 불필요한 사실에 얽매이지 않는 '명쾌한 추상화'이다.

`'읽기 쉬운 코드와 고치기 쉬운 코드는 엄연히 다르다'`, 테스트 케이스가 없는 코드는 깨끗한 코드가 아니다라는 말은
라는 가장 근본적인 원칙 중 하나가 된 TDD 개발 방식을 이끌었다.

`'같은 작업을 여러 차례 반복한다면 코드가 아이디어를 제대로 표현하지 못한다는 증거다'`, 표현력은 의미 있는 이름을 포함하며,
확정하기 전에 이름을 여러 차례 바꾼다. 객체, 메서드가 여러 기능을 수행한다면 여러 객체, 메서드로 나눈다.

`'언어를 단순하게 보이도록 만드는 열쇠는 프로그래머다'`, 읽으면서 짐작한 대로, 명백하고 단순해 마음이 끌리는, 다음에 벌어질 상황이 보이는
코드가 깨끗한 코드이다. 코드가 그 문제를 풀기 위한 언어처럼 보인다면 아름다운 코드라 할 수 있다.

### 우리들 생각

`'각 문과에 입문한 학생들은 창시자의 가르침을 익히고 연마한다, 물론 절대적으로 옳은 문파는 없다. 자신의 문파가 가르치는 교훈과 기술을 가장 좋다고 간주한다.'`,
우리 생각이 절대적으로 옳다라고 단정은 금물이다. 우리들 못지않게 전문가가 존재하며, 마땅히 그들에게서도 배우라고 권한다.

### 우리는 저자다

`'주변 코드가 읽기 쉬우면 새 코드를 짜기도 쉽다'`, 급하다면, 서둘러 끝내야 한다면 쉽게 짜려면 읽기 쉽게 만들면 된다.

### 보이스카우트 규칙

`'지속적인 개선이야말로 전문가 정신의 본질이 아니던가'`, 한꺼번에 많은 시간과 노력을 투자해 코드를 정리할 필요가 없고,
하나를 개선하고, 조금 긴 함수를 분할하고 중복을 제거하며 복잡한 `if` 문 제거면 충분하다.

### 프리퀄과 원칙

### 결론

`'연습해 연습'`, 다양한 경험적 교훈과 체계와 절차와 기법도 열거한다. 좋은 코드 뿐만 아니라, 나쁜 코드를 보는 것도 경험이다.