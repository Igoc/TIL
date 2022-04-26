## AWS CloudFront

AWS에서 제공하는 CDN 서비스로, 캐싱을 통해 사용자에게 좀 더 빠른 속도로 데이터를 제공하기 위해 사용된다.

### 원리

AWS CloudFront에 캐싱되는 데이터는 전 세계 이곳저곳에 위치한 Edge Location에 저장되며, 사용자로부터 요청이 왔을 때 가장 가까운 Edge Location으로 연결해주어 빠른 속도로 데이터를 제공한다.

### 이점

특정 리전의 AWS S3에 업로드한 객체를 글로벌하게 서비스하려고 할 때, AWS CloudFront를 이용하면 모든 리전에 AWS S3를 만들지 않아도 사용자가 객체를 빠르게 획득할 수 있다.

### 구성 정보

#### ID

AWS CloudFront 생성 시 자동으로 부여되는 고유한 값이다.

#### 도메인 이름(Domain Name)

AWS CloudFront에 캐싱된 데이터에 접근할 수 있는 URL이다.

#### 원본(Origin)

AWS CloudFront가 캐싱하는 데이터의 원본이 담긴 곳의 URL이다.

### 설정

#### 기본값 루트 객체(Default Root Object)

루트 URL에 요청했을 때 반환할 객체를 설정하는 부분으로, 일반적인 웹사이트의 경우 index.html로 설정한다.

### 무효화(Invalidation)

AWS CloudFront에 캐싱된 파일을 삭제할 수 있는 기능이다.