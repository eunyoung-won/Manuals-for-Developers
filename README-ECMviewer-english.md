# KukuDocs ECM Viewer API Guide
<span style="color:grey">Last Modify: 12 Mar 2019
Version: v11</span>
<br><br>
## 1. Files Included
``` JS
+ css
-      viewer_min.css      	// CSS file
+ fonts              	// Web fonts for UI icons 
-      kk-icon.eot
-      kk-icon.svg
-      kk-icon.ttf
-      kk-icon.woff
+ js
-      HTML5MainViewer_min.js 	// JS main file
-      require-min.js   	           // require.js file
-      worker_min.js                      // worker file (for rendering PDF or TIFF)
- index.html          	// HTML sample file
- iframe.html          	// HTML sample file (for iframe)
```
<br><br>
## 2. API Settings
API configures the settings to operate the ECM Viewer.
``` JS
define('Settings', function() {

     "wrap" : "html5viewer",  // DIV's ID that defines the Viewer 
     "limit" : {
	"maxAnno" : 66,  	  // The max number of annotations ( /element )
	"maxMasking" :66,	  // The max number of redactions ( /element )
	"maxBoxW" : 1000,           // The max width of a box or shape 
	"maxBoxH" : 500,              // The max height of a box or shape
	"minBoxW" : 50,                // The min width of a box or shape
	"minBoxH" : 50,                 // The min height of a box or shape
                "maxMemoW" : 1000,     // The max width of a note
                "maxMemoH" : 500,        // The max height of a note
                "minnoteW" : 300,        // The min width of a note
                "minMemoH" : 50,            // The min height of a note
                "maxMaskingW" : 1000, // The max width of a redaction
                "maxMaskingH" : 500,    // The max height of a redaction
                "minMaskingW" : 50,      // The min width of a redaction
                "minMaskingH" : 50        // The min height of a redaction
       },
       "thumbnail" : {
 	"display" : true,     // Display thumbnails ( true | false )
                "title" : "hidden",   // Show thumbnail titles (hidden | title | page)
                "direction" : "hidden",   // Show thumbnail descriptions (hidden | title | page)
                "width" : 100         // The thumbnail image width in pixel
       },
       "toolbar" : {
	"display" : true,     // Display the toolbar ( true | false )
"print" : "show",  	  //Show the print button (show | hidden)	
                "thumbView" : "show", // Show the toggle button for thumbnails (show | hidden)
"thumbList" : "show", // Show the toggle button for the thumbnail list (show | hidden)
	"pageNav" : "show",	  //Show the Page Navigation button (show | hidden)
 	"zoom" : "show",   	  // Show the Zoom-In and -Out button (show | hidden)
 	"fit" : "show",    	  // Show the Fit-Width or -Height button (show | hidden)
 	"rotate" : "show"  	  // Show the Rotation button (show | hidden)
	"save" : "show",      // Show the Save button (show | hidden)
"transfer" : "show",  // Show the Export button (show | hidden)
	"annotation" : "show",// Show the Annotation button (show | hidden)
	"imgMasking" : "show" // Show the Redaction button (show | hidden)
     }, 
     "annotation" : {         // Annotation font settings.
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
   	"annotationURL" : "…servlet URL to request annotations… ",
       /* annotationURL : servlet URL to request annotations per elementID 
        Processing one by one
        parameter:  element_id (GET request method)*/
"annotationPram" : {   // Send GET parameter through the annotation URL 
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
 	"saveURL": "Servlet URL to save annotations",
 	"saveParam":{
       	      "key1":"value1",
       	      "key2":"value2"
                },
	"imgSaveURL": "Servlet URL to save images",
 	"imgSavePram":{
       	     "key1":"value1",
       	     "key2":"value2"
 	},
 	"transferURL" : " Servlet URL to send images",
/*
transferURL: Used when images are sent to external parties
This action is the same as Save. . . .
*/
 	"transferPram":{
                     "key1":"value1",
                     "key2":"value2"
 	}
   },
   "extension" : {
      "textboxURL" : "Servlet URL for textbox control",
      "textboxParam":{
         "key1":"value1",
         "key2":"value2"
      }
   }
});
```
<br><br>
## 3. Action API
It allows to request actions to the HTML5 Viewer from the outside of iframe. This request method is Post Message. Below is the procedure of Post Message. 
``` JS
var obj = document.getElementById("html5viewer");
var objDoc = obj.contentWindow || obj.contentDocument;
objDoc.postMessage(action,"*");
```
HTML5 Viewer API provides values in the place of "action". Below is the Action API. 

<br>

### a. Button Action

**Annotation Section**

Action Name| Description
---|---
Save | Save annotations
SaveImg | Save redactions
Transfer | Export images
Download | Download the selected image
Print | Print
PrintAPI | PrintAPI <br> Parameter <br> **mode**: print mode (**image**: only image, **all**: annotations + images) <br> **label**: print label <br> **val** : print pages <br> (**one**: current page, **start**: from the first page to the current page, **end**: from the current page to the last page, **part**: selected pages) <br> **printsubmode** : Partial custom values  (Apply when val : part)
imgMasking | Insert redactions
insertMemo | Insert notes
insertShape | Insert shapes
insertLine | Insert lines
insertStamp | Insert stamps
inserLink | Insert links
insertYpan| Highlight text
textBoxList | Request the text box list
upBrightness | Increase the brightness of a selected image
downBrightness | Decrease the brightness of a selected image
contextMenuOn | Activate Contextmenu
contextMenuOff | Inactivate Contextmenu

<br>

**Viewer Section**

Action Name | Description
--- | ---
fitWidth | Fit to width 
fitHeight | Fit to height
fitAll | Fit to screen
fitSelected | Zoom to selection
zoomin | Zoom in
zoomout | Zoom out
zoomdefault | Zoom to 100% 
zoomto | Magnify to a certain percentage 
Loupe | Loupe magnifying glass
rotateRight | Rotate 90 degrees clockwise
rotateRight180 | Rotate 180 degrees clockwise
rotateRightAll | Rotate all images 90 degrees clockwise 
rotateRightAll180 | Rotate all images 180 degrees clockwise 
rotateLeft | Rotate 90 degrees counterclockwise 
nextPage | Move to the next page
endPage | Move to the last page
prevPage | Move to the previous page
startPage | Move to the first page
thumbView | Thumbnail toggle button
thumbList | Thumbnail list toggle button
closeToolbar | Toggle to hide/show the tool bar and tab bar
dragscroll | Inactivate the drag action 
selectAll | Select all thumbnails

<br>

**Image & Sketch**

Action Name | Description
--- | ---
imgCrop | View the selected image on a maginified pop-up
imgCropDownload | Download the selected image
sketchAction | Add sketch

<br>

**Toggle Action**

Action Name | Description
--- | ---
toggleShape | Hide/show annotations

<br>

### b. Combo box API
Action name | Description
--- | ---
toolbar:{id:"insertShape",val:"`rect`"} | **INSERT SHAPES** <br> <br> **Rectangles** <br> "textbox", "rect", "roundRect", "snip1Rect", "snip2SameRect", "snip2DiagRect", "snipRoundRect", "round1Rect", "round2SameRect", "round2DiagRect",”alpharect”,”alphaellipse” <br><br> **Basic Shapes** <br> "ellipse", "triangle", "rtTriangle", "parallelogram", "trapezoid", "diamond", "pentagon", "hexagon", "heptagon", "octagon", "decagon", "dodecagon", "corner", "diagStripe", "plus", "plaque" <br><br> **Block Arrows** <br> "rightArrow", "leftArrow", "downArrow", "upArrow", "leftRightArrow", "upDownArrow", "quadArrow", "bentArrow", "uturnArrow", "bentUpArrow", "curvedRightArrow", "curvedLeftArrow", "curvedUpArrow", "curvedDownArrow", "notchedRightArrow", "homePlate", "chevron"
toolbar:{id:"insertStamp",val:"`check`"} | **INSERT STAMPS** <br><br> **Stamps** <br> "check" , "disagree"
toolbar:{id:"insertYpan",val:"`mk_ypan_1`"} | **HIGHLIGHT** <br><br> **Highlight** <br> "mk_ypan_1", "mk_ypan_2", "mk_ypan_3", "mk_ypan_4", "mk_ypan_5"
toolbar:{id:"insertLine",val:"`line`"} | **INSERT LINES** <br><br> **Lines** <br> "line", "straightconnector1-1", "straightconnector1-2"
toolbar:{id:"insertLink",val:"`memo`"} | **INSERT LINKS** <br><br> **Link to an existing file** <br> " "
<br>

## 4. External function API
#### a. function name: replaceElement
Change and load images on Viewer. This method is the same as loadingAPI.
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

#### b. function name: resetElement
Erase images on Viewer.
``` JS
{"resetElement":"true"}
```
<br>

#### c. function name: addElement
Add images.
``` JS
{"addElement":{"element_id":"jpeg_01","indexKey" : "1", "title":"jpeg_01", "filename":"jpeg_01.jpg", "ext" : "jpg", "url" : "./data/jpeg_01.jpg", "anno" : "./data/jpeg_01.json"}}
```
<br>

#### d. function name: removeElement
Delete images.
``` JS
{"removeElement":{"element_id":"jpeg_05"}}
```
<br>

#### e. function name: getViewerMeta
Request the metadata of Viewer status. 
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

#### f. function name: getElementMeta
Request the metadata of selected elements.
``` JS
"getElementMeta"


It returns getElementMeta through Callback API.
{
     "elementId": 1234,
     "title":”texttext”,
     "imgupdate":true,
     "isedit":true
}
```
<br>

#### g. function name: goPage
Jump to the element.
``` JS
{"goPage":1}
```
<br>

#### h. function name: getElementList
Return the element list loaded on Viewer.
``` JS
"getElementList"

It returns getElementList through Callback API 

 [“element1”,“element4”,“element4”,“element4”,“element5” ...]
``` 
<br>

#### i. function name: updateElementSequence
Change the order of the elements loaded on Viewer.
``` JS
{"updateElementSequence":[“element1”,“element4”,“element4”,“element4”,“element5” ...] }
```
<br>

#### j. function name: saveAnnoElementOne
Save annotations per page.
``` JS
{"saveAnnoElementOne":{
    "Element_id":"jpeg_05",
    "Key1":"value1",
    "Key2":"value2"
}}
```
<br>

#### k. function name: saveImgElementOne
Save redactions per page.
``` JS
{"saveImgElementOne":{"element_id":"jpeg_05"}}
```
<br>

#### l. function name: getSaveAnnoElementOne
Get the element’s annotations through Post Message.
``` JS
{"getSaveAnnoElementOne":{"element_id":"jpeg_05"}}


It returns getSaveAnnoElementOne through Callback API 
```
<br><br>

## 5. Callback function API
Callback Function API passes a message from the HTML5 Viewer to the outside of iframe. This method is called Post Message. Below is the procedure.
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

#### a. function name: saveAnnoCallback
Change and load images on the Viewer. This method is the same as loadingAPI.
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

#### b. function name: getViewerMeta
Request the status of the metadata of the Viewer.
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

#### c. function name: getElementMeta
Request the metadata of the selected element.
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

#### d. function name: getElementList
Get the list of the elements loaded on the Viewer.
``` JS
"getElementList"

It returns getElementList through Callback API

 [“element1”,“element4”,“element4”,“element4”,“element5” ...]
```
<br>

#### e. function name: applyCallback
Press the Apply button to return events.
``` JS
```
<br>

#### f. function name: deleteCallback
Select annotations and press the Delete button to return events. 
``` JS
```
<br>

#### g. function name: getElementIndex
``` JS
This return is callback API that returns getElementIndex.

{"element_id":”jpeg_05”, "index":2 }
```
<br>

#### h. function name: getMultiselectsIndex
``` JS
It returns getMultiselectsIndex through Callback API 

{"element_id":”jpeg_05”, "index":2 }
```
<br><br>

## 6. Annotation DATA
``` JS
{
   "elementid": "jpeg_05",
   "documentid": "jpeg_05",
   "page": {
       "number": "1",
       "rotate": "0"                        //  Rotation  : 0, 90, 180, 270 
   },
   "scale": "1",
   "calibrationunit": "px",
   "annotations": [
       {
           "objectType": "yp",                           //  Highlight text
           "prstgeom": "mk_ypan_4",                //  Types of highlighter         
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
           "objectType": "mm",                           //  Note 
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
               "text": "\uba54\ubaa8\ud14c\uc2a4\ud2b8"   //  UTF-8 encoding
           },
           "information": {
               "user": "userid",
               "adddate": "201805180300",
               "modifydate": "201805180300"
           }
       },
       {
           "objectType": "st",                             //  stamp
           "prstgeom": "stamp",              //  stamp
           "stemp": "note",                  //  stamp featured note
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
           "objectType": "sp",                             //  shapes
           "prstgeom": "rect",                             //  rectangles
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
           "objectType": "sp",                             //  shapes
           "prstgeom": "ellipse",                       //  oval
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
           "objectType": "ln",                             //  line
           "prstgeom": "line",                             //  line type : line
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
           "objectType": "ln",                             //  line
           "prstgeom": "line",                             //  line type : line
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
               "text": "stickynote"
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
## 8. Annotation Converter
Annotation Converter is a module that converts annotation data from LEADTOOL’s XML to KukuDoc’s JSON.

**command line**

``` JS
  # [php folder path]/php  /Absolit path/convert.php  [input file]  [output file]
```