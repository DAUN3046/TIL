# async, await
비동기 처리 문법
```js
async function 함수() {
  await 비동기처리할메소드명
}
```

```js
response = await fetch('http://...');
topics = await response.json();
console.log(topics);
```
fetch(promise를 리턴함) 앞에 await 붙이면 첫 번째 then의 response가 저장됨
