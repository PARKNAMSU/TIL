# INCRBY , DECRBY

<br>

## π incrby

incrby λͺλ Ήμ΄λ λ€μ μ§μ ν μ«μλ§νΌ κ°μ μ¦κ°μν¨λ€(μλ κ°μ΄ 10 μΈ κ°μ λν΄ incrby 20 μ ν  κ²½μ° -> 30)

`incrby [key] [value]` νμμΌλ‘ μ¬μ©νλ€.

```shell
> set a 10
> OK

> incrby a 20
> 30
```

<br>

incrby μλ μμλ μλ ₯ κ°λ₯νμ§λ§, μμλ μλ ₯μ΄ λΆκ°λ₯νλ€.

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

## π decrby

decrby λ incrby μ λ°λλ‘ μ§μ ν λ§νΌ κ°μ κ°μμν¨λ€.

μ¬μ©λ²μ incrbyμ λμΌνλ€.

```shell
> set a 10
> OK

> decrby a 5
> 5
```

<br>

decrby μμ μμ μ¬μ© μ κ°μ΄ μ§μ ν λ§νΌ μ¦κ°νλ€.

```shell
> set a 10
> OK

> decrby a -5
> 15
```

decrby μ­μ incrby μ λ§μ°¬κ°μ§λ‘ μμ μ¬μ©μ΄ λΆκ°λ₯νλ€.

<br>

## μ°Έμ‘°

[redis gate](http://redisgate.kr/redis/command/decrby.php)
