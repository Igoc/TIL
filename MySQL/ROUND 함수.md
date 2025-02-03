## ROUND 함수

- 숫자를 지정한 자릿수 + 1 위치에서 반올림한다.
- 반올림할 자릿수는 음수일 수 있으며, 소수점 바로 왼쪽에 있는 숫자의 자릿수가 0이다.

### 예시

``` mysql
SELECT ROUND(-1.23), ROUND(-1.58), ROUND(1.58), ROUND(1.298, 1), ROUND(1.298, 0), ROUND(23.298, -1);
```

순서대로 -1, -2, 2, 1.3, 1, 20이라는 결과가 반환된다.

## 참고 자료

- [MySQL :: MySQL 8.4 Reference Manual :: 14.6.2 Mathematical Functions](https://dev.mysql.com/doc/refman/8.4/en/mathematical-functions.html#function_round)