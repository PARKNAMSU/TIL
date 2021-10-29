# 리액트의 state와 리액트의 생명주기

### state 추가
props와 달리 변경할 수 있는 값인 state를 클래스 컴포넌트에 추가한다.

```javascript
class Main extends React.Component {
  constructor(props){
    super(props);
    this.state = {content:'Hellow It is React Basic!!'};
  }
  render(){
    return (
      <div>
        <h1>{this.props.title}</h1>
        <h3>{this.state.content}</h3>
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

### state 변경
state에 직접 값을 할당하는 것은 constructor 내부에서 밖에 할 수 없다.<br>
대신, this.setState(value) 로 값을 할당한다.

```
this.setState({value:'some value'});
```
setState 로 값을 변경할 수도 있지만, 새로운 프로퍼티도 추가할 수 있다.<br>
setState 로 추가한 object는 원래 state에 병합된다. 
```
this.setState({name:'park'});
//state가 병합되어 value 프로퍼티와 name 프로퍼티를 가진다.
```

<br>

### 생명주기 메서드
클래스 컴포넌트에서는 componentDidMount와 componentWillUnmount 메소드를 사용하여 컴포넌트가 마운트 될때와 마운트 해제가 될때 어떠한 동작을 실행할 수 있다.
```javascript
class Main extends React.Component {
  constructor(props){
    super(props);
    console.log('constructor 실행');
    this.state = {content:'Hellow It is React Basic!!'};
    
  }
  
  componentDidMount(){ //component가 mount 될때 실행
    console.log('component mount');
    this.setState({name:'park'});
  }
  componentWillUnmount(){ //component가 unmount 될때 실행
    console.log('component unmount');
  }
  render(){
    console.log('component rendering')
    return (
      <div>
        <h1>{this.props.title} </h1>
        <h3>{this.state.content} </h3>
        {this.state.name ? <p>{'name:' + this.state.name}</p>:''}
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

ReactDOM.render(<App />,document.getElementById('root'))
```
### 결과
<img width="1174" alt="스크린샷 2021-10-29 오후 4 41 53" src="https://user-images.githubusercontent.com/62639722/139395657-c46a3ef3-5e6e-4280-9287-02d6d2cd8f4c.png">
<br>위 클래스 컴포넌트의 실행순서는 아래와 같다.<br>
<br>

1. 생성자(constructor) 가 실행된다.
3. render()함수가 실행되어 컴포넌트를 생성한다.
4. dom에 마운트되면 componentDidMount 실행된다.
5. componentDidMount에서 state가 업데이트 되므로 render가 다시 실행된다.
6. 만약 dom에서 컴포넌트가 삭제되면 componentWillUnmount를 실행한다.

### [Codepen에서 실행](https://codepen.io/parknamsu/pen/MWvveZv?editors=1111)
<br>참조<br>
[react 공식문서](https://ko.reactjs.org/docs/state-and-lifecycle.html)
