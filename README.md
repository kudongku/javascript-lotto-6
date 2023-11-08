1. 기능 목록 만들기

2. 구현하기 (기능단위별로 커밋하기)

### 라이브러리

    - `@woowacourse/mission-utils`에서 제공하는 `Random` 및 `Console` API를 사용하여 구현해야 한다.
      - Random 값 추출은 `Random.pickUniqueNumbersInRange()`를 활용한다.
      - 사용자의 값을 입력 받고 출력하기 위해서는 `Console.readLineAsync`, `Console.print`를 활용한다.
        MissionUtils.Random.pickUniqueNumbersInRange(1, 45, 6);

- 실행의 시작점은 `App.js`의 `play` 메서드이다. 아래와 같이 프로그램을 실행시킬 수 있어야 한다.
  const app = new App();
  app.play();

1. 로또 구입 금액을 입력 (로또 구입 금액을 입력 받는다. 구입 금액은 1,000원 단위로 입력 받으며 1,000원으로 나누어 떨어지지 않는 경우 예외 처리한다.)
   14000

2. 구입 금액에 해당하는 만큼 로또를 발행해야 한다. (로또 1장의 가격은 1,000원이다.)

3. 당첨 번호 입력받는다. (당첨 번호를 입력 받는다. 번호는 쉼표(,)를 기준으로 구분한다.)
   1,2,3,4,5,6

4. 보너스 번호를 입력 받는다.
   7

5. 사용자가 구매한 로또 번호와 당첨 번호를 비교한다.

6. 발행한 로또 수량 및 번호를 출력한다. 로또 번호는 오름차순으로 정렬하여 보여준다.
   8개를 구매했습니다.
   [8, 21, 23, 41, 42, 43]
   [3, 5, 11, 16, 32, 38]
   [7, 11, 16, 35, 36, 44]
   [1, 8, 11, 31, 41, 42]
   [13, 14, 16, 38, 42, 45]
   [7, 11, 30, 40, 42, 43]
   [2, 13, 22, 32, 38, 45]
   [1, 3, 5, 14, 22, 45]

7. 당첨 내역을 출력한다.
   3개 일치 (5,000원) - 1개
   4개 일치 (50,000원) - 0개
   5개 일치 (1,500,000원) - 0개
   5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
   6개 일치 (2,000,000,000원) - 0개

8. 수익률은 소수점 둘째 자리에서 반올림한다. (ex. 100.0%, 51.5%, 1,000,000.0%)
   총 수익률은 62.5%입니다

9. 로또 게임을 종료한다.
   프로그램 종료 시 `process.exit()`를 호출하지 않는다.

10. 예외처리
    사용자가 잘못된 값을 입력할 경우 `throw`문을 사용해 예외를 발생시킨다. 그런 다음, "[ERROR]"로 시작하는 에러 메시지를 출력하고 해당 부분부터 입력을 다시 받는다.
    예시 [ERROR] 숫자가 잘못된 형식입니다.
    예외 상황 시 에러 문구를 출력해야 한다. 단, 에러 문구는 "[ERROR]"로 시작해야 한다.
    [ERROR] 로또 번호는 1부터 45 사이의 숫자여야 합니다.

# 예시

    구입금액을 입력해 주세요.
    8000

    8개를 구매했습니다.
    [8, 21, 23, 41, 42, 43]
    [3, 5, 11, 16, 32, 38]
    [7, 11, 16, 35, 36, 44]
    [1, 8, 11, 31, 41, 42]
    [13, 14, 16, 38, 42, 45]
    [7, 11, 30, 40, 42, 43]
    [2, 13, 22, 32, 38, 45]
    [1, 3, 5, 14, 22, 45]

    당첨 번호를 입력해 주세요.
    1,2,3,4,5,6

    보너스 번호를 입력해 주세요.
    7

    당첨 통계

    ---

    3개 일치 (5,000원) - 1개
    4개 일치 (50,000원) - 0개
    5개 일치 (1,500,000원) - 0개
    5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
    6개 일치 (2,000,000,000원) - 0개
    총 수익률은 62.5%입니다.

    ---

3. 구현완료하면 test
   npm test

4. test 완료한 후 GitHub을 통해 제출해야 한다. (https://github.com/woowacourse/woowacourse-docs/tree/master/precourse)

5. GitHub에 미션을 제출한 후 [우아한테크코스 지원](https://apply.techcourse.co.kr) 사이트에 접속하여 프리코스 과제를 제출한다.
   (https://github.com/woowacourse/woowacourse-docs/tree/master/precourse#제출-가이드)

- 로또 게임 규칙
  - 1개의 로또를 발행할 때 중복되지 않는 6개의 숫자를 뽑는다. 로또 번호의 숫자 범위는 1~45까지이다.
  - 당첨 번호 추첨 시 중복되지 않는 숫자 6개와 보너스 번호 1개를 뽑는다.
  - 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 아래와 같다.
    - 1등: 6개 번호 일치 / 2,000,000,000원
    - 2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원
    - 3등: 5개 번호 일치 / 1,500,000원
    - 4등: 4개 번호 일치 / 50,000원
    - 5등: 3개 번호 일치 / 5,000원
