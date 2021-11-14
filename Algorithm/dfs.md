# DFS(Depth First Search)

### DFS 란? 
DFS 는 깊이를 우선적으로 탐색하는 그래프 탐색 알고리즘으로, 정점의 자식노드를 우선적으로 탐색하는 탐색 기법이다.

<br>

![image](https://user-images.githubusercontent.com/62639722/141681988-3b7834a9-8036-4632-8793-7cb46ea0e1e8.png)

<br>
DFS의 구현은 탐색을 해야할 노드를 담을 queue와 탐색을 완료한 노드를 담을 stack을 이용하여 구현한다.

<br>

### example

```javascript
const graph = {
    A: ["B", "C"],
    B: ["A", "D"],
    C: ["A", "G", "H", "I"],
    D: ["B", "E", "F"],
    E: ["D", 'F'],
    F: ["D", 'E'],
    G: ["C"],
    H: ["C", "J"],
    I: ["C", "J"],
    J: ["I", "H"],
};

function dfs(graph, first) {

    //탐색 완료된 느도를 담을 stack
    let stack = [];
    //탐색을 해야할 노드를 담을 queue
    let queue = [];

    //처음 탐색을 시작할 정점
    queue.push(first);

    //처리해야 할 queue가 없으면 종료
    while(queue.length > 0){
        //처리 queue의 첫번째 노드
        let node = queue.shift();

        //노드가 완료 stack에 있지 않을때만
        if(!stack.includes(node)){
            //완료 스택에 노드를 추가
            stack.push(node);
            //노드의 자식요소를 처리 큐에 추가
            queue = [...queue,...graph[node]];
        }
    }
    return stack;
}
```

<br>

참조 : https://ryusm.tistory.com/48 
