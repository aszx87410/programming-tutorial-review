# 新鮮人工程師

## 背景
剛畢業，之前寫過php，找工作則是找到寫asp.net的，所以現在在公司是寫vb.net，對node.js有興趣

## 疑問

### exports與module.exports的區別
可以參考這篇：[exports 和 module.exports 的区别](https://cnodejs.org/topic/5231a630101e574521e45ef8)

我這邊快速講一下，先看下面這個例子
``` javascript
var a = {name: "peter"};
var b = a;

console.log(a); // peter
console.log(b); // peter

b.name = 'nick';
console.log(a); // nick
console.log(b); // nick
/*
b = a 這行是說「b存的內容是a所指向的記憶體位置」
所以當b的值變了以後，a也會跟著變
因為他們是同一塊記憶體位置
*/

b = {name: "good"};
console.log(a); //nick
console.log(b); //good

/*
現在把b指到一塊新的記憶體去，所以b改變了
a依然維持原樣
*/
```



## 資源整理
1. [nodejs包教不包會](https://github.com/alsotang/node-lessons)
2. [node入門](http://www.nodebeginner.org/index-zh-tw.html)
3. [七天學會nodejs](https://nqdeng.github.io/7-days-nodejs/)
4. [给 JavaScript 初心者的 ES2015 实战](http://gank.io/post/564151c1f1df1210001c9161)
5. [React Native 帶來的跨平台 mobile app 開發典範轉移](https://speakerdeck.com/coodoo/react-native-dai-lai-de-kua-ping-tai-mobile-app-kai-fa-dian-fan-zhuan-yi)
6. [ECMAScript 6入门](http://es6.ruanyifeng.com/)
7. [深入浅出ES6](http://www.infoq.com/cn/articles/es6-in-depth-an-introduction)