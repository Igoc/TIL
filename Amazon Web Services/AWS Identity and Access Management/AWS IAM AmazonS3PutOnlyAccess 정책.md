## AmazonS3PutOnlyAccess 정책

``` json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:Put*",
                "s3-object-lambda:Put*"
            ],
            "Resource": "*"
        }
    ]
}
```

## 참고 자료

- [Actions, resources, and condition keys for Amazon S3 - Amazon Simple Storage Service](https://docs.aws.amazon.com/AmazonS3/latest/userguide/list_amazons3.html)