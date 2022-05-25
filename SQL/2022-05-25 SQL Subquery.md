## SQL Subquery

하나의 SQL 쿼리문 안에 또 다른 SQL 쿼리문이 포함되어 있는 것을 의미한다.

``` sql
/* orders 테이블에서 payment_method가 card인 행들의 user_id를 가져온 후, users 테이블에서 해당 user_id를 갖는 행들로부터 email 가져오기 */
SELECT u.email FROM users AS u
WHERE u.user_id IN (
    SELECT o.user_id FROM orders AS o
    WHERE o.payment_method = "card"
);

/* comments 테이블에서 post_id, user_id, likes를 가져온 후, 해당 user_id를 갖는 사용자의 likes 평균을 추가로 가져오기 */
SELECT c1.post_id, c1.user_id, c1.likes, (
    SELECT AVG(c2.likes) FROM comments AS c2
    WHERE c2.user_id = c1.user_id
) AS avg_likes
FROM comments AS c1;

/* check_in 테이블에서 course_id 별로 몇 명의 사용자가 체크인했는지와 orders 테이블에서 course_id 별로 몇 개의 주문이 있는지를 가져온 후, 두 결과를 INNER JOIN */
SELECT a.course_id, a.check_in_cnt, b.order_cnt
FROM (
    SELECT course_id, COUNT(DISTINCT user_id) AS check_in_cnt
    FROM check_in
    GROUP BY course_id
) AS a INNER JOIN (
    SELECT course_id, COUNT(*) AS order_cnt
    FROM orders
    GROUP BY course_id
) AS b ON a.course_id = b.course_id;
```