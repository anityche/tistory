
### 알아두면 좋은 자바스크립트 사용

```javascript
/* 
둘 중에 유효한 값이 자동으로 들어감
*/
var target = e.srcElement || e.target;

/*
단 한번만 실행되고 자신을 빈 깡통으로 초기화 시킴 (fake overliding)
*/
function oneRun() {
    .................
    .................
    oneRun = function() {}
}

/*
부하가 큰 사용법 이므로,
*/
var strHTML = "<div id = 'abcd'>";
strHTML += " HTML 텍스트....";
............
strHTML += "</div>";

/*** 다음과 같이 사용하자 ***/

var strHTML = new Array();
strHTML.push("html 텍스트");
..........
return strHTML.join("");	// 인자로 null string을 주었기에 배열의 텍스트가 그냥 이어짐



```

