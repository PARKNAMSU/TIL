# 리액트의 state와 리액트의 생명주기

### state 추가
props와 달리 변경할 수 있는 값인 state를 클래스 컴포넌트에 추가한다.

```javascript
class Main extends React.Component {
  constructor(props){
    super(props);
    this.state.content = 'Hellow It is React Basic!!';
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
...
