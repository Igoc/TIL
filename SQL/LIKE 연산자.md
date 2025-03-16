## LIKE 연산자

`WHERE` 절에서 지정된 패턴과 일치하는 값을 검색하는 데 사용된다.

### 예시

``` sql
SELECT *
FROM customer
WHERE name LIKE 'a%';
```

customer 테이블에서 name이 a로 시작하는 모든 행을 선택한다.

## 참고 자료

- [SQL LIKE Operator](https://www.w3schools.com/sql/sql_like.asp)