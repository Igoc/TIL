## HAVING 절

`WHERE` 절에는 집계 함수가 포함될 수 없기 때문에, 조건에 집계 함수를 사용하려면 `HAVING` 절을 사용해야 한다.

### 예시

``` sql
SELECT country
FROM customer
GROUP BY country
HAVING COUNT(id) >= 5;
```

customer 테이블에서 country에 포함된 id가 5개 이상인 행을 선택한다.

## 참고 자료

- [SQL HAVING Clause](https://www.w3schools.com/sql/sql_having.asp)