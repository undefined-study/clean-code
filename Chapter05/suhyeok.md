# [5장] 형식 맞추기

코드 형식을 맞추기 위한 간단한 규칙을 정하고 그 규칙을 착실히 따라야 한다.

## 형식을 맞추는 목적

코드 형식은 중요하다.

융통성 없이 맹목적으로 따르면 안 된다.

오늘 구현한 코드의 가독성은 앞으로 바뀔 코드의 품질에 지대한 영향을 미친다.

원래 코드는 사라질지라도 개발자의 스타일과 규율은 사라지지 않는다.

## 적절한 행 길이를 유지하라

일반적으로 큰 파일보다 작은 파일이 이해하기 쉽다.

### 신문 기사처럼 작성하라

이름은 간단하면서도 설명이 가능하게 짓는다.

처음에는 고차원 개념과 알고리즘을 설명하고 아래로 내려갈수록 의도를 세세하게 묘사한다. 마지막에는 가장 저차원 함수와 세부 내역이 나온다.

### 개념은 빈 행으로 분리하라

### 세로 밀집도

세로 밀집도는 연관성을 의미한다.

서로 밀접한 코드 행은 세로로 가까이 놓여야 한다는 뜻이다.

### 수직 거리

변수는 사용하는 위치에서 최대한 가까이 선언한다.

종속 함수

한 함수가 다른 함수를 호출한다면 두 함수는 세로로 가까이 배치한다. 또한 가능하다면 호출하는 함수를 호출되는 함수보다 먼저 배치한다.

### 세로 순서

함수 호출 종속성은 아래 방향으로 유지한다.

## 가로 형식 맞추기

### 들여쓰기

범위로 이뤄진 계층을 표현하기 위해 코드를 들여쓴다.

## 팀 규칙

프로그래머라면 각자 선호하는 규칙이 있다. 하지만 팀에 속한다면 자신이 선호해야 할 규칙은 바로 팀 규칙이다.

스타일은 일관적이고 매끄러워야 한다.

## 밥 아저씨의 형식 규칙

코드 자체가 최고의 구현 표준 문서가 되는 예다.