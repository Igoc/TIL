## Configuration 애노테이션과 싱글톤

- 스프링에서는 CGLIB을 사용해 `@Configuration`이 붙은 클래스의 바이트코드를 조작하여, 싱글톤 패턴 없이도 빈으로 등록된 인스턴스를 싱글톤으로 관리한다.
- `@Configuration` 없이 `@Bean`만 사용할 경우 빈으로 등록되나 싱글톤을 보장하지 않는다.

## 참고 자료

- [스프링 핵심 원리 - 기본편](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%ED%95%B5%EC%8B%AC-%EC%9B%90%EB%A6%AC-%EA%B8%B0%EB%B3%B8%ED%8E%B8)