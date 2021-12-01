# EC2

### EC2란?
EC2는 AWS에서 제공하는 Cloud Computing 서비스 이다.

Cloud를 통해 Server, Storage, DataBase 등 컴퓨팅 서비스를 제공, 즉 아마존에서 가상 컴퓨터 한대를 대여하는 것과 같다.

이렇게 대여한 컴퓨터를 Instance 라고 한다.

<br>

### Login 및 EC2 접속

먼저 aws에 접속하여 콘솔에 로그인을 클릭한다.
![image](https://user-images.githubusercontent.com/62639722/144190851-ee72b751-731c-467b-86c2-616b0de8e7de.png)

<br>

루트 사용자로 로그인을 진행한다.(계정이 없는경우 회원가입 진행)
![image](https://user-images.githubusercontent.com/62639722/144190958-aa50abd8-e848-40a4-b233-18489e033f72.png)

<br>

로그인 후 상단 검색창에서 EC2를 검색한 후 EC2를 클릭하여 접속한다.
![image](https://user-images.githubusercontent.com/62639722/144191249-bc0e9fa2-3745-4f84-8d41-68be8da5a1fc.png)

<br>

### Instance 생성

EC2에 접속하면 인스턴스 시작을 클릭한다.
![image](https://user-images.githubusercontent.com/62639722/144191881-495cd3d3-41ba-4167-b116-30229a6829e1.png)

<br>

원하는 Machin Image(컴퓨팅 환경) 을 선택한다.
![image](https://user-images.githubusercontent.com/62639722/144192071-7c8aceb5-59ba-4d19-a717-1356edb015dc.png)

<br>

원하는 Instance 유형을 선택한 후 하단 우측 검토 및 시작 버튼을 클릭한다.(비용 지불 원하지 않을 시 프리티어 선택)
![image](https://user-images.githubusercontent.com/62639722/144192384-a9dd38de-2805-431d-b373-2a65abcaabb3.png)

<br>

하단 우측 시작하기 버튼을 클릭한다.
![image](https://user-images.githubusercontent.com/62639722/144192485-0ce0d2bd-01b5-4f17-ad83-587e612ef930.png)

<br>

새 키페어 생성을 선택하고 키퍼에 유형, 키페어 이름을 입력하고 인스턴스 다운로드 후 인스턴스 시작 버튼을 클릭한다.
![image](https://user-images.githubusercontent.com/62639722/144192782-cdd2eae2-af24-46fc-b88d-7a615f539875.png)

<br>

### Instance 연결

인스턴스 탭으로 돌아와서 생성한 인스턴스 선택 후 연결을 클릭한다.
![image](https://user-images.githubusercontent.com/62639722/144193326-383a8071-1633-4006-a3a0-a4526afcb38e.png)

<br>

해당 메뉴얼에 따라 연결을 진행한다.(pem 파일 권한 400 으로 변경 후 ssh명령어를 이용해 가상 머신 접속)
![image](https://user-images.githubusercontent.com/62639722/144193689-903acb6f-ae9e-4ec1-b47f-cb68b24e959a.png)

<br>

인스턴스 접속이 완료되었다.
![image](https://user-images.githubusercontent.com/62639722/144194451-96fc0b71-8871-4f97-aedd-d1a7938eb07b.png)

<br>

### 인스턴스 개발 환경 세팅(node.js)

패키지 정보를 최신 상태로 유지한다.
```
sudo apt update
```

[nvm 메뉴얼](https://github.com/nvm-sh/nvm) 에 따라 nvm 설치 후 설치 버전으로 설치 확인한다.
```
nvm --version
```

node.js를 설치한다.
```
nvm install node 
```

npm 명령어가 정상적으로 입력되지 않을 수 있으므로 아래 내용을 터미널에 입력한다.
```
sudo apt install npm
```

### GitHub에서 프로젝트 Clone

자신의 GitHub 주소로 이동하여 인스턴스에 해당 프로젝트를 클론한다.(ssh 등록이 필요한 경우 ssh를 등록한다.)

clone 이 완료되면 sudo 를 이용하여 서버를 실행한다.
![image](https://user-images.githubusercontent.com/62639722/144196133-32f25e42-a18e-4c27-a85c-89f4842128a7.png)

<br>

### 보안 설정

서버 실행은 완료 되었지만 보안 설정이 안되어 있으므로 좌측 탭에서 보안그룹으로 이동한다.
![image](https://user-images.githubusercontent.com/62639722/144196475-8391eaa1-47aa-400a-b9f7-695abe85e50c.png)

<br>

인스턴스에서 자신의 인스턴스의 보안그룹 이름을 확인 후 해당 보안을 선택하여 인바운드 규칙 편집을 클릭한다.
![image](https://user-images.githubusercontent.com/62639722/144197024-2db8deda-147a-4f46-9f3e-a9875e81aa06.png)

<br>

규칙추가 -> http -> AnyWhere IPv4 를 진행한 후 규칙저장을 클릭한다.
![image](https://user-images.githubusercontent.com/62639722/144197412-3cbad00a-dae9-4de9-9d5b-150f53871c10.png)

<br>

퍼블릭 IPv4 DNS 주소에 접속하여 서버가 잘 동작하는지 확인한다.
![image](https://user-images.githubusercontent.com/62639722/144197715-c70734ac-0087-487f-91e5-7cb1ab949f55.png)

### PM2 모듈로 서버를 background에서 실행

서버를 가상 인스턴스에서 성공적으로 실행시켰지만 만약 로컬 터미널 강제 종료 시 ssh 프로세스가 종료되면서 인스턴스의 노드가 종료되므로 서버도 같이 다운된다.

PM2 모듈울 설치하면 서버를 background 에서 실행할 수 있게 만들어 터미널을 종료해도 Instance가 실행중이면 서버가 다운되지 않게 할 수 있다.

서버 폴더에서 npm install로 pm2를 설치한다.
```
npm install pm2 -g
```

pm2에 관리자 권한을 주기 위해 authbind를 추가로 설치한다.
```
sudo apt-get update

sudo apt-get install authbind

sudo touch /etc/authbind/byport/80

sudo chown ubuntu /etc/authbind/byport/80

sudo chmod 755 /etc/authbind/byport/80

authbind --deep pm2 update
```

pm2에 관리자 권한을 주어 서버를 실행시킨다.
```
authbind --deep pm2 start app.js
```

서버가 잘 실행되었으면 status가 online 상태로 되어있다.
![image](https://user-images.githubusercontent.com/62639722/144200268-a2ff3bc3-a63f-4e95-9b2d-f15b3d965069.png)

<br>

## 참조

[codestate](https://codestates.com/)<br>
[aws](https://aws.amazon.com/ko/console/)
