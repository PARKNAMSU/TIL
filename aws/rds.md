# RDS

### RDS란?
RDS 는 Relation Database Service의 약자로 aws에서 제공하는 관계형 데이터베이스 서비스 이다.

사실 EC2 인스턴스에 데이터베이스 환경을 구축해도 되지만, RDS를 이용하면 데이터베이스 생성, 백업 및 DB확장 등을 RDS에서 제공해주기 때문에,<br>
RDS를 이용하면 더 간편하게 데이터베이스 환경을 구축할 수 있다.

하지만 전적으로 데이터베이스 구축 과정을 본인이 관리하고 싶으면, RDS를 이용하는 것보다 EC2 인스턴스에 직접 데이터베이스를 구축하는 것이 좋다.

### DB 인스턴스 생성

aws에 로그인을 하고 검색창에 RDS를 입력하여 진입한 후 데이터베이스 생성을 클릭한다.

![image](https://user-images.githubusercontent.com/62639722/144596694-ee4d9c22-d279-47be-9f93-a41117517123.png)

<br>

원하는 데이터베이스를 선택한다.

![image](https://user-images.githubusercontent.com/62639722/144596796-e00c7401-0627-4a16-ac91-f78eb6fce3ae.png)

<br>

스크를올 내려 db버전과 템플릿을 선택한다.<br>
무료 인스턴스를 원할 시 프리티어를 사용한다.

![image](https://user-images.githubusercontent.com/62639722/144596994-1c7af30a-6d61-470c-92d0-4c6b80604091.png)

<br>

설정에서 db 인스턴스 식별자, 마스터 사용자 이름, 비밀번호를 입력한다.

![image](https://user-images.githubusercontent.com/62639722/144597220-d38a2f45-d536-4a97-be53-a48bd693da1f.png)

<br>

스크롤을 내려 퍼블릭 액세스를 _예_ 로 변경 및 기존의 보안그룹이 있으면 선택, 없다면 새로 생성 후 포트를 입력한다.

![image](https://user-images.githubusercontent.com/62639722/144597617-2611d563-8c01-4290-9c86-de3cc18f1fad.png)

<br>

추가구성에서 초기 데이터베이스 이름 입력 및 옵션들을 설정한다.

![image](https://user-images.githubusercontent.com/62639722/144597822-615fedbd-01fd-4b0b-b8c1-e3e394156ade.png)

<br>

완료 시 데이터베이스 탭에 들어오면 상태가 생성중으로 되어있고, 생성완료가 되면 db사용이 가능하고, 생성완료까지 10분정도 소요된다.

![image](https://user-images.githubusercontent.com/62639722/144597999-f580071f-100d-4840-aa80-1442af726b2e.png)
