## UNION 절

- 두 개 이상의 쿼리 결과를 결합하는 데 사용된다.
- 각각의 쿼리 결과에 포함된 열의 개수와 순서가 일치해야 한다.
- 결합하려는 열들은 비슷한 자료형을 갖고 있어야 한다.
- 결합 후 중복된 값들은 제거되어 1개씩만 남으며, 중복된 값들을 제거하고 싶지 않다면 `UNION ALL`을 사용해야 한다.

### 예시

``` sql
SELECT title
FROM album
UNION
SELECT title
FROM music;
```

album 테이블에서 선택한 title 열과 music 테이블에서 선택한 title 열을 결합한 뒤 중복된 값들은 제거한다.

## 참고 자료

- [SQL UNION Operator](https://www.w3schools.com/sql/sql_union.asp)
- [MySQL :: MySQL 8.4 Reference Manual :: 15.2.18 UNION Clause](https://dev.mysql.com/doc/refman/8.4/en/union.html)