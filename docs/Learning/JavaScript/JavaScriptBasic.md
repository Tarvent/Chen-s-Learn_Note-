# JS 入门

JavaScript is a programming language that is commonly used to create interactive and dynamic effects on websites. It is an interpreted, high-level, client-side programming language that is primarily used to make webpages dynamic and interactive. JavaScript code is integrated into an HTML or XHTML document and runs directly in the browser, rather than on a server. This allows for things like form validation, creating cookies, and providing real-time updates without the need for a page refresh. JavaScript is often used in conjunction with other technologies such as HTML and CSS to create complex web pages and web applications. JavaScript is supported by all modern web browsers and is an essential language for web developers to learn.

# 廖雪峰javascript教程

<aside> 👉🏻 https://www.liaoxuefeng.com/wiki/1022910821149312/1023442583285984

# 尚硅谷JAVASCRIPT

<aside> 👉🏻 https://www.bilibili.com/video/BV1YW411T7GX?p=2
  # 黑马

  <aside> 👉🏻 https://www.bilibili.com/video/BV1Sy4y1C7ha?from=search&seid=13957718775931314902
P85

[黑马课程](https://www.notion.so/5cc8421afa0e474392394fd056802e80)

------

------

要特别注意相等运算符`==`。JavaScript在设计时，有两种比较运算符：

第一种是`==`比较，它会自动转换数据类型再比较，很多时候，会得到非常诡异的结果；

第二种是`===`比较，它不会自动转换数据类型，如果数据类型不一致，返回`false`，如果一致，再比较。

由于JavaScript这个设计缺陷，*不要*使用`==`比较，始终坚持使用`===`比较。

另一个例外是`NaN`这个特殊的Number与所有其他值都不相等，包括它自己

```jsx
NaN === NaN; // false
isNaN(NaN); // true
```

## js字符串替换

在JavaScript中，字符串是不可变的

需要自己定义`replaceAt()`

1. 

```jsx
String.prototype.replaceAt=function(index, replacement) {
    return this.substr(0, index) + replacement+ this.substr(index + replacement.length);
}
var hello="Hello World";
alert(hello.replaceAt(2, "!!")); //should display He!!o World
```

1. 

```jsx
const replaceStr1 = (str, index, char) => {
    const strAry = str.split('');
    strAry[index] = char;
    return strAry.join('');
  }
  replaceStr(str1, 4, '-'); // => Good-Morning
  replaceStr(str2, 4, '-'); // => Hell- World
```

## js字符转数组

```jsx
// 第一种 split拆分 "abc".split('') ==> ["a","b","c"] 
// 第二种 [...] [..."abc"] ==> ["a","b","c"] Array.from("abc") ==> ["a","b","c"]

lines[i].split('')；
```

## js 截取前后字符

前

```jsx
//前
publicstaticvoidsubstringTest01(){
    String str = "http_https://www.baidu.com/";
    //截取_之前字符串
    String str1 = str.substring(0, str.indexOf("_"));
    System.out.println("截取_之前字符串:"+str1);
}
```

后

```jsx
//截取正数第二个"_"后面的内容
publicstaticvoidsubstringTest03() {
    String str ="0123456_89_sdfdsdsf_23423_auauauau";
    //获得第一个点的位置
int index = str.indexOf("_");
    System.out.println("获得第一个点的位置:"+index);
    //根据第一个点的位置 获得第二个点的位置
    index = str.indexOf("_", index + 1);
    System.out.println("根据第一个点的位置 获得第二个点的位置:"+index);
    //根据第二个点的位置，截取 字符串。得到结果 result
    String result = str.substring(index + 1);
    //输出结果
    System.out.println("输出结果:"+result);
}
```

## js 组成

1. ECMA
2. DOM 文档对象模型
3. BOM 浏览器对象模型 弹出对话框， 分辨率

# js书写位置

- 行内

- 内嵌式

  ~~~html
  <script> 
  
  </script>
  ~~~

  

  

- 引入式

# JS 注释

单行注释 //

多行注释 /*..........*

------

JS动态语言，变量的数据类型是可以变化的

# 数据类型分类

简单数据类型

复杂数据类型

# switch 语法

```jsx
switch(){
    case value1:
         1;
         break;
    case value2:
         2；
         break;

     default：
         最后的语句
}
```

------

## SELECTING

- getElementById
- getElementsByTagName
- getElementsByClassName

# querySelector

- querySelectorAll

------



# working with innerText&textContent

## Finding parents/children/siblings(兄弟姐妹)



# DOM（获取HTML）

##  getElementByid()

1. 参数 id是大小写敏感的字符串
2. 返回的是object
3. id经常可以设置为唯一的

## getElementsByTagName()

以伪数组形式存储    

- 父元素的子元素 ‘元素’.getElementsByTagName()

## getElementByClass（）



## querySelectorAll / querySelector

- querySelectorAll 选择所有例如 button, querySelectorAll()[0/1/2等数字选择第几个]
- querySelector选择第一个
