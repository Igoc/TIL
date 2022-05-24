## SQL GROUP BY

동일한 범주를 가진 행을 그룹화하기 위해 사용되는 문장이다.

``` sql
/* people 테이블에서 last_name 별로 데이터 개수 세기 */
SELECT last_name, COUNT(*) FROM people GROUP BY last_name;
```