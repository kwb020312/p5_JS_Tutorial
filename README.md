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

// setup()을 따로 호출하지 않아도 실행됨
```

을 했을 때 

<img src="gitImages\startCanvas.png">

다음과 같은 화면이 출력되면 설치가 완료된 것이다.

## circle & rect & point

P5_JS 의 도형 만들기는 함수로 이미 정의되어있는데,
원 만들기는 아래와 같다.

```javascript
circle(x,y,size)
```

위처럼 정의할 수 있다 x y 축은 좌표평면의 x y 가 아닌 웹페이지 상에서의 left , top 의 값을 의미한다.

<img src="gitImages\circle.png">

사각형은 아래와 같은 문법으로 만들 수 있다.

```javascript
rect(x,y,width,[height])
```

[height] 부분은 생략이 가능하며 생략일 경우 width 사이즈의 정사각형이 만들어진다.

점의 경우에는

```javascript
point(x,y)
```

좌표의 설정만으로 매우 작은 점 하나를 찍을 수 있다.
매우 작아 동그라미 쳐 놓았음

<img src="gitImages\rect.png">

