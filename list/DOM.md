# DOM
## 정의
**DOM(Document Object Model)** | XML, HTML 문서의 각 항목을 계층으로 표현하여 생성, 변형, 삭제할 수 있도록 돕는 인터페이스
<p align = "center">
<img src = "https://user-images.githubusercontent.com/49031232/167849158-70f037c0-5bbd-48f9-9005-f8e702fb5292.png">
</p>
<p align = "center">
사진 출처 - 위키백과
</p>

## 특징
- **BOM(Browser Object Model)** 의 하나로, **트리 구조**로 되어있다.
- 자바스크립트로 요소에 접근해서 **요소를 조작**할 수 있다.
- after, before 같은 **가상 요소를 포함하지 않는다.**

다음은 빈 HTML body에div 태그를 추가하는 JS 코드와 그 실행결과(웹페이지 화면)이다.
```js
var body = document.body;
var divText = document.createElement('div');
var divHTML = document.createElement('div');
var divTextContent = document.createElement('div');
divText.innerText = "This is innerText.";
divHTML.innerHTML = "This is innerHTML.";
divTextContent.textContent = "This is textContent.";
body.append(divText);
body.append(divHTML);
body.append(divTextContent);
```
![image](https://user-images.githubusercontent.com/49031232/167904826-20db6f43-7845-41b8-95a8-84b4610b82fe.png)

### `innerText`, `innerHTML`, `textContent`의 차이
|종류|기능|
|:--:|:--:|
|`innerText`|Element 내의 보여지는 텍스트 값을 읽음|
|`innerHTML`|Element의 HTML, XML의 전체 내용을 읽음|
|`textContent`|Node가 가지고 있는 텍스트 값을 그대로 읽음|
- `innerText`는 보이지 않는 값을 가져오지 않는다. ex.) `display: none;`값
- `innerHTML`은 HTML 태그 요소를 가져와서 조작할 수 있기 때문에 XSS공격에 취약할 수 있다.
- `textContent`는 보이지 않는 값도 가져온다.

다음은 `innerText`, `innerHTML`, `textContent`의 차이를 알아보기 위한 코드와 그 실행결과(콘솔)이다.
> HTML 코드
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  <div id="divEx">이것은 보이는 글자입니다.          사이에 긴 공백이 있습니다.
    <span style='display:none'>
      이것은 숨겨진 글자입니다.
    </span>
  </div>
</body>
</html>
```
> JS 코드
```js
var divEx = document.querySelector('#divEx');
console.log(divEx.innerHTML);
console.log(divEx.innerText);
console.log(divEx.textContent);
```
> `innerHTML`의 실행결과
```console
"이것은 보이는 글자입니다.          사이에 긴 공백이 있습니다.
    <span style=\"display:none\">
      이것은 숨겨진 글자입니다.
    </span>
  "
```
> `innerText`의 실행결과
```console
"이것은 보이는 글자입니다. 사이에 긴 공백이 있습니다."
```
> `textContent`의 실행결과
```console
"이것은 보이는 글자입니다.          사이에 긴 공백이 있습니다.
    
      이것은 숨겨진 글자입니다.
    
  "
```
