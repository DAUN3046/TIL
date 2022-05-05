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
  id: 1001;
};

user.id = 1002; // error
```
### Record\<T\>
프로퍼티 키를 K, 값을 T로 하는 타입 생성
```typescript
interface Info {
  name: string;
}

type ClassA = |'num1'|'num2'|'num3';

const x: Record<ClassA, Info> = {
  num1: { name: "Kim" },
  num2: { name: "Lee" },
  num3: { name: "Park" },
}
```
### Pick\<T, K\>
사용할 프로퍼티만 집합으로 선택하여 저장
```typescript
interface Restaurant {
  name: string;
  open: boolean;
}

type Restaurants = Pick<Restaurant, 'name'>;

const KoRestaurant: Restaurants = {
  name: "명가숯불갈비",
  open: true // error 선택하지 않은 값
}
```
### Omit\<T, K\>
모든 프로퍼티에서 K를 제거한 타입
```typescript
interface Restaurant {
  name: string;
  open: boolean;
}

type Restaurants = Omit<Restaurant, 'name'>;

const KoRestaurant: Restaurants = {
  name: "명가숯불갈비", // error 제외시킨 값
  open: true
}
```
### Exclude\<T, U\>
T 중 U와 겹치는 타입을 제외한 타입
```typescript
type OnlyNumber = Exclude<string|number, string>;
```
### Extract\<T, U\>
T중 U와 겹치는 타입만 추출
```typescript
type OnlyNumber = {
  firstNum: 1001;
  secondNum: 1002;
}

type NumnStr = {
  firstNum: 1001;
  firstStr: "A";
}

type Extracted = Extract<OnlyNumber|NumnStr, NumnStr>;
// NumnStr과 같은 타입
```
### NonNullable\<T\>
null과 undefined를 제외한 타입
```typescript
type T0 = NonNullable<string|number|undefined>;
// string과 number만
type T1 = NonNullable<null, undefined, string[]>;
// string[]만
```
### Parameters\<T\>
함수 매개변수 타입을 튜플로 구성
```typescript
declare function f1(arg: { a: number; b: string }) 

type T0 = Parameters<() => string>;
// type T0 = []
type T1 = Parameters<(s: string) => void>;
// type T1 = [s: string]
type T2 = Parameters<<T>(arg:T) => T>;
// type T2 = [arg: unknown]
type T3 = Parameters<typeof f1>;
// type T3 = [arg: {
    a: number;
    b: string;
  }]
type T4 = Parameters<any>;
// type T4 = unknown[]
type T5 = Parameters<never>;
// type T5 = never
type T6 = Parameters<string>;
// error! typr T6 = never
type T7 = Parameters<Function>
// error! type T7 = never
```

# 참고자료
https://www.typescriptlang.org/docs/handbook/utility-types.html
