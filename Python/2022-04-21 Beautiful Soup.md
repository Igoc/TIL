## Beautiful Soup

HTML 파일로부터 원하는 데이터를 쉽게 가져올 수 있도록 파싱(Parsing)을 해주는 Python 패키지이다.

### 패키지 설치

Beautiful Soup 패키지를 사용하려면 Requests 패키지를 이용해야 해서 같이 설치를 해줘야 한다.

``` bash
pip install beautifulsoup4
pip install requests
```

### 템플릿

``` python
from bs4 import BeautifulSoup

import requests

# HTTP 헤더 설정
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/73.0.3683.86 Safari/537.36'
}

# URL로부터 HTML 파일 획득
data = requests.get('<URL>', headers=headers)

# 획득한 HTML 파일 파싱
soup = BeautifulSoup(data.text, 'html.parser')
```

### 예시

``` python
from bs4 import BeautifulSoup

import requests

headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/73.0.3683.86 Safari/537.36'
}

data = requests.get('https://movie.naver.com/movie/sdb/rank/rmovie.nhn?sel=pnt&date=20200303', headers=headers)

soup = BeautifulSoup(data.text, 'html.parser')

# Selector를 이용하여 영화 데이터 뽑아오기
movies = soup.select('#old_content > table > tbody > tr')

for movie in movies:
    title_tag = movie.select_one('td.title > div > a')

    if title_tag != None:
        print(title_tag.text)
```

``` bash
[출력]
그린 북
가버나움
베일리 어게인
주전장
포드 V 페라리
아일라
원더
당갈
쇼생크 탈출
터미네이터 2:오리지널
보헤미안 랩소디
덕구
나 홀로 집에
월-E
살인의 추억
빽 투 더 퓨쳐
...
```