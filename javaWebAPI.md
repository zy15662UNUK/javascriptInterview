##### ECMA 262标准，js基础知识，JS-web-API：W3C标准
- 浏览器js是这两者结合

##### W3C
- DOM 操作
- BOM 操作：页面宽度等
- 事件绑定
- ajax请求http协议）
- 存储
- 没有规定任何js基础
- 不管变量类型，原型，作用域
- JS 内置全局函数和对象：object array Boolean string math json
- 浏览器的document， window，当然会有更多很多未定义的浏览器内置全局变量

##### DOM：
- 本质：tree数据结构主干+分支。html是字符串，但是浏览器把它结构化成了js也能识别也能操作的模型

- DOM节点操作：
  1. 获取DOM节点

    ```
    var div1 = document.getElementById("div1"); //元素
    var divList = document.getElemensByTagName("div");  //集合array
    console.log(divList.length);
    console.log(divList[0]);
    var containerList = document.getElementByClassName(".container");
    var pList = document.querySelectorAll('p'); //集合array
    ```
    获取的都是DOM对象
  2. property

    ```
    var pList = document.querySelectorAll('p');
    var p = pList[0];
    console.log(p.style.width); //获取样式
    p.style.width = '100px';  // 修改样式
    console.log(p.className); //获取class
    p.className = 'p1'; //修改class
    console.log(p.nodeName);  //获取nodeName p
    console.log(p.nodeType);  //获取nodeType。是数字。 text是3， p是1
    ```
    style，className是js object属性，就和js object.后面相同

  3. attribute

    ```
    var pList = document.querySelectorAll('p');
    var p = pList[0];
    p.getAttribute("data-name");
    p.setAttribute("data-name", "imooc");
    p.getAttribute("style");
    p.setAttribute("style", "font-size:30px");
    ```
    attribute是文档标签的属性，比如class，src之类的，并不是js对象的属性

- DOM结构操作：
  1. 新增节点

  ```
  var div1 = document.getElementById("div1"); //元素
  var p1 = document.createElement('p'); //创造一个新节点
  p1.innerHTML = "p1";
  div1.appendChild(p1); //添加新创造的p节点作为子节点
  p2 = document.getElementById('p2');
  div1.appendChild(p2); //把已经有的移动到div1之下
  ```

  2. 获取父级元素
  3. 获取子元素

  ```
  var div1 = document.getElementById('div1');
  var parent = div1.parentElement;  //集合
  var child = div1.childNodes;
  div1.removeChild(child[0]); //集合
  ```
  4. 删除节点

  ```
  div1.removeChild(child[0]);
  ```
##### DOM操作题目
- DOM是那种基本的数据结构？
  tree。

- DOM操作常用的API有哪些？
  获取DOM节点和他的property还有attr 新增节点 获取父级元素 获取子元素删除节点

- DOM节点attr和property有何区别？
  property只是一个js对象属性修改获取
  attribute是对html标签属性修改获取

##### BOM操作
- Browser Object Model
- navigator：浏览器属性
- screen：屏幕属性，宽高

  ```
  var us = navigator.userAgent; //string,浏览器特性
  var isChrome = ua.indexOf("chrome");
  console.log(isChrome);

  console.log(screen.width);
  console.log(screen.height);
  ```
- location：地址栏信息
- history：历史，前进后退

  ```
  //location
  console.log(location.href);
  console.log(location.protocol); // http: https
  console.log(location.pathname); // '/learn/199'
  console.log(location.search); //  ?后面参数
  console.log(location.hash); //  #后面内容

  //history
  location.back();
  history.forward;
  ```
##### BOM 题目
- 如何检测浏览器特性（android/iOS）

  ```
  var us = navigator.userAgent; //string,浏览器特性
  var isChrome = ua.indexOf("chrome");  //字符串中找有没有浏览器关键字，但是通常只能确定浏览器类型，不能知道所有类型
  console.log(isChrome);
  ```
- 拆解url的各部分

  ```
  //location
  console.log(location.href); //全部域名
  console.log(location.protocol); // http: https
  console.log(location.pathname); // '/learn/199'
  console.log(location.search); //  ?后面参数
  console.log(location.hash); //  #后面内容
  ```
