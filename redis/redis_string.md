# Redis String Type

<br>

## 📕 Redis String Type Introduce

Redis 에는 String 타입을 저장할 수 있고, 아래와 같은 특징을 가지고 있다.

* String 을 저장할 때는 key - value 쌍으로 저장할 수 있고, key 와 value 는 1:1 관계를 가지고 있다.
* Redis 에서는 Binary-safe 문자열을 사용하며 key 와 value 모두 숫자, 한글, 이미지 등을 사용할 수 있다.
* key 와 value 의 최대길이른 512MB 이다.

<br>

## 📗 Redis Key Design

key 디자인을 할 때는 적절한 사이즈를 유지하는 것이 좋다.

* 사용자 관점: "user_100_infomation"
* 메모리 절약 관점: "u100i"

<br>

key 를 구성할 때는 단어 사이에 구분자, 특히 `_` 를 사용하는 것이 좋다.

<br>

## 참조

[redis gate](http://redisgate.kr/redis/command/strings.php)
