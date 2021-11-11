# MySql 설치 및 세팅(Mac)

### MySql 설치
brew 를 이용하여 MySql을 설치한 후 완료되면 정보를 확인하여 제대로 설치되었는지 확인한다.
```
brew install 
brew info mysql
```

<br>

### MySql 서비스 실행
brew 를 이용하여 MySql을 실행시킨다.

```
brew services start mysql
```

<br>

> 성공 시
<img width="451" alt="스크린샷 2021-11-11 오후 2 47 37" src="https://user-images.githubusercontent.com/62639722/141244739-80547255-6cd4-4cd4-8d33-d8028c692584.png">

<br>

### MySql 접속
처음 접속시에는 비밀번호가 설정되어있지 않으므로 아래와 같이 유저명으로만 접속한다.<br>

__root 계정으로 접속__
```
mysql -u root
```

<br>

접속 후 아래 명령어를 터미널에 입력하여 계정의 비밀번호를 설정한다.
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your password';
```

<br>

이제 접속 시 아래와 같이 커맨드를 입력하여 비밀번호도 함께 입력해야 한다.
```
mysql -u root -p
```

![image](https://user-images.githubusercontent.com/62639722/141246081-7c559be5-d562-49a5-bb13-bad5d675309e.png)

<br>
참조<br>

[codestate](https://urclass.codestates.com/)
