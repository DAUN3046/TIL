# Type
## 기본 자료형(primitive type)
### boolean
참 거짓 저장
```typescript
let isStart: boolean = true;
```
### number
부동 소수값 저장
```typescript
let dex: number = 1000;
let hex: number = 0fff; // 10진수가 아니어도 number로 사용 가능
```
### string
문자열 저장
```typescript
let str: string = "Hello world";
```
### null
값이 비어있는 상태 저장
```typescript
let n: null = null;
```
### undefined
값이 할당되지 않은 상태 저장
```typescript
let un: undefined = undefined;
```
### typeof
데이터 타입 확인
```typescript
typeof null // 'object' 라고 뜨지만 null은 객체가 아니다!
// js 초기 버전의 typeof 구현에 null이 없는 오류이다.
// null 타입을 체크할 땐 ===로 하자.
typeof undefined // 'undefined'
```
## 참조 자료형(reference type)
기본 자료형이 아닌 타입

### object
```typescript
function makeValue(o: object): void{};

makeValue({age: 20});
makeValue([1, 2]); // success
makeValue(1); // error
makeValue("Hello"); // error
makeValue(null) // error
```
## TypeScript 추가 제공 자료형
### tuple
길이와 요소들의 타입이 정해진 배열을 저장
```typescript
let score: [string, number] = ["Math", 90];

score[1].concat("English"); // number에 string 연산 불가, type error
score[2] = "English"; // 정의되지 않은 index이므로 error
``` 
### enum
상수들의 집합 저장
- **numeric enums**
```typescript
enum Subject {Calculus, SetTheory, LinearAlgebra};
```
이 때 Calculus의 값이 0, SetTheory의 값은 1, LinearAlgebra의 값은 2
- **string enums**
```typescript
enum Subject2 {Calculus = "A+", SetTheory = "A0", LinearAlgebra = "A+"};
```
- Heterogeneous enums

굳이 섞어 쓰는 것은 별로 권장되지 않음
```typescript
enum Status {
  On: "On",
  Off: 1,
}
```
### any
모든 타입 저장 가능. 컴파일 시 타입 검사 X
```typescript
let value: any = "Hello";
let value2: any = 1;
let value3: any = [0, "Bye"];
```
### void
any의 반대. 함수의 반환 값이 없을 때, 변수에 undefined나 null이 있을 때 사용.
```typescript
let empty: void = null;
function printScore(): void {
  console.log(100);
}
```
### never
항상 오류이거나 반환이 없음. 종료되지 않는 함수.
```typescript
function infiniteLoop(): never {
  while (true) {}
}

function infiniteLoop(): never {
  while (true) { break; } // 종료되는 함수이므로 error
}


function error(msg: string): never {
  throw new Error(msg);
}
```
## Utility Types
### Partial\<T\>
프로퍼티의  만드는 타입 구성
```typescript
interface Size {
  height:number;
  weight: number;
}

type blockSize = Partial<Size>;
const empty: blockSize = {};
const triangle: blockSize = { height: 30};
const rectangle: blockSize = { height: 10, weight: 20};
```
### Readonly\<T\>
재할당 방지
```typescript
interface User {
  id: number;
}

const user: Readonly<User> = {
  id: 1001,
};

user.id = 1002; // error
```
### Record\<T\>


### Pick\<T, K\>
