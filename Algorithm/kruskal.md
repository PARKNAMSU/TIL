# Kruskal Algorithm

### Kruskal Alogrithm 이란?
Kruskal Algorithm 이란 가장 적은 비용으로 모든 노드를 연결하기 위한 알고리즘 이다.
<br>
Kruskal Algorithm은 비용을 계산해야 하기 때문에 가중치 그래프를 사용한다.
<br><br>
> 가중치 그래프란?

가중치 그래프는 그래프의 간선에 가중치(비용,거리 등)을 추가한 그래프를 말한다.
 
 ![image](https://user-images.githubusercontent.com/62639722/142419834-6f5dd5b2-c677-4444-83d9-27576b6c8b66.png)

위와 같이 간선들에 비용이 추가된 것을 가중치 그래프라고 한다.

### Kruskal Algorithm 진행 순서

Kruskal Algorithm의 진행 순서는 아래와 같다.
<br>

1. 가중치 그래프를 생성한다.
```javascript
//간선 class
class Edge {

    //연결할 node1, node2, 비용(거리)을 입력받는다.
    constructor(a,b,distance){
        this.a = a;
        this.b = b;
        this.distance = distance;
    }
    toString(){
        return `node1: ${this.a} node2: ${this.b} distance: ${this.distance}`;
    }
}

//그래프에 간선을 추가한다.
const makeEdges = () => {
    let arr = [];
    arr.push(new Edge(1,7,12))
    arr.push(new Edge(1,4,28))
    arr.push(new Edge(1,2,67))
    arr.push(new Edge(1,5,17))
    arr.push(new Edge(2,4,24))
    arr.push(new Edge(2,5,62))
    arr.push(new Edge(3,5,20))
    arr.push(new Edge(3,6,37))
    arr.push(new Edge(4,7,13))
    arr.push(new Edge(5,6,45))
    arr.push(new Edge(5,7,73))

    return [arr,7];
}
```
2. 간선들의 비용을 오름차순으로 정렬한다.
```javascript
//가중치 그래프
let [edges,max] = makeEdges();
//각 정점
let set = new Array(max);
//비용 합계
let sum = 0;

//추가한 간선을 오름차순으로 정렬한다.
edges.sort((item1,item2) => {
    return item1.distance - item2.distance;
});
```
3. 각각의 정점들의 부모(root)를 본인으로 설정한다.
```javascript
// 각각의 그래프의 root를 본인으로 설정
for(let i = 0; i<set.length; i++)
    set[i] = i;
```
5. 오름차순으로 정렬한 간선들을 순회하며 연결하며 비용을 계산한다. (이때 연결된 2개의 정점의 부모가 다르면 숫자가 큰 정점의 부모를 작은 정점의 부모로 설정하고 같으면 연결하지 않는다)
```javascript
for(let i=0; i < edges.length; i++){
    //노드의 root가 같지 않을시에만 실행
    if(!isSameParent(set,edges[i].a-1,edges[i].b-1)){

        // 비용을 추가하고 각 노드의 부모를 합침
        sum += edges[i].distance;
        unionParent(set,edges[i].a-1,edges[i].b-1)
        console.log(edges[i].toString());
    }
}
```
9. 순회가 끝나면 연결된 그래프의 비용을 리턴한다.
```javascript
return sum;
```
<br>

### 전체 코드
```javascript
//해당 node의 root를 찾는다.
const getParent = (graph, node) => {
    if(graph[node] === node) 
        return node;
    return getParent(graph,graph[node]);
}
//root가 같은지 비교한다.
const isSameParent = (graph,node1,node2) => {
    let a = getParent(graph,node1);
    let b = getParent(graph,node2);

    return a === b ? true:false;
}
//root를 같게 만들어 간선을 합친다.
const unionParent = (graph,node1,node2) => {
    let a = getParent(graph,node1);
    let b = getParent(graph,node2);

    if(a < b) 
        graph[b] = a;
    else
        graph[a] = b;
}

//간선 class
class Edge {

    //연결할 node1, nod2, 비용(거리)을 입력받는다.
    constructor(a,b,distance){
        this.a = a;
        this.b = b;
        this.distance = distance;
    }
    toString(){
        return `node1: ${this.a} node2: ${this.b} distance: ${this.distance}`;
    }
}

//그래프에 간선을 추가한다.
const makeEdges = () => {
    let arr = [];
    arr.push(new Edge(1,7,12))
    arr.push(new Edge(1,4,28))
    arr.push(new Edge(1,2,67))
    arr.push(new Edge(1,5,17))
    arr.push(new Edge(2,4,24))
    arr.push(new Edge(2,5,62))
    arr.push(new Edge(3,5,20))
    arr.push(new Edge(3,6,37))
    arr.push(new Edge(4,7,13))
    arr.push(new Edge(5,6,45))
    arr.push(new Edge(5,7,73))

    return [arr,7];
}

// kruskal 알고리즘을 통해 최적의 비용을 구한다.
const kruskal = () => {
    //가중치 그래프
    let [edges,max] = makeEdges();
    //각 정점
    let set = new Array(max);
    //비용 합계
    let sum = 0;

    //추가한 간선을 오름차순으로 정렬한다.
    edges.sort((item1,item2) => {
        return item1.distance - item2.distance;
    });
    // 각각의 그래프의 root를 본인으로 설정
    for(let i = 0; i<set.length; i++)
        set[i] = i;
    
    for(let i=0; i < edges.length; i++){
        //노드의 root가 같지 않을시에만 실행
        if(!isSameParent(set,edges[i].a-1,edges[i].b-1)){

            // 비용을 추가하고 각 노드의 부모를 합침
            sum += edges[i].distance;
            unionParent(set,edges[i].a-1,edges[i].b-1)
            console.log(edges[i].toString());
        }
    }
    return sum;
}
```
