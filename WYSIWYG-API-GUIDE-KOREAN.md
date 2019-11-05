# API 정리 문서 (v1.4.38)

2019.01.04

<br><br>

# 문서 정보

### 문서 개요

이 문서는 “KukudocsEditor”에서 사용되는 API 정보를 담고 있습니다.  

<br><br>

### 독자

이 문서의 독자는 “KukudocsEditor”를 이용하여 웹 사이트를 운영하고, 웹 에디터를 관리하는 사 용자입니다.

<br><br>

### 문의처

이 문서의 내용에 오류가 있거나 내용과 관련된 의문사항이 있으면 담당자에게 문의하십시오.

<br><br>

### 문서 버전 및 이력

버전|일자|이력사항
:-:|:-:|---
1.0|2017. 07. 19|Version 1.0 문서배포
1.0|2017. 07. 26|API 항목 추가 및 수정
1.1|2017. 08. 12|메뉴얼 상세 내용 추가
1.2|2017. 09. 01|이력 변경 없음
1.3|2017. 09. 15|동영상 삽입 이미지, emoticonList 관련 API 내용 추가
1.4|2017. 09. 29|인용구문, templateList 관련 API 설정 내용 추가
1.4.1|2017. 11. 15|IE 안정성 개선 및 API 문서 정리
1.4.4|2018. 01. 15|오탈자 수정 및 문서 정리
1.4.5|2018. 01. 22|문서 버전 정리
1.4.6|2018. 01. 30|1.4.6 버전 정리
1.4.7|2018. 02. 02|오탈자 수정 및 SetAttributeValueByBody 위치 이동(57->53)
1.4.8|2018. 02. 06|1.4.8 버전 정리
1.4.8|2018. 02. 06|getImageUploadURL / setImageUploadURL 누락 정정
1.4.9|2018. 02. 19|1.4.9 버전 정리
1.4.10|2018. 03. 09|1.4.10 버전정리 및 getPublicPathURL, setPublicPathURL 추가
1.4.11|2018. 03. 19|1.4.11 버전 정리
1.4.12|2018. 03. 23|1.4.12 버전 정리 및 GetEditorContent Parameter 추가
1.4.13|2018. 03. 29|1.4.13 버전 정리 및 <br> getKeyEvent, setKeyEvent, getMouseEvent, setMouseEvent API 수정
1.4.14|2018. 04. 12|1.4.14 버전 정리
1.4.15|2018. 04. 20|1.4.15 버전 정리
1.4.16|2018. 04. 25|1.4.16 버전 정리
1.4.17|2018. 04. 25|1.4.17 버전 정리
1.4.18|2018. 05. 04|1.4.18 버전 정리
1.4.19|2018. 05. 10|1.4.19 버전 정리
1.4.20|2018. 05. 12|1.4.20 버전 정리 및 GetEditorContent API Parameter 수정
1.4.21|2018. 05. 17|1.4.21 버전 정리
1.4.22|2018. 06. 25|1.4.22 버전 정리
1.4.23|2018. 07. 04|1.4.23 버전 정리
1.4.24|2018. 07. 24|1.4.24 버전 정리 및 제거 API 수정 (getElementParentCells) / 오탈자 수정
1.4.25|2018. 08. 22|1.4.25 버전 정리
1.4.26|2018. 09. 12|1.4.26 버전 정리
1.4.27|2018. 09. 28|1.4.27 버전 정리
1.4.28|2018. 10. 11|1.4.28 버전 정리
1.4.29|2018. 10. 26|1.4.29 버전 정리 및 InsertTextByFocus, InsertHTMLByFocus, executeCommand API 추가 적용
1.4.30|2018. 11. 09|1.4.30 버전 정리
1.4.31|2018. 11. 13|1.4.31 버전 정리
1.4.32|2018. 11. 30|1.4.32 버전 정리
1.4.33|2018 .12. 10|1.4.33 버전 정리
1.4.34|2018. 12. 18|1.4.34 버전 정리
1.4.35|2018. 12. 20|1.4.35 버전 정리
1.4.36|2018. 12. 21|1.4.36 버전 정리
1.4.37|2018. 12. 27|1.4.37 버전 정리
1.4.38|2019. 01. 04|1.4.38 버전 정리

<br><br>

# 1. API (Application Programming Interface)
이 장에서는 KukudocsEditor의 API를 설명합니다.

<br><br>

## 1.1 getRootElement()

getRootElement()|
---|
editor의 전체 DOM을 get 한다. <br> (※ editor란 toolbar, Content, Footer를 포함한 영역을 의미한다.)|
**Syntax**|
Editor_Instance.getRootElement();|
**Return**|
Type: Element <br> 전체 Editor영역의 DOM을 반환|

<br><br>

## 1.2 getToolbarElement()

getToolbarElement ()|
---|
Toolbar영역의 DOM을 get 한다. <br> (※ Toolbar란 Content 영역을 편집할 때 사용하는 기능들의 UI를 의미한다.)|
**Syntax**|
Editor_Instance. getToolbarElement();|
**Return**|
Type: Element <br> Toolbar영역의 DOM을 반환|

<br><br>

## 1.3 getContentViewElement()

getContentViewElement()|
---|
Content 영역의 DOM을 get 한다. <br> (※ Content란 Editor를 편집하는 영역을 의미한다.)|
**Syntax**|
Editor_Instance.getContentViewElement();|
**Return**|
Type: Element <br> Content 영역의 DOM을 반환|

<br><br>

## 1.4 getFooterElement()

getFooterElement()|
---|
Footer 영역의 DOM을 get 한다. <br> (※ Footer란 Editor, HTML, TEXT, Preview의 Mode를 선택하는 영역을 의미한다.)|
**Syntax**|
Editor_Instance.getFooterElement();|
**Return**|
Type: Element <br> Footer 영역의 DOM을 반환|

<br><br>

## 1.5 getEditorWidth()

getEditorWidth()|
---|
editor의 전체 Width Size를 get 한다. <br> (※ editor란 toolbar, Content, Footer를 포함한 영역을 의미한다.)|
**Syntax**|
Editor_Instance.getEditorWidth();|
**Return**|
Type: Int (Number) <br> Editor영역의 전체 Width를 반환|

<br><br>

## 1.6 getEditorHeight()

getEditorHeight()|
---|
editor의 전체 Height Size를 get 한다. <br> (※ editor란 toolbar, Content, Footer를 포함한 영역을 의미한다.)|
**Syntax**|
Editor_Instance.getEditorHeight();|
**Return**|
Type: Int (Number) <br> Editor영역의 전체 Height를 반환|

<br><br>

## 1.7 getEditorContentWidth()

getEditorContentWidth()|
---|
Content 영역의 Width Size를 get 한다. <br> (※ Content란 Editor를 편집하는 영역을 의미한다.)|
**Syntax**|
Editor_Instance.getEditorContentWidth();|
**Return**|
Type: Int (Number) <br> Content 영역의 Width를 반환|

<br><br>

## 1.8 getEditorContentHeight()

getEditorContentHeight()|
---|
Content 영역의 Height Size를 get 한다. <br> (※ Content란 Editor를 편집하는 영역을 의미한다.)|
**Syntax**|
Editor_Instance.getEditorContentHeight();|
**Return**|
Type: Int (Number) <br> Content 영역의 Height를 반환|

<br><br>

## 1.9 getOptions()

getOptions()|
---|
Editor에 설정된 Options의 객체 정보를 get 한다. <br> (※ Options이란 Editor를 생성할 때 설정한 정보들을 의미한다.)|
**Syntax**|
Editor_Instance.getOptions();|
**Return**|
Type: Object <br> Editor의 Option 정보를 가지는 객체 반환|

<br><br>

## 1.10. getHelpURL()

getHelpURL()|
---|
Editor에 설정된 도움말 웹사이트의 정보를 get한다. <br> (※ 도움말 웹사이트이란 사용자에게 기능적 설명을 제공하는 웹사이트를 의미한다.)|
**Syntax**|
Editor_Instance.getHelpURL();|
**Return**|
Type: String <br> Editor의 도움말 URL의 정보를 반환|

<br><br>

## 1.11 setHelpURL(helpURL)

setHelpURL(helpURL)|
---|
Editor에 설정된 도움말 웹사이트의 정보를 set한다. <br> (※ 도움말 웹사이트이란 사용자에게 기능적 설명을 제공하는 웹사이트를 의미한다.)|
**Syntax**|
Editor_Instance.setHelpURL(“http://www.kukudocs.com/help”);|
**Parameter**|
helpURL <br> - Type : String <br> - description : 도움말을 표시할 웹사이트 주소를 설정 한다.|
**Return**|
-|

<br><br>

## 1.12 getLoadingImageURL()

getLoadingImageURL()|
---|
Image Upload시 사용하는 Loading 이미지 정보를 get한다.|
**Syntax**|
Editor_Instance.getLoadingImageURL();|
**Return**|
Type: String <br> Editor의 Loading Image URL 정보를 반환|

<br><br>

## 1.13 setLoadingImageURL(loadingImageURL)

setLoadingImageURL(loadingImageURL)|
---|
Image Upload시 사용하는 Loading 이미지 정보를 set한다.|
**Syntax**|
Editor_Instance.setLoadingImageURL(“./images/loading.gif”);|
**Parameter**|
helpURL <br> - Type : String <br> - description : Loading Image로 사용할 이미지의 주소를 설정 한다.|
**Return**|
-|

<br><br>

## 1.14 getErrorImageURL()

getErrorImageURL()|
---|
Image Upload시 발생하는 Error에 사용하는 Error 이미지 정보를 get한다.|
**Syntax**|
Editor_Instance.getErrorImageURL();|
**Return**|
Type: String <br> Editor의 Error Image URL 정보를 반환|

<br><br>

## 1.15 setErrorImageURL(errorImageURL)

setErrorImageURL(errorImageURL)|
---|
Image Upload시 발생하는 Error에 사용하는 Error 이미지 정보를 set한다.|
**Syntax**|
Editor_Instance.setErrorImageURL(“./images/error.png”);|
**Parameter**|
errorImageURL <br> - Type : String <br> - description : Error Image로 사용할 이미지의 주소를 설정 한다.|
**Return**|
-|

<br><br>

## 1.6 getPlayImageURL()

getPlayImageURL()|
---|
동영상 Upload시 편집화면에서 사용할 동영상 표현 이미지의 URL 정보를 get한다.|
**Syntax**|
Editor_Instance.getPlayImageURL();|
**Return**|
Type: String <br> 동영상 임을 표현하는 Image URL 정보를 반환|

<br><br>

## 1.7 setPlayImageURL(playImageURL)

setPlayImageURL(playImageURL)|
---|
동영상 Upload시 편집화면에서 사용할 동영상 표현 이미지의 URL 정보를 set한다.|
**Syntax**|
Editor_Instance.setPlayImageURL(“./images/play.png”);|
**Parameter**|
playImageURL <br> - Type : String <br> - description : 동영상 표시 Image로 사용할 이미지의 주소를 설정 한다.|
**Return**|
-|

<br><br>

## 1.18 getEmoticonList()

getEmoticonList()|
---|
이모티콘으로 사용하는 이미지의 URL List 정보를 get한다.|
**Syntax**|
Editor_Instance.getEmoticonList();|
**Return**|
Type: String <br> 이모티콘으로 사용하는 Image URL List 정보를 반환|

<br><br>

## 1.19 setEmoticonList(emoticonList)

setEmoticonList(emoticonList)|
---|
이모티콘으로 사용하는 이미지의 URL List 정보를 set한다.|
**Syntax**|
Editor_Instance.setEmoticonList( [ “./emoticon1.png”, “./emoticon1.png” ] );|
**Parameter**|
emoticionList <br> - Type : Array[String] <br> - description : 이모티콘으로 사용할 Image들을 설정 한다.|
**retern**|
-|

<br><br>

## 1.20 getTemplateList()

getTemplateList()|
---|
Template으로 사용하는 Template List(Object) 정보를 get한다.|
**Syntax**|
Editor_Instance.getTemplateList();|
**Return**|
Type: Array[Objecy] <br> Template로 사용하는 Template List(Object List) 정보를 반환|

<br><br>

## 1.21 setTemplateList(templateList)

setTemplateList(templateList)|
---|
template으로 사용하는 Template List(Object Array) 정보를 set한다.|
**Syntax**| 
Editor_Instance.setTemplateList( [{ <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; name : '부서양식', <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; items : [ {<br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; name : '회의록', <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; type : 'url', <br>  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; value : '/template/meeting_log.html' <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }] <br> }] );|
**Parameter**|
templateList <br> - Type : Array[Object] <br>  - description : Template로 사용할 내용들에 대해서 Template List 정보를 설정 한다.|
**Return**|
-|

<br><br>

## 1.22 getUseFooterMenu()

getUseFooterMenu()|
---|
Editor에 설정된 Footer Menu의 사용 유무를 get한다.|
**Syntax**|
Editor_Instance.getUseFooterMenu();|
**Return**|
-|

<br><br>

## 1.23 setUseFooterMenu(useFooterMenu)

setUseFooterMenu(useFooterMenu)|
---|
Editor에 설정된 Footer Menu의 사용 유무를 set한다. <br> (※ 사용(true)를 Parameter로 전달시 Footer Menu가 나타나고, 미사용(false)를 전달시에는 Footer Menu가 사라진다.)|
**Syntax**|
Editor_Instance.setUseFooterMenu(true);|
**Parameter**|
useFooterMenu <br> - Type : Boolean <br> - description : Footer Menu의 사용 유무를 설정 한다.|
**Return**|
-|

<br><br>

## 1.24 getFileUploadURL()

getFileUploadURL()|
---|
Editor에 설정된 File Upload URL정보를 get한다. <br> (※ File Upload URL이란 사용자가 파일을 업로드할 위치의 URL 정보로 업로드하는 파일을 받아들이는 서버의 처리 주소를 의미한다. / Image, Video업로드 주소가 없을 때 기본값으로 사용되어 진다.)|
**Syntax**|
Editor_Instance.getFileUploadURL();|
**Return**|
Type: String <br> File Upload URL의 정보를 반환|

<br><br>

## 1.25 setFileUploadURL(fileUploadURL)

setFileUploadURL(fileUploadURL)|
---|
Editor에 설정된 File Upload URL정보를 set한다. <br> (※ File Upload URL이란 사용자가 파일을 업로드할 위치의 URL 정보로 업로드하는 파일을 받아들이는 서버의 처리 주소를 의미한다. / Image, Video업로드 주소가 없을 때 기본값으로 사용되어 진다.)|
**Syntax**|
Editor_Instance.setFileUploadURL(“http://www.kukudocs.com/upload”);|
**Parameter**|
fileUploadURL <br> - Type : String <br> - description : File Upload를 처리할 서버의 주소를 설정 한다.|
**Return**|
-|

<br><br>

## 1.26 getImageUploadURL()

getImageUploadURL()|
---|
Editor에 설정된 Image Upload URL정보를 get한다. <br> (※ Image Upload URL이란 사용자가 Image를 업로드할 위치의 URL 정보로 업로드하는 Image를 받아들이는 서버의 처리 주소를 의미한다.)|
**Syntax**|
Editor_Instance.getImageUploadURL();|
**Return**|
Type: String <br> Image Upload URL의 정보를 반환|

<br><br>

## 1.27 setImageUploadURL(imageUploadURL)

setImageUploadURL(imageUploadURL)|
---|
Editor에 설정된 File Upload URL정보를 set한다. <br> (※ Image Upload URL이란 사용자가 Image를 업로드할 위치의 URL 정보로 업로드하는 Image를 받아들이는 서버의 처리 주소를 의미한다.)|
**Syntax**|
Editor_Instance.setImageUploadURL(“http://www.kukudocs.com/imageUpload”);|
**Parameter**|
imageUploadURL <br> - Type : String <br> - description : Image Upload를 처리할 서버의 주소를 설정 한다.|
**Return**|
-|

<br><br>

## 1.28 getVideoUploadURL()

getVideoUploadURL()|
---|
Editor에 설정된 Video Upload URL정보를 get한다. <br> (※ Video Upload URL이란 사용자가 동영상을 업로드할 위치의 URL 정보로 업로드하는 동영상을 받아들이는 서버의 처리 주소를 의미한다.)|
**Syntax**|
Editor_Instance.getVideoUploadURL();|
**Return**|
Type: String <br> Video Upload URL의 정보를 반환|

<br><br>

## 1.29 setVideoUploadURL(videoUploadURL)

setVideoUploadURL(videoUploadURL)|
---|
Editor에 설정된 Video Upload URL정보를 set한다. <br> (※ Video Upload URL이란 사용자가 동영상을 업로드할 위치의 URL 정보로 업로드하는 동영상을 받아들이는 서버의 처리 주소를 의미한다.)|
**Syntax**|
Editor_Instance.setVideoUploadURL(“http://www.kukudocs.com/videoUpload”);|
**Parameter**|
videoUploadURL <br> - Type : String <br> - description : Video Upload를 처리할 서버의 주소를 설정 한다.|
**Return**|
-|

<br><br>

## 1.30 getKeyEvent()

getKeyEvent()|
---|
Editor에 Key Event발생시 실행되는 Key Event Function를 get 한다. <br> (※ KeyEvent는 키보드의 입력이 감지되었을 경우 사용자가 외부에서 삽입한 KeyEvent 실행 함수가 존재할 때 호출된다.)|
**Syntax**|
Editor_Instance.getKeyEvent();|
**Return**|
Type: {object [Key : Function]} <br> 사용자가 입력한 KeyEvent 함수 정보를 반환|

<br><br>

## 1.31 setKeyEvent(Key_event_Object)

setKeyEvent(Key_event_Object)|
---|
Editor에 Key Event발생시 실행되는 Key Event Function를 set 한다. <br> (※ KeyEvent는 키보드의 입력이 감지되었을 경우 사용자가 외부에서 삽입한 KeyEvent 실행 함수가 존재할 때 호출된다.)|
**Syntax**|
Editor_Instance.setKeyEvent( { ‘keydown’ : keyDownFn … } );|
**Parameter**|
Key_event_Object <br> - Type : Object ( ‘event_name’ : callbackFunction ) <br> - description : Editor의 Key Event 발생시 호출될 외부의 함수를 설정 한다.|
**Return**|
-|

<br><br>

## 1.32 getMouseEvent()

getMouseEvent()|
---|
Editor에 Mouse Event발생시 실행되는 Mouse Event Function를 get 한다. <br> (※ MouseEvent는 마우스의 동작이 감지되었을 경우 사용자가 외부에서 삽입한 MouseEvent 실행 함수가 존재할 때 호출된다.)|
**Syntax**|
Editor_Instance.getMouseEvent();|
**Return**|
Type: Function <br> 사용자가 입력한 MouseEvent함수 정보를 반환|

<br><br>

## 1.33 setMouseEvent(Mouse_event_Object)

setMouseEvent(Mouse_event_Object)|
---|
Editor에 Mouse Event발생시 실행되는 Mouse Event Function를 set 한다. <br> (※ MouseEvent는 마우스의 동작이 감지되었을 경우 사용자가 외부에서 삽입한 MouseEvent 실행 함수가 존재할 때 호출된다.)|
**Syntax**|
Editor_Instance.setMouseEvent( { ‘mousedown’ : mouseDownFn … } );|
**Parameter**|
Mouse_event_Object <br> - Type : Object ( ‘event_name’ : callbackFunction ) <br> - description : Editor의 Mouse Event 발생시 호출될 외부의 함수를 설정 한다.|
**Return**|
-|

<br><br>

## 1.34 getCellLockName()

getCellLockName()|
---|
Editor의 Content 중 Cell에 해당하는 Element의 편집을 제한하기 위해 설정하는 Options의 Attribute Name을 반환.|
**Syntax**|
Editor_Instance.getCellLockName();|
**Return**|
Type: String <br> Cell_Lock을 지정하는 Attribute Name 정보를 반환|

<br><br>

## 1.35 setCellLockName(cell_lock_name)

setCellLockName(cell_lock_name)|
---|
Editor의 Content 중 Cell에 해당하는 Element의 편집을 제한하기 위해 설정하는 Options의 Attribute Name을 설정.|
**Syntax**|
Editor_Instance.setCellLockName(‘free’);|
**Parameter**|
cell_lock_name <br> - Type : String <br> - description : Content영역에 입력된 Cell Element의 편집을 방지하는 Attribute Name 을 설정 한다.|
**Return**|
-|

<br><br>

## 1.36 GetAllElements()

GetAllElements()|
---|
Content 영역에 존재하는 모든 Element들을 찾아서 반환한다.<br> (※ Content란 Editor를 편집하는 영역을 의미한다.)|
**Syntax**|
Editor_Instance.GetAllElements();|
**Return**|
Type: Array [Element] <br> 사용자가 입력한 MouseEvent함수 정보를 반환|

<br><br>

## 1.37 GetCurrentElement(tagName)

GetCurrentElement(tagName)|
---|
현재 Cursor 또는 Selection위치의 Element를 가져온다. <br> (※ Selection 상태일 경우에는 복수의 Element List로 반환한다.)|
**Syntax**|
Editor_Instance.GetCurrentElement(tagName);|
**Parameter**|
tagName [option] <br> - Type : String <br> - description : 현재 Cursor 또는 Selection에 해당하는 Element를 반환할 tagName|
**Return**|
Type: null or Element or Array[Element] <br> elementID에 해당하는 Element를 반환한다. (Element가 존재하지 않을 시 null 반환)|

<br><br>

## 1.38 GetElement(elementID)

GetElement(elementID)|
---|
Element의 ID가 Parameter로 전달된 elementID에 해당하는 Element를 찾는다.|
**Syntax**|
Editor_Instance.GetElement(“elementID”);|
**Parameter**|
elementID <br> - Type : String <br> - description : Element의 ID에 해당하는 String형의 값.|
**Return**|
Type: Element or null <br> elementID에 해당하는 Element를 반환한다. (Element가 존재하지 않을 시 null 반환)|

<br><br>

## 1.39 SetEditorSize(width, height)

SetEditorSize(width, height)|
---|
Editor의 전체 width, height의 사이즈를 변경하는 기능|
**Syntax**|
Editor_Instance.SetEditorSize(“100px”, “300px”); <br> or <br> Editor_Instance.SetEditorSize(100, 300);|
**Parameter**|
width <br> - Type : String or Number <br> - description : Editor 전체의 Width를 지정하는 String 또는 Number 형의 값. <br><br> height <br> - Type : String or Number <br> - description : Editor 전체의 height를 지정하는 String 또는 Number 형의 값.|
**Return**|
-|

<br><br>

## 1.40 SetEditorWidth(width)

SetEditorWidth(width)|
---|
Editor의 width의 사이즈만 변경하는 기능|
**Syntax**|
Editor_Instance.SetEditorWidth(“100px”);|
**Parameter**|
width <br> - Type : String or Number <br> - description : Editor 전체의 Width를 지정하는 String 또는 Number 형의 값|
**Return**|
-|

<br><br>

## 1.41 SetEditorHeight(height)

SetEditorHeight(height)|
---|
Editor의 height의 사이즈만 변경하는 기능|
**Syntax**|
Editor_Instance.SetEditorHeight(“300px”);|
**Parameter**|
height <br> - Type : String or Number <br> - description : Editor 전체의 height를 지정하는 String 또는 Number 형의 값|
**Return**|
-|

<br><br>

## 1.42 GetEditorSize()

GetEditorSize()|
---|
Editor의 width, height 사이즈를 가져온다.|
**Syntax**|
var editorSize = Editor_Instance.GetEditorSize();<br><br>console.log( editorSize.width, editorSize.height );|
**Return**|
Type: Object { width, height } <br> Editor의 width와 height의 정보를 Object 형태 Wrapping하여 반환한다.|

<br><br>

## 1.43 SetEditMode(modeType)

SetEditMode(modeType)|
---|
Editor의 편집Mode(Editor, HTML, TEXT, Preview)를 설정하는 기능|
**Syntax**|
Editor_Instance.SetEditMode(0); <br> // ModeType (0 : Editor, 1 : HTML, 2 : TEXT, 3 : Preview)|
**Parameter**|
modeType <br> - Type : Number <br> - description : Editor의 편집 Mode를 설정하는 Number형의 값. <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(0 : Editor, 1 : HTML, 2 : TEXT, 3 : Preview)|
**Return**|
-|

<br><br>

## 1.44 GetEditorContent(isWrapping, isBackground)

GetEditorContent(isWrapping, isBackground)|
---|
Content 영역내에 입력되어 있는 HTML의 정보를 가져오는 기능 <br> (※ Content란 Editor를 편집하는 영역을 의미한다.)|
**Syntax**|
Editor_Instance.GetEditorContent(/*option*/ true , /*option*/ true); <br> //parameter true시 DIV Wrapping / 배경이미지 포함 HTML을 반환|
**Parameter**|
isWrapping <br> - Type : Boolean <br> - description : Export HTML를 DIV 감싸서 내려주는 옵션 <br><br> isBackground <br> - Type : Boolean <br> - description : Export HTML에 Background이미지를 포함시키는 옵션|
**Return**|
Type: String <br> Content영역에 편집되어 있는 컨텐츠를 HTML Code형식의 String으로 반환한다.|

<br><br>

## 1.45 GetEditorTextContent()

GetEditorTextContent()|
---|
Content 영역내에 입력되어 있는 컨텐츠를 Text로 가져오는 기능 <br> (※ Content란 Editor를 편집하는 영역을 의미한다.)|
**Syntax**|
Editor_Instance.GetEditorTextContent();|
**Return**|
Type: String <br> Content영역에 편집되어 있는 컨텐츠를 Plain Text형식의 String으로 반환한다. <br> ※ 객체형식(Table, Image, Hyperlink 등)의 내용은 제거되어 순수 Text로만 반환한다.|

<br><br>

## 1.46 GetContentHTMLFile()

GetContentHTMLFile()|
---|
Content 영역내에 입력되어 있는 HTML의 정보를 가져오는 기능 <br> (※ Content란 Editor를 편집하는 영역을 의미한다.)|
**Syntax**|
Editor_Instance.GetContentHTMLFile();|
**Return**|
Type: String <br> Content영역에 편집되어 있는 컨텐츠를 DocType, Language, Title, Encoding 정보를 포함하는 HTML Code형식의 String으로 반환한다. (HTML 파일 형태의 내용으로 반환)|

<br><br>

## 1.47 GetAttribute(element, AttributeName

GetAttribute(element, AttributeName|
---|
Parameter로 전달되어지는 Element의 AttributeName의 Value값을 찾는 기능|
**Syntax**|
Editor_Instance.GetAttribute(element, “id”);|
**Parameter**|
element <br> - Type : Element <br> - description : attribute의 value를 찾을 대상이 되는 Element. <br><br> AttributeName <br> - Type : String <br> - description : element에서 찾을 attribute name 정보 값|
**Return**|
Type: String or null <br> Attribute name에 해당하는 value 값을 반환한다. (attribute name이 없을 경우 null)|

<br><br>

## 1.48 SetAttribute(element, AttributeName, AttributeValue)

SetAttribute(element, AttributeName, AttributeValue)|
---|
Parameter로 전달되어지는 Element을 대상으로 AttributeName 속성에 AttributeValue값을 지정하는 기능|
**Syntax**|
Editor_Instance.SetAttribute(element, ‘id’, ‘kukudocsEditor’);|
**Parameter**|
element<br>- Type : Element<br>- description : attribute를 변경할 대상이 되는 Element<br><br> AttributeName<br>- Type : String<br>- description : element에 지정할 attribute name 정보 값 <br><br>AttributeValue<br>- Type : String<br>- description : element에 지정할 attribute Value 값|
**Return**|
Type: Boolean (true : 성공, false : 실패) <br> Element에 Attribute정보가 정상적으로 적용되었는지에 대한 여부 반환|

<br><br>

## 1.49 SetEditorContent(htmlString)

SetEditorContent(htmlString)|
---|
Content 영역에 HTML Code를 삽입하는 기능|
**Syntax**|
Editor_Instance.SetEditorContent(“<div><span>Hello</span></div>”);|
**Parameter**|
htmlString<br>- Type : String <br>- description : Content영역에 삽입할 HTML Code 형식의 String 값.|
**Return**|
Type: Boolean (true : 성공, false : 실패) : 성공유무 정보 반환|

<br><br>

## 1.50 SetEditorTextContent(textString)

SetEditorTextContent(textString)|
---|
Content 영역에 Plain Text를 삽입하는 기능|
**Syntax**|
Editor_Instance.SetEditorTextContent(“Hello, Kukudocs Editor!”);|
**Parameter**|
htmlString <br> - Type : String <br> - description : Content영역에 삽입할 Plain Text 형식의 String 값.|
**Return**|
Type: Boolean ( true : 성공, false : 실패) : 성공유무 정보 반환|

<br><br>

## 1.51 SetFocus(element)

SetFocus(element)|
---|
Parameter로 전달된 Element에 Focus를 지정하는 기능|
**Syntax**|
Editor_Instance.SetFocus(element);|
**Parameter**|
element <br> - Type : Element <br> - description : Focus를 지정할 Element|
**Return**|
-|

<br><br>

## 1.52 IsExistsElement(elementID)

IsExistsElement(elementID)|
---|
Parameter로 전달된 elementID를 가지는 Element의 존재 여부를 확인하는 기능|
**Syntax**|
Editor_Instance.IsExistsElement(“editorSampleID”);|
**Parameter**|
elementID <br> - Type : String <br> - description : Element를 찾기 위한 Element의 ID에 해당하는 String 값|
**Return**|
Type: Boolean ( true : 존재, false : 미존재 )<br>ID에 해당하는 Element가 존재하는지에 대한 여부 반환|

<br><br>

## 1.53 GetAttributeValueByBody(attributeName)

GetAttributeValueByBody(attributeName)|
---|
Body(Editor)에 존재하는 Attribute 중 Parameter로 전달된 name에 해당하는 Value값을 찾는 기능|
**Syntax**|
Editor_Instance.GetAttributeValueByBody(“id”);|
**Parameter**|
attributeName<br>- Type : String<br>- description : Body(Editor)의 Attribute를 찾을 name에 대한 String 값|
**Return**|
Type: String <br> Body(Editor)에 지정된 Attribute Name이 존재할 경우 Attribute Value값을 반환|

<br><br>

## 1.54 SetAttributeValueByBody(attributeName, attributeValue)

SetAttributeValueByBody(attributeName, attributeValue)|
---|
Body(Editor)에 Attribute name에 Value값을 지정하는 기능|
**Syntax**|
Editor_Instance.SetAttributeValueByBody(“id”, “kukudocsEditor”);|
**Parameter**|
attributeName<br>- Type : String<br>- description : Body(Editor)의 Attribute를 찾을 name에 대한 String 값<br><br>attributeValue<br>- Type : String<br>- description : Body(Editor)의 Attribute Name에 지정할 Value 대한 String 값|
**Return**|
Type: Boolean (true : 성공, false : 실패) <br>Body(Editor)에 지정된 Attribute Name에 Attribute Value값 지정 성공여부 반환|

<br><br>

## 1.55 IsCellLockByID(elementID)

IsCellLockByID(elementID)|
---|
지정된 ID의 Cell에 쓰기금지(Lock) 적용 여부에 대한 결과를 가져온다. <br> (※ 쓰기금지에 대한 Attribute 기준은 free Attribute가 없으면 Lock, 있으면 쓰기가능)|
**Syntax**|
Editor_Instance.IsCellLockByID(‘cell’);|
**Parameter**|
elementID <br>- Type : String <br>- description : 지정할 Cell의 ID 값|
**Return**|
Type: Boolean ( true : 쓰기금지, false : 쓰기가능) <br> 지정된 elementID에 해당하는 Cell에 free Attribute가 존재하면 쓰기가능(false) 없으면 쓰기금지(true)를 반환|

<br><br>

## 1.56 SetCellLockByID(elementID, isLock)

SetCellLockByID(elementID, isLock)|
---|
지정된 ID의 Cell에 쓰기금지(Lock) 적용 <br> (※ 쓰기금지시 free Attribute제거, 쓰기가능시 free Attribute 삽입)|
**Syntax**|
Editor_Instance.SetCellLockByID(‘cell’, true);|
**Parameter**|
elementID<br>- Type : String<br>- description : Lock의 여부를 설정할 Cell의 ID 값 <br><br>isLock <br> - Type : Boolean <br> - description : Lock의 여부 (true : Lock 설정, false : Lock 해제)|
**Return**|
Type : Boolean (true : 설정 성공, false : 설정 실패) <br> Lock 설정여부에 대해 성공여부를 반환한다.|

<br><br>

## 1.57 IsCellLockByFocus()

IsCellLockByFocus()|
---|
선택한 Focus에 쓰기금지 적용이 되어있는지에 대한 여부 반환 <br> (※ 쓰기금지에 대한 Attribute 기준은 free Attribute가 없으면 Lock, 있으면 쓰기가능)|
**Syntax**|
Editor_Instance.IsCellLockByFocus()|
**Return**|
Type: Boolean ( true : 쓰기금지, false : 쓰기가능) <br> 지정된 Focus에 해당하는 Cell에 free Attribute가 존재하면 쓰기가능(false) 없으면 쓰기금지(true)를 반환|

<br><br>

## 1.58 SetCellLockByFocus(isLock)

SetCellLockByFocus(isLock)|
---|
지정된 Focus의 Cell에 쓰기금지(Lock) 적용 <br> (※ 쓰기금지시 free Attribute제거, 쓰기가능시 free Attribute 삽입)|
**Syntax**|
Editor_Instance.SetCellLockByFocus(true);|
**Parameter**|
isLock<br> - Type : Boolean <br> - description : Lock의 여부 (true : Lock 설정, false : Lock 해제)|
**Return**|
Type : Boolean (true : 설정 성공, false : 설정 실패) <br> Lock 설정여부에 대해 성공여부를 반환한다.|

<br><br>

## 1.59 GetAttributeValueByID(elementID, attributeName)

GetAttributeValueByID(elementID, attributeName)|
---|
elementID를 가지는 Element의 Attribute 중 Parameter로 전달된 name에 해당하는 Value값을 찾는 기능|
**Syntax**|
Editor_Instance.GetAttributeValueByID(“elementID”, “class”);|
**Parameter**|
elementID<br>- Type : String<br>- description : elementID를 ID로 가지고 있는 Element를 찾기 위한 String 값<br><br>attributeName<br>- Type : String<br>- description : Body(Editor)의 Attribute를 찾을 name에 대한 String 값|
**Return**|
Type: String<br>elementID에 해당하는 Element의 Attribute Name이 존재할 경우 Attribute Value값 반환|

<br><br>

## 1.60 SetAttributeValueByID(elementID, attributeName, attributeValue)

SetAttributeValueByID(elementID, attributeName, attributeValue)|
---|
elementID를 ID로 가지고 있는 Element의 Attribute name에 Value값을 지정하는 기능|
**Syntax**|
Editor_Instance.SetAttributeValueByID(“elementID”, “class”, “blue_theme”);|
**Parameter**|
elementID<br>- Type : String<br>- description : elementID를 ID로 가지고 있는 Element를 찾기 위한 String 값<br><br>attributeName<br>- Type : String<br>- description : Body(Editor)의 Attribute를 찾을 name에 대한 String 값<br><br>attributeValue<br>- Type : String<br>- description : Body(Editor)의 Attribute Name에 지정할 Value 대한 String 값|
**Return**|
Type: Boolean ( true : 성공, false : 실패) <br> elementID로 지정된 Element의 Attribute Name에 Attribute Value값 지정 성공여부 반환|

<br><br>

## 1.61 GetHtmlByID(elementID)

GetHtmlByID(elementID)|
---|
elementID를 가지는 Element의 innerHTML을 가져오는 기능|
**Syntax**|
Editor_Instance.GetHtmlByID(elementID);|
**Parameter**|
elementID <br> - Type : String <br> - description : elementID를 ID로 가지고 있는 Element를 찾기 위한 String 값|
**Return**|
Type: String <br> elementID에 해당하는 Element의 InnerHTML 정보 반환|

<br><br>

## 1.62 SetHtmlByID(elementID, htmlString)

SetHtmlByID(elementID, htmlString)|
---|
elementID를 가지는 Element에 HTML Code를 삽입하는 기능|
**Syntax**|
`Editor_Instance.SetHtmlByID(“elementID”, “<div><span>hello</span></div>”);`|
**Parameter**|
elementID<br>- Type : String <br> - description : elementID를 ID로 가지고 있는 Element를 찾기 위한 String 값<br><br>htmlString<br>- Type : String<br>- description : elementID를 가지는 Element에 삽입할 HTML Code 형식의 String 값.|
**Return**|
Type: Boolean ( true : 성공, false : 실패)<br>elementID로 지정된 Element에 HTML 삽입 성공여부 반환|

<br><br>

## 1.63 GetTextByID(elementID)

GetTextByID(elementID)|
---|
elementID를 가지는 Element의 Plain Text 값을 가져오는 기능|
**Syntax**|
Editor_Instance.GetTextByID(elementID);|
**Parameter**|
elementID<br>- Type : String<br>- description : elementID를 ID로 가지고 있는 Element를 찾기 위한 String 값|
**Return**|
Type: String<br>elementID에 해당하는 Element의 Plain Text값 반환|

<br><br>

## 1.64 SetTextByID(elementID, textValue)

SetTextByID(elementID, textValue)|
---|
elementID를 가지는 Element에 Plain Text 값을 삽입하는 기능|
**Syntax**|
Editor_Instance.SetTextByID(“elementID”, “Hello,KukudocsEditor”);|
**Parameter**|
elementID <br>- Type : String <br>- description : elementID를 ID로 가지고 있는 Element를 찾기 위한 String 값 <br><br>SetTextByID<br>- Type : String<br>- description : elementID를 가지는 Element에 삽입할 Plain Text 형식의 String 값.|
**Return**|
Type: Boolean ( true : 성공, false : 실패) <br> elementID로 지정된 Element에 Plain Text 삽입 성공여부 반환|


<br><br>

## 1.65 GetAttributeValueByFocus(attributeName, tagName)

GetAttributeValueByFocus(attributeName, tagName)|
---|
선택한 Element의 AttValue 가져오는 기능 <br>(※ 단 tagName은 Optional한 Parameter이며, 인자로 전달하지 않을시에는 TD, TH의 Cell Type Element를 기본으로 탐색한다.)|
**Syntax**|
Editor_Instance.GetAttributeValueByFocus(“id”);|
**Parameter**|
attributeName<br>- Type : String<br>- description : 현재 선택되어진 element의 attribute Value를 찾기 위한 Attribute Name 값<br><br>tagName [optional]<br>- Type : String <br> - description : 현재 Cursor 또는 Selection에 해당하는 Element를 반환할 tagName|
**Return**|
Type: String <br> 현재 선택되어진 Element의 Attribute Name에 해당하는 Value값을 반환|

<br><br>

## 1.66 SetAttributeValueByFocus(attrName, attrValue, tagName)

SetAttributeValueByFocus(attrName, attrValue, tagName)|
---|
선택한 Element의 AttValue 삽입하는 기능 <br> (※ 단 tagName은 Optional한 Parameter이며, 인자로 전달하지 않을시에는 TD, TH의 Cell Type Element를 기본으로 탐색한다.)|
**Syntax**|
Editor_Instance.SetAttributeValueByFocus(“id”, ‘sample’);|
**Parameter**|
attributeName<br>- Type : String <br>- description : 현재 선택되어진 element의 attribute Value를 찾기 위한 Attribute Name 값<br><br>AttributeValue <br> - Type : String <br> - description : Attribute Name에 적용할 attribute Value 값 <br><br> tagName [option] <br> - Type : String <br> - description : 현재 Cursor 또는 Selection에 해당하는 Element를 반환할 tagName|
**Return**|
Type: Boolean (성공:true, 실패 : false) <br> 현재 선택되어진 Element의 Attribute Name에 Value값을 삽입 성공 여부 반환|

<br><br>

## 1.67 getPublicPathURL()

getPublicPathURL()|
---|
Image 등과 같은 Public(Static) Resource를 사용시 사용하는 리소스의 웹경로의 설정 주소 정보를 get한다.|
**Syntax**|
Editor_Instance.getPublicPathURL();|
**Return**|
Type: String <br> Editor의 Public Resource의 위치 웹경로에 대한 URL 정보를 반환|

<br><br>

## 1.68 setPublicPathURL(publicPathURL)

setPublicPathURL(publicPathURL)|
---|
Image 등과 같은 Public(Static) Resource를 사용시 사용하는 리소스의 웹경로의 설정 주소 정보를 set한다.|
**Syntax**|
//예)현재 웹 주소의 경로에서부터 접근 가능한 Public 리소스에 대한 웹 경로
Editor_Instance.setPublicPathURL(“./”);|
**Parameter**|
helpURL <br> - Type : String <br> - description : Public Path로 사용할 시작 경로를 설정 한다.|
**Return**|
-|

<br><br>

## 1.69 InsertTextByFocus (textValue)

InsertTextByFocus (textValue)|
---|
Content 영역에 선택(Cursor, Selection)되어진 위치에 Text를 삽입하는 기능|
**Syntax**|
Editor_Instance.InsertTextByFocus (“Insert Text”);|
**Parameter**|
textValue<br>- Type : String <br>- description : Content영역에 선택위치에 삽입할 Plain Text 형식의 String 값.|
**Return**|
Type: Boolean ( true : 성공, false : 실패) : 성공유무 정보 반환|

<br><br>

## 1.70 InsertHTMLByFocus (htmlValue)

InsertHTMLByFocus (htmlValue)|
---|
Content 영역에 선택(Cursor, Selection)되어진 위치에 HTML를 삽입하는 기능|
**Syntax**|
`Editor_Instance.InsertHTMLByFocus(“<div><span>Hello</span></div>”);`|
**Parameter**|
htmlValue <br> - Type : String <br> - description : Content영역에 선택위치에 삽입할 HTML Code 형식의 String 값.|
**Return**|
Type: Boolean ( true : 성공, false : 실패) : 성공유무 정보 반환|

<br><br>

## 1.71 executeCommand (CommandName, ShowDefaultUI, Value)

executeCommand (CommandName, ShowDefaultUI, Value)|
---|
Content 영역에 직접 ExecuteCommand 호출 기능 <br> (Document.executeCommand Interface)<br><br>[참조] <br> https://developer.mozilla.org/ko/docs/Web/API/Document/execCommand|
**Syntax**|
Editor_Instance.executeCommand(“fontName”, false, ‘Arial’);|
**Parameter**|
CommandName <br> - Type : String <br> - description : Content영역에 적용할 Command Name 형식의 String 값. <br> 사용 가능한 명령어 목록은 Commands를 참고하세요. <br><br> ShowDefaultUI<br>- Type : Boolean <br> - description : 기본 사용자 UI가 나타나야하는지 보여주는 Boolean 값 <br><br>Value <br>- Type : String <br> - description : 입력변수가 필요한 명령어 (insertImage와 같이 삽입할 이미지의 URL이 필요한)의 경우 이 String으로 정보를 전달합니다. 변수가 필요하지 않으면 null을 표기합니다.|
**Return**|
Type: Boolean ( true : 성공, false : 실패) : 성공유무 정보 반환|
