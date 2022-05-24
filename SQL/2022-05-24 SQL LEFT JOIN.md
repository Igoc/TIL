## SQL LEFT JOIN

공통된 데이터가 담겨 있는 열을 이용하여 두 개의 테이블을 합치되, 왼쪽 테이블을 기준으로 오른쪽 테이블에서 매칭되는 데이터를 연결하기 위해 사용되는 키워드이다.

``` sql
/* customers 테이블과 orders 테이블을 LEFT JOIN하여 모든 데이터 가져오기 */
SELECT * FROM customers LEFT JOIN orders ON customers.customer_id = orders.customer_id;

/* customers 테이블과 orders 테이블을 LEFT JOIN 한 후, orders 테이블에 있는 order_id가 NULL인 데이터만 가져오기 */
SELECT * FROM customers LEFT JOIN orders ON customers.customer_id = orders.customer_id WHERE orders.order_id IS NULL;

/* customers 테이블과 orders 테이블을 LEFT JOIN 한 후, orders 테이블에 있는 order_id가 NULL이 아닌 데이터만 가져오기 */
SELECT * FROM customers LEFT JOIN orders ON customers.customer_id = orders.customer_id WHERE orders.order_id IS NOT NULL;
```