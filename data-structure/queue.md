# Queue

## Queue 란?

<img width="607" alt="image" src="https://user-images.githubusercontent.com/62639722/153699428-7d1b9066-4017-40a7-bd02-c0f6e9fb68c8.png">

큐와 스택은 순차적으로 데이터가 쌓인다는 것은 같지만, 스택은 출입구가 하나만 존재하여 가장 나중에 들어온 데이터가 가장 먼저 추출되고
큐는 출구와 입구가 각각 존재하여 가장 먼저 들어온 데이터부터 먼저 추출되는 자료구조 이다. **(FIFO 자료구조)**

<br>

## Queue의 장점

* 동적인 메모리 크기를 가지고 있다.
* 데이터를 받는 순서대로 정렬된다.
* 빠른 런타임

<br>

## Queue의 단점

* 가장 오래된 요소만 추출할 수 있다.
* 한번에 하나의 데이터만 처리가 가능하다.

<br>

## 사용 예시

* 프린트 대기열(가장 먼저 들어온 요청부터 처리해야 함)
* LRU(Least Recently Used) 알고리즘 구현(가장 오랫동안 참조되지 않은 페이지를 캐시에서 교체시키는 알고리즘)

<br>

## 참조

[zenoan.log](https://velog.io/@jha0402/Data-structure-%EA%B0%9C%EB%B0%9C%EC%9E%90%EB%9D%BC%EB%A9%B4-%EA%BC%AD-%EC%95%8C%EC%95%84%EC%95%BC-%ED%95%A0-7%EA%B0%80%EC%A7%80-%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0)
[nnm.log](https://velog.io/@hyeon930/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-%EC%BA%90%EC%8B%9C-Java)
