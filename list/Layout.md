# Layout
> 레이아웃 설정에 필요한 개념들

## Margin, Border, Padding
![image](https://user-images.githubusercontent.com/49031232/161989788-ef6cffc9-14a0-4c95-a47d-840357e29f7a.png)

`border`는 테두리, `margin`은 테두리 바깥 여백, `padding`은 테두리 안쪽 여백이다.

추울 때 패딩 입는다. 바깥쪽부터 margin - border - padding - content 순서 기억해두자.


## Block, Inline
| |Block|Inline|
| :---: | --- | --- |
|특성| - width, height **있음** </br> - margin, padding **있음** </br> - 상하로 배치됨| - width, height **없음** </br> - margin, padding. **없음** </br> - 좌우로 배치됨|
|예시|  `<p>` `<h1>` `<ol>` `<ul>` `<table>`|`<a>` `<strong>` `<br>`|

`<img>`는 inline 중에서도 **inline block**이다. 딱 자신만큼의 공간만을 가지며 가로로 이어진다. 
block 요소 사용 시 **형제지간의 마진 병합**과 **부모자식간의 마진 병합**에 유의한다.

## display
```css
p { display: inline; }
a { display: block; }
a { display: inline-block; }
```

Block과 Inline 요소의 성격을 바꿀 때 사용한다.

## float
```css
.left { float: left; }
.left2 { float: left; }
.right { float: right; }
```
왼쪽이나 오른쪽으로 정렬시킬 때 사용한다. g연이어 사용하면 해당 방향으로 겹치지 않게 줄지어 정렬된다. 다만 이름대로 둥둥 떠있듯이 배치되어 있기 때문에 의도대로 배치가 되지 않을 때도 있다. 이 때 `clear` 속성으로 float 속성을 해제할 수 있다. 더 찾아보니 가상요소 선택자인 `::after`를 이용해 빈 개체에 `clear`를 적용해 안정적으로 만드는 방식을 많이 사용한다고 한다.

<예시>
```css
.clear { clear: both; }
```
```css
.clear2::after{ display:block; content:""; clear:both }
```

## 공백 제거
```css
<style>
  * {
  margin: 0;
  padding: 0;
  }
</style>
```
반드시 <html>과 <body>태그가 가지고 있는 margin과 padding값을 0으로 초기화해야된다. 현업에서는 *로 모든 html을 선택하여 초기화해준다.

## Flex
> 1차원 일렬로 구현

|![image](https://user-images.githubusercontent.com/49031232/161988608-90e59739-9777-40e5-884a-219ed8f6ac1d.png)|
|:--:| 
|*© 2017 Victoria Kirst \<vrk@stanford.edu>*|

우선, 다음과 같이 컨테이너에 flex를 적용시켜 기본적인 배치를 해준다. 
```css
 .container {
	display: flex;
}
``` 
이 코드를 적용하고 나면 컨테이너 내의 각 item들은 자신이 가진 내용만큼만 자리를 차지하게 된다.
  
## Grid
> 2차원 행렬 구현

※ 계속 공부하며 추가할 것.

## 공유받은 좋은 참고자료들
- CSS 사전 https://opentutorials.org/course/718/3798
- CSS 단위 https://webdesign.tutsplus.com/ko/articles/7-css-units-you-might-not-know-about--cms-22
- Flex 간단 설명 https://studiomeal.com/archives/197
- Grid 간단 설명 https://studiomeal.com/archives/533
- Flex 영상강의 https://www.youtube.com/watch?v=fYq5PXgSsbE
