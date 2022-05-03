# Event Loop
- JavaScript의 일반적인 동작 방식
- Event Loop의 구성요소: Call Stack, Message Queue, Job Queue

|종류|기능|
|:--:|:--:|
|Call Stack|함수들이 등록되는 LIFO 스택.</br>이벤트 루프가 콜스택이 빌 때까지 스택의 함수를 실행.|
|Message Queue|setTimeout같은 지연실행함수를 등록하는 FIFO 큐.</br>콜스택이 비면 메시지 큐에 등록된 함수를 콜스택으로 보냄.|
|Job Queue|Promise에 등록된 콜백을 등록하는 FIFO 큐.</br>콜스택이 비지 않아도 잡 큐에 등록된 함수를 콜스택으로 보냄.|

함수의 실행 순서에 유의!
