# JWT

### 토큰 기반 인증 (Token-based Authentication)

JWT(JSON Web Token) 은 토큰 기반 인증 중 대표적인 것이다.
<br>

기존에 세션을 사용할 때는 사용자가 로그인과 같은 인증을 하면 그 정보를 서버 또는 데이터베이스에 저장하였고,
클라이언트가 제한된 정보를 요청할 때마다 매번 서버나 데이터베이스에서 세션 정보를 찾아야 했고 이는 서버에 부담을 주었다.

<br>

토큰기반 인증은 유저의 민감 정보를 암호화하여 클라이언트에 저장하고, 토큰을 이용하여 암호화된 정보를 사용할 수 있다.

<br>

### JWT 토큰의 종류

JWT의 토큰은 아래와 같은 2가지로 구성되어 있다.

* Access Token
* Refresh Token

Access Token을 이용하여 암호화된 정보에 접근할 권한을 얻을 수 있다. <br>

하지만 Access Token을 해커와 같은 악의적인 유저가 얻는다면 사용자의 정보가 이용당할 수 있기때문에 Access Token의 유효기간은 보통 매우 짧다. <br>

Access Token의 유효기간이 끝나면 Refresh Token을 이용하여 Access Token을 재발급받는다.

<br>

하지만 Refresh Token마저 강탈당할 경우 사용자의 정보가 마음대로 사용될 수 있기때문에,
정보를 지키는 것이 매우 중요한( __ex 인터넷 뱅킹__ ) 곳은 JWT를 잘 사용하지 않는다.

<br>

### JWT 구조

JWT는 .으로 나누어진 3가지 부분이 존재한다. <br>

1. Header
```
{
  "alg": "HS256",
  "typ": "JWT"
}
```
Header 는 토큰의 종류와 어떠한 알고리즘으로 암호화 되어있는지가 담겨있다. <br>

2. Payload
```
{
  "name":"Son Heungmin"
  "age":25
}
```
Payload에는 암호화 된 정보들이 담겨있다. <br>

3. Signature <br>

header 와 payload를 비밀키와 함께 암호화한 데이터가 담겨져 있다.



