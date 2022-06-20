## Dockerfile for Spring

아래와 같은 Dockerfile 템플릿을 이용하여, Spring 애플리케이션을 위한 이미지를 생성할 수 있다.

``` dockerfile
# OpenJDK 11 버전을 베이스 이미지로 사용
FROM openjdk:11-jdk-alpine

# JAR 파일 복사
COPY build/libs/<JAR 파일명> app.jar

# 컨테이너가 시작될 때 JAR 파일 실행
ENTRYPOINT ["java", "-jar", "/app.jar"]
```