# String Set Get

<br>

## set, get

set 명령어는 데이터를 저장하는 명령이다.  
사용법은 `set [key] [value]` 이다.

get 명령어는 데이터를 가져오는 명령어다.
사용법은 `get [key]` 를 입력한다.

※ terminal 에서 redis 명령어 입력 시 앞에 redis-cli 를 입력한다.

```
>set name hong
>OK

>get name
>"hong"
```

<br>

value 에 띄어쓰기를 하고싶은 경우, 데이터 저장 시 value 를 "" 로 감싸준다.

```
>set name "hong gildong"
>OK

>get name
>"hong gildong"
```

<br>

set 명령어만 사용 시 같은 key의 데이터를 다시 저장하면 나중에 저장한 데이터로 겹쳐쓰기가 된다.

```
>set name hong
>OK
>set name park
>OK

>get name
>"park"
```

<br>

## NX 옵션

NX 옵션을 사용하면 value 겹쳐쓰기가 방지된다.

```
>set name hong NX
>OK
>set name park NX
>(nil)

>get name
>"hong"
```

<br>

## XX 옵션

XX 옵션은 해당 키에 이미 데이터가 존재 할 경우에만 저장된다.

```
> set b hi
> OK

> set a hihi XX
> (nil)
> set b hihi XX
> OK

> get a
> (nil)
> get b
> "hihi"
```

<br>

## EX 옵션

EX 옵션은 뒤에 초단위를 지정하여 해당 초단위 후에 데이터가 삭제되게 한다.

```
> set name hong EX 5
> OK

# 2초 후
> get name 
>"hong"

# 5초 후
> get name
> (nil)
```

<br>

※ PX 옵션은 EX 옵션과 같지만 밀리초 단위로 지정한다.

<br>

## 새 값 저장 후 저장한 값 가져오기

`set [key] [value] get` 을 사용하면 값을 추가한 후 바로 가져올 수 있다.(6.2 이후부터 추가)

```
> set a hihi get
> "hihi"
```

<br>

버전이 맞지않아 사용할 수 없는 경우는 getset 명령어를 사용한다.

```
> getset a hihi
> "hihi"
```

<br>

## 참조

[redis gate](http://redisgate.kr/redis/command/set.php)

