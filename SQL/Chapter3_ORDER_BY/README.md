# 9강 정렬 - ORDER BY

```sql
SELECT 열명 FROM 테이블명 WHERE 조건식 ORDER BY 열명
```

- 검색 결과의 행 순서를 바꿀 수 있다.

## 1. ORDER BY로 검색 결과 정렬하기

- SELECT 명령의 ORDER BY 구로 정렬하고 싶은 열을 지정한다.
- 저정된 열의 값에 따라 행 순서가 변경된다.

```sql
SELECT * FROM sample31 ORDER BY age;
```

## 2. ORDER BY DESC로 내림차순 정렬하기

```sql
SELECT 열명 FROM 테이블명 WHERE 조건식 ORDER BY 열명 DESC
```

## 3. 대소관계

- 수치형 데이터

  - `1 < 2 < 10 < 100`

- 날짜시간형 데이터

  - `1999년 < ... < 2013년 < 2014년`

- 문자형 데이터

  - 자모음 배열 순서를 적용 == 사전식 순서에 의해 결정된다.

  - 나비, 가방 가족 정렬할 경우
    1. 가방
    2. 가족
    3. 나비

### 사전식 순서시 주의점

|   a |   b |
| --: | --: |
|   1 |   1 |
|   2 |   2 |
|  10 |  10 |
|  11 |  11 |

- a 열이 문자열형(VARCHAR), b 열이 수치형(INTEGER)

- 해당 테이블 정렬시

  |   a |   b |
  | --: | --: |
  |   1 |   1 |
  |  10 |   2 |
  |  11 |  10 |
  |   2 |  11 |

## 4. ORDER BY는 테이블에 영향을 주지 않는다.

<br>

# 10강 복수의 열을 지정해 정렬하기

```sql
SELECT 열명 FROM 테이블명 WHERE 조건식 ORDER BY 열명1 [ASC|DESC], 열명2 [ASC|DESC]
```

## 1. 복수 열로 정렬 지정

```sql
SELECT 열명 FROM 테이블명 WHERE 조건식 ORDER BY 열명1, 열명2
```

- 열명1로 정렬하고 값이 같은 부분은 b열로 정렬한다.

## 2. 정렬방법 지정하기

```sql
SELECT 열명 FROM 테이블명 WHERE 조건식 ORDER BY 열명1 [ASC|DESC], 열명2 [ASC|DESC]
```

- 복수 열을 지정한 경우에도 각 열에 대해 개별적으로 정렬방법을 지정할 수 있다.

## 3. NULL 값의 정렬순서

- ORDER BY로 지정한 열에서 NULL 값을 가지는 행은 가장 먼저 표시되거나 가장 나중에 표시된다.

- NULL에 대한 대소비교 방법은 데이터베이스 제품에 따라 기준이 다르다.

- MySQL의 경우 NULL 값을 가장 작은 값으로 취급해 ASC에서 가장 먼저 표시한다.

# 11강 결과 행 제한하기 - LIMIT

```sql
SELECT 열명 FROM 테이블명 LIMIT 행수 [OFFSET 시작행]
```

## 행수 제한

- MySQL과 PostgreSQL에서만 사용할 수 있다.

```sql
SELECT 열명 FROM 테이블명 WHERE 조건식 ORDER BY 열명 LIMIT 행수 [OFFSET 시작행]
```

- WHERE 구나 ORDER BY 구의 뒤에 지정

- LIMIT 다음에는 최대 행수를 수치로 지정한다.

### 정렬 후 제한하기

- `WHERE no <= 3` 과 같은 조건을 붙인다면 `LIMIT 3` 같은 결과를 얻을 수 있다.
- 하지만 기능과 내부 처리 순서가 다르다.
- ORDER BY로 정렬된 뒤 최종적으로 처리한다.

### 다른 데이터베이스에서의 행 제한

- `TOP`을 사용할 수 있다.

```sql
SELECT TOP 3 FROM sample33;
```

- Oracle의 경우 ROWNUM이라는 열을 사용해 WHERE 구로 조건을지정하여 행 제한이 가능하다.

```sql
SELECT * FROM sample33 WHERE ROWNUM <= 3;
```

## 오프셋 지정

- 페이지 나누기 시 첫 번째 페이지 첫 행을 결정할 떄 쓰인다.

```sql
SELECT * FROM sample33 LIMIT 3 OFFSET 0;
```

- sample33에서 LIMIT 3 OFFSET 0으로 첫 번째 페이지 표시

- 시작할 행 - 1로 기억하면 편하다.

# 12강 수치 연산

## 사칙 연산

- 연산자는 기호로 표기한다.

  - `+ = * / %`

### 연산자의 우선순위

1. `* / %`

2. `+ -`

우선 순위가 같다면 왼쪽에서 오른쪽으로 계산

<br>

우선 순위가 다르다면 우선순위가 높은 것 먼저 계산

## SELECT 구로 연산하기

```sql
SELECT *, price * quantity FROM sample33;
```

- 연산된 필드 값이 추가된다.

## 열의 별명 - AS

```sql
SELECT *, price * quantity AS amount FROM sample33;
```

- `price * quantity`라고 명명된 열은 알아보기 어려우므로 별명을 통해 재지정하는 것이 좋다.

- 키워드 생략도 가능하다.

  - 단 별명 한글로 지정하는 경우 오작동 방지를 위해 더블쿼트("")로 둘러싸서 지정한다.

  - 데이터베이스 객체명 -> 더블쿼트

  - 문자열 상수 -> 싱글쿼트

## WHERE 구에서 연산하기

```sql
SELECT *, price * quantity AS amount FROM sample33 WHERE amount >= 2000;
```

- `WHERE 구 -> SELECT 구` 순서로 처리된다.

## NULL 값의 연산

- NULL로 연산하면 결과는 NULL이 된다.
