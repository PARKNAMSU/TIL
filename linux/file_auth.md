# Linux(Mac) 파일 Read, Write, Execute 권한

### Directory, File 생성
터미널에서(혹은 GUI) 에서 파일을 저장해 놓을 directory와 File 을 생성한다.
<br>

```
mkdir [폴더명]
nano [파일명]
```

나노 편집기를 이용하여 파일 내용 입력 후 ctr(^) + x, Y를 입력하여 저장한다.
![image](https://user-images.githubusercontent.com/62639722/140681744-6c047323-b961-4f54-bba9-a86c541686ab.png)

<br>

### 권한 확인

해당 directory 에서 터미널에 ls -l 을 이용하여 파일 권한을 확인한다.

<img width="467" alt="스크린샷 2021-11-08 오후 12 55 21" src="https://user-images.githubusercontent.com/62639722/140682028-87059194-ba18-445c-b1c7-cf72c8cd59e2.png">

__rwx 의 의미__
* r : 파일을 읽는 권한(read)
* w : 파일을 쓰는 권한(write)
* x : 파일을 실행하는 권한(execute)

<br>

권한을 나타내는 출력창의 의미

![image](https://user-images.githubusercontent.com/62639722/140682739-5ff95c10-788a-411b-895a-97db90a22978.png)

<br>

### 권한의 변경(chmod)

터미널에 chmod 와 아래의 표현식을 이용하여 파일, 폴더의 권한을 변경한다.

![image](https://user-images.githubusercontent.com/62639722/140683395-7407d216-e8c4-43b1-8b47-3f1f326d4bbb.png)

```
chmod g+w [filename]

chmod u=rwx [filename]
```

### Absolute Form

Absolute Form 은 권한을 숫자7까지의 3bit의 합으로 나타낸다.
* r : 4
* w : 2
* x : 1

<br>

user 에 rwx, group 에 rx, other 에 x 권한 부여
```
chmod 751 [filename]
```

<br>

참조<br>

[codestate](https://urclass.codestates.com/)
