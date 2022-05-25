## MySQL SUBSTRING

문자열에서 부분 문자열을 추출하기 위해 사용되는 함수이다.

``` sql
/* customers 테이블에서 customer_name 데이터를 가져온 후, 두 번째 위치에서 시작해 길이가 5인 부분 문자열 추출 */
SELECT SUBSTRING(customer_name, 2, 5) FROM customers;
```