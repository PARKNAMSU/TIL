# 환경 변수(Environment Variable)

### export
터미널에 export를 이용하여 설정된 환경변수를 확인할 수 있다.<br>

```
export
```

export 명령어 뒤에 새로운 환경변수를 입력하여 환경변수를 생성할 수 있다.<br>

환경변수를 확인할 때는 echo $(dollar sign)[환경변수] 를 입력하여 확인한다.<br>


```
export TEST_ENV_VAL="It is a Test Env Value"
echo $TEST_ENV_VAL
```

<br>

![image](https://user-images.githubusercontent.com/62639722/140686494-5e7a46b6-c30b-47ef-aacd-cc1dfc8377e2.png)


<br>

참조<br>
[codestate](https://urclass.codestates.com/)
