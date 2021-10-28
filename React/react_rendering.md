# 리액트 엘리먼트 렌더링

### react와 react-dom import
랜더링할 js 파일에 react 와 react-dom 라이브러리를 import 한다.
```javascript
import React from 'react'; // 리액트 사용
import ReactDOM from 'react-dom'; //리액트 dom으로 랜더링할 때 사용
```

<br>

### 랜더링할 dom 생성
html 문서에 리액트 엘리먼트가 랜더링할 `<div>` 태그를 생성한다.
  ```html
  <div id='root'></div>
  ```

<br>

### 리액트 엘리먼트 생성
랜더링할 리액트 엘리먼트를 생성한다.(JSX문법 사용)
```javascript
let App = () => { // 리액트 엘리먼트를 생성할때는 앞글자를 대문자로 생성
  return (
    <div>
      <h1>Hellow React!!</h1>
    </div>
  )
}
```

<br>

### 리액트 엘리먼트 랜더링
리액트 엘리먼트를 dom에 랜더링 시킨다.
```javascript
ReactDom.render(
  <App />,
  document.getElementById('root');
)
```
