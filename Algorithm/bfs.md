# BFS(Breadth First Search)

### 너비 우선 탐색(BFS) 이란?
너비 우선 탐색(BFS)이란 그래프 탐색할 때 너비를 우선적으로 해서 탐색하는 것을 의미한다.<br>
즉 root node 부터 탐색하여 인접한 노드들을 탐색하는 것을 의미한다.<br>

![image](https://user-images.githubusercontent.com/62639722/140917995-c0cb3d58-1842-49ff-9dcc-b95fcb15fa0d.png)
1번부터 탐색하여 너비를 우선적으로 탐색한다.

### example
```javascript
function bfs(tree,find){

    //root 노드를 queue에 추가
    let queue = [tree];

    //root 노드가 찾는 값일 시 바로 종료
    if(queue[0].value === find){
        return tree.index;
    }
    
    //더이상 확인할 노드가 존재하지 않을 시 종료
    //queue에 들어있는 값을 확인하기 위한 반복문
    while(queue[0].childNode !== undefined){

        //childNode(인접 노드)의 값을 확인하고 없을 시 인접 노드를 queue에 추가
        for(node of queue[0].childNode){

            if(node.value === find)
                return node.index;
            queue.push(node);
        }
        //다 처리되면 queue에서 값 제거
        queue.shift();
    }
    return 'na';
}

let tree = {
    index:1,
    value:'a',
    childNode:[
        {  
            index:2,
            value:'b',
            childNode:[
                {
                    index:4,
                    value:'d'
                },
                {
                    index:5,
                    value:'e'
                }
            ]
        },
        {  
            index:3,
            value:'c',
            childNode:[
                {
                    value:'f',
                    index:6
                }
            ]
        }
    ] 
}


console.log(bfs(tree,'f'));
```

<br>

참조<br>

[안경잡이 개발자](https://m.blog.naver.com/PostList.naver?blogId=ndb796&categoryNo=128&logCode=0)
