## GitHub Actions for AWS Elastic Beanstalk

아래와 같은 GitHub Actions 템플릿을 이용하여, main 브랜치에 push가 발생했을 때 자동으로 AWS Elastic Beanstalk에 배포가 이루어지도록 만들 수 있다.

``` yaml
name: <GitHub Actions 이름>

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout source code
        uses: actions/checkout@master

      - name: Set up Python 3.8
        uses: actions/setup-python@v1
        with:
          python-version: '3.8'

      - name: Generate deployment package
        run: zip -r deployment.zip . -x '*.git*'

      - name: Get timestamp
        uses: gerred/actions/current-time@master
        id: current-time

      - name: Run string replace
        uses: frabert/replace-string-action@master
        id: format-time
        with:
          pattern: '[:\.]+'
          string: '${{ steps.current-time.outputs.time }}'
          replace-with: '-'
          flags: 'g'

      - name: Deploy to EB
        uses: einaregilsson/beanstalk-deploy@v16
        with:
          aws_access_key: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws_secret_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          application_name: ${{ secrets.APPLICATION_NAME }}
          environment_name: ${{ secrets.ENVIRONMENT_NAME }}
          version_label: 'python-${{ steps.format-time.outputs.replaced }}'
          region: ap-northeast-2
          deployment_package: deployment.zip
```