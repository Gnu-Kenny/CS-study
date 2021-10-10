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
