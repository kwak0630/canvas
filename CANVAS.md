# CANVAS

- canvas 는 HTML 요소 중 하나

- 스크립트를 사용하여 그림을 그림

- 그래프, 사진 합성, 간단한 애니메이션

- 초기 값 300*150 (속성 사용하여 변경 가능)



#### 기초 사용법

```html
<canvas id="tutorial" width="150" height="150"></canvas>
```



##### 대체 콘텐츠

video, audio, picture 처럼 img와는 달리 ie9 이하의 버전이나 텍스트 기반 브라우저 등과 같은 캔버스를 지원하지 않는 오래된 브라우저들을 위한 대체 컨텐츠를 정의하기 쉽다.

canvas 속성안에 삽입

캔버스 태그를 지원하지 않는 브라우저는 컨테이너를 무시하고 내부의 대체 컨텐츠만 렌더링

캔버스 태그를 지원하는 브라우저는 컨테이나 내부 내용을 무시하고 정상적으로 렌더링

```html
<canvas id="stockGraph" width="150" height="150">
  야야야야야~~
</canvas>

<canvas id="img" width="150" height="150">
  <img src="images/sally.png" width="150" height="150" alt=""/>
</canvas>
```



##### 렌더링 컨텍스트

canvas 요소에는 getContext() 렌더링 컨텍스트와 그리기 함수를 가져오는데 사용하는 메서드가 있따.

getContext() 가 하나의 매개변수. 

```js
var canvas = document.getElementById('tutorial');
var ctx = canvas.getContext('2d');
```

 [`canvas`]는 [`document.getElementById()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)메소드를 호출하여 DOM 노드를 검색. 

getContext()를 사용하여 드로잉 컨텍스트에 액세스 할 수 있습니다 .

```js
var canvas = document.getElementById('tutorial');

if (canvas.getContext) {
  var ctx = canvas.getContext('2d');  // drawing code
} else {
}
```



##### 예제

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8"/>
    <title>Canvas tutorial</title>
    <script type="text/javascript">
      function draw(){
        var canvas = document.getElementById('tutorial');=
        if (canvas.getContext){
          var ctx = canvas.getContext('2d');
        }
      }
    </script>
    <style type="text/css">
      canvas { border: 1px solid black; }
    </style>
  </head>
  <body onload="draw();">
    <canvas id="tutorial" width="150" height="150"></canvas>
  </body>
</html>
```



#### 도형 그리기

- 기본적으로 그리드의 원점은 좌측상담의 (0,0)

- 모든 요소들은 이 원점을 기준으로 위치
- 왼쪽에서 x, 위에서 y : (x,y)



##### 직사각형

`fillRect(x, y, width, height)`

색칠된 직사각형

`strokeRect(x, y, width, height)`

직사각형 윤곽선

`clearRect(x, y, width, height)`

특정 부분을 지우는 직사각형이며, 이 지워진 부분은 완전히 투명

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

<http://code.d2.co.kr/sallykwak/study/03_canvas/>