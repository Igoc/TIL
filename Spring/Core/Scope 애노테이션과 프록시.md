## Scope 애노테이션과 프록시

- `Scope` 애노테이션의 `proxyMode` 옵션을 `ScopedProxyMode.INTERFACES` 또는 `ScopedProxyMode.TARGET_CLASS`로 설정하면, 스프링 컨테이너에 원본 객체 대신 프록시 객체가 등록된다.
- 프록시를 적용할 대상이 인터페이스라면 `ScopedProxyMode.INTERFACES`를 사용하고, 클래스라면 `ScopedProxyMode.TARGET_CLASS`를 사용하면 된다.
- 등록된 프록시 객체는 메서드가 호출될 때 원본 객체를 조회하여 요청을 위임한다.
- Prototype, Request처럼 지연 초기화가 이루어지는 스코프를 사용한다면, 실제로 사용되는 시점까지 빈의 생성을 지연할 수 있다.

## 참고 자료

- [스프링 핵심 원리 - 기본편](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%ED%95%B5%EC%8B%AC-%EC%9B%90%EB%A6%AC-%EA%B8%B0%EB%B3%B8%ED%8E%B8)