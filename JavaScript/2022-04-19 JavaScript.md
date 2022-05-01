## JavaScript

JavaScript는 브라우저가 알아들을 수 있는 프로그래밍 언어이다.

### JavaScript 기초

`<head>...</head>` 태그 안에 `<script>...</script>` 태그로 공간을 만들어 JavaScript를 작성한다.

### 변수

``` javascript
// 재할당이 가능한 변수 선언
let name = 'Alice';
name = 'Bob';

// 재할당이 불가능한 변수 선언
const age = 20;
```

#### 배열(Array)

순서를 고려하여 데이터를 보관하는 자료형이다.

``` javascript
// 배열 선언
let array = [1, 2, 'Alice', 3];

console.log(array[1]);
console.log(array[2]);

// 배열에 새로운 요소 추가
array.push('Bob');

console.log(array);

// 배열의 길이 획득
console.log(array.length);
```

``` bash
[출력]
2
Alice
[1, 2, "Alice", 3, "Bob"]
5
```

#### 객체(Object)

키(Key)-값(Value) 쌍으로 구성된 데이터를 가지고 있는 자료형이다.

``` javascript
// 객체 선언
let dict = {
    'name': 'Alice',
    'age': 21
};

console.log(dict['name']);
console.log(dict['age']);

// 객체에 새로운 키-값 추가
dict['height'] = 160;

console.log(dict);
```

``` bash
[출력]
Alice
21
{
    age: 21,
    height: 160,
    name: "Alice"
}
```

### 기본 제공 함수

#### 알파벳을 대문자로 변경

``` javascript
let name = 'alice';
name.toUpperCase();
```

#### 특정 문자로 문자열 나누기

``` javascript
let email = 'test@example.com';
email.split('@');
```

#### 특정 문자로 배열 요소 합치기

``` javascript
let loc = ['서울시', '마포구', '망원동'];
loc.join('-');
```

### 함수

``` javascript
// 함수 선언
function sum(num1, num2) {
    return num1 + num2;
}

// 함수 호출
sum(3, 5);
```

### 조건문

``` javascript
let age = 25;

if (age > 20) {
    alert('성인');
}
else if (age > 10) {
    alert('청소년');
}
else {
    alert('아동');
}
```

### 반복문

``` javascript
for (let index = 0; index < 10; index++) {
    console.log(index);
}
```

``` bash
[출력]
0
1
2
3
4
5
6
7
8
9
```

#### 배열 원소 순회

``` javascript
let people = ['철수', '영희', '민수', '형준', '기남', '동희'];

for (let index = 0; index < people.length; index++) {
    console.log(people[index]);
}
```

``` bash
[출력]
철수
영희
민수
형준
기남
동희
```