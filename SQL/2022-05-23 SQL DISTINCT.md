## SQL DISTINCT

중복되는 데이터를 제외하고 가져오기 위해 사용되는 문장이다.

``` sql
/* orders 테이블에서 payment_method의 중복된 데이터들을 제외하고 가져오기 */
SELECT DISTINCT payment_method FROM orders;
```