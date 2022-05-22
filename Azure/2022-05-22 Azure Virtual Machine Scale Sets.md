## Azure Virtual Machine Scale Sets

서버 로드율에 따라 가상 머신의 개수를 자동으로 확장 또는 축소할 수 있는 기능을 제공하는 서비스이다.

### 부하 테스트

``` bash
# 새로운 패키지 버전이 있는지 확인
sudo apt-get update

# 부하 패키지 설치
sudo apt-get install stress

# 300초동안 CPU 1개를 부하
stress --cpu 1 --timeout 300 &

# CPU 사용량 확인
top
```