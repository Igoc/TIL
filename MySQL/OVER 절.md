## OVER 절

윈도우 함수를 표현하기 위해 사용되며, 결과를 단일 행으로 그룹화하는 집계 함수와 달리 윈도우 함수는 결과를 각 행마다 생성한다.

### 예시

``` mysql
SELECT
    country, profit,
    SUM(profit) OVER() AS total_profit,
    SUM(profit) OVER(PARTITION BY country) AS country_profit
FROM sales;
```

sales 테이블에서 country와 profit 열을 선택하고, 각 행마다 전체 수익 합계에 해당하는 total_profit과 국가별 수익 합계에 해당하는 country_profit 열을 추가한다.

## 참고 자료

- [MySQL :: MySQL 8.4 Reference Manual :: 14.20.2 Window Function Concepts and Syntax](https://dev.mysql.com/doc/refman/8.4/en/window-functions-usage.html)