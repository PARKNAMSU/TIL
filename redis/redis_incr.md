# INCR

<br>

## incr

incr 명령어는 데이터의 숫자를 1 씩 증가시킨다.

존재하지 않은 키일 경우 생성하여 0으로 초기화 한 후 증가시킨다.

```
> set a 10
> OK
> incr a
> 11

> incr b
> 1
```

## Error

문자형 데이터에 incr 를 사용했을 경우와 incr 명령의 결과로 정수값의 범위를 초과했을 경우 에러가 발생한다.

레디스의 정수는 64비트 부호 정수이고, 범위는 `-9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807` 이다.

<br>

## 페이지 조회수 확인에 사용

해당페이지의 날짜별로 조회수 확인이 필요한 경우, incr 를 이용하여 incr [pagename]:[date] 형태로 많이 사용된다.

```
> incr myPage:20220324
> 1

> incr index:20220324
> 1
```

<br>

## 참조

[redis gate](http://redisgate.kr/redis/command/incr.php)
