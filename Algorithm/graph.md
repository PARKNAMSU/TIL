# 그래프(Graph) 자료구조

### 그래프(Graph) 란?
그래프란 정점(vertex) 과 간선(edge) 로 구성되어 있는 자료구조를 말한다.<br>

### 그래프(Graph) 용어
* 정점(vertex) : node 라고도 하며, 그래프 에서는 각 지점을 의미한다.
* 간선(edge) : 정점과 정점을 연결하는 선이다.
* in-degree : 다른 정점에서 들어오는 간선의 수이다.
* out-degree : 정점에서 나가는 간선의 수이다.
* Directed Graph : 방향이 있는 그래프를 의미한다.
* Undirected Graph : 방향이 없는 그래프를 의미한다. 즉, 간선이 연결되어 있으면 서로 이동할 수 있는 양방향 그래프이다.

__Directed Graph 의 구조__
![image](https://user-images.githubusercontent.com/62639722/141252136-2704d4d6-0d9e-4f23-8383-c28c518daf92.png)

Directed Graph의 구조를 보면 화살표가 향하는 방향으로만 이동할 수 있는 단방향 그래프이다.<br>
여기서 정점2로 들어오는 간선은 1에서 들어오는 간선 하나이므로 정점2의 in-degree는 1개이고, 정점2에서 3,5로 이동되는 간선 2개이므로 out-degree는 2개이다.

<br>

__Undirected Graph 의 구조__
![image](https://user-images.githubusercontent.com/62639722/141252696-1d1d4b1a-9c82-47fd-b130-ee3b9c120bbf.png)

Directed Graph에서는 화살표가 향하는 방향으로만 이동이 가능했지만, Undirected Graph는 양방향으로 이동이 가능한 양방향 그래프 이다.
