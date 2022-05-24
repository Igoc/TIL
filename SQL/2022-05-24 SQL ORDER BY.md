## SQL ORDER BY

가져온 데이터를 오름차순 또는 내림차순으로 정렬하기 위해 사용되는 키워드이다.

``` sql
/* customers 테이블의 데이터를 country를 기준으로 오름차순 정렬하여 가져오기 */
SELECT * FROM customers ORDER BY country;

/* customers 테이블의 데이터를 first_name을 기준으로 오름차순 정렬하여 가져오기 */
SELECT * FROM customers ORDER BY first_name ASC;

/* customers 테이블의 데이터를 first_name을 기준으로 내림차순 정렬하여 가져오기 */
SELECT * FROM customers ORDER BY first_name DESC;

/* customers 테이블의 데이터를 country를 기준으로 오름차순 정렬하고, first_name을 기준으로 내림차순 정렬하여 가져오기 */
SELECT * FROM customers ORDER BY country ASC, first_name DESC;
```