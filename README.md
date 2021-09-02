# Camp 51.9 (영등포고등학교 메이커 스페이스)

 안녕하세요. 영등포고등학교 메이커스페이스 Camp51.9 메니저(3)로 활동하고있습니다. 저는 장비 및 프로그램 관리를 하고있습니다.

[Camp51.9 Information]: https://www.makeall.com/reservation/info.php?space_no=1677	"메이크올"
[Camp51.9 Website]: https://camp.ydp.hs.kr/	"Camp51.9"
[개인 포트폴리오]: https://sungjaesportfolio.netlify.app/	"Sungjae's Portfolio"



## 3D Printer Managed Web Site  Project

 기관을 이용하는 분들이 3D 프린터 8대의 상황을 웹 사이트에 나타내고 사용자 정보를 데이터베이스에 저장 그리고 구글 스프레트시트API를 사용하여 3D 프린터를 이용한 사람들의 정보를 기록하는 웹사이트 프로젝트입니다.

[2020.01.25 ~ 2020.02.28 ]   완성 - 

[Camp51.9 이용대장]: https://peaceful-euler-43deb6.netlify.app/	"3D 프린터 이용대장"

### 결과물

#### 사용 사진

<img src="사진\이용대장 사용.jpg" alt="KakaoTalk_20210331_173248259" style="zoom:100%; float: left;" />

Camp 51.9 3D 프린터 및 레이저커터실의 **3D프린터 8대**와 **이용대장**을 학생들이 사용하고 있는 모습입니다. 이용대장은 라즈베리파이를 이용해 열었고 화면 옆에 구글 스프레드시트는 스프레드시트 API를 이용하여 사용로그를 시록합니다.



#### 주요 기능

**1. 팝업창**

   영등포고 재학생, 외부 일반인으로 나눈 팝업창

   재학생 팝업창은 **소속** 대신 **학번** 입력창

![기능 1  팝업창](https://user-images.githubusercontent.com/88194064/131792745-f7d6c626-4eaa-432c-a4b6-3016d061748d.gif)

**2. 프린터 사용 상태 표시**

   사용가능(READY), 사용완료(FINISH), 타이머 + 카카오톡 예약(영상 x)

![기능 2  프린터 상태 표시](https://user-images.githubusercontent.com/88194064/131792975-b6849e50-a683-48a9-8f9d-62e22fabc556.gif)

**3. 데이터베이스 정보 저장**

   영상 참고

**4. 구글 스프레드시트 API 문서화**

   영상 참고

![기능 2,3,4](https://user-images.githubusercontent.com/88194064/131792838-db9a57af-69aa-4621-82a8-6a1abd5c168e.gif)

**5. 그 외**

+ 이미 사용중인 프린터 사용 불가 알림창

+ X 버튼 클릭시 form 태그 값 초기화
+ 비어있는 텍스트 박스가 있는 경우 알림 후 포커싱
+ 등등

### 개요

 이번 겨울방학 동안 웹 프로그래밍을 한번 공부하고자 했습니다.  무언가를 직접 만들며 공부하는 것이 더 효율적이라고 생가각한 저는 목표를 정하였습니다. 목표를 정하는데 많은 시간이 들진 않았습니다. 사람들이 쓸 수 있는 사이트를 만들고 싶었고 완성도있는 웹 사이트를 만들어보고 싶었습니다. 기관의 3D 프린터실 이용대장은 사용자들이 손으로 직접 써서 이용해 왔습니다. 그러다보니 기관을 사용하는 학생들이 손으로 이용대장을 쓰기 번거롭고 수기로 쓰여지는 이용대장을 보는데 불편함이 있었습니다. 그 문제점을 해결하고자 이번 프로젝트를 진행 하였습니다.

### 시작

 이 글에서는 HTML과 CSS 말고 사이트에 사용된  JavaScript함수와 데이터베이스([firebase](https://firebase.google.com/)) 구글스프레트시트 API 등을 다루고자 합니다. 사이트를 만들기위해 먼저 여러가지 HTML 태그들을 공부했고 CSS는 유튜브나 [w3schools](https://www.w3schools.com/ )  를 참고하여 공부했습니다.

### JavaScript

#### JavaScript - 현재 시간 불러오기

 사용 기록을 남기는 이용대장을 입력하기 위해서 현재시간을 불러와 기록할 필요가 있었습니다. 자바스크립트에서 현재시간을 불러 변수로 저장하는 방법을 알아보겠습니다.

```javascript
var today = new Date(); //현재 시간을 불러옵니다.
console.log(today); //현재 시간을 콘솔창에 표시
```



<img src="사진\자바스크립트_현재시간.png" alt="자바스크립트 안내" style="zoom:100%; float:left;" /> 

 

 

 











 







개발자 모드 콘솔창에 현재 시간이 나타나는 것을 볼 수 있습니다.

```javascript
var month0 = today.getMonth(); //월 불러오기
```



<img src="사진\자바스크립트_월.png" style="zoom:100%; float:left;" /> 

























제가 글을 쓰는 시간은 3월인데 콘솔 창에는 2라고 표시 되네요?

 자바스크립트에서  월을 숫자로 표시하기때문에 0부터 시작합니다.

Jan. --> [0]

Feb. -->[1]

Mar. --> [2]

⁝

변수에는 +1 을 하여 저장하면 되겠죠?

##### 현재 연도 날짜 시간 나타내기

```javascript
var year = today.getFullYear();	// 연도
var month = today.getMonth() + 1; //월
var date = today.getDate();   //일
var hour = today.getHours();   //시
var minute = today.getMinutes(); //분
var second = today.getSeconds(); //초

console.log(year + "/" + month + "/" + date + " - "
            + hour + ":" + minute + ":" + second);
```



<img src="사진\자바스크립트_0붙히기(1).png" style="zoom:150%; float:left;" /> 







이렇게 현재시간을 콘솔창에 띄워 보았는데요. 

 사용자가 이용대장을 작성한 시간을 문서화 하기 위해 2021/3/29  15:27:6 대신에 한자리 수에는 0을 붙혀 나타내고 싶어졌습니다.  ex) 2021/03/29 - 15:27:06

 한자리 수 일때 즉, 0~9 일때는 그 숫자 앞에 "0"을 문자열로 붙혀 변수에 저장해 이용할 것입니다.

```javascript
var second0 = today.getSeconds();

if(second0 < 10){   				//0 ~ 9초 일때 
	var second = "0" + second0;		//0을 붙혀 문자열 저장
}
else{
    var second = second0;			//한자리가 아니면 그냥 저장
}

console.log(second);
```



<img src="사진\자바스크립트_0붙히기(2).png" alt="자바스크립트_0붙히기(2)" style="zoom:100%; float:left;" /> 









한자리 일때 0이 잘 붙어나오는 것을 보실 수 있습니다. 

날짜 시간에도 0을 붙혀주는 코드를 짜주면 보기 더욱 편하겠죠?

#### JavaScript - innerHTML

지금까지 알아본 시간을 콘솔창 말고 HTML 태그안에 집어 넣어 나타내 봅시다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <P id = "timer"></P>
    <script>
        var today = new Date(); //현재 시간을 불러옵니다.
        var year = today.getFullYear();	// 연도
        var month = today.getMonth() + 1; //월
        var date = today.getDate();   //일
        var hour = today.getHours();   //시
        var minute = today.getMinutes(); //분
        var second = today.getSeconds(); //초

        timer.innerHTML = year + "/" + month + "/" + date + " - "
                        + hour + ":" + minute + ":" + second;
    </script>
</body>
</html>
```

```javascript
태그 아이디.innerHTML = 넣고싶은 글자;
```



<img src="사진\자바스크립트_타이머(1).png" alt="자바스크립트_타이머(1)" style="zoom:120%;"/> 

위 코드를 입력해 페이지를 열어보면 페이지를 연 시간이 페이지에 **한번** 나타납니다. 

제가 원하는건 시간이 **타이머**처럼 나타나는 것입니다.



#### JavaScript - setInterval(), setTimeout()

##### setInterval() Method

innerHTML을 1초에 반복적으로 실행할 수 있다면 웹페이지에 실시간으로 시간을 나타낼 수 있을겁니다.

```javascript
setInterval(function(){ alert("Hello");}, 1000);  //1초마다 실행
```



 시간을 웹페이지에 입력해주는 코드를 setInterval()를 이용해 반복적으로 실행시킵니다.

```javascript
setInterval(function(){
    var today = new Date(); //현재 시간을 불러옵니다.
    var year = today.getFullYear();	// 연도
    var month = today.getMonth() + 1; //월
    var date = today.getDate();   //일
    var hour = today.getHours();   //시
    var minute = today.getMinutes(); //분
    var second = today.getSeconds(); //초
    
	timer.innerHTML = year + "/" + month + "/" + date + " - "
                        + hour + ":" + minute + ":" + second;
}, 1000);
```

![자바스크립트_타이머_2_](https://user-images.githubusercontent.com/88194064/131793368-23a07a52-2b08-4330-98ed-4204f8a94cad.gif)

**실시간**으로 시간을 읽어 웹페이지에 나타내주는 것을 볼 수 있습니다.



##### setTimeout() Method

setTimeout()는 정해진 시간이 지나면 한번 실행시켜줍니다.

```javascript
setTimeout(function(){ alert("Hello"); }, 3000);	//3초가 지나면 한번 실행
```

## Firebase

[파이어베이스]: https://firebase.google.com/	"firebase"

**파이어베이스**(Firebase)는 2011년 파이어베이스(Firebase, Inc)사가 개발하고 2014년 [구글](https://ko.wikipedia.org/wiki/구글)에 인수된 [모바일](https://ko.wikipedia.org/wiki/모바일_응용_소프트웨어) 및 [웹 애플리케이션](https://ko.wikipedia.org/wiki/웹_애플리케이션) 개발 플랫폼이다.[[위키백과]](https://ko.wikipedia.org/wiki/%ED%8C%8C%EC%9D%B4%EC%96%B4%EB%B2%A0%EC%9D%B4%EC%8A%A4)

