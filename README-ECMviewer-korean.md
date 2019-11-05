# 쿠쿠닥스 ECM Viewer API 가이드
Last Modify : 2019-03-12 
적용버전 : v11 
<br><br>

## 1. 파일구성

``` JS
+ css
-      viewer_min.css      	// 뷰어 css 파일
+ fonts              	// 뷰어 UI 를 구성하는 아이콘 웹폰트
-      kk-icon.eot
-      kk-icon.svg
-      kk-icon.ttf
-      kk-icon.woff
+ js
-      HTML5MainViewer_min.js 	// js 메인파일
-      require-min.js   	           // require.js 파일
-      worker_min.js                      // worker 파일 (PDF, TIFF 렌더링시 필요)
- index.html          	// 예제 html 파일
- iframe.html          	// 예제 html 파일 (iframe 사용시)
```
<br><br>

## 2. API settings

뷰어를 동작시키는에 필요한 설정을 하는 API 이다.
``` JS
define('Settings', function() {

     "wrap" : "html5viewer",  // 뷰어를 표현하는 DIV의 ID
     "limit" : {
	"maxAnno" : 66,  	  // 최대 주석 개수 ( /element )
	"maxMasking" :66,	  // 최대 블랙마킹 개수 ( /element )
	"maxBoxW" : 1000,           // 최대 도형 가로 사이즈 
	"maxBoxH" : 500,              // 최대 도형 세로 사이즈
	"minBoxW" : 50,                // 최소 도형 가로 사이즈
	"minBoxH" : 50,                 // 최소 도형 세로 사이즈
                "maxMemoW" : 1000,     // 최대 메모 가로 사이즈
                "maxMemoH" : 500,        // 최대 메모 세로 사이즈
                "minMemoW" : 300,        // 최소 메모 가로 사이즈
                "minMemoH" : 50,           // 최소 메모 세로 사이즈
                "maxMaskingW" : 1000, // 최대 블랙마킹 가로 사이즈
                "maxMaskingH" : 500,    // 최대 블랙마킹 세로 사이즈
                "minMaskingW" : 50,      // // 최소 블랙마킹 가로 사이즈
                "minMaskingH" : 50        // 최소 블랙마킹 세로 사이즈
       },
       "thumbnail" : {
 	"display" : true,     // 썸네일뷰를 보여줄지 설정 ( true | false )
                "title" : "hidden",   // 썸네일 타이틀 노출여부 (hidden | title | page)
                "direction" : "hidden",  // 썸네일 설명 노출여부 (hidden | title | page)
                "width" : 100         // // 썸네일 이미지의 가로 사이즈(px)
       },
       "toolbar" : {
	"display" : true,     // // 툴바를 보여줄지 설정 ( true | false )
"print" : "show",  	  // 프린트 버튼 설정 (show | hidden)		
                "thumbView" : "show", // 썸네일 토글 버튼 설정 (show | hidden)
"thumbList" : "show", // 썸네일 리스트 토글 버튼 설정 (show | hidden)
	"pageNav" : "show",	  // page 이동버튼 설정 (show | hidden)
 	"zoom" : "show",   	  // 확대/축소 버튼 설정 (show | hidden)
 	"fit" : "show",    	  // 가로세로맞춤버튼 설정 (show | hidden)
 	"rotate" : "show"  	  // 회전 버튼 설정 (show | hidden)
	"save" : "show",      // 저장 버튼 설정 (show | hidden)
"transfer" : "show",  // 외주전송 버튼 설정 (show | hidden)
	"annotation" : "show",// 주석 버튼 설정 (show | hidden)
	"imgMasking" : "show" // 마스킹 버튼 설정 (show | hidden)
     }, 
     "annotation" : {         // 주석 기본색 폰트를 설정합니다.
 	"fontFamily" : "Noto Sans",
 	"fontSize" : "30",
 	"fontColor" : "#000000" ,
 	"bgColor" : "#ff0000",
 	"lineColor" : "0000ff"
    }, 
         "loading" : {
   	"tooltip" : "on",
   	"indexKey" : "12345678",
  	"userinfo" : "123456|Michael|123412341234",
 	"wartermark" : "TEXTTEXT",
	"defaultZoom" : "fitAll",   // fitWidth : fitHeight : fitAll
	"dblclickZoom" : "fitWidth",
   	"annotationURL" : "….주석 블러오는 서블릿 주소 … ",,
        /* annotationURL : 주석을 불러오는 서블릿 주소 elementID 하나당
        하나씩 처리하며 GET 방식으로 element_id 을 보내면
        parameta :  element_id (GET방식)*/
"annotationPram" : {  //annotationURL 로 파라메터를 던진다. (GET방식)
Key1 : “key1”,
     Key2 : “key2”
},
 	"imageType" : "image",
 	"loadingType" : "image",
	"basePath" : "../js/build/lib",
 	"files" : [{
"element_id" : "jpeg_01",
"indexKey" : "1",
"title" : "jpeg_01",
"Filename" : "jpeg_01.jpg",
"ext" : "jpg",
"url" : "./data/jpeg_01.jpg",
"anno" : "./data/jpeg_01.json"
     	        },
....
]
       },
      "actioncallback" : { 
	"applyCallback" : true
      },
      "save" : {
 	"saveURL": "주석저장 서블릿 URL",
 	"saveParam":{
       	      "key1":"value1",
       	      "key2":"value2"
                },
	"imgSaveURL": "이미지저장 서블릿 URL",
 	"imgSavePram":{
       	     "key1":"value1",
       	     "key2":"value2"
 	},
 	"transferURL" : "이미지전송 서블릿 URL",
/*
transferURL: 이미지를 외부 인증기관으로 전송할 때 서블릿의 URL을 설정한다.
이부분은 저장 과 유사한 동작방식을 갖는다.
*/
 	"transferPram":{
                     "key1":"value1",
                     "key2":"value2"
 	}
   },
   "extension" : {
      "textboxURL" : "텍스트상자 관리 서블릿 URL",
      "textboxParam":{
         "key1":"value1",
         "key2":"value2"
      }
   }
});
```
<br><br>

## 3. Action API

Iframe 밖에서 HTML5뷰어에 각종 Action을 호출한다. 이를 호출하는 방식을 Post Meassage 방식이다. 기본적으로 Post Meassage 를 호출하는 방식을 다음과 같다.
``` JS
var obj = document.getElementById("html5viewer");
var objDoc = obj.contentWindow || obj.contentDocument;
objDoc.postMessage(action,"*");
```
HTML5 뷰어 API에서는 action 대신 들어갈 값을 제공한다. HTML5 뷰어 action API은 다음과 같다.
<br>

### a. 버튼 Action

**Annotation 섹션**

Action 명칭| 내용
---|---
Save | 주석저장
SaveImg | 마스킹 저장
Transfer | 외부 이미지전송
Download | 선택한 이미지 다운로드
Print | 프린트
PrintAPI | 프린트API <br> 파라메터 <br> mode : 프린트 모드  ( image : 이미지 , all : 주석+이미지 ) <br> label : 프린트 라벨  <br> val : 프린트 범위 <br> (one : 현재페이지,  start : 처음부터 현재까지 , end : 현재부터 마지막까지,  part : 부분인쇄) <br> printsubmode : 부분지정값  (val: part 일때 적용)
imgMasking | 마스킹 추가
insertMemo | 메모추가
insertShape | 도형추가
insertLine | 선 추가
insertStamp | 스탬프 추가 
inserLink | 링크 추가 
insertYpan| 형광팬
textBoxList | 텍스트박스 리스트 호출
upBrightness | 선택된 이미지 밝게
downBrightness | 선택된 이미지 어둡게
contextMenuOn | Contextmenu 활성화
contextMenuOff | Contextmenu 비활성화

<br>

**Viewer 섹션**

Action 명칭 | 내용
--- | ---
fitWidth | 폭맞춤 
fitHeight | 높이맞춤
fitAll | 화면맞춤
fitSelected | 선택한영역 맞춤 
zoomin | 확대
zoomout | 축소
zoomdefault | zoom 을 100% 로 돌려놓음
zoomto | 특정 사이즈로 지정하여 확대(축소) 
Loupe | 돋보기툴
rotateRight | 오른쪽으로 90도 회전
rotateRight180 | 오른쪽으로 180도 회전
rotateRightAll | 오른쪽으로 90도 회전 모든 이미지
rotateRightAll180 | 오른쪽으로 180도 회전 모든 이미지  
rotateLeft | 왼쪽으로 90도 회전
nextPage | 다음 페이지
endPage | 마지막 페이지
prevPage | 이전 페이지
startPage | 첫 페이지 
thumbView | 썸네일보기 토글
thumbList | 썸네일전체보기 토글
closeToolbar | 툴바 와 텝바를 히든/쇼 (토글) 합니다.
dragscroll | 드래그 기능 활성화
selectAll | 썸네일 전체선택

<br>

**Image & Sketch**

Action 명칭 | 내용
--- | ---
imgCrop | 선택 이미지 팝업 돋보기
imgCropDownload | 선택 이미지 다운로드 
sketchAction | Sketch 추가

<br>

**Toggle Action**

Action 명칭 | 내용
--- | ---
toggleShape | 주석  보기 / 안보이기
<br>

### b. Combo box API

Action 명칭 | 내용
--- | ---
toolbar:{id:"insertShape",val:"`rect`"} | **도형 추가** <br><br> **사각형** <br> "textbox", "rect", "roundRect", "snip1Rect", "snip2SameRect", "snip2DiagRect", "snipRoundRect", "round1Rect", "round2SameRect", "round2DiagRect",”alpharect”,”alphaellipse” <br><br>**기본도형**<br> "ellipse", "triangle", "rtTriangle", "parallelogram", "trapezoid", "diamond", "pentagon", "hexagon", "heptagon", "octagon", "decagon", "dodecagon", "corner", "diagStripe", "plus", "plaque" <br><br> **블록 화살표** <br> "rightArrow", "leftArrow", "downArrow", "upArrow", "leftRightArrow", "upDownArrow", "quadArrow", "bentArrow", "uturnArrow", "bentUpArrow", "curvedRightArrow", "curvedLeftArrow", "curvedUpArrow", "curvedDownArrow", "notchedRightArrow", "homePlate", "chevron"
toolbar:{id:"insertStamp",val:"`check`"} | **스탬프 추가**<br><br> **스탬프** <br> "check" , "disagree"
toolbar:{id:"insertYpan",val:"`mk_ypan_1`"} | **텍스트 강조** <br><br> **형광펜** <br> "mk_ypan_1", "mk_ypan_2", "mk_ypan_3", "mk_ypan_4", "mk_ypan_5"
toolbar:{id:"insertLine",val:"`line`"} | **선 추가**<br><br> **선** <br> "line", "straightconnector1-1", "straightconnector1-2"
toolbar:{id:"insertLink",val:"`memo`"} | **첨부 링크 추가** <br><br> **첨부** <br> " "
<br>

## 4. 외부함수 API

#### a. 함수 명칭: replaceElement

뷰어의 이미지를 변경하여 로딩합니다. 해당부분은 loadingAPI와 형식이 동일합니다.

``` JS
{"replaceElement" : {
	"thumbnail" : {
		"display" : true,
		"canvas" : false,
		"width" : 100
	},
	"annotation" : {
		"fontFamily" : "Noto Sans",
		"fontSize" : "30",
		"bgColor" : "rgb(91, 155, 213)"
	},
	
	"loading" : {
		"type" : "image",
		"tooltip" : "on",
		"actionCallback" : "off",
		"setKey" : "12345678",          
		"userinfo" : "123456|yuho|ray@kukudocs.com",
		"wartermark" : "123456789",
		
		"annotationURL":"./service/anno.php",

		"imageType" : "image",
		"loadingType" : "image",
		"basePath" : "../js/build/lib",
		"files" : [
			{"element_id":"jpeg_01", "indexKey":"1", "title":"jpeg_01", "filename":"jpeg_01.jpg", "ext":"jpg","url":"./data/jpeg_01.jpg"},
                                     ….
		]
	},
	"save" : {
		"saveURL":"/service/save.php",
		"saveParam":{
			"key1":"@value1",
			"key2":"@value2"
		},
		"imgSaveURL":"/service/imgSave.php",
		"imgSavePram":{
			"key1":"@value1",
			"key2":"@value2"
		}
	}
}}
```
<br>

#### b. 함수 명칭: resetElement

이미지가 없는 뷰어 상태로 만듦.
``` JS
{"resetElement":"true"}
```
<br>

#### c. 함수 명칭: addElement

이미지를 추가합니다.
``` JS
{"addElement":{"element_id":"jpeg_01","indexKey" : "1", "title":"jpeg_01", "filename":"jpeg_01.jpg", "ext" : "jpg", "url" : "./data/jpeg_01.jpg", "anno" : "./data/jpeg_01.json"}}
```
<br>

#### d. 함수 명칭: removeElement

이미지를 삭제합니다.
``` JS
{"removeElement":{"element_id":"jpeg_05"}}
```
<br>
####e. 함수 명칭: getViewerMeta
뷰어의 상태 메타정보를 호출합니다. 
``` JS
"getViewerMeta"

It returns getViewerMeta through Callback API
{
     "thumbView": true,
     "zoom":1,
     "element":1234,
     "rotate":0,
     "page":1,
     "imgupdate":true,
     "isedit":true
}
```
<br>

#### f. 함수 명칭: getElementMeta

선택된 element의 메타정보를 호출합니다. 
``` JS
"getElementMeta"


It returns getElementMeta through Callback API 
{
     "elementId": 1234,
     "title":”texttext”,
     "imgupdate":true,
     "isedit":true
}
```
<br>

#### g. 함수 명칭: goPage

해당 element로 이동합니다.
``` JS
{"goPage":1}
```
<br>

#### h. 함수 명칭: getElementList

뷰어에 로딩된  element들을 List로 반환합니다. 
``` JS
"getElementList"

It returns getElementList through Callback API 

 [“element1”,“element4”,“element4”,“element4”,“element5” ...]
``` 
<br>

#### i. 함수 명칭: updateElementSequence

뷰어에 로딩된 element들의 순서를 변경합니다.
``` JS
{"updateElementSequence":[“element1”,“element4”,“element4”,“element4”,“element5” ...] }
```
<br>

#### j. 함수 명칭: saveAnnoElementOne

주석 페이지 단위로 저장합니다.
``` JS
{"saveAnnoElementOne":{
    "Element_id":"jpeg_05",
    "Key1":"value1",
    "Key2":"value2"
}}
```
<br>

#### k. 함수 명칭: saveImgElementOne

마스킹 페이지 단위로 저장합니다.
``` JS
{"saveImgElementOne":{"element_id":"jpeg_05"}}
```
<br>

#### l. 함수 명칭: getSaveAnnoElementOne

해당 element의 주석들을 postmessage로 받아옵니다.
``` JS
{"getSaveAnnoElementOne":{"element_id":"jpeg_05"}}


retuen 은 콜백 API getSaveAnnoElementOne 으로 리턴된다.  
```
<br><br>

## 5. 콜백함수 API

HTML5뷰어에서 iframe 밖으로 메시지를 전달한다. 이를 호출하는 방식을 Post Meassage 방식이다.
기본적으로 Post Meassage 를 호출하는 방식을 다음과 같다.
``` JS
$(window).on("message", function(e) {
     var data = e.originalEvent.data;
     if(typeof(data.saveAnnoCallback) != "undefined"){
         console.log(data.saveAnnoCallback);
     }
     if(typeof(data.getViewerMeta) != "undefined"){
		console.log(data.getViewerMeta);
     }
     ...
});
``` 
<br>

#### a. 함수 명칭: saveAnnoCallback

뷰어의 이미지를 변경하여 로딩합니다. 해당부분은 loadingAPI와 형식이 동일합니다.
``` JS
saveAnnoCallback

{
     "elementid":”1234”,
     "documentid":”1234”,
     "page":{
          "number":"1",
     },
     "scale":"1",
     "calibrationunit":"px",
     "annotations":annotationData
     }
						};

```
<br>

#### b. 함수 명칭: getViewerMeta

뷰어의 상태 메타정보를 호출합니다. 
``` JS
"getViewerMeta"

It returns getViewerMeta through Callback API 

{
     "thumbView": true,
     "zoom":1,
     "element":1234,
     "rotate":0,
     "page":1,
     "imgupdate":true,
     "isedit":true
}
```
<br>

#### c. 함수 명칭: getElementMeta

선택된 element의 메타정보를 호출합니다. 
``` JS
"getElementMeta"


It returns getElementMeta through Callback API 

{
     "elementId": 1234,
     "title":”texttext”,
     "imgupdate":true,
     "isedit":true
}
```
<br>

#### d. 함수 명칭: getElementList

뷰어에 로딩된  element들을 List로 반환 합니다. 
``` JS
"getElementList"

It returns getElementList through Callback API

 [“element1”,“element4”,“element4”,“element4”,“element5” ...]
```
<br>

#### e. 함수 명칭: applyCallback

주석 선택 후 적용 버튼을 누르면 이벤트를 반환합니다. 
``` JS
```
<br>

#### f. 함수 명칭: deleteCallback

주석 선택 후 삭제 버튼을 누르면 이벤트를 반환합니다. 
``` JS
```
<br>

#### g. 함수 명칭: getElementIndex

``` JS
retuen 은 콜백 API getElementIndex 으로 리턴된다.  

{"element_id":”jpeg_05”, "index":2 }
```
<br>

#### h. 함수 명칭: getMultiselectsIndex

``` JS
retuen 은 콜백 API getMultiselectsIndex 으로 리턴된다.   

{"element_id":”jpeg_05”, "index":2 }
```
<br><br>

## 6. 주석 DATA

``` JS
{
   "elementid": "jpeg_05",
   "documentid": "jpeg_05",
   "page": {
       "number": "1",
       "rotate": "0"                        //  회전  : 0, 90, 180, 270 
   },
   "scale": "1",
   "calibrationunit": "px",
   "annotations": [
       {
           "objectType": "yp",                           //  형광펜 (하이라이트) 
           "prstgeom": "mk_ypan_4",                //  형광펜 종류             
           "x": 115,
           "y": 431,
           "l": 115,
           "t": 431,
           "w": 1377,
           "h": 118,
           "degree": 0,
           "information": {
               "user": "userid",
               "adddate": "201805180300",
               "modifydate": "201805180300"
           }
       },
       {
           "objectType": "mm",                           //  메모 
           "prstgeom": "memo",
           "x": 98,
                      "y": 733,
           "l": 98,
           "t": 733,
           "w": 343,
           "h": 334,
           "degree": 0,
           "content": {
               "style": {
                   "font-family": "Verdana",
                   "font-size": "33.8px",
                   "font-weight": "Normal",
                   "font-style": "Normal",
                   "text-decoration": "0",
                   "color": "#FF0000"
               },
               "text": "\uba54\ubaa8\ud14c\uc2a4\ud2b8"   //  UTF-8 인코딩 
           },
           "information": {
               "user": "userid",
               "adddate": "201805180300",
               "modifydate": "201805180300"
           }
       },
       {
           "objectType": "st",                             //  스템프
           "prstgeom": "stamp",              //  스템프
           "stemp": "note",                 //  스템프 기능 노트
           "x": 532,
           "y": 783,
           "l": 532,
           "t": 783,
           "w": 80,
           "h": 100,
           "degree": 0,
           "content": {
               "text": "\uc811\ucc29\uba54\ubaa8",
               “Path”: “”,
               “Base64”: “”,
           },
           "fillColor": "#00FF00",
           "information": {
               "user": "userid",
               "adddate": "201805180300",
               "modifydate": "201805180300"
           }
       },
       {
           "objectType": "sp",                             //  도형
           "prstgeom": "rect",                             //  사각형
           "x": 874,
           "y": 739,
           "l": 874,
           "t": 739,
           "w": 766,
           "h": 511,
           "degree": 0,
           "fillColor": "#FFFFFF",
           "fillOpacity": 0,
           "strokeColor": "#FF0000",
           "strokeOpacity": "1",
           "strokeWidth": "4",
           "strokeType": "solid",
           "content": {
               "style": {
                   "font-family": "Verdana",
                   "font-size": "93.6px",
                   "font-weight": "Normal",
                   "font-style": "Normal",
                   "text-decoration": "0",
                   "color": "#FF0000"
               },
               "text": "\ud14d\uc2a4\ud2b8\ud14c\uc2a4\ud2b8"
           },
           "information": {
               "user": "userid",
               "adddate": "201805180300",
               "modifydate": "201805180300"
           }
       },
       {
           "objectType": "sp",                             //  도형
           "prstgeom": "ellipse",                       //  타원
           "x": 833,
           "y": 2092,
           "l": 833,
           "t": 2092,
           "w": 390,
           "h": 195,
           "degree": 0,
           "fillColor": "#FFFFFF",
           "fillOpacity": 0,
           "strokeColor": "#FF0000",
           "strokeOpacity": "1",
           "strokeWidth": "1",
           "strokeType": "solid",
           "content": {
               "style": {
                   "font-family": "Arial",
                   "font-size": "13px",
                   "font-weight": "Normal",
                   "font-style": "Normal",
                   "text-decoration": "0"
               }
           },
           "information": {
               "user": "userid",
               "adddate": "201805180300",
               "modifydate": "201805180300"
           }
       },
       {
           "objectType": "ln",                             //  선
           "prstgeom": "line",                             //  선종류 : line
           "w": 612,
           "h": 15,
           "psl": 848,
           "pst": 1043,
           "pel": 1460,
           "pet": 1058,
           "x": 848,
           "y": 1043,
           "l": 848,
           "t": 1043,
           "xlx": 1,
           "strokeColor": "#FF0000",
           "strokeOpacity": "1",
           "strokeWidth": "1",
           "strokeType": "solid",
           "information": {
               "user": "userid",
               "adddate": "201805180300",
               "modifydate": "201805180300"
           }
       },
       {
           "objectType": "ln",                             //  선
           "prstgeom": "line",                             //  선종류 : line
           "w": 612,
           "h": 15,
           "psl": 848,
           "pst": 1043,
           "pel": 1460,
           "pet": 1058,
           "x": 848,
           "y": 1043,
           "l": 848,
           "t": 1043,
           "xlx": 1,
           "strokeColor": "#FF0000",
           "strokeOpacity": "1",
           "strokeWidth": "1",
           "strokeType": "solid",
           "information": {
               "user": "userid",
               "adddate": "201805180300",
               "modifydate": "201805180300"
           }
       },
      {
           "objectType": "lk",
           "prstgeom": "memo",
           "l": 532,
           "t": 783,
           "x": 532,
           "y": 783,
           "w": 100,
           "h": 100,
           "content": {
               "subject": "undefined",
               "path": "undefined",
               "text": "접착메모"
           },
           "information": {
               "user": "userid",
               "adddate": "201805180300",
               "modifydate": "201805180300"
           }
       }
    ]
}
```
<br><br>

## 7. 주석 Converter

리드툴즈의 XML 주석 DATA를 쿠쿠닥스의 JSON 주석DATA로 변환하는 모듈입니다.

**command line 사용방식**

``` JS
  # [php folder path]/php  /Absolit path/convert.php  [input file]  [output file]
```