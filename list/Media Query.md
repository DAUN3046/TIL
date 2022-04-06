# Media Query

다양한 모바일 기기들과 창으로 볼 때에도 가독성이 좋게끔, 화면의 크기에 따라 동적으로 꿈틀대는 사이트를 만들 수 있다.

- 형식 예시1

```css
@media all (min-width: 360px) and (max-width: 720px) {
    .box1{
        background-color: blue;
        transition: background-color 0.3s;   
    }
}
```

이 예시에선 모든 장치에 대해 뷰포트의 너비가 `min-width`보다 크고 `max-width`보다 작을 때 `box1` 클래스가 스무스하게 파란색으로 변한다. 현업에서 `transition`의 시간 설정은 `0.3s`가 많이 쓰인다고 한다.

※ 관련된 특성이나 함수는 필요할 때마다 찾아서 추가한다.

- `and` 연산자 사용 가능
