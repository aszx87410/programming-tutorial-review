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

那其實上面提到的那些，你可以看成這樣
``` javascript
module.exports = {};
exports = module.exports;
```

其實這就跟上面的`a`跟`b`的例子是一樣的，也就是說，`exports`是指向`module.exports`，但要注意的是，實際上導出的是`module.exports`

所以你可以
``` javascript

//方法1
exports.name = "nick";

//方法2
module.exports.name = "nick";

//這兩個方法其實是一樣的

//或是你可以
module.exports = {
  name: "nick"
}
```

但是你不可以
``` javascript
exports = {
  name: "nick"
}
```
上面這例子就像一開始那個`b = {name: "good"}`一樣，你會把`exports`重新分配一塊記憶體並且指向，而原本的`module.exports`依然是`{}`，所以不會導出任何東西。

### express基本操作
我覺得沒什麼比看code更能快速了解一個架構，所以直接帶著看[ntucourse.info](https://github.com/ntu-infoplat/ntucourse.info)這個project，基本上就是分成：`views`, `models`, `service`, `routes`這幾塊。

### Promise
以往在javascript裡面進行非同步操作的時候可能會碰到幾個問題，例如說`callback hell`

``` javascript
getUser(function(users){
  getFriend(users[0].id, function(friend){
    getPost(friend.id, function(post){
      console.log(post);
    })
  })
})
```

那自從我們有了`Promise`以後，可以變這樣
``` javascript
getUser().then(function(users){
  return getFriend(users[0].id);
}).then(function(friend){
  return getPost(friend.id);
}).then(function(post){
  console.log(post)
});
```

就把原本的層層結構壓平了，你只要一直`.then`就好  
但事實上這樣子的寫法依舊有些問題，而且也不是很好看
於是到了`es7`，目前有一項功能叫做`async/await`

```javascript
async function getData(){
  var users = await getUser();
  var friend = await getFriend(users[0].id);
  var post = await getPost(friend.id);
  console.log(post);
}
```

是不是很棒！  
根本就是當做同步的程式碼來寫，只是前面多了一個`await`而已  
可以這樣寫其實是因為ES6多一個東西叫做`generator`  
想知道更多可以參考我之前寫過的：[[Javascript] Promise, generator, async與ES6](http://huli.logdown.com/posts/292655-javascript-promise-generator-async-es6)`

### 其他framework
介紹了一下nodejs除了`express`以外還有`sails.js`，那這套其實就跟`rails`很像，就像是php有`laravel`一樣，這三套其實我覺得概念都滿相同的。


## 資源整理
1. [nodejs包教不包會](https://github.com/alsotang/node-lessons)
2. [node入門](http://www.nodebeginner.org/index-zh-tw.html)
3. [七天學會nodejs](https://nqdeng.github.io/7-days-nodejs/)
4. [给 JavaScript 初心者的 ES2015 实战](http://gank.io/post/564151c1f1df1210001c9161)
5. [React Native 帶來的跨平台 mobile app 開發典範轉移](https://speakerdeck.com/coodoo/react-native-dai-lai-de-kua-ping-tai-mobile-app-kai-fa-dian-fan-zhuan-yi)
6. [ECMAScript 6入门](http://es6.ruanyifeng.com/)
7. [深入浅出ES6](http://www.infoq.com/cn/articles/es6-in-depth-an-introduction)