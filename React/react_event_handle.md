# React 이벤트 처리

### 이벤트 처리
react에서 이벤트를 처리할 때는 문자열로 전달하는것이 아닌 함수 이벤트 핸들러를 전달한다.<br>
또한 html에서는 이벤트가 소문자 형태 였지만, react는 CamelCase 문법을 사용한다.

**html 에서 이벤트 처리**
```html
<buttom onclick="clickEvent()" />
```

<br>

**React 에서 이벤트 처리**
```javascript
//function 컴포넌트 사용시 (class 컴포넌트는 this.clickEvent로 전해주어야 한다.)
<button onClick={clickEvent} />
```

<br>

### bind 사용
ES6 Class 문법으로 컴포넌트 사용 시 전달한 핸들러 함수에서 this를 처리하려면 bind로 this를 전달해 주어야 한다.<br>
```javascript
class Test extends React.Component{
  clickEvent(){
    console.log(this)
  }
  render(){
    <div>
      <button onClick={this.clickEvent.bind(this)} />
    </div>
  }
}
```

<br>

화살표 함수 사용 시 bind로 this를 전달해 
주지 않아도 된다.

```javascript
class Test extends React.Component{
  clickEvent = () => {
    console.log(this)
  }
  render(){
    <div>
      <button onClick={this.clickEvent} />
    </div>
  }
}
```

<br>

핸들러에 인자를 전달해 주고 싶을때는 bind를 이용하거나 콜백에 화살표 함수를 사용한다.
```javascript
class Test extends React.Component{
  clickEvent = (value) => {
    console.log(value)
  }
  render(){
    <div>
      <button onClick={this.clickEvent.bind(this,'bind')} />
      <button onClick={() => this.clickEvent('arrow')}/>
    </div>
  }
}
```

<br>

### 핸들러 예제
```javascript
class HandleTest extends React.Component{

    constructor(props){
        super(props)
        this.state = {name:'',age:0,tempName:'',tempAge:''}
    }
    handleClick(){
        if( this.state.tempName === '' || this.state.tempAge  === ''){
            alert("이름 또는 나이를 입력하세요");
            return;
        }
        this.setState({
            name:this.state.tempName,
            age:Number(this.state.tempAge)
        })
    }
    handleChange(e,type){
        this.setState({
            [type]:e.target.value
        })
    }
    render(){
        return (
            <div>
                <br />
                <div>   
                    이름: <input type="text"  id="name" onChange={(e) => {this.handleChange(e,'tempName')}}/>
                    나이: <input type="number" id="age" onChange={(e) => {this.handleChange(e,'tempAge')}}/>
                    <br /><br />
                    <button onClick={this.handleClick.bind(this)}>입력</button>
                </div>
                <div>
                    {this.state.name === '' ? <h3>이름과 나이를 입력하세요</h3>
                            :<h3>당신의 이름은 {this.state.name} 나이는 {this.state.age} 입니다.</h3>}
                </div>
            </div>
        )
    }
}
```

<br>

[codePen에서 확인](https://codepen.io/parknamsu/pen/ZEJvNLr)

<br>참조<br>
[react 공식문서](https://ko.reactjs.org/docs/handling-events.html)
