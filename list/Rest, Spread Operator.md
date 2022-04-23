# Rest Operator
함수의 인자, 배열, 객체 중 나머지 값을 묶어 사용하는 것
1. 객체의 경우
```js
const object = {
  name: "Daun",
  Major: "Math",
  job: "Student",
};

const { name, ...rest } = object2; // name을 제외한 나머지 필드를 object2에 할당 
```
2. 배열의 경우
```js
// 코드 출처: elice 자바스크립트 심화 01 실행 컨텍스트
function sumArray(sum, arr) {
if (arr.length === 0) return sum;
const [head, ...tail] = arr;
return sumArray(sum + head, tail);
}
sumArray(0, [1, 2, 3, 4, 5]);
```

# Spread Operator
묶인 배열 혹은 객체를 각각의 필드로 변환한 것
1. 객체의 경우
```js
function getMax(object){
  return Math.max(
    ...Object.values(object)
    )
}
```
2. 배열의 경우
```js
function getMax(arr){
  return Math.max(...arr)
}
```
## 참고할만한 자료
- [JavaScript Rest vs Spread Operator – What’s the Difference?](https://www.freecodecamp.org/news/javascript-rest-vs-spread-operators/)
