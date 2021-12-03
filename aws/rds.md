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
