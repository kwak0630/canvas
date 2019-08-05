# CANVAS 2

##### 도형그리기

###### 직사각형

fillRect(x, y, width, height) : 색칠된 직사각형

clearRect(x, y, width, height) : 특정부분을 지우는 직사각형, 지워진 부분은 투명

strokeRect(x, y, width, height) : 직사각형의 윤곽선

x와 y는 캔버스 좌측상단에서의 위치

width, height는 사각형의 크기

```js
function draw() {
  var canvas = document.getElementById('canvas');
  if (canvas.getContext) {
    var ctx = canvas.getContext('2d');

    ctx.fillRect(25, 25, 100, 100);
    ctx.clearRect(45, 45, 60, 60);
    ctx.strokeRect(50, 50, 50, 50);
  }
}
```



###### path 그리기

직사각형 외의 유일한 원시적인 도형

점들의 집합, 선의 한 부분으로 연결되어 여러가지 곡선이나 도형을 그림

1. 경로 생성
2. 그리기 명령어
3. 경로를 렌더링 하기 위해 윤곽선을 그리거나 도형 내부 채우기

beginPath() : 새로운 선을 그리겠다는 선언

moveTo(x, y) : x,y 로 지정된 좌표로 옮김

lineTo(x, y) : 드로잉 위치에서 x,y로 지정된 위치까지 선 그림

fill(), stroke() : 경로의 내부를 채워서 내부가 채워진 도형을 그림

```js
function draw2() {
  var canvas = document.getElementById('canvas2');
  if (canvas.getContext) {
    var ctx = canvas.getContext('2d');

    ctx.beginPath();
    ctx.moveTo(75, 50);
    ctx.lineTo(100, 75);
    ctx.lineTo(100, 25);
    ctx.fill();
  }
}
```



###### 원 그리기

arc(), arcTo() 메소드

선을 그리는 방식과 유사

arc(x, y, 반지름, 시작각도, 종료각도, 그리는 방향)  : 그리는 방향 true 이면 시계 반대방향 / false 이면 시계 방향

```js
function draw3(){
    var ctx = document.getElementById('canvas3').getContext("2d");

    ctx.beginPath();
    ctx.arc(75, 75, 50, 0,(Math.PI/180) *360,false);

    ctx.fillStyle = "#ffcc00";  //채울 색상
    ctx.fill(); //채우기
    ctx.stroke(); //테두리
}
```



##### 스타일과 색 적용

###### 색상

fillStyle : 도형을 채우는 색 설정

strokeStyle : 도형의 윤곽선 색을 설정

초기 색상값은 #000000

```js
// fillStyle에 적용되는 색은 모두 '오렌지'

ctx.fillStyle = "orange";
ctx.fillStyle = "#FFA500";
ctx.fillStyle = "rgb(255, 165, 0)";
ctx.fillStyle = "rgba(255, 165, 0, 1)";
```

###### 투명도

globalAlpha : 0 ~ 1 사이, 초기값은 1(완전히 투명)

```js
// 외곽선과 채움 스타일에 투명 적용

ctx.strokeStyle = 'rgba(255, 0, 0, 0.5)';
ctx.fillStyle = 'rgba(255, 0, 0, 0.5)';
```

###### 선모양

lineWidth : 두께

lineCap : 선의 끝 모양 (butt, round, square)

lineJoin :  만나는 모서리 (round, bevel, miter)

```js
function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  for (var i = 0; i < 10; i++){
    ctx.lineWidth = 1 + i;
    ctx.beginPath();
    ctx.moveTo(5 + i * 14, 5);
    ctx.lineTo(5 + i * 14, 140);
    ctx.stroke();
  }
}
```

```js
function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  var lineCap = ['butt','round','square'];

  // 안내선을 그린다
  ctx.strokeStyle = '#09f';
  ctx.beginPath();
  ctx.moveTo(10, 10);
  ctx.lineTo(140, 10);
  ctx.moveTo(10, 140);
  ctx.lineTo(140, 140);
  ctx.stroke();

  // 선을 그린다
  ctx.strokeStyle = 'black';
  for (var i=0;i<lineCap.length;i++){
    ctx.lineWidth = 15;
    ctx.lineCap = lineCap[i];
    ctx.beginPath();
    ctx.moveTo(25 + i * 50, 10);
    ctx.lineTo(25 + i * 50,140);
    ctx.stroke();
  }
}
```

```js
function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  var lineJoin = ['round', 'bevel', 'miter'];
  ctx.lineWidth = 10;
  for (var i=0;i<lineJoin.length;i++){
    ctx.lineJoin = lineJoin[i];
    ctx.beginPath();
    ctx.moveTo(-5, 5 + i * 40);
    ctx.lineTo(35, 45 + i * 40);
    ctx.lineTo(75, 5 + i * 40);
    ctx.lineTo(115, 45 + i * 40);
    ctx.lineTo(155, 5 + i * 40);
    ctx.stroke();
  }
}
```

###### 그림자

shadowOffsetX : 수평거리, 기본값 0

shadowOffsetY : 수직거리, 기본값 0

shadowBlur : 흐림효과, 기본값 0

shadowColor : 그림자 효과의 색상, 기본값 검정

```js
function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');

  ctx.shadowOffsetX = 2;
  ctx.shadowOffsetY = 2;
  ctx.shadowBlur = 2;
  ctx.shadowColor = "rgba(0, 0, 0, 0.5)";
 
  ctx.font = "20px Times New Roman";
  ctx.fillStyle = "Black";
  ctx.fillText("Sally", 5, 30);
}
```



##### 텍스트

fillText(text, x, y, [maxwidth]) : x,y 위치에 주어진 텍스트를 채운다. 최대폭은 옵션값

strokeText(text, x, y, [maxwidth]) : x,y 위치에 주어진 텍스트를 칠한다. 최대폭은 옵션값

```js
function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  ctx.font = '48px serif';
  ctx.fillText('Hello world', 10, 50);
}
```

```js
function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  ctx.font = '48px serif';
  ctx.strokeText('Hello world', 10, 50);
}
```

###### 텍스트 스타일 적용

font : 텍스트 스타일. css font 와 동일하게 사용. 기본값은 sans-serif의 10px

textAlign : start, end, left, right, center. 기본값 start

textBaseline : 베이스라인. top, hanging, middle, alphabetic, ideographic, bottom. 기본값 alphabetic

direction : 글자방향. ltr, rtl, inherit. 기본값 inherit