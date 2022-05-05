# Class

클래스의 요소는 필드(field), 생성자(constructor), 메소드(method)가 있으며, 이를 멤버member)라고 한다.

## 접근 제어자
- public > protected > private

ts는 package 개념이 없으므로 default 접근 제어자도 존재하지 않는다.

### public
프로그램 내에서 자유롭게 접근할 수 있는 멤버이다.

기본적으로 접근 제어자를 명시하지 않으면 public으로 간주한다.

### protected
멤버가 포함된 클래스와 그 하위의 클래스에 대해 외부에서의 접근을 막는다.

하위 클래스에서는 사용 가능하다.

### private
선언된 클래스 외부에서 접근할 수 없는 멤버이다.

## 상속
subclass **extends** superclass 형식으로 클래스를 상속한다.

## getters & setters
비공개로 설정하는 속성은 `private`으로 정의하고, 이를 읽고 수정하는 것은 getter와 setter를 사용한다.

속성에 직접 접근해서 수정하면 데이터 무결성이 깨질 수 있다. -> 캡슐화
```typescript
class Cat {
  private _name: string
  get name() {
    return this._name;
  }
  set name(name: string) {
    this._name = name;
}
let mine = new Cat();
console.log(nabi.name) // undefined
mine.name = "nabi";
console.log(nabi.name); // nabi
```
### readonly
읽기만 가능한 속성 선언
```typescript
class Cat {
  readonly name: string = "nabi"; // 선언 초기화
  constructor (name: string) {
    this.name = name;
  }
}
let mine = new Cat("Som"); // 생성자 초기화
mine.name = "Sally"; // error
```
### static
전역 멤버(클래스의 모든 객체가 공유하는 멤버) 선언

클래스나 객체를 생성하지 않고 클래스 내부의 함수나 인자를 사용할 수 있다.
```typescript
class LongCat{
  static size(length: number) :number {
    return this.length * 1.5;
  }
}
let length = 20;
console.log(`My cat is ${LongCat.size(length)} inches long.`)
```

## Abstract Class
코드 중복을 최소화하기 위해 사용.
```typescript
abstract class Sound {
  public sound(){
    console.log("전방 함성!");
    this.go(); // Child에서 구현
    console.log("좋다!");
  }
  abstract go(): void
}

class Cat extends Sound {
  go(): void {
    console.log("야옹~");
  }
}

const nabi = new Cat();
nabi.do();

// 전방 함성!
// 야옹~
// 좋다!
```
