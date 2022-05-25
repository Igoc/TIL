## MySQL SUBSTRING_INDEX

구분자를 기준으로 문자열을 나눈 후, 나눠진 문자열들 중에서 특정 인덱스에 해당하는 것을 가져오기 위해 사용되는 함수이다.

``` sql
/* users 테이블에서 email을 가져온 후, @를 기준으로 문자열을 나누고 첫 번째 것을 취하기 */
SELECT SUBSTRING_INDEX(email, "@", 1) FROM users;

/* users 테이블에서 email을 가져온 후, @를 기준으로 문자열을 나누고 마지막 것을 취하기 */
SELECT SUBSTRING_INDEX(email, "@", -1) FROM users;
```