## MySQL ROUND

숫자를 지정된 소수 자릿수로 반올림하기 위해 사용되는 함수이다.

``` sql
/* products 테이블에서 가져온 price 데이터를 소수점 첫째 자리로 반올림 */
SELECT ROUND(price, 1) FROM products;
```