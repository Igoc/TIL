## BeanDefinition

- 빈의 설정 메타 정보를 담고 있는 객체이다.
- 스프링 컨테이너는 자바 코드나 XML 등으로부터 생성된 `BeanDefinition`을 기반으로 빈을 생성한다.
- `BeanDefinition`을 생성하는 방법은 크게 `GenericXmlApplicationContext`처럼 직접 등록하는 방식과 `AnnotationConfigApplicationContext`처럼 팩토리 메서드를 통해 등록하는 방식으로 나뉜다.

## 참고 자료

- [스프링 핵심 원리 - 기본편](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%ED%95%B5%EC%8B%AC-%EC%9B%90%EB%A6%AC-%EA%B8%B0%EB%B3%B8%ED%8E%B8)