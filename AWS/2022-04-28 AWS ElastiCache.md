## AWS ElastiCache

인메모리 데이터베이스인 Redis 또는 Memcached를 이용하여, 캐시 환경을 손쉽게 구축할 수 있도록 만들어진 웹 서비스이다.

### AWS ElastiCache 외부 접속

기본적으로 AWS ElastiCache는 AWS VPC 내부에서만 사용하도록 설계된 서비스이며, 인터넷 트래픽 지연 및 보안 문제로 인해 외부에서 접속하는 것을 권장하지 않는다. 그러나 테스트나 개발 목적으로 AWS VPC 외부에서 접속해야 하는 경우가 있는데, 그런 경우엔 [Accessing ElastiCache resources from outside AWS](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/accessing-elasticache.html#access-from-outside-aws) 문서에 소개된 방법을 통해 외부에서 접속이 가능하다.

### 비용 계산

[AWS Pricing Calculator ElastiCache](https://calculator.aws/#/createCalculator/ElastiCache)를 통해 AWS ElastiCache 리소스 구성에 따른 대략적인 비용을 산출해볼 수 있다.