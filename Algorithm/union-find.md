# Union-Find
### 합집합 찾기(Union-Find)란?

Union-Find 알고리즘은 대표적인 그래프 알고리즘 으로 합집합을 찾는 알고리즘 이다.

여러개의 노드가 존재할 때, 2개의 노드를 찾아서 해당 노드들이 서로 연결되어 있는지 찾는 알고리즘 이다.

### 그래프 만들기

![image](https://user-images.githubusercontent.com/62639722/141730347-12b3fddd-56d9-4f69-bb92-7cf70e2bdb9a.png)

위와 같이 모든 노드가 간선으로 연결되지 않은 경우는 아래와 같은 표와 같이 부모를 자기 자신으로 가리키게 한다.<br>
아래 표에서 위칸은 자신, 아래칸은 부모 노드를 가리킨다.

![image](https://user-images.githubusercontent.com/62639722/141730694-b6b8b265-5a90-482e-87f7-25770a3d779e.png)


<br><br>

![image](https://user-images.githubusercontent.com/62639722/141730808-1cdc0e28-3069-41ac-ba47-53c250540032.png)

이때 1과 2를 연결해 줌으로써 2의 부모노드를 1로 변경한다.

![image](https://user-images.githubusercontent.com/62639722/141730988-b15779a1-e430-486a-94e4-572df6427b27.png)

<br><br>

![image](https://user-images.githubusercontent.com/62639722/141731101-c80867cf-04c8-4185-b82a-712fe3f98574.png)

3과 2를 연결해줘서 3의 부모노드를 2로 변경한다.

![image](https://user-images.githubusercontent.com/62639722/141731181-20a66745-7554-40ab-83ee-335ce0c5b671.png)

<br><br>

결국 1과 2가 연결되어 있고, 3과 2가 연결되어 있으므로 1과 3도 연결되어 있다. <br>
이때 3과 1이 연결되어 있다는 것은 재귀함수를 통해 자신의 부모의 노드를 재귀적으로 탐색 함으로써 root노드인 1까지 탐색한다.

![image](https://user-images.githubusercontent.com/62639722/141731644-93de2d47-74a8-42cd-aa87-40dd2bdb83ba.png)

<br>

### example
