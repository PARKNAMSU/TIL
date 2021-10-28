# 리액트 클래스 컴포넌트

### 리액트 함수 컴포넌트를 클래스 컴포넌트로 변경
아래 함수 컴포넌트틀을 클래스 컴포넌트로 변경한다.
```javascript
const Main = (props) => {
  return (
    <div>
      <h1>props.title</h1>
    </div>
  );  
}
const App = () => {
  return (
    <div>
      <Main title='Main Page' />
    </div>
  );
}
```

<br>

클래스 함수로의 변경과정은 다음과 같다.
1. React.Component를 상속받는 클래스를 생성한다.
2. render()라는 메서드를 생성한다.(오버라이드?)
3. 함수의 return을 render메서드로 이동시킨다.
4. 생성자(constructor) 로 props을 받고 super 에 props를 준다.
5. this.props로 props를 불러온다.
```javascript
class Main extends React.Component {
  constructor(props){
    super(props);
  }
  render(){
    return (
      <div>
        <h1>{this.props.title}</h1>
      </div>
    );
  }
}

class App extends React.Component {
  render(){
    return (
      <div>
        <Main title='Main Page' />
      </div>
    );
  }
}
```

<br>

### [Codepen 에서 확인](https://codepen.io/parknamsu/pen/qBXjKzV)

<br>

참조<br>
[react 공식문서](https://ko.reactjs.org/docs/state-and-lifecycle.html)
