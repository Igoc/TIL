## AWS OpenSearch Service

AWS Elasticsearch Service의 후속 서비스로, OpenSearch Service와 Elasticsearch OSS를 이용하여 클러스터를 손쉽게 구성할 수 있는 관리형 서비스이다.

### ELK 스택

<u>E</u>lasticsearch, <u>L</u>ogstash, <u>K</u>ibana 프로젝트로 구성된 스택을 의미하는 약어로, 여러 시스템과 애플리케이션으로부터 자동으로 로그를 집계하고 분석하여 시각화 결과를 생성해주는 도구이다.

#### Elasticsearch

오픈 소스 검색 엔진으로 ELK 스택에서 로그 분석 및 검색 요청을 처리하기 위한 용도로 사용된다. AWS OpenSearch Service를 이용하여 클러스터를 생성할 경우, Elasticsearch를 사용할 수 있는 환경을 자동으로 구축해준다.

#### Logstash

다양한 소스로부터 데이터를 수집하고 변환하여 원하는 대상에 전송할 수 있도록 만들어주는 오픈 소스 데이터 수집 도구로, ELK 스택에서 서비스들로부터 로그를 수집하여 Elasticsearch로 전달하기 위한 용도로 사용된다. AWS OpenSearch Service를 이용하여 클러스터를 생성하더라도 Logstash를 사용할 수 있는 환경을 구축해주지 않기 때문에, 사용자가 직접 Logstash 환경을 구성해야만 한다.

##### 설치 방법

Ubuntu OS를 기준으로 아래와 같은 절차를 통해 Logstash를 설치할 수 있다.

###### Java 설치

Logstash 설치 시 Java 8 버전을 필요로 하기 때문에, 아래와 같은 방법으로 Java 8을 설치해주어야 한다.

``` bash
sudo apt-get install openjdk-8-jdk
```

###### Logstash 설치

AWS OpenSearch Service에서 사용하는 Elasticsearch 버전과 Logstash 버전이 일치하지 않으면 *ConfigurationError: Could not connect to a compatible version of Elasticsearch* 에러가 발생하기 때문에 버전을 맞춰주는 것이 중요하다. 예를 들어 AWS OpenSearch Service에서 Elasticsearch 7.10 버전을 사용한다면, Logstash 7.10.x 버전을 설치해야만 정상적으로 실행된다.

``` bash
# Elasticsearch 7.10 버전을 사용하는 경우, Logstash 7.10.2 버전의 패키지를 설치
wget https://artifacts.elastic.co/downloads/logstash/logstash-oss-7.10.2-amd64.deb

# 다운로드한 패키지를 설치
sudo dpkg -i logstash-oss-7.10.2-amd64.deb
```

###### Logstash 설정 파일 생성

Logstash 환경을 구성하기 위해 /etc/logstash/conf.d 폴더 아래에 <설정 파일명>.conf 형식의 이름을 갖는 설정 파일을 생성해야 한다.

```
input {
    tcp {
        port => <Logstash 포트>
    }
}

output {
    elasticsearch {
        hosts => ["<AWS OpenSearch Service 엔드포인트>:443"]
        index => "<로그 인덱스 형식>"
        user => "<Kibana 사용자명>"
        password => "<Kibana 비밀번호>"
        ssl => true
        ilm_enabled => false
    }
}
```

###### Logstash 서비스 실행

``` bash
sudo systemctl start logstash.service
```

#### Kibana

로그 및 이벤트 검토에 사용하는 오픈 소스 데이터 시각화 도구로, ELK 스택에서 로그를 시각화하기 위한 용도로 사용된다. AWS OpenSearch Service를 이용하여 클러스터를 생성할 경우, Kibana를 사용할 수 있는 환경을 자동으로 구축해준다.

### 비용 계산

[AWS Pricing Calculator OpenSearch Service](https://calculator.aws/#/createCalculator/OpenSearchService)를 통해 AWS OpenSearch Service 리소스 구성에 따른 대략적인 비용을 산출해볼 수 있다.