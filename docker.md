# Docker AWS에 배포하기
---
![image](https://github.com/Technician-for-AI-Speech-Service/AWS_Cloud/assets/112459716/2179922c-4f12-40ad-85e1-1970cba27023)
---
## 1. Ubuntu 환경에 docker 설치하기
---
1. 우분투 시스템 패키지 업데이트(EC2 Ubuntu 환경)
```python
sudo apt-get update
```
2. 필요한 패키지 설치
```python
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
```
3. Docker의 공식 GPG키를 추가
```python
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
4. Docker의 공식 apt 저장소를 추가
```python
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```
5. 시스템 패키지 업데이트
```python
sudo apt-get update
```
6. Docker 설치
```python
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
7. Docker 설치 확인
```python
sudo docker --version
```
---
## 2. Docker를 사용하여 이미지 빌드하기
---
- -t는 태그명 지정할 때 사용하는 옵션임. 뒤에 공백 . 꼭 붙혀줘야함 태그 설정안하면 latest로 자동으로 생성됨
```python
docker build -t $이미지명:$태그 .
```
- 이번 프로젝트 같은 경우는 requirements.txt에 tensorflow-gpu=2.3 버전을 제거하고 tensorflow 만 작성해줘야함
---
## 3. Docker 실행시키기
---
