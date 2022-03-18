# SQL CRUD(Create, Read, Update, Delete)

<br>
아래와 같은 테이블이 있다고 가정

<img width="133" alt="image" src="https://user-images.githubusercontent.com/62639722/159026676-1ee944d3-2407-4b84-bfae-8628cfb76ab8.png">

## Create

테이블에 데이터를 Create 하는 것은 INSERT 문을 사용하여 할 수 있다.

```sql
INSERT INTO student(id,name,age,grade,major) VALUES('someId','홍길동',21,2,'economics');
```

테이블 이름() 안에 컬럼을 명시하고 VALUES() 안에 데이터들을 삽입한다.(VALUES 안에는 테이블 이름() 안에 명시한 컬럼 순서대로 삽입해야 한다.

<br>

## Read

테이블의 데이터를 Read 할떄는 Select 문을 사용하여 할 수 있다.

```sql
SELECT * FROM student
SELECT id,name,grade FROM student
```

SELECT 와 FROM 사이에 읽고싶은 데이터를 명시하고(`*` 입력하면 모든 컬럼 Select) FROM 뒤에 데이터를 가져올 테이블을 명시한다.

<br>

WHERE 문을 사용하여 원하는 데이터만 필터링하여 가져올 수 있다. (`SELECT [column] FROM [table] WHERE [조건]`)

```sql
SELECT * FROM student WHERE major = 'computerscience'
```

<br>

## Update

테이블의 데이터를 변경할때는 Update 문을 사용한다.

Update 문을 사용할때는 Where 문을 사용하지 않으면 모든 데이터가 업데이트 되므로 데이터 변경시에는 Where 문을 사용해야 한다.

```sql
UPDATE student SET major = 'computerscience' WHERE name = '홍길동'
```
  
`UPDATE [table] SET [column = value] WHERE [조건]` 형태로 사용한다.  

<br>

## Delete

테이블의 데이터를 삭제할 때는 Delete 문을 사용한다. 

Delete 문을 사용할때는 Where 문을 사용하지 않으면 모든 데이터가 삭제 되므로 데이터 변경시에는 Where 문을 사용해야 한다.

```sql
DELETE FROM student WHERE id = 'slsl1234'
```

`DELETE FROM [table] WHERE [조건]` 형태로 사용한다.

<br>

## 참조

[TCP School](http://www.tcpschool.com/mysql/mysql_basic_delete)
