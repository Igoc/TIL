## GitHub Actions for AWS S3 with Webpack

아래와 같은 GitHub Actions 템플릿을 이용하여, main 브랜치에 push가 발생했을 때 자동으로 Webpack을 빌드해서 AWS S3에 배포되도록 만들 수 있다.

``` yaml
name: <GitHub Actions 이름>

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [12.x]

    steps:
      - name: Checkout source code
        uses: actions/checkout@master

      - name: Set up Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v1
        with:
          node-version: ${{ matrix.node-version }}

      - name: Install packages and build project
        run: |
          npm install
          npx webpack

      - name: Deploy to S3
        env:
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        run: aws s3 cp --recursive --acl public-read --region <AWS 리전> dist s3://<S3 버킷 이름>
```