# Create Table

<br>

## 데이터 베이스 생성 및 사용

`test` 라는 데이터 베이스를 생성한다.

```
CREATE test;
```
<br>

만약 데이터 베이스를 삭제하고 싶다면 `DROP` 명령어를 사용한다.

```
DROP test;
```

<br>

해당 데이터베이스를 사용하기 위해 `USE` 명령어를 사용한다.

```
USE test;
```

<br>

## 테이블 생성

`CREATE TABLE` 을 사용하여 테이블을 생성한다.

```
CREATE TABLE [name](
  column1 [data_type] PRIMARY KEY,
  column2 [data_type] NOT NULL,
  column3 [data_type] DEFAULT [value]
)
```
왼쪽부터 `컬럼` `데이터 타입` `제약조건` 형태로 컬럼을 설정한다.  
제약조건은 없을경우 생략 가능하다.

<br>

## 제약조건

Mysql 의 제약조건은 아래와 같다.

* NOT NULL : null 값 허용 안함
* UNIQUE : 테이블에서 해당 컬럼과 중복된 값이 없어야 함
* PRIMARY KEY : row 의 기본키
* FOREIGN KEY : 다른 테이블의 필드를 참조하는 키
* DEFAULT : 해당 필드의 기본값

<br>

## FOREIGN KEY

FOREIGN KEY는 다른 테이블의 필드를 참조하고 있는 필드로 사용 방법은 다음과 같다.  
(Student 테이블의 pk인 email 을 class 테이블의 Application_subject 테이블의 student_email 컬럼이 참조한다고 가정)

`FOREIGN KEY ([참조하는 컬럼])
REFERENCES [참조되는 테이블]([참조되는 컬럼]) ON UPDATE [옵션] ON DELETE [옵션]`

```
// AUTO_INCREMENT 옵션은 insert 시 0부터 자동으로 숫자 증가하며 생성됨
CREATE TABLE Application_subject(
  id INT AUTO_INCREMENT PRIMARY KEY,
  class_name VARCHAR,
  room_name VARCHAR,
  student_email VARCHAR,
  FOREIGN KEY (student_email)
  REFERENCES Student(email) ON UPDATE CASCADE ON DELETE CASCADE
)
```

<br>

## ON DELETE, ON UPDATE

ON DELETE, ON UPDATE 는 참조되는 테이블에서 데이터의 수정 또는 삭제가 발생하면 참조하고 있는 테이블의 row 는 어떤식으로 처리할건지에 관한 옵션이다.

ON DELETE 는 참조되는 테이블의 데이터가 삭제될 경우, ON UPDATE 는 업데이트 될 경우를 설정해 준다.

**옵션**

* CASCADE : 참조되는 테이블에서 데이터를 삭제하거나 수정하면, 참조하는 테이블에서도 삭제와 수정이 같이 발생한다.
* SET NULL : 참조되는 테이블에서 데이터를 삭제하거나 수정하면, 참조하는 테이블의 데이터는 NULL로 변경된다.
* NO ACTION : 참조되는 테이블에서 데이터를 삭제하거나 수정해도, 참조하는 테이블의 데이터는 변경되지 않는다.
* SET DEFAULT : 참조되는 테이블에서 데이터를 삭제하거나 수정하면, 참조하는 테이블의 데이터는 필드의 기본값으로 설정된다.
* RESTRICT : 참조하는 테이블에 데이터가 남아 있으면, 참조되는 테이블의 데이터를 삭제하거나 수정할 수 없다.

<br>

## 참조

[TCP School](http://www.tcpschool.com/mysql/mysql_constraint_foreignKey)
