# Scope
- 타입이 지정되지 않은 변수(이하 슈퍼변수라고 하겠음)는 어디에서 실행하건 global 변수이다 ex) name = 'daun'

- var은 local이라  global execute context에서 선언되었을 때만 전역이다.

- js의 빌트인 api들은 윈도우 안에 들어있다

- 슈퍼변수와 var은 gloval execute context에서 둘 다 global scope이다.

- 함수 안에선 let과 var 모두 local scope이므로 똑같이 동작한다. global 선언 시 var는 global 객체로 들어가고 let은 script scope로 들어간다.
