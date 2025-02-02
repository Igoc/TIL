## DENSE_RANK 함수

- 파티션 내 현재 행의 순위를 반환한다.
- 동일한 값이 있다면 같은 순위를 부여받으며, 동일한 값이 여러 개 있어도 다음 순위는 밀리지 않는다.

### 예시

``` mysql
SELECT
    id,
    DENSE_RANK() OVER(ORDER BY size) AS ranking
FROM germ;
```

germ 테이블에서 id 열을 선택하고, size 순위에 해당하는 ranking 열을 추가한다.

## 참고 자료

- [MySQL :: MySQL 8.4 Reference Manual :: 14.20.1 Window Function Descriptions](https://dev.mysql.com/doc/refman/8.4/en/window-function-descriptions.html#function_dense-rank)