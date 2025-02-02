## PERCENT_RANK 함수

파티션 내 현재 행의 백분율(0 ~ 1)을 반환한다.

### 예시

``` mysql
SELECT
    id,
    PERCENT_RANK() OVER(ORDER BY size) AS percentage
FROM germ;
```

germ 테이블에서 id 열을 선택하고, size의 백분율에 해당하는 percentage 열을 추가한다.

## 참고 자료

- [MySQL :: MySQL 8.4 Reference Manual :: 14.20.1 Window Function Descriptions](https://dev.mysql.com/doc/refman/8.4/en/window-function-descriptions.html#function_percent-rank)