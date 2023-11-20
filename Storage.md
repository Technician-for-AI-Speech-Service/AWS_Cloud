# EC2 환경에 용량추가 
---

## 1. 용량 확인법
```python
df -hT #각 볼륨의 파일 시스템 용량, 타입 확인
```

## 2. 인스턴스 EBS(Elastic Block Store) 확인
![image](https://github.com/Technician-for-AI-Speech-Service/AWS_Cloud/assets/112459716/f2d5da22-7874-4db7-8f58-2a995e56e6a5)

-lsblk 명령어로 인스턴스에 연결된 블록 디바이스 확인 
![image](https://github.com/Technician-for-AI-Speech-Service/AWS_Cloud/assets/112459716/520fca43-4bba-4e89-a614-968497b2e8d5)

## 3. 파티션 용량 올리기
```python
sudo growpart <볼륨> <파티션번호>
# ex) sudo growpart /dev/xvda 1
```

## 4. 파일 시스템의 크기 늘리기

```python
sudo resize2fs<파티션>
# sudo resize2fs /dev/xvda1
```
