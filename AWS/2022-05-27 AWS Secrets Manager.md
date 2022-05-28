## AWS Secrets Manager

암호와 같은 자격 증명을 하드 코딩하는 대신 API 호출을 통해 획득할 수 있도록 관리해주는 AWS 서비스이다.

### 자동 교체 구성

특정 주기마다 보안 암호가 자동으로 교체될 수 있도록 설정할 수 있는 기능이다.

### Python과 연동

#### 패키지 설치

``` bash
pip install boto3
```

#### 예제

``` python
import boto3

# 세션 생성
session = boto3.session.Session()

# AWS Secrets Manager에 접속
client = session.client(
    service_name='secretsmanager',
    aws_access_key_id='<AWS IAM 액세스 키 ID>',
    aws_secret_access_key='<AWS IAM 비밀 액세스 키>',
    region_name='<AWS 리전>'
)

# 보안 암호 목록 획득
secrets = client.get_secret_value(SecretId='<AWS Secrets Manager 보안 암호 이름>')
secrets = eval(secrets['SecretString'])

# 보안 암호 값 획득
secret_value = secrets['<보안 암호 키>']
```