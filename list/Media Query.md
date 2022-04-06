# Media Query

다양한 모바일 기기들과 창으로 볼 때에도 가독성이 좋게끔, 화면의 크기에 따라 동적으로 꿈틀대는 사이트를 만들 수 있다.

```css
@media all (min-width: 360px) and (max-width: 720px) {
    .box1{
        background-color: blue;
        transition: background-color 1.5s;   
    }
}
```
