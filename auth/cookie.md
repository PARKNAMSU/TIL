# Cookie

### Cookie란 ?
cookie란 서버에서 클라이언트에 데이터를 저장하는 방법 중 하나이다.<br>

cookie는 서버가 원하면 cookie를 이용하여 클라이언트에서 데이터를 가져올 수 있다는 특징을 가지고 있다.<br>

하지만 데이터를 저장하고 특정 조건을 만족해야지 데이터를 서버로 가져올 수 있고,
이러한 조건들을 __쿠키옵션__ 으로 나타낼 수 있다.

<br>

### Cookie Options

#### Domain
쿠키에서의 도메인은 포트, 서브 도메인, 세부 경로를 포함하지 않는다.
죽, _http://www.localhost.com:3000/users_ 의 Domain은 localhost.com 이 된다.<br>

Domain 옵션을 설정하면 클라이언트에서 요청 시 서버에 등록한 Domain 옵션과 같아야 쿠키를 전송할 수 있다.

