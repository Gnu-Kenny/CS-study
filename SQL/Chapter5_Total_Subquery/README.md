# 집계와 서브쿼리

**대표 집계 함수**

> COUNT(집합)  
> SUM(집합)  
> AVG(집합)  
> MIN(집합)  
> MAX(집합)

<br>

## 1. 행 개수 구하기 - COUNT

```sql
SELECT COUNT(*) FROM sample51;
```

- SQL은 집합을 다루는 집계함수를 제공한다. 인수로 집합을 지정.

- 위의 식에서는 테이블에 있는 행의 개수를 출력한다.

- 이 때 COUNT 집계함수는 '모든 열 = 테이블 전체'라는 의미로 사용한다.

- 집계함수는 집합으로부터 하나의 값을 반환한다.

- **즉, COUNT 집계함수로 행 개수를 구할 수 있다.**

### WHERE 구 지정

```sql
SELECT COUNT(*) FROM sample51 WHERE name='A';
```

- SELECT구는 WHERE구보다 나중에 내부적으로 처리된다.

- 따라서 WHERE구로 조건을 지정하면 테이블 전체가 아닌, 검색된 행이 COUNT로 넘겨진다.

- 즉, WHERE 구의 조건에 맞는 행의 개수를 반환한다.

## 2. 집계함수와 NULL 값

```sql
SELECT COUNT(no), COUNT(name) FROM sample51;
```

- COUNT 인수로 열명을 지정할 수 있다.

- 열 명을 지정하면 그 열에 한해서 행의 개수를 구할 수 있다.

- 집계함수는 집합 안에 NULL 값이 있을 경우 이를 제외하고 처리한다.

- COUNT(\*) 를 하는 경우에는 모든 열의 행수를 카운트하기 때문에 NULL 값이 있어도 해당 정보가 무시되지 않는다.

- 집계 함수는 집합 안에 NULL 값이 있을 경우 무시한다.

## 3. DISTINCT로 중복 제거

```sql
SELECT DISTINCT name FROM sample51;
```

- 데이터가 중복되지 않는 '유일한 값'을 가지도록 중복된 값을 제거하는 함수를 DISTINCT라 한다.

- SELECT 구에서 DISTINCT를 지정하면 중복된 데이터를 제외한 결과를 클라이언트로 반환한다.

- ALL, DISTINCT 중 어느것도 지정하지 않은 경우 중복된 값은 제거되지 않는다. 즉, 생략한 경우 ALL 로 간주한다.

## 4. 집계함수에서 DISTINCT

```sql
SELECT COUNT(ALL name), COUNT(DISTINCT name) FROM sample51;
```

- 집계함수의 인수로 DISTINCT를 사용한 수식을 지정할 수 있다.

- 위의 식에서는 name열에서 NULL 값을 제외하고, 중복하지 않는 데이터의 개수를 반환한다.

# 21강 COUNT 이외의 집계 함수

## 1. SUM으로 합계 구하기

```sql
SELECT SUM(quantity) FROM sample51;
```

- SUM 집계함수를 사용해 집합의 합계를 구할 수 있다.
- SUM 집계함수에 지정되는 집합은 수치형 뿐이다.
- 문자열형이나 날짜시간형의 집합에서 합계를 구할 수는 없다.
- SUM 집계함수도 마찬가지로 NULL 값을 무시한다. 따라서 NULL 값을 제거한 뒤에 합계를 낸다.

## 2. AVG로 평균내기

```sql
SELECT AVG(quantity), SUM(quantity)/COUNT(quantity) FROM sample51;
```

- AVG 집계함수를 통해 평균값을 간단하게 구할 수 있다.

- AVG 집계함수에 주어지는 집합은 수치형만 가능하다.

- 또한 NULL 값은 무시하므로 NULL 값 제거 뒤에 평균값을 계산한다.

- NULL 값을 0으로 간주해서 평균내고 싶은 경우 CASE를 사용해 NULL을 0으로 변환 뒤 계산한다.

- ```sql
  SELECT AVG(CASE WHEN quantity IS NULL THEN 0 ELSE quantity END) AS avgnull0 FROM sample51;
  ```

## 3. MIN, MAX로 최솟값, 최댓값 구하기

```sql
SELECT MIN(quantity), MAX(quantity), MIN(name), MAX(name) FROM sample51;
```

- MIN, MAX 집계함수를 사용해 집합에서 최솟값과 최댓값을 구할 수 있다.

- 문자열형과 날짜시간형에도 사용할 수 있다.

- NULL 값은 무시한다.

# 22강 그룹화 - GROUP BY

GROUP BY 구를 사용해 집계함수로 넘겨줄 집합을 그룹으로 나눈다.

## 1. GROUP BY로 그룹화

```sql
SELECT name FROM sample51 GROUP BY name;
```

- 위의 식에서 name 열에서 같은 값을 가진 행끼리 묶어 그룹화한 집합을 집계함수로 넘겨줄 수 있다.

- 그룹으로 나눌 때 GROUP BY 구를 사용하여 그룹화할 열을 지정할 수 있다.

- GROUP BY 구에 열을 지정하여 그룹화하면 지정된 열의 값이 같은 행이 하나의 그룹으로 묶인다.

- 결과적으로 각각의 그룹 값이 반환된다.

- 따라서 GROUP BY를 지정해 그룹화하면 DISTINCT와 같이 중복을 제거하는 효과가 있다.

<br>

**GROUP BY 함수를 집계함수와 같이 사용해보자.**

```sql
SELECT name, COUNT(name), SUM(quantity) FROM sample51 GROUP BY name;
```

- 점포별, 상품별, 월별, 일별 등 특정 단위로 집계할 때 GROUP BY를 자주 사용한다.
- 매출 실적을 조사하는 동시에 SUM 집계함수로 합계를 낼 수 있으며, COUNT로 건수를 집계하기도 한다.

## 2. HAVING 구로 조건 지정

```sql
SELECT name, COUNT(name) FROM sample51 GROUP BY name HAVING COUNT(name)=1;
```

- 집계 함수는 WHERE구의 조건식에서는 사용할 수 없다.

- WHERE구로 행을 검색하는 처리가 GROUP BY로 그룹화하는 처리보다 순서상 앞서기 때문이다.

- 내부 처리 순서는 다음과 같다.

- WHERE → GROUP BY → SELECT → ORDER BY

- 따라서 집계한 결과에서 조건에 맞는 값을 따로 걸러내기 위해서는 HAVING 구를 사용한다.

- HAVING 구는 GROUP BY구의 뒤에 기술하며 WHERE 구와 동일하게 조건식을 지정할 수 있다.

<br>

### 내부처리 순서

**WHERE → GROUP BY → HAVING → SELECT → ORDER BY**

## 3. 복수열의 그룹화

```sql
SELECT MIN(no), name, SUM(quantity) FROM sample51 GROUP BY name;
```

- GROUP BY에 지정한 열 이외의 열은 집계함수를 사용하지 않은 채 SELECT 구에 기술해서는 안된다.

- GROUP BY로 그룹화하면 클라이언트로 반환되는 결과는 그룹당 하나의 행이 된다.

- 이 때 집계함수를 사용하면 집합은 하나의 값을 계산되므로, 그룹마다 하나의 행을 출력할 수 있다.

- GROUP BY에서 지정한 열 이외의 열은 집계함수를 사용하지 않은 채 SELECT 구에 지정할 수 없다.

## 4. 결괏값 정렬

```sql
SELECT name, COUNT(name), SUM(quantity) FROM sample51 GROUP BY name ORDER BY SUM(quantity) DESC;
```

- GROUP BY로 구로 그룹화한 경우에도 ORDER BY를 사용해 정렬할 수 있다.

- 기본값은 ASC이다.
