## GitHub Actions for AWS CloudFront

아래와 같은 GitHub Actions 템플릿을 이용하여, main 브랜치에 push가 발생했을 때 자동으로 AWS CloudFront에 배포가 이루어지도록 만들 수 있다.

``` yaml
name: <GitHub Actions 이름>

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    env:
      AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
      AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
      AWS_REGION: 'ap-northeast-2'

    steps:
      - name: Checkout source code
        uses: actions/checkout@master

      - name: Upload index to S3 bucket
        uses: jakejarvis/s3-sync-action@master
        with:
          args: --acl public-read --exclude '*' --include 'index.html'
        env:
          AWS_S3_BUCKET: ${{ secrets.BUCKET_NAME }}

      - name: Invalidate CloudFront caches
        uses: chetan/invalidate-cloudfront-action@master
        env:
          DISTRIBUTION: ${{ secrets.DISTRIBUTION_ID }}
          PATHS: '/index.html'
        continue-on-error: true
```