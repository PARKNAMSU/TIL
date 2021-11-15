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
* Change Name of File

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
