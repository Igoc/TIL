## Flask MySQL

관계형 데이터베이스인 MySQL을 Flask에 연결할 수 있도록 해주는 패키지이다.

### 패키지 설치

``` bash
pip install Flask-MySQL
```

### 템플릿

``` python
from flask import Flask, jsonify

from flaskext.mysql import MySQL

app = Flask(__name__)
app.config['MYSQL_DATABASE_HOST'] = '<MySQL 주소>'
app.config['MYSQL_DATABASE_USER'] = '<MySQL 사용자>'
app.config['MYSQL_DATABASE_PASSWORD'] = '<MySQL 비밀번호>'
app.config['MYSQL_DATABASE_DB'] = '<MySQL 데이터베이스>'

mysql = MySQL()
mysql.init_app(app)

@app.route('/')
def index():
    # MySQL 연결
    connection = mysql.connect()
    cursor = connection.cursor()

    ...

    # MySQL 연결 끊기
    connection.close()

    return jsonify({'status': 'success'})

if __name__ == '__main__':
    app.run('0.0.0.0', port=5000, debug=True)
```