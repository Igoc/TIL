## AWS Serverless Application Model

AWS에서 서버리스 애플리케이션을 구축하기 위해 사용할 수 있는 오픈 소스 프레임워크로, [AWS Serverless Application Model](https://aws.amazon.com/ko/serverless/sam/)에서 자신의 OS에 맞는 AWS Serverless Application Model을 다운받을 수 있다.

### 명령어

#### 버전 확인

``` bash
sam --version
```

#### 프로젝트 생성

``` bash
sam init
```

#### 프로젝트 빌드 및 배포

``` bash
# 프로젝트 빌드
sam build

# 프로젝트 배포
sam deploy

# 대화형 모드를 이용하여 프로젝트 배포
sam deploy --guided
```

#### Docker를 이용하여 로컬 환경에서 실행

Hot Reload 기능이 없기 때문에 수정했을 때마다 프로젝트 빌드를 먼저 수행해야 한다.

``` bash
# Docker를 이용하여 로컬 환경에서 실행
sam local start-api
```

#### 로그 확인

``` bash
# 특정 AWS Lambda 함수의 로그 확인
sam logs -n <AWS Lambda 함수명> --stack-name <AWS CloudFormation 스택명>

# 특정 AWS Lambda 함수의 실시간 로그 확인
sam logs -n <AWS Lambda 함수명> --stack-name <AWS CloudFormation 스택명> --tail
```

### AWS VPC 설정

template.yaml 파일에서 AWS VPC 설정이 필요한 AWS Lambda 함수의 Properties 아래에 다음과 같이 속성을 추가하면 된다.

``` yaml
...

Resources:
    <AWS Lambda 함수명>:
        Type: AWS::Serverless::Function
        Properties:
            ...

            VpcConfig:
                SecurityGroupIds:
                    - <AWS VPC 보안 그룹 ID>
                SubnetIds:
                    - <AWS VPC 서브넷 ID>

...
```

### AWS Secrets Manager 연동

template.yaml 파일에서 AWS Secrets Manager 연동이 필요한 AWS Lambda 함수의 Properties 아래에 다음과 같이 속성을 추가하면 된다.

``` yaml
...

Resources:
    <AWS Lambda 함수명>:
        Type: AWS::Serverless::Function
        Properties:
            ...

            Policies:
                Statement:
                    Sid: AWSSecretsManagerGetSecretValuePolicy
                    Effect: Allow
                    Action: secretsmanager:GetSecretValue
                    Resource: <AWS Secrets Manager 보안 암호 ARN>

...
```