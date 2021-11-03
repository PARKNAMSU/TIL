# Redux 개발환경 세팅 및 기본 사용법
## Redux 개발환경 세팅


<br>

### Redux Core 설치
npm install 을 이용하여 Redux Core를 설치한다.
```
npm install redux
```

<br>

### Redux Toolkit 설치
npm install 을 이용하여 Redux Toolkit을 설치한다.
```
npm install @reduxjs/toolkit
```

<br>

하지만 아래와 같이 react앱을 설치하면 위에 두개의 과정을 건너뛰어도 된다

<br>

### React Redux 프로젝트 설치
터미널에 react redux 프로젝트를 설치하여 프로젝트를 생성한다.<br>
바로 프로젝트를 설치하면 Redux Core와 Toolkit을 따로 설치하지 않아도 된다.
```
npx create-react-app redux-app --template redux
```

## Redux 기본 사용법

### reducer 생성
저장소에 저장되어 상태를 처리할 reducer를 생성한다.
```javascript

let myRedux = (state = [], action) => { /* state: 저장소에 저장할 state
                                           action: 실행할 행동과 데이터 */

    //type에 따라 분기별로 나누어서 실행
    switch(action.type){
        //state 데이터 추가
        case 'ADD_STATE': {
            action.payload.index = state.length+1;
            state = [...state,action.payload];
            return [...state];
        }
        //state 데이터 삭제
        case 'DELETE_STATE': {
            let find = state.findIndex(item => item.index === action.payload.index);
            state.splice(find,1);
            console.log(state);
            return [...state];
        }
        //state 데이터 수정
        case 'MODIFY_STATE': {
            let find = state.findIndex(item => item.index === action.payload.index);
            state[find] = action.payload;
            return [...state];
        }
        //처음 랜더링 시 state제공을 위해 default 생성
        default :
            return state;
    }
}

export default myRedux;
```

### action method 생성
dispath가 reducer에게 요청할 action method를 생성한다.
```javascript
const add = (data) => {
    /* 행동할 타입과 전달할 데이터를 설정해 준다. */
    return { 
        type:'ADD_STATE',
        payload:{
            data,
            index:0
        }
    }
}

const remove = (index) => {
    return {
        type:'DELETE_STATE',
        payload:{
            index
        }
    }
}

const modify = ( { data, index } ) => {
    return {
        type:'MODIFY_STATE',
        payload:{
            data,
            index
        }
    }
}

export {add, remove, modify}
```

### React앱 랜더링 및 저장소 생성
react앱 랜더링 시 생성한 저장소를 provider 태그를 이용해 react앱에 제공해 준다.
```javascript
//reducer를 이 store에 저장하면서 저장소를 생성한다.
let store = createStore(myRedux);

//Provider 태그를 react앱에 감싸서 store를 제공해 준다.
ReactDOM.render(
  <Provider store={store} >
    <App />
  </Provider>,
  document.getElementById('root')
);
```

### app에서 redux 상태를 사용
react앱에서 redux를 이용하여 동적 ui개발을 한다.
```javascript
import './App.css';
import React, { useState } from 'react'
import { useDispatch, useSelector } from 'react-redux'
import { add, remove, modify } from './methods/methods';
function App() {

  //useSelector로 store에 있는 state를 가져옴 
  const state = useSelector(state => state);
  //reducer 에 action을 요청할 dispatch 생성
  const dispatch = useDispatch();
  const [ text, setText ] = useState('');
 
  const changeHandle = (e) => {
    setText(e.target.value);
  }
  
  const addHanedle = () => {
    if(text === ''){
      alert("내용을 입력하세요");
      return;
    }
    console.log(`${text} 데이터 입력`);
    //dispatch를 이용해 reducer에 해당 action 요청
    dispatch(add(text));
  }

  const deleteHandle = (index) => {
    console.log(`${index} 번 데이터 삭제`);
    dispatch(remove(index));
  }

  const modifyHande = (index,data) => {
    let mody_data = prompt("수정할 텍스트를 입력하세요",data);
    if(mody_data === ''){
      alert("텍스트가 비어있습니다.");
    }
    console.log(`'${data}' -> '${mody_data}' 로 변경`);
    dispatch(modify({
      data:mody_data,
      index
    }))
  }
  
  //state를 사용해 동적으로 화면 구성
  return (
    <div className="App">
      {
        state.length > 0 ?
        state.map((item,idx) => {
          console.log(item)
          return (
            <div key={idx}>
              <h2>{item.data}</h2>
              <button onClick={deleteHandle.bind(null,item.index)}>삭제</button>
              <button onClick={modifyHande.bind(null,item.index,item.data)}>수정</button>
            </div>
          )
        })
        :
        <h1>데이터가 없습니다.</h1>
      }

      <hr />
      <div>
        <input type="text" placeholder="add some text" onChange={changeHandle}></input>
        <button onClick={addHanedle}>추가</button>
      </div>
    </div>
  );
}

export default App;
```

<br>

참조<br>

[Redux 공식문서](https://ko.redux.js.org/introduction/getting-started)
