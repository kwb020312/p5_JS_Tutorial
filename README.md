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

## fill & nofill

도형에게 색을 입힌다 , 도형에게 빈 색을 입힌다 두개의 방법으로 우린 도형을 꾸밀 수 있다.

```javascript
fill('red')
circle(10,10,10)
```

fill 함수는 4가지 인자를 받는데 3화소색 기준 fill(R,G,B,Opacity)
이며 투명도는 0 이 완전투명 255 는 불투명을 의미한다.

위와 같은 명령어를 입력한다면 빨갛게 채워진 원을 볼 수 있다.
반면 빈 속을 넣고싶을 때에는

```javascript
noFill()
circle(10,10,10)
```

스타일 뒤에 오는 도형은 위에 겹쳐진 모든 성질을 부여받는다.

## stroke & strokeWeight

테두리의 색은 도형의 색 만큼이나 많이 쓰이는데,

```javascript
stroke('red')
strokeWeight(10)
circle(10,10,10)
```

테두리의 색이 붉은색 이며 굵기는 10 인 원을 생성한다.
즉 위와같이 겹겹이 쌓아서 한번에 스타일을 줄 수 있음

<img src="gitImages\fill&stroke.png">

## draw & random

setup 함수는 실행되며 한 번만 실행되며 판을 그릴 때 사용하였다.
그렇다면 반복적으로 변화를 주고싶을 때 어떻게 해야할까?

```javascript
// 이름은 반드시 draw 여야함
function draw() {
    // 매우 빠르게 반복실행됨
    // 사이즈가 0 ~ 100 사이의 원이 빠르게 무한히 생성됨
    // random(100) === Math.random() * 100
    circle(0,0,random(100))
}
```

<img src="gitImages\draw & random.png">

## 이동하는 애니메이션

부드러운 모션을 주려면 어떻게 해야할까??

```javascript
function setup() {
    // 윈도우 창의 width 값 , height 값을 줌 (최대값)
    createCanvas(windowWidth,windowHeight)
    // x 축 변수 선언 (기존 JS 와 다르게 스코프 영향 X)
    x = 0;
}

function draw() {
    // 회색의 뒷배경 즉 원이 여러개 찍히지 않고 하나 찍히고 가려지고 반복
    background(220)
    x += 10;
    circle(x,100,100)
}
```

위와같이 선언한다면 부드러운 애니메이션 효과를 줄 수있다.

## mouseX & mouseY

다양한 이벤트 중 마우스 이벤트는 특별히 많이 쓰이기도 하는데

```javascript
// 실행될 때 판을 그려주는 함수
function setup() {
    createCanvas(windowWidth, windowHeight)
}
// 매우 빠른 반복실행
function draw() {
    // x 축 좌표는 매 초마다 마우스의 x축을 따르며 y 축 좌표도 마찬가지,
    // 랜덤 값은 -10 ~ 10 사이의 크기로 결정된다.
    circle(mouseX,mouseY,random(-10,10))
}
```
<img src="gitImages\heart.png">

## mousePressed & mouseIsPressed

마우스가 누른 상태로 지속되는가 와 마우스를 눌렀는가 로 구분할 수 있는 해당 이벤트들은

```javascript
// 매우 빠른 반복실행
function draw() {
    // 마우스를 누른 동안
    if(mouseIsPressed) circle(mouseX,mouseY,random(10))
}
// 마우스를 누른 순간 단 한번
function mousePressed() {
    // rgb 랜덤 값으로 배경 색 변경
    background(random(255),random(255),random(255))
}
```

mouseIsPressed 는 마우스를 누르고 있는 동안 계속 실행되며 true 를 반환하기에 draw 함수 내부 if 문에 사용하기에 적합하다

반면 색상이 계속 바뀌면 눈이 아프기 때문에 마우스를 누른 순간 딱 한번 실행하고 싶다면 mousePressed 함수를 만든다면 마우스를 누른 순간 이벤트가 발생하며 한 번만 실행된다.

<img src="gitImages\mouseEvent.png">