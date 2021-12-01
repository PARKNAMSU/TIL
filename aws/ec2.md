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


