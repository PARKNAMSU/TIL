# Redux Introduce
### Redux란?
Redux는 React에서 많이 사용되는 상태관리 라이브러리 중 하나이다.<br>
Redux는 리액트 컴포넌트와 상태(state)를 분리시켜 주고 상태를 예측 가능하게 만들어 준다.

### React에서 Redux를 사용하는 이유
React는 위에서 아래로 단방향의 데이터 흐름을 가지고 있기 때문에 부모에서 자식으로의 데이터 전달은 가능하지만 자식에서 다른 자식으로의 데이터 전달은 힘들었다.<br>
또한 프로젝트가 복잡해 지면 상태를 관리하고 유지보수 하는 것이 힘들어졌다.<br>
하지만 Redux를 프로젝트에 도입하면 상태를 store에서 관리하기 때문에 더욱 편리하게 데이터를 사용할 수 있고 상태와 컴포넌트를 분리함으로써 유지보수에서도 이점을 보이고 있다.

### Redux의 상태 변화 흐름

<img width="1066" alt="reduce" src="https://user-images.githubusercontent.com/62639722/140012458-92c8681e-bcca-4d0d-a39f-deb75841cedf.png">

1. UI에서 어떠한 action을 dispatch에게 요청한다.
2. dispatch를 통해 스토어에서 action에 맞는 reducer함수를 실행한다.
3. 그 실행을 통한 상태의 변화를 스토어에 상태에 저장한다.
4. 스토어는 그 스토어를 구독중인 UI에게 상태가 변했음을 전달해 주고 UI는 새로운 데이터에 맞게 다시 랜더링 된다.

