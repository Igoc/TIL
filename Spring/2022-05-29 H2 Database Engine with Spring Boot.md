## H2 Database Engine with Spring Boot

H2 Database Engine은 자바 기반의 관계형 데이터베이스 관리 시스템으로, Spring Boot를 이용하여 임베드해서 사용할 수 있다.

### 라이브러리 설치

#### Gradle

```
runtimeOnly 'com.h2database:h2'
```

### H2 Console 활성화

application.properties 파일 안에 다음의 내용을 추가한 후, 서버를 실행하고 /h2-console로 접속하면 된다.

```
spring.h2.console.enabled=true
spring.datasource.url=jdbc:h2:mem:testdb;MODE=MYSQL
```