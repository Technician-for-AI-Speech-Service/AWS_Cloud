# AWS_Cloud
# 1. Flask 서비스 AWS로 배포하기 - AWS 서버 대여

---

## 1. AWS 가상서버 대여하기

- EC2 서비스로 들어가기 
  
  

  ![db4e4807-5dd9-4c33-839c-91059676ff29](file:///C:/Users/gjaischool1/Pictures/Typedown/db4e4807-5dd9-4c33-839c-91059676ff29.png)



- 인스턴스 클릭
  
  

  ![ccafd0b1-0fb9-4e1f-a8af-b0e5bd7ddbdb](file:///C:/Users/gjaischool1/Pictures/Typedown/ccafd0b1-0fb9-4e1f-a8af-b0e5bd7ddbdb.png)



- 인스턴스 시작 버튼 클릭 
  
  

  ![44a29c43-c2fd-4dff-aecb-0c1725634cfc](file:///C:/Users/gjaischool1/Pictures/Typedown/44a29c43-c2fd-4dff-aecb-0c1725634cfc.png)

- 들어가서 Ubuntu Server 22.04 선택
  ![be3aea5a-1918-4b45-983c-0b0e6072ebb0](file:///C:/Users/gjaischool1/Pictures/Typedown/be3aea5a-1918-4b45-983c-0b0e6072ebb0.png)
  
  

- 인스턴스 유형(프리티어) - t2.micro(1CPU, 1GB메모리)
  
  

  ![2ebcb943-46a5-4185-be67-3bc5ce906dad](file:///C:/Users/gjaischool1/Pictures/Typedown/2ebcb943-46a5-4185-be67-3bc5ce906dad.png)



- 인스턴스 시작 버튼 클릭 ->키패어생성
  
  

![76024d1f-8e68-48d0-98dd-a89032af0def](file:///C:/Users/gjaischool1/Pictures/Typedown/76024d1f-8e68-48d0-98dd-a89032af0def.png)



- 키페어 생성되면 .pem 파일이 중요함(이러면 인스턴스 생성 완료) 지금은 중지 상태지만 바로 생성하면 시작 상태로 변경됨
  
  

![665fa656-2244-4ba6-bee1-bdf691fea4ea](file:///C:/Users/gjaischool1/Pictures/Typedown/665fa656-2244-4ba6-bee1-bdf691fea4ea.png)

---

## 2. .pem 파일 경로 설정 (윈도우ver)

- 로컬디스크C -> 사용자 -> gjaischool1 에 .ssh폴더 만들기

![31605ef6-e939-4b28-9c9a-112de2256c21](file:///C:/Users/gjaischool1/Pictures/Typedown/31605ef6-e939-4b28-9c9a-112de2256c21.png)



- 권한 설정 (.ssh파일 우클릭 -> 속성 -> 보안 -> 고급 -> 상속 사용안함 -> 이개체에서 상속된 사용자 권한을 모두 제거 -> 추가 -> 보안주체선택 )
  ![fdb2bd0e-4f00-40a8-9e78-04f121f8d1ee](file:///C:/Users/gjaischool1/Pictures/Typedown/fdb2bd0e-4f00-40a8-9e78-04f121f8d1ee.png)

- 확인 후 쓰기권한 체크후 적용해준다.

- 끝을 낸 뒤 .pem 파일을 해당 .ssh 폴더에 넣어준다.
  
  --- 

## 3. ec2 서버에 접속하기

- $ssh -i [키 페어 경로] [유저 이름]@[퍼블릭 DNS 주소]  -> user이름은 보통 ubuntu로 설정됨 

![ea16fc7e-16af-4be8-8d71-6840c88034b5](file:///C:/Users/gjaischool1/Pictures/Typedown/ea16fc7e-16af-4be8-8d71-6840c88034b5.png)



- enter 후 -> yes 입력후 엔터 -> 우분투 환경에 잘 접속된것을 확인할 수 있음 *※* 만약에 yes가 안뜬다면  위과정을 잘 실행했는지 다시한번 확인
  
  

  ![781bcb8a-d305-48c1-a5cc-f5178c388336](file:///C:/Users/gjaischool1/Pictures/Typedown/781bcb8a-d305-48c1-a5cc-f5178c388336.png)

- 패키지 정보를 업데이터 : sudo apt-get update

- 패키지 의존성 검사 및 업그레이드: sudo apt-get dist-upgrade

- 이런 화면이 나오면 enter 클릭
  ![ebc17b42-da35-42c7-b383-9e188983a19c](file:///C:/Users/gjaischool1/Pictures/Typedown/ebc17b42-da35-42c7-b383-9e188983a19c.png)

- python3 패키지 매니저(pip3) 설치 : sudo apt-get install python3-pip

---

## 4. Github에 프로젝트 업로드하기

- vscode 사용 
  
  ![a5cd79c3-2379-4277-998f-7591ce18fbf8](file:///C:/Users/gjaischool1/Pictures/Typedown/a5cd79c3-2379-4277-998f-7591ce18fbf8.png)

- debug는 상관없고 host는 0.0.0.0으로 설정해줘야함 

- app.py 가있는곳으로 터미널 접속하기 

- 종속성 만들기 : pip3 freeze >> requirements.txt

- 종속성 내용 확인하여 잘 들어갔는지 확인 : cat requirements.txt

- git 초기화 : git init 

- git에 현재 폴더 전체를 담기 : git add .

- 담은 파일들을 업로드할 레포지토리 주소를 origin이라는 이름으로 추가 : git remote add origin [레포지토리 주소]

- commit 하기 : git commit -m "하고싶은말"

- 담은 파일들을 origin이라는  front_end_v1 이름의 브랜치에 레포지토리 주소로 업로드 ex):  git push origin front_end_v1
  
  ### front_end_v1 브랜치를 default로 설정하기

- 내가 올린 원격저장소 branch 클릭

![1a4f28ba-e911-451e-83e9-f3e779799276](file:///C:/Users/gjaischool1/Pictures/Typedown/1a4f28ba-e911-451e-83e9-f3e779799276.png)

- switch 버튼을 통해 front_end_v1브랜치로 default 바꿔준다. 이러면 EC2 서버에 업로드할 준비가 끝남
  
  

  ![272e0e3c-60f3-4352-ae55-c698ccef771a](file:///C:/Users/gjaischool1/Pictures/Typedown/272e0e3c-60f3-4352-ae55-c698ccef771a.png)

---

## 5. EC2 서버에서 git clone 하기

- 이 프롬프트에서 실행

![f943049d-e1f0-4ddd-ab23-a2ff2dae2d72](file:///C:/Users/gjaischool1/Pictures/Typedown/f943049d-e1f0-4ddd-ab23-a2ff2dae2d72.png)

- 프로젝트 파일은 모두 srv폴더에 다운을 받는다 

- 현재 유저인 ubuntu로 소유권 바꾸기 : sudo chown -R ubuntu:ubuntu /srv/

- cd /

- ls -al -> drwxr-xr-x 2 ubuntu ubuntu 4096 Jan 12 17:33 srv 권한이 ubuntu로 바뀐걸 확인할 수 있음

- srv 폴더로 이동 : cd /srv

- git clone [레포지토리 주소]

- ls를 통해 레포지토리 이름과 동일한 폴더가 생기는지 확인 

---

## 6. uWSGI 연결하기

- 가상환경을 만들기전에 python3-venv를 설치: sudo apt-get install python3-venv

- 가상환경의 위치는 현재사용하고 있는 유저인 ubuntu 홈폴더에 만들기

- cd ~

- python3 -m venv myvenv

- 가상환경 활성화: source myvenv/bin/activate

- cd /srv/레포지토리이름/

- 종속성 설치: pip3 install -r requirements.txt (설치가 안되면 일일히 설치해줘야함)

- sudo python3 app.py 하면 서버가 실행됨 

---

## 7. 보안그룹 인바운드 규칙 주기 (위에걸로는 포트설정이 안되어 있어 실행이 안됨)

- 인스턴스 ID 클릭
  ![28cd51e6-1219-48ed-8654-8e618521f191](file:///C:/Users/gjaischool1/Pictures/Typedown/28cd51e6-1219-48ed-8654-8e618521f191.png)

- 보안 클릭

![0b5a3f22-e484-45b1-8fca-c5e256796f3a](file:///C:/Users/gjaischool1/Pictures/Typedown/0b5a3f22-e484-45b1-8fca-c5e256796f3a.png)

- 보안그룹 밑에 sg-... 클릭
  ![22337eb5-c0e5-423f-9186-202fc30a86c3](file:///C:/Users/gjaischool1/Pictures/Typedown/22337eb5-c0e5-423f-9186-202fc30a86c3.png)

- 인바운드 규칙 편집 

![3e12985a-877e-4aec-a7b5-29d724628bb2](file:///C:/Users/gjaischool1/Pictures/Typedown/3e12985a-877e-4aec-a7b5-29d724628bb2.png)

- 규칙추가

![d8e541b4-5306-4e40-86e8-a45b529c69f0](file:///C:/Users/gjaischool1/Pictures/Typedown/d8e541b4-5306-4e40-86e8-a45b529c69f0.png)

- 플라스크는 5000 포트 django는 80 포트를 사용함 위의 규칙대로 설정해주면 됨

- 다시 sudo python3 app.py 실행 

- 이제 퍼블릭 IPv4 주소 + :port 번호 입력하면 접속가능함 

![4c6ac52f-2f89-47e3-8ddf-7091148c59f9](file:///C:/Users/gjaischool1/Pictures/Typedown/4c6ac52f-2f89-47e3-8ddf-7091148c59f9.png)
