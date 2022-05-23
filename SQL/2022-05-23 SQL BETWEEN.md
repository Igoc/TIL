## SQL BETWEEN

주어진 범위 내에서 값을 선택하기 위해 사용되는 연산자이다.

``` sql
/* orders 테이블에서 order_date가 2022-01-01 ~ 2022-01-05에 해당하는 행의 데이터만 가져오기 */
SELECT * FROM orders WHERE order_date BETWEEN "2022-01-01" AND "2022-01-06";
```