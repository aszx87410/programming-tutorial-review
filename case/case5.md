# 5. 資管碩畢
## 背景介紹
資管所畢業，但因為是管理組所以對程式沒那麼熟悉，最近工作上會用到php，所以想要了解php相關的東西。有寫過asp。

## 疑問

### php簡單介紹
因為有學過asp，所以php這邊的簡單介紹還滿順利的，基本上php跟asp都是在做同一件事情。會需要asp跟php是因為，我們需要一些「動態」的東西，例如說使用者登入以後都會有個歡迎頁面，「XXX，你好！」，如果我們純粹只用html，是沒有辦法達成這樣的功能的，因為html是靜態的，輸出的內容永遠都一樣。這個時候我們就會需要php，動態針對不同的使用者輸出不同的內容。

``` php
<?
 $username = "peter";
 echo "你好，".$username
?>
```

### php流程控制、迴圈
其實與c#大同小異，最大差別在於「型態」  

c#屬於`靜態型別`的語言，你在宣告變數的時候需要指定型態；而php屬於`動態型別`，不需要指定型態就可以使用。  

要特別小心的是在做整數跟字串相加的時候有可能會出現問題。php屬於`弱型別`，所以會自動做型別轉換。

ps. 這邊發現我當時有點小講錯，把靜態動態與強弱弄混了，可參考[Static Typing, Dynamic Typing, Strong Typing, Weak Typing](http://swaywang.blogspot.tw/2013/04/static-typing-static-typetype.html)

至於流程控制、迴圈的程式碼都跟其他的差不多
``` php
if($score>=60){
 //pass
}else{
 //fail
}

for($i=0;$i<10;$i++){
  //...
}
```

### php函式、陣列
其實也都大同小異，但php的陣列比起c#較為自由  
index可以用字串來當，也不用事先指定大笑
``` php
$arr = array();
$arr[0] = 10;
$arr["hello"] = "world";
```

函式的話因為滿像的所以就沒講了

### 如何與資料庫連結？
一般在使用資料庫你會到一個後台去下指令，然後就會有結果跑出來。  
在php裡面，有提供內建的函式去做這件事情。
1. 你把要查詢的query給php
2. php幫你拿去資料庫執行
3. php幫你把結果拿回來
4. 你在php裡面對這些結果做事情

```php
//資料庫位置
$db_server = "localhost";

//資料庫名稱
$db_name = "course";

//資料庫管理者帳號
$db_user = "username";

//資料庫管理者密碼
$db_passwd = "password";
$mysqli = new mysqli($db_server, $db_user, $db_passwd,$db_name);

//對資料庫連線
if(!$mysqli){
	die("Connection error: " . mysqli_connect_errno());
}else{
	$mysqli->select_db($db_name);
	$mysqli->set_charset("utf8");
}

//下指令
$sql="select id from users where username=? and password=?";
$stmt = $mysqli->prepare($sql);
$stmt->bind_param("ss",$username,$password);
$stmt->execute();
$stmt->bind_result($id);
if($stmt->fetch()){
	// 有資料
	
}else{
	//沒資料	
}
$stmt->close();
```
### session的觀念
由於`http`的連線是沒有狀態的，所以server要怎麼知道現在的request跟上一個request是同一個人？或是說，在你登入之後，server要怎麼知道你已經登入了？這個時候就要靠session這個東西。

session可以儲存一些資訊，每次在發送request的時候就會帶著這段資訊一起到伺服器去，例如說今天你登入以後，server給你一張通行證，可能是一段看起來很像亂碼的英文加數字，你每次都帶著這通行證，server就知道說你是同一個人了。

### 簡單資訊安全觀念講解
第一個講到的是SQL injection，因為它的書上的教學所用的sql語法是用字串串接的方式，所以有可能會有一些資安上的疑慮，比方說你的程式碼原本是這樣：
```php
//輸入帳號：peter
//密碼：a123

$sql = 
 "select id from users where username = '" + $user + "' and password = '" + $pwd + "'";
 
//會變成
select id from users where username = 'peter' and password = 'a123'
```

那如果有人輸入一段很奇怪的帳號：`' or 1=1--`
```sql
select id from users where username = ''or 1=1--' and password = 'a123'
```

由於`--`是註解的意思，所以後面的語法會被忽略
`or 1=1`永遠成立，所以這個敘述永遠都會查到東西，也就是永遠都可以登入成功！




### git是什麼？

## 相關資源


