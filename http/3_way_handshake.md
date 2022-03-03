# 3 way handshake

<br>

## 3 way handshake 란?

3 way handshake는 TCP 연결 시 장치들 사이의 논리적인 접속을 성립하기 위해 사용된다.

HTTP 연결 시 TCP 연결을 위해 3 way handshake를 사용하여 서버와 클라이언트 사이의 접속을 성립하게 된다.

<br>

## 3 way handshake 성립 과정

<img width="615" alt="image" src="https://user-images.githubusercontent.com/62639722/156575491-7f7845e4-aeba-43e6-9d00-1abd6689ea29.png">

1. 클라이언트에서 서버에 접속을 요청하는 SYN 패킷을 보낸다.
2. 서버는 클라이언트로 부터 SYN 패킷을 받고 클라이언트에게 요청을 수락하는 ACK와 SYN 패킷을 보내고 클라이언트의 응답을 기다린다.
3. 클라이언트가 서버로부터 ACK와 SYN 패킷을 받으면 포트를 오픈하고 서버에 ACK 패킷을 보낸다.
4. Ack 패킷을 받으면 서버는 established 상태가 되고 클라이언트와 서버가 연결된다.

<br>

## 참조

[tistory 블로그](https://mindnet.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-22%ED%8E%B8-TCP-3-WayHandshake-4-WayHandshake)
