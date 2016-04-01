
### Masonry Library

크기가 불규칙한 이미지를 뿌려주기 위해 *[메이슨리][Masonry]*라는 라이브러리를 사용하여 테스트를 좀 해봤는데 
크롬에서는 이미지 크기가 겹치는 등, 정상적으로 출력이 되지 않는 경우가 있었고, 특히 IE 10 버전 이후에서는 
아예 노출이 되지 않기도 했는데 호환성보기 설정의 영향을 받기도 하는 듯 했다.

[Masonry]:http://masonry.desandro.com "Masonry Library"

파이어폭스에서 그나마 정상적이었는데 처음 불러온 데이터 이후의 리스트, 즉 두번째 페이지에 해당하는 데이터를
받아서 추가로 뿌려줄 때 총 4열이라면 1열에만 뿌려주는 문제가 있었다. 다시 레이어의 영역을 계산하는데 뭔가
문제가 있지 싶어서 살펴보다가 자바스크립트의 영역이 복잡해서 라이브러리 사이트에서 추가적으로 데이터를
로드할 때 뭔가 지원하는 함수라던지 선언이 있을것 같아 찾아보니 `appended` 라는 함수가 있었고 

```javascript
if (_page == 1){ //첫 페이지일 때만 init
    str += "</div>";
    $items = $(str);

    $(".space_blocks_grid").append($items);
    $('.space_blocks').masonry({
        "itemSelector" : ".space_items",
        "columnWidth" : 232,
        "gutter": 10,
        'isFitWidth' : true
    });
} else { //두번째 페이지 부터 appended
    $items = $(str);
    $(".space_blocks").append($items).masonry('appended', $items);
}
```

테스트를 다시 해봤는데 이번에는 처음 로드한 영역 끝 지점인 곳에서 부터 시작 지점으로 계산하는 듯 
처음 로드한 지점의 레이어가 붕 떠버리는 현상이 생긴다. 마음 같아서는 분석해서 뭔가 그럴싸하게 피드백이라도
날리고 싶었지만 영어도 안되고..

그래서 일종의 편법으로 4열의 블록 영역을 만들어 놓고 차례로 돌아가며 데이터를 뿌려주었던 동료의 예전 
방식을 생각하고 참조해서 만들어보기로 했다.

뭐 대충 아래의 이미지를 뿌려주는 영역이 있다고 가정하고 `brick_layout`라는 클래스를 가진 4개의 영역을 생성.

```html
<style>
.brick_layout {width:232px;float:left;margin-right:5px;}
</style>
<!-- photo grid area -->
<div id="space_blocks_grid" class="space_blocks_grid">
    <div class="brick_layout brick_1"></div>
    <div class="brick_layout brick_2"></div>
    <div class="brick_layout brick_3"></div>
    <div class="brick_layout brick_4"></div>
</div>
<!-- // photo grid area -->

<script>
var brick_num = 1; //전역

function grid(){
    var str = "", i = 0;
    for (; i < jsonObj.length; i++) {
        if (brick_num === 5) { //4열이니까 5열일 때 1열로
            brick_num = 1;
        }
        str = "<div class='space_items'>";  //그려주는 데이터(생략)

        $(".brick_"+brick_num).append(str);
        brick_num++;
    }
}
</script>
```

이런 식인데.. 문제는 종종 높이가 긴~ 데이터가 있다는 점이다. 그럼 해당 열은 저~ 아래로 출력이 되어서
예를 들면 4열 중 3열에 긴~ 이미지가 들어가면 순차적으로 계속해서 이미지를 그려줄 때 3열은 저~ 아래로
붙는 다는 점이다.

그래서 각 4열의 높이를 계산해서 높이가 작은 열에 이미지를 꽂아 넣는 코드를 작성하기 시작.

```javascript
var brick_num = 1;
function grid(){
    if (typeof jsonObj != "undefined" && jsonObj.length > 0){
        var str = "", i = 0;
        for (; i < jsonObj.length; i++) {
            str = "<div class='space_items'>";   //그려주는 데이터(생략)
            totalCnt++;

            $(".brick_"+brick_num).append(str);
            getMinBrick();
        }
    }
}

function custonSort(a, b){
    var temp = $(".brick_layout").eq(a-1).height()
        , dummy = $(".brick_layout").eq(b).height();
    if ( temp === dummy || temp < dummy){
        return a;
    } else {
        return (b+1);
    }
}

function getMinBrick(){
    var i = 0;
    for (; i < 4; i++){
        brick_num = custonSort( brick_num, i );
    }
}
```

뭐 대충 요렇게 작성하긴 했는데 음... 종종 한 쪽 열에 치중되는 경향이 있었다. 아마 예상하기로는 `grid()`
함수에서 반복으로 데이터를 그리는 부분에서 `getMinBrick()` 함수를 실행하고 최저 높이의 열 값을 구하기 
이전에 다음 데이터를 그려주는 현상이 있지 않을까 싶다.

>예상이나 짐작으로 코드를 짜면 안됩니다!  
로그를 찍어봐도 반복문의 로그가 연속으로 찍히는 일이 없기에.. 느낌이 왠지 그렇다는거임.

그래서 `return` 값을 받도록 반복문을 수정했다. 

```javascript
$(".brick_"+brick_num).append(str);
getMinBrick();

//위 코드를 다음과 같이 
$(".brick_"+getMinBrick()).append(str);
```

좀 나아지긴 했는데 그래도 영... 하지만 정해진 시간안에 결과물을 내놓아야 하는 입장이라 먼저 소스는 toss.

