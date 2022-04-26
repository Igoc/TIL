## GitHub Actions

GitHub에서 제공하는 CI/CD 도구로, 일련의 워크플로(Workflow)를 자동화할 수 있도록 도와준다.

### 지속적인 통합(CI, Continuous Integration)

서비스 파일이 테스트를 거쳐 원격 저장소에 자동으로 업로드되는 프로세스를 의미한다.

### 지속적인 서비스 제공(CD, Continuous Delivery)

원격 저장소에 업로드된 서비스 파일을 자동으로 프로덕션 환경에 배포하는 프로세스를 의미한다.

### 사용법

.github/workflows 폴더 안에 YAML 형식의 파일을 생성함으로써 사용할 수 있다.

### Secrets

토큰과 같이 보안에 민감한 정보를 숨길 수 있는 기능으로, Settings에 있는 Secrets 메뉴에서 설정할 수 있다. 이렇게 설정한 Secrets 값은 아래와 같은 방식을 통해 GitHub Actions에서 접근할 수 있다.

``` yaml
${{ secrets.<Secrets 이름> }}
```