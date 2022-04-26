# Promise

- Promise의 콜백은 잡 큐 사용. 잡 큐는 잡 큐의 경우 setTimeout() 등의 API가 사용하는 태스크 큐보다 우선순위가 높음.

- Promise.prototype.finally() 메서드는 성공, 실패에 상관없이 settled되면 항상 호출된다
