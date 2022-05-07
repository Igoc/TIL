## AWS Certificate Manager

AWS 리소스에 사용할 SSL/TLS 인증서를 손쉽게 관리하고 배포할 수 있는 서비스이다.

### DNS 검증

CNAME을 이용하여 DNS 소유자를 검증하는 방식이다.

#### CNAME 이름

검증을 위해 입력해야 할 CNAME 이름을 나타내는 부분이며, 가비아처럼 CNAME 이름에 자신의 도메인은 생략하여 입력하는 곳이라면 앞부분의 문자열만 사용하면 된다.

#### CNAME 값

검증을 위해 입력해야 할 CNAME 값을 나타내는 부분이다.