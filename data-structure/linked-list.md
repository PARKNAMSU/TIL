# Linked List

## Linked List 란?

<img width="444" alt="image" src="https://user-images.githubusercontent.com/62639722/153745404-d3a9c5b1-5c46-4ae5-bf86-28c2f8b3859c.png">

연결 리스트는 배열, 스택, 큐 와는 다르게 데이터의 물리적 배치를 사용하지 않는다.  
Index를 사용하지 않고 참조 시스템을 사용하는데, 각 요소는 노드라는 공간에 저장되고, 각각의 노드에는 다음 노드를 가리키는 주소 또는 포인터가 저장되어 있다.  
연결된 다음 노드가 없을 때 까지 모든 노드들은 각각 다음 노드를 가리키고 있다.

<br>

## Linked List의 종류

* 단순 연결 리스트 (Singly Linked List)

<img width="414" alt="image" src="https://user-images.githubusercontent.com/62639722/153745572-95230704-1510-41c2-8c54-d4a5ecca58f5.png">

한쪽 방향으로만 링크 되어있는 연결 리스트

<br>

* 원형 연결 리스트 (Circular Linked List)

<img width="457" alt="image" src="https://user-images.githubusercontent.com/62639722/153745616-816c1aff-449e-4270-9653-1cc55d6c7642.png">

단순 연결 리스트처럼 단방향으로 링크되어 있지만, 마지막 노드와 첫번째 노드가 링크되어 있다.

<br>

* 이중 연결 리스트 (Doubly Linked List)

<img width="422" alt="image" src="https://user-images.githubusercontent.com/62639722/153745668-c223f5be-2972-47a0-b15c-d7a8e1b5dfef.png">

양방향 모두 링크되어 있다.

<br>

## Linked List 장점

* 새로운 요소들의 추가 삭제 시 효율이 좋다.
* 배열처럼 구조를 재구성할 필요가 없다.
* 동적인 메모리 크기를 가지고 있다.
* 메모리를 효율적으로 쓸 수 있기때문에 대용량 처리에 적합하다.

<br>

## Linked List 단점

* 배열보다 더 많은 메모리 공간을 차지한다.
* 노드 검색 시 처음부터 끝까지 검색하기 때문에 비효율적이다.

<br>

## Linked List 사용

* 메모리의 크기가 고정되어 있지 않아야 하는 경우
* 빠르게 삽입/삭제 작업이 필요한 경우
* 이미지 뷰어, 갤러리
* 뮤직 플레이어

<br>

## 참조

[velog zenoan](https://velog.io/@jha0402/Data-structure-%EA%B0%9C%EB%B0%9C%EC%9E%90%EB%9D%BC%EB%A9%B4-%EA%BC%AD-%EC%95%8C%EC%95%84%EC%95%BC-%ED%95%A0-7%EA%B0%80%EC%A7%80-%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0). 
[Develop Log of Sky Titan](https://skytitan.tistory.com/45)
