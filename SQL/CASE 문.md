## CASE 문

- 조건을 만족할 경우 해당하는 결과를 반환한다.
- 현재 조건이 참이라면 다음 조건을 확인하지 않고 바로 결과를 반환한다.
- ELSE가 없는 상태에서 모든 조건이 참이 아니라면 NULL을 반환한다.

``` sql
CASE
    WHEN <condition 1> THEN <result 1>
    WHEN <condition 2> THEN <result 2>
    WHEN <condition N> THEN <result N>
    ELSE <result>
END
```

## 참고 자료

- [SQL CASE Expression](https://www.w3schools.com/sql/sql_case.asp)
- [MySQL :: MySQL 8.4 Reference Manual :: 15.6.5.1 CASE Statement](https://dev.mysql.com/doc/refman/8.4/en/case.html)