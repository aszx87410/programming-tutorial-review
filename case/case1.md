# 1. 資策會出身前端工程師

## 背景介紹
資策會出身，上了半年的課，課程時間是週一到週五，朝九晚五，感覺可以學到滿多東西的。上課內容前後端都包，後端是C#，前後端比重大概一比一。

結業之後到台北找工作，目前算是專做前端，一開始是負責換一些圖，現在則是debug、新增一些小功能，用的是jQuery比較多。

## 疑問與回答
### RWD
我心目中的RWD就是用css去動態調整一些寬高比例之類的，但因為他們公司的RWD有極大部分仰賴javascript，難怪他會覺得奇怪，我也覺得奇怪...
不知道是真的這樣，還是這家公司比較奇特？

### jQuery事件概念
令人困擾的 function(e)的e到底是什麼？window.event又是什麼？後來我就解釋說那個e是因為除了事件本身，要帶一些額外資訊，像是click的事件，如果你要抓他是點擊哪個位置怎麼辦？又沒有一個單獨一個事件可以做這件事情，所以一起算在點擊裡面，而這個e就會包含其他一堆有的沒有的數字，可以自己log出來看看，就會比較了解。

window可以想成是你的整個畫面、整個瀏覽器，所以一些範圍比較大的東西都跟window有關，順便有提到全域變數就是會依附在window上面

### 基本程式概念複習
變數、判斷式、迴圈、函式

### 新技術討論
sass/scss/less的差異以及起源
我解釋說css在以前不被注重，一直到現在越來越被當成是一回事，現在寫scss其實就跟寫程式沒什麼兩樣，能夠幫助我們更快的寫出好的css。sass跟scss的差異在於大括號，還有scss跟css相容。less我就不熟了。

Single Page Application
我有稍微講了一下backbone, angular, ember這三套都是在做差不多的事情，就是把前端的網頁變成跟一個桌面軟體、一個app差不多，所以前端也會有mvc，前端也會有router要去管理

### debug實戰
他拿出一段公司的code，說是有一個地方有些bug，於是就稍微看了一下
花了一點時間發現應該是有其他檔案也有改到東西，時間也差不多，就先到此結束。

回家之後我自己砍站改code，發現是因為程式中有一段要抓取display:none元素的高度，但是在某些情況下抓不到，我猜測是因為這個的緣故（不過好像也不太像），總之最後改成 visibility: hidden來實作就解決這個問題。

## 相關資源
1. [Learn to Code HTML & CSS](http://learn.shayhowe.com/html-css/)
2. [高雄前端社群 -前端資源懶人包](https://docs.google.com/document/d/13nK_XY9u5uIleTpSCw88lMupzgCSwXd6j6je44eLhMQ/edit?pli=1)
3. [學習html與css](http://marksheet.io/)
4. [前端工程——基础篇](https://github.com/fouber/blog/issues/10)
5. [CSS 最核心的几个概念](http://www.jianshu.com/p/3a18fcd9fcda)
6. [为JavaScript程序员准备的10本免费书籍](http://info.9iphp.com/10-free-javascript-books-for-beginners/)

