## SQL INNER JOIN

공통된 데이터가 담겨 있는 열을 이용하여 두 개의 테이블을 합치되, 교집합인 데이터만 연결하기 위해 사용되는 키워드이다.

``` sql
/* customers 테이블과 orders 테이블을 INNER JOIN하여 모든 데이터 가져오기 */
SELECT * FROM customers INNER JOIN orders ON customers.customer_id = orders.customer_id;
```