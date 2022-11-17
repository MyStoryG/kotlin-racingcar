# kotlin-racingcar

# step4) 레이싱 게임
## 기능 요구 사항
초간단 자동차 경주 게임을 구현한다.

- 각 자동차에 이름을 부여할 수 있다. 자동차 이름은 5자를 초과할 수 없다.
- 전진하는 자동차를 출력할 때 자동차 이름을 같이 출력한다.
- 자동차 이름은 쉼표(,)를 기준으로 구분한다.
- 자동차 경주 게임을 완료한 후 누가 우승했는지를 알려준다. 우승자는 한 명 이상일 수 있다.

## 구현할 기능 목록
-[X] 횟수 0 이하 입력 시 예외 처리
-[X] 자동차 이름 입력 받기
-[X] 자동차 이름 공백 입력 시 예외 처리
-[X] 자동차 이름 출력
-[X] 자동차 이름 5자 초과 금지
-[ ] 이름 중복 체크
-[ ] 이름 중 하나 이상 공백이 있을 경우 예외 처리하도록 조건 강화
-[ ] 우승자 선택하기
-[ ] 우승자 출력하기
-[ ] 테스트 코드 작성

# step3) 레이싱 게임
## 기능 요구 사항
초간단 자동차 경주 게임을 구현한다.

- 주어진 횟수 동안 n대의 자동차는 전진 또는 멈출 수 있다.
- 사용자는 몇 대의 자동차로 몇 번의 이동을 할 것인지를 입력할 수 있어야 한다.
- 전진하는 조건은 0에서 9 사이에서 무작위 값을 구한 후 무작위 값이 4 이상일 경우이다.
- 자동차의 상태를 화면에 출력한다. 어느 시점에 출력할 것인지에 대한 제약은 없다.

# step2) 문자열 계산기
## 기능 요구 사항
- 사용자가 입력한 문자열 값에 따라 사칙 연산을 수행할 수 있는 계산기를 구현해야 한다.
- 문자열 계산기는 사칙 연산의 계산 우선순위가 아닌 입력 값에 따라 계산 순서가 결정된다. 즉, 수학에서는 곱셈, 나눗셈이 덧셈, 뺄셈 보다 먼저 계산해야 하지만 이를 무시한다.
- 예를 들어 "2 + 3 * 4 / 2"와 같은 문자열을 입력할 경우 2 + 3 * 4 / 2 실행 결과인 10을 출력해야 한다.
## 프로그래밍 요구 사항
- 메서드가 너무 많은 일을 하지 않도록 분리하기 위해 노력해 본다.

## 힌트
테스트할 수 있는 단위로 나누어 구현 목록을 만든다.
- 덧셈
- 뺄셈
- 곱셈
- 나눗셈
- 입력값이 null이거나 빈 공백 문자일 경우 IllegalArgumentException throw
- 사칙연산 기호가 아닌 경우 IllegalArgumentException throw
- 사칙 연산을 모두 포함하는 기능 구현

## 개인적으로 추가 고려한 사항
- 시작 시 "계산식을 입력하세요." 문구 출력
- 처음 입력이 연산자로 시작 시 IllegalArgumentException 발생 (ex. - 1 + 2)
- 마지막 입력이 연산자로 끝날 시 IllegalArgumentException 발생 (ex. 1 +)
- 위 두 경우에 대하여 "- 1 + 2" = 1, "1 +" = 1 로 처리하도록 변경이 쉬운 구조로 작성
- 0으로 나눌 시 IllegalArgumentException 발생
- 음수, 소수 계산 가능하도록 하기
- 결과는 소수 두 번째 자리에서 반올림하여 나타내기
- 
## 피드백 반영 사항
- 상수 클래스 제거하여 결합도 낮추기
- 들여쓰기 레벨 낮추기
- Enum 사용하여 조건문 없애기
- Exception 메시지로 로그 처리
- IndexOutOfBoundsException 마지막 연산에서 발생하기
- Operand에서 Double 자료형 가지도록 수정
- 테스트 코드 메서드 분리하여 한가지 기능만 검사하도록 수정
- 백틱을 활용하여 테스트 의도 명시적으로 나타내기
- assertAll()로 assert 단언문 복수개를 대체
## 미반영사항
- operand의 operandList를 꺼내지 않고 사용하기 : 프로퍼티에 직접 접근하는 대신 메시지를 던지는 것이 어떤 의미인지 파악 못함
- 유효성 검사 로직을 별도 클래스로 분리하는 대신 필요한 도메인 객체에서 선언하기 : (상수는 그렇게 적용해 보았으나) 유효성 검사 로직을 중복으로 선언 시 변경점 발생 시 어려움이 있다고 판단되어 보류하고 문의
