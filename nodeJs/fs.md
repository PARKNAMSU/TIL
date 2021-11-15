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
  fs.readFile('info.json', function(err, data) {
    res.writeHead(200, {'Content-Type': 'application/json'});
    res.write(data.toString());
    return res.end();
  });
}).listen(8080);
```
