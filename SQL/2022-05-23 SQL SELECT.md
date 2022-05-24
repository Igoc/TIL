## SQL SELECT

데이터베이스에서 데이터를 선택해서 가져오기 위해 사용되는 문장이다.

``` sql
/* orders 테이블의 모든 데이터 가져오기 */
SELECT * FROM orders;

/* orders 테이블의 food_name, payment_method 열에 있는 데이터만 가져오기 */
SELECT food_name, payment_method FROM orders;
```