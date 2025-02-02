## DISTINCT 절

쿼리 결과에서 중복된 값들을 제거하여 1개씩만 남긴다.

### 예시

``` sql
SELECT DISTINCT country
FROM customer;
```

customer 테이블에서 country 열을 선택한 뒤 중복된 값들은 제거한다.

## 참고 자료

- [SQL SELECT DISTINCT Statement](https://www.w3schools.com/sql/sql_distinct.asp)