# ajax-note
XAMPP下的原生JS的ajax、jQuery的ajax以及跨域问题解决方法的jsonp用法
## 使用方法：
打开XAMPP的Apache服务（端口被占用则修改config文件）  
打开指定url  
## 各文件作用：
XMLHttpRequest.html及server.php作为原生JavaScript实现的ajax的前后端文件  
XMLHttpRequestJson.html及serverjson.php作为返回数据类型为json的前后端文件  
XMLHttpRequestjQuery.html及serverjson2.php作为jQuery实现的ajax的前后端文件  
XMLHttpRequestjQueryJsonp.html及serverjsonp.php作为使用jsonp解决ajax跨域问题的前后端文件 
## 来源：
[慕课网Ajax全接触教程](https://www.imooc.com/learn/250)
## 1. Ajax概念介绍
### 1.1 Ajax
什么是Ajax：  
![ajax](http://wx2.sinaimg.cn/mw690/006epDUlgy1fvrir9puofj30k806caaa.jpg)  
![ajax2](http://wx1.sinaimg.cn/mw690/006epDUlgy1fvris9mrelj30o1071dg6.jpg)  
### 1.2 Ajax-同步和异步
![同步](http://wx1.sinaimg.cn/mw690/006epDUlgy1fvrj0drr9zj30xb0e3gm6.jpg)  
![异步](http://wx4.sinaimg.cn/mw690/006epDUlgy1fvrj0e5ablj30wh0dydgd.jpg)  
为了解决同步带来的问题，ajax使用`XMLHttpRequest`对象来进行不用全局刷新的和服务器端的通信。  
![xhr](http://wx2.sinaimg.cn/mw690/006epDUlgy1fvrj0emouoj30ju0bb74k.jpg)  
ajax的关键点：  
![ajax](http://wx4.sinaimg.cn/mw690/006epDUlgy1fvrj0ezh3tj30rh05amxo.jpg)  
### 1.3 Ajax-XMLHttpRequest对象创建
![xhr](http://wx3.sinaimg.cn/mw690/006epDUlgy1fvrj66gc6lj30y20gljs1.jpg)  
### 1.4 Ajax-HTTP请求
![http](http://wx3.sinaimg.cn/mw690/006epDUlgy1fvrjdl9y9gj30ph08z3yt.jpg)  
![http](http://wx4.sinaimg.cn/mw690/006epDUlgy1fvrjdlp6zij30o80begm0.jpg)  
![http](http://wx3.sinaimg.cn/mw690/006epDUlgy1fvrjdm2ml0j30rv0gmdhg.jpg)  
![http](http://wx4.sinaimg.cn/mw690/006epDUlgy1fvrjdmk3k6j30tk0chta9.jpg)  
![http](http://wx3.sinaimg.cn/mw690/006epDUlgy1fvrjdn1g4ej30t20cqjry.jpg)  
![http](http://wx4.sinaimg.cn/mw690/006epDUlgy1fvrjdnh162j30v309b75b.jpg)  
![http](http://wx3.sinaimg.cn/mw690/006epDUlgy1fvrjdnubirj30go0a1glt.jpg)  
![http](http://wx2.sinaimg.cn/mw690/006epDUlgy1fvrjdodhhuj30uf0ce0u9.jpg)  
### 1.5 Ajax-XMLHttpRequest发送请求
![xhr](http://wx2.sinaimg.cn/mw690/006epDUlgy1fvrjki2wg2j30vt07twer.jpg)  
`open()`方法和`send()`方法可以将`XHR`对象发送到服务器。  
其中`open()`的参数如下：  
1. `method`参数为发送请求的方法，包括`get`和`post`。  
2. `url`参数为请求的地址。
3. `async`参数为请求同步/异步。默认为`true`即异步。  
`send()`方法的`sting`参数，在使用`get`方法时已存在于`url`中可以不填写或者为`none`。在使用`post`方法时就需要填写。  
![send](http://wx2.sinaimg.cn/mw690/006epDUlgy1fvrjq4dgapj30tp0co0t6.jpg)  
上图所示表明发送`post`请求时需要在`open()`和`send()`中间指明HTTP头信息。  
### 1.6 Ajax-XMLHttpRequest取得响应
![取得响应](http://wx4.sinaimg.cn/mw690/006epDUlgy1fvrkgbm9wqj30xb0e6wfl.jpg)  
通过监听`readyState`属性来进行进一步操作：  
![readyState](http://wx4.sinaimg.cn/mw690/006epDUlgy1fvrkgc4upbj30n50arq3l.jpg)  
![代码](http://wx1.sinaimg.cn/mw690/006epDUlgy1fvrkgcjvegj30pv0cs3yy.jpg)  
## 2. Ajax简单例子
### 2.1 Ajax-例子简介
![example](http://wx1.sinaimg.cn/mw690/006epDUlgy1fvrkkt1o47j30te084aac.jpg)  
![example](http://wx3.sinaimg.cn/mw690/006epDUlgy1fvrkktfti2j30pn03jq32.jpg)  
此例子单纯仅靠HTML、CSS、JavaScript是无法完成的，需要接触后台语言：  
![php](http://wx3.sinaimg.cn/mw690/006epDUlgy1fvrkktyzcrj30wo0g0gmy.jpg)  
步骤如下：  
![步骤](http://wx2.sinaimg.cn/mw690/006epDUlgy1fvrkkucjw5j30t305yt8y.jpg)  
### 2.2 Ajax-服务器端实现
参考此仓库下的[server.php](https://github.com/shaoyuyun/ajax-note/blob/master/server.php)。  
### 2.3 PHP服务端代码测试
可以使用Fiddler工具来帮助测试。  
### 2.4 客户端实现
参考此仓库下的[XMLHttpRequest.html](https://github.com/shaoyuyun/ajax-note/blob/master/XMLHttpRequest.html)。  
## 3. JSON格式
### 3.1 json基本概念
![概念](http://wx2.sinaimg.cn/mw690/006epDUlgy1fvrkwpkphfj30vc0dmt9o.jpg)  
![比较](http://wx4.sinaimg.cn/mw690/006epDUlgy1fvrkwc6epij30vn0af0t7.jpg)  
![语法](http://wx2.sinaimg.cn/mw690/006epDUlgy1fvrkwcnokej30uu0gcwf9.jpg)  
![例子](http://wx3.sinaimg.cn/mw690/006epDUlgy1fvrkwczte3j30f20c9mx8.jpg)  
### 3.2 json解析、格式化和校验工具
json解析有两种方法：  
![解析](http://wx4.sinaimg.cn/mw690/006epDUlgy1fvrl1iv7rkj30w20b00td.jpg)  
![例子](http://wx4.sinaimg.cn/mw690/006epDUlgy1fvrl1jb3v3j30z10ckt9u.jpg)  
也可以使用在线工具：  
![工具](http://wx3.sinaimg.cn/mw690/006epDUlgy1fvrl1jrb74j30ig0egjrj.jpg)  
## 4. jQuery中的AJAX
### 4.1 jQuery中的AJAX
![jQuery](http://wx1.sinaimg.cn/mw690/006epDUlgy1fvrl5ba3dwj30wa0gsgmp.jpg)  
![改写](http://wx1.sinaimg.cn/mw690/006epDUlgy1fvrl5bof1xj30dn01la9w.jpg)  
参考此仓库下的[XMLHttpRequestjQuery.html](https://github.com/shaoyuyun/ajax-note/blob/master/XMLHttpRequestjQuery.html)及[serverjson2.php](https://github.com/shaoyuyun/ajax-note/blob/master/serverjson2.php)。  
## 5. 扩展知识介绍（跨域）
![跨域](http://wx4.sinaimg.cn/mw690/006epDUlgy1fvrl80lzzdj30tz0dy0tg.jpg)  
![例子](http://wx3.sinaimg.cn/mw690/006epDUlgy1fvrl93oj9nj30ys04rdgb.jpg)  
![1](http://wx4.sinaimg.cn/mw690/006epDUlgy1fvrlaskzuoj30v304nq3d.jpg)  
![2](http://wx1.sinaimg.cn/mw690/006epDUlgy1fvrlat009aj30ui0b5my8.jpg)  
![3](http://wx4.sinaimg.cn/mw690/006epDUlgy1fvrlatc7itj30g407ct8r.jpg)  
### 5.1 处理跨域方式--代理
![proxy](http://wx3.sinaimg.cn/mw690/006epDUlgy1fvrlcp0pt1j30vb0ffq46.jpg)  
### 5.2 处理跨域方式--JSONP
JSONP可以用于处理主流浏览器的`get`请求产生的跨域问题。JSONP利用的是js代码可以跨域访问的特性。  
![jsonp](http://wx3.sinaimg.cn/mw690/006epDUlgy1fvrled0o81j30u50gd74v.jpg)  
参考此仓库下的[XMLHttpRequestjQueryJsonp.html](https://github.com/shaoyuyun/ajax-note/blob/master/XMLHttpRequestjQueryJsonp.html)及[serverjsonp.php](https://github.com/shaoyuyun/ajax-note/blob/master/serverjsonp.php)。  
### 5.3 处理跨域方式--XHR2
![XHR2](http://wx1.sinaimg.cn/mw690/006epDUlgy1fvrlj2unyfj30tx0dst9h.jpg)  
![XHR2](http://wx3.sinaimg.cn/mw690/006epDUlgy1fvrlm5lcuvj30uh0cwjsy.jpg)  