p5_JS

해당 repository 는 <a href="https://www.youtube.com/channel/UCvc8kv-i5fvFTJBFAk6n1SA">생활코딩</a> 님의 유튜브 채널을 참고하여 만들어졌습니다.

p5.js는 모션 그래픽을 위한 도구입니다. 

이 도구를 이용하면 웹브라우저 위에 자유롭게 그림을 그릴 수 있고, 그림을 움직이게 할 수 있고, 그림과 상호작용할 수 있습니다.  - 생활코딩님

## 설치

CDN

```html
<script src="https://cdn.jsdelivr.net/npm/p5@1.2.0/lib/p5.min.js"></script>
```

CDN 을 집어넣고 

```javascript
// 함수명은 setup 고정이여야 함
function setup() {
    // 400 (가로) * 800 (세로) 의 화면을 만듦
    createCanvas(400, 800)
    // 배경의 색을 회색으로 지정
    background('gray')
}
```

을 했을 때 

<img src="gitImages\startCanvas.png">

다음과 같은 화면이 출력되면 설치가 완료된 것이다.