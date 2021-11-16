# File System

### NodeJS File System Module
'fs'를 require하여 NodeJS에서 파일 시스템을 사용할 수 있다.

```javascript
const fs = require('fs');
```

<br>

파일 시스템은 아래와 같은 기능이 있다
* Read File
* Create File
* Update File
* Delete File
* Rename File

<br>

### Read File
fs.readFile([fileName],[callBack]) 을 이용하여 파일의 내용을 읽어올 수 있다.

__info.json__

```json
{
  "id":"1",
  "name":"park",
  "age":"25"
}
```

<br>

__server.js__

```javascript
var http = require('http');
var fs = require('fs');

http.createServer(function (req, res) {
  //1번째 인자로 파일의 경로/이름 , 2번째 인자로 데이터를 가져오고 실행 할 콜백함수를 실행
  fs.readFile('info.json', function(err, data) {
    res.writeHead(200, {'Content-Type': 'application/json'});
    //받아온 데이터를 클라이언트에 write
    res.write(data.toString());
    return res.end();
  });
}).listen(5000);
```
<br>

### Write File
fs.appendFile(), fs.writeFile(), fs.open()을 이용하여 파일을 생성할 수 있다.
* appendFile : 파일이 있는 경우 해당파일에 내용을 추가시킨다.
* writeFile : 파일이 있는 경우 해당파일에 내용을 덮어쓴다.
* open : r,+r, w, +w, a, +a 같은 다양한 모드들이 존재
  * r : 읽기로 열기, 파일 존재하지 않을 시 에러
  * r+ : 읽기/쓰기로 열기, 파일 존재하지 않을 시 에러
  * w : 쓰기로 열기, 파일 존재하지 않을 시 생성되고 존재 시 덮어쓰기
  * w+ : 읽기/쓰기로 열기, 파일 존재하지 않을 시 생성되고 존재 시 덮어쓰기
  * a : 추가 쓰기로 열기, 파일 존재하지 않을 시 생성
  * a+ : 읽기/추가 쓰기로 열기, 파일 존재하지 않을 시 생성

<br>

__appendFile, writeFile__
``` javascript
const fs = require('fs');

function appendFile(fileName,fileText){
  fs.appendFile(fileName,fileText,(err) => console.log("append!!"));
}

function writeFile(fileName,fileText){
  fs.writeFile(fileName,fileText,(err) => console.log("write!!"));
}

appendFile('text1.txt','파일을 append 하였습니다.');
writeFile('text2.txt','파일을 write 하였습니다.');
```

<br>

__open__
```javascript
const fs = require('fs');

//openFile은 빈 파일이 생성됨
function openFile(fileName){
  fs.open(fileName,'w',(err,file) => console.log("opened!!"));
};

openFile('text3.txt');
```

<br>

### Update File
create 했을때 사용했던 appendFile, writeFile을 이용하여 파일 내용을 변경할 수 있다.

<br>

### Delete File
unlink 메서드를 이용하여 파일을 삭제할 수 있다.
```javascript
const fs = require('fs');

function deleteFile(fileName){
  fs.unlink(fileName,(err) => {
    if(err)
      throw err;
    console.log('deleted!!');
  });
}
```

<br>

### Rename File
rename 을 이용하여 파일의 이름을 변경할 수 있다.
```javascript
const fs = require('fs');

function renameFile(fileName,chgName){
  // 현재 파일, 바꿀 파일이름, 콜백함수
  fs.rename(fileName,chgName,(err) => {
    if(err)
      throw err;
    console.log('renamed!!');
  });
}
```
