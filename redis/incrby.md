# INCRBY , DECRBY

<br>

## 📒 incrby

incrby 명령어는 뒤에 지정한 숫자만큼 값을 증가시킨다(원래 값이 10 인 값에 대해 incrby 20 을 할 경우 -> 30)

`incrby [key] [value]` 형식으로 사용한다.

```shell
> set a 10
> OK

> incrby a 20
> 30
```

<br>

incrby 에는 음수도 입력 가능하지만, 소수는 입력이 불가능하다.

```shell
> set a 10
> OK

> incrby a -5
> 5
```

<br>

```shell
> set a 10
> OK

> incrby a 1.5
> ERR value is not an integer or out of range
```

<br>

## 📕 decrby

decrby 는 incrby 와 반대로 지정한 만큼 값을 감소시킨다.

사용법은 incrby와 동일하다.

```shell
> set a 10
> OK

> decrby a 5
> 5
```

<br>

decrby 에서 음수 사용 시 값이 지정한 만큼 증가한다.

```shell
> set a 10
> OK

> decrby a -5
> 15
```

decrby 역시 incrby 와 마찬가지로 소수 사용이 불가능하다.

<br>

## 참조

[redis gate](http://redisgate.kr/redis/command/decrby.php)
