# Layout
제대로 된 웹페이지를 만들기 위해선 들어가는 모든 요소들을 잘 배치하는 것이 중요하다. 다음은 레이아웃설정에 필요한 개념들이다.

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
.clear2::after{display:block;content:"";clear:both}
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
1차원 일렬

## Grid
2차원 행렬

※ 계속 공부하며 추가할 것.

