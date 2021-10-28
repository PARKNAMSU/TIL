# 리액트 컴포넌트와 props

###함수 컴포넌트와 클래스 컴포넌트

함수 컴포넌트는 [리액트 랜더링](https://github.com/PARKNAMSU/TIL/blob/main/React/react_rendering.md) 에서 사용한 방식으로, 함수를 이용해 컴포넌트를 생성하는 것이다.
```javascript
const App = () => {
  return(
     <div>
      <h1>I'm Function Component!!</h1>
     </div>
  );
}
```

클래스 컴포넌트는 클래스를 사용해서 컴포넌트를 생성하는 것이다.
```javascript
class App extends React.Component{ // React.Component를 상속받아야 클래스 컴포넌트로 사용할 수 있음
  render(){ render()를 이용하여 컴포넌트 구조 생성
    <div>
      <h1>I'm Class Component!!</h1>
    </div>
  }
}
```

<br>

### 컴포넌트 합성
사용자가 생성한 컴포넌트를 이용하여 새로운 컴포넌트를 생성할 수 있다.
```javascript
const Header = () => {
  return (
    <div>
      <ul>
        <li>menu1</li>
        <li>menu2</li>
      </ul>
    </div>
  );
}

const Main = () => {
  return (
    <div>
      <h1>Main Contents</h1>
    </div>
  );
}

const App = () => {
  return (
    <div>
      <Header />
      <Main />
    </div>
  );
}
```

### props 
상위 컴포넌트에서 키/값 형태로 하위 컴포넌트에 props를 할당할 수 있다.<br>
주의할 점은 props는 읽기 전용 이므로 값을 변경할 수 없다는 점이다.
```javascript
const Main = (props) => {
  return (
    <div>
      <h1>{props.title}</h1> // 상위 컴포넌트에서 할당받은 title을 props.title 형태로 사용할 수 있다. ({}내부에 자바스크립트 문법 사용)
    </div>
  );
}

const App = () => {
  return (
    <div>
      <Main title='Main Title' /> // html 의 attribute 처럼 key = value 형태로 하위 컴포넌트에 props 를 할당한다.
    </div>
  );
}
```
'{}' 를 이용하여 JSX태그 내에서 자바스크립트 코드를 사용할 수 있다.

<br>참조<br>
[React 공식문서](https://ko.reactjs.org/docs/components-and-props.html)
