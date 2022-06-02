## GitHub Actions for AWS Serverless Application Model

아래와 같은 GitHub Actions 템플릿을 이용하여, main 브랜치에 push가 발생했을 때 자동으로 AWS Serverless Application Model 프로젝트 빌드 및 배포가 이루어지도록 만들 수 있다.

``` yaml
name: <GitHub Actions 이름>

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - uses: actions/setup-python@v3
        with:
          python-version: "3.9"

      - uses: aws-actions/setup-sam@v2

      - uses: aws-actions/configure-aws-credentials@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: ap-northeast-2

      - run: sam build --use-container

      - run: sam deploy --no-confirm-changeset --no-fail-on-empty-changeset
```