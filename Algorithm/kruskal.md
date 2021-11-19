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
```javascirpt
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
3. 각각의 정점들의 부모(root)를 본인으로 설정한다.
4. 오름차순으로 정렬한 간선들을 순회하며 연결하며 비용을 계산한다.
5. 이때 연결된 2개의 정점의 부모가 다르면 숫자가 큰 정점의 부모를 작은 정점의 부모로 설정하고 같으면 연결하지 않는다.
6. 순회가 끝나면 연결된 그래프의 비용을 리턴한다.

<br>

### Kruskal Al
