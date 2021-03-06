# Cloud Computing

### 기존의 서버
기존의 서버 방식은 전산실 등에 서버용 컴퓨터를 구축하고 인터넷을 연결하여 서비스를 제공했다.

서버의 수용능력의 한계에 다다르면 컴퓨터의 개수를 늘리거나 컴퓨터의 사양을 업그레이드 하였다.

하지만 이러한 서버 구축 방식은 아래와 같은 문제점들이 있다.

* 지속적인 관리의 필요
* 공간의 한계 

이러한 이유 떄문에 서버의 증설이 어렵게 되자, 대기업들은 서버 및 데이터를 따로 관리하는 데이터 센터를 증축하였다.

이때부터 데이터 센터의 자원을 대여하여 이용할 수 있게 되었고, Cloud Computing 서비스가 발전하기 시작하였다.

<br>

### Cloud Service
데이터 센터에서 서버의 자원, 공간, 네트워크를 제공하는 환경을 '온프라미스' 라고 한다.

현대의 Cloud Computing은 이 온프라미스와 비슷하지만
온프라미스는 물리적인 컴퓨터를 제공하는 반면 최근의 Cloud Computing은 물리적인 것이 아닌 가상머신을 제공한다.

가상머신을 제공하는 클라우드 환경은 아래와 같은 장점이 있다.

* 컴퓨터의 사양을 유연하게 조정할 수 있음
* 고정적인 비용이 들어가는 온프라미스와 달리 사용한 만큼의 비용만 지불하면 됨
*  컴퓨터의 스냅샷을 이용해 다른 컴퓨터로 즉시 이주(migration)가 가능

하지만 클라우드 환경도 단점이 존재하는데, 서버의 운영환경 자체가 클라우드 제공자에게 종속되어 버리므로, 
클라우드 서비스에 문제가 발생하면 배포중인 서버 환경에도 영향을 미칠 수 있다.

<br>

### Cloud Service 의 형태

클라우드 서비스의 형태는 Saas, Paas, Iaas 3가지가 존재한다.

* Saas : Software as a Service 의 약지로, 클라우드 제공자가 당장 사용 가능한 소프트웨어를 제공하는 것을 말한다.<br>ex) Netflix, Spotify ...

* Paas : Platform as a Service 의 약자로, 클라우드 제공자가 데이터베이스, 개발 플랫폼 까지를 제공한다.<br>ex)Oracle Cloud, Google App Engine ...

* Iaas : Infrastructure as a Service 의 약자로, 클라우드 제공자가 가상 컴퓨터 까지 제공한다.<br>ex)AWS, Microsoft Azure

<br>

### AWS
AWS는 Amazon Web Service 의 약자로 아마존에서 제공하는 클라우드 서비스이다.

AWS는 클라우드로 Computing, Network, Storage, DataBase 서비스 등 웹 서비스 및 소프트웨어 개발 및 배포에 필요한 다양한 제품들을 제공하고 있다. [aws 제품](https://aws.amazon.com/ko/products/?nc2=h_ql_prod_fs_f&aws-products-all.sort-by=item.additionalFields.productNameLowercase&aws-products-all.sort-order=asc&awsf.re%3AInvent=*all&awsf.Free%20Tier=*all&awsf.tech-category=*all)

<br>

참조 : [codestate](https://codestates.com/)
