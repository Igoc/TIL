## RANK 함수

- 파티션 내 현재 행의 순위를 반환한다.
- 동일한 값이 있다면 같은 순위를 부여받으며, 다음 순위는 동일한 값의 개수만큼 밀린다.

### 예시

``` mysql
SELECT
    id,
    RANK() OVER(ORDER BY size) AS ranking
FROM germ;
```

germ 테이블에서 id 열을 선택하고, size 순위에 해당하는 ranking 열을 추가한다.

## 참고 자료

- [MySQL :: MySQL 8.4 Reference Manual :: 14.20.1 Window Function Descriptions](https://dev.mysql.com/doc/refman/8.4/en/window-function-descriptions.html#function_rank)