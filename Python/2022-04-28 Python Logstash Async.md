## Python Logstash Async

Logstash에 비동기적으로 로그를 전송할 수 있도록 만들어주는 Python 패키지이다.

### 패키지 설치

``` bash
pip install python-logstash-async
```

### 템플릿

``` python
from logstash_async.handler import AsynchronousLogstashHandler

import logging

logger = logging.getLogger('python-logstash-logger')
logger.addHandler(AsynchronousLogstashHandler('<Logstash 주소>', '<Logstash 포트>', database_path=''))

# INFO 레벨의 로그 전송
logger.info('<로그 메시지>')
```