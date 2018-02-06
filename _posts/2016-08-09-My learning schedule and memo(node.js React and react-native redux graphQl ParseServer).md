1. node.js 
2. express.js
3. canvas do self diagnose
4. react native hibird app
5.flux and redux difference
6.javascript suit for browsers

***

props and state in react :
props translate from the parent component to the child component. it can not be changed.and you can traslate from the parent properties. like <container listdata={data}> list data is the props of the child component . props is one way data flow.

state is the a kind data can be changed and immediatly changed to the view. when react view component need changed according the value of aother component. like when we need filter the list of table of list after when enter the filer text. 


flux and redux  try to store the state in storage. and when these state changed and tell the view to change accordingly.
flux has many stores and redux only have one store. and redux has no dispatcher. 

mainly has action store and reducer.



redux connect has two parameter  mapStateToProps, and mapDispatchToProps

graphQL is a query language for api. it's more like json grammer.it connect with client side and server side . the customer can change the excute sql language by change the graphQL in the client side. and excute more effiently than normal sql language. it works good with node.js mongoDB and react or react native. graphQL can mix different table together. not like sql connnect tables with id . but in graphQL forexample table user and table story . in table story  the autor colum can be type of user. and user table story column can be the type of story table .
graphQL mutation is for post request query is basicly for get request. mutation try to change database. and query try to get data from database. and query is parallel ,mutaion is sequence mean task can be excuted only after the former one complete.


Apollo Optics and Scaphold.io! Apollo and scapHold can manage graphQL。 see the exact time when client excute the graphQL.and decrease the time of graphQL.

parseServer is backend technology. it can query database through REST api to get data with formate of json.


How to imporve website user experience . lazy load picture like react-lazy-load

http/2 is much better than http/1



***

react native 

--Mounting

These methods are called when an instance of a component is being created and inserted into the DOM:

    constructor()
    componentWillMount()
    render()
    componentDidMount()

Updating

An update can be caused by changes to props or state. These methods are called when a component is being re-rendered:

    componentWillReceiveProps()
    shouldComponentUpdate()
    componentWillUpdate()
    render()
    componentDidUpdate()

Unmounting

This method is called when a component is being removed from the DOM:

    componentWillUnmount()



what is single page application--- only one html like index.hmtl .  when route to another page we only send the data from backend to page and load page.without send html page is much faster.  
 BUT google search is not well served single page application. because page in SPAis mainly ajax data from bandend.and google search not well with crawl ajax or javascript.
 
 ***

nodejs 事件驱动型非阻塞i/o

静态语言（强类型语言）

静态语言是在编译时变量的数据类型即可确定的语言，多数静态类型语言要求在使用变量之前必须声明数据类型。
例如：C++、Java、Delphi、C#等。
动态语言（弱类型语言）

动态语言是在运行时确定数据类型的语言。变量使用之前不需要类型声明，通常变量的类型是被赋值的那个值的类型。
例如PHP/ASP/Ruby/Python/Perl/ABAP/SQL/JavaScript/Unix Shell等等。
强类型定义语言

强制数据类型定义的语言。也就是说，一旦一个变量被指定了某个数据类型，如果不经过强制转换，那么它就永远是这个数据类型了。举个例子：如果你定义了一个整型变量a,那么程序根本不可能将a当作字符串类型处理。强类型定义语言是类型安全的语言。
弱类型定义语言

数据类型可以被忽略的语言。它与强类型定义语言相反, 一个变量可以赋不同数据类型的值。强类型定义语言在速度上可能略逊色于弱类型定义语言，但是强类型定义语言带来的严谨性能够有效的避免

IDE for react native . atom+nuclide  watchman (dynamic watch code and reload) flow (identify the  code like wrong type etc.)


REST is the way HTTP should be used. and http protocal using tcp/ip transfer layer. (ftp etc also using tcp/ip)

***

relational database(mySql and postgreSQL) and non-relational database noSQL (mongoDB) realtional dabase save data in different table and connect with relation like prime-key ID. save id in one table and use the id to find detail. non-relational database save all the data in one document. when save in the two table save it twice. you can use lookup to query in mongoDB like JOIN in sql. MongoDB $lookup is useful and powerful, but even this basic example requires a complex aggregate query

---
redis database is store in memory.so the max storage is 1.5 GB. it query language is total different. it offers many functions to query like lrem zadd average etc. can be use in calculation or statistic . like 评分，统计

---
 node debugging tools(need practice)
 node.js with socket.io make real-time chat module. like imsessionwindow
 
 ---
 less vs sass 
 Variable Handling
 LESS uses @, Sass uses $.
 $color: black;           
.scoped { 
  $color: white;
  color: $color;        
}                        
.unscoped {     
  // LESS = black (global)
  // Sass = white (overwritten by local)
  color: $color;          
}
Less change the local viriable does not change the gloable one. but sass change the local and change the gloable

---
const mongoose = require('mongoose');
mLab is a fully managed cloud database service that hosts MongoDB databases;
Heroku is a cloud platform as a service (PaaS) supporting several programming languages that is used as a web application deployment model

---
 do not use map index as the key of each item:
Let me explain, a key is the only thing React uses to identify DOM elements. What happens if you push an item to the list or remove something in the middle? If the key is same as before React assumes that the DOM element represents the same component as before. But that is no longer true.

-----
CMD是SeaJS 在推广过程中对模块定义的规范化产出

对于依赖的模块AMD是提前执行，CMD是延迟执行。不过RequireJS从2.0开始，也改成可以延迟执行（根据写法不同，处理方式不通过）。

CMD推崇依赖就近，AMD推崇依赖前置。

//AMD
define(['./a','./b'], function (a, b) {
 
    //依赖一开始就写好
    a.test();
    b.test();
});
 
//CMD
define(function (requie, exports, module) {
     
    //依赖可以就近书写
    var a = require('./a');
    a.test();
     
    ...
    //软依赖
    if (status) {
     
        var b = requie('./b');
        b.test();
    }
});
虽然 AMD也支持CMD写法，但依赖前置是官方文档的默认模块定义写法。

AMD的API默认是一个当多个用，CMD严格的区分推崇职责单一。例如：AMD里require分全局的和局部的。CMD里面没有全局的 require，提供 seajs.use()来实现模块系统的加载启动。CMD里每个API都简单纯粹。

UMD
UMD是AMD和CommonJS的糅合

AMD模块以浏览器第一的原则发展，异步加载模块。
CommonJS模块以服务器第一原则发展，选择同步加载，它的模块无需包装(unwrapped modules)。
这迫使人们又想出另一个更通用的模式UMD （Universal Module Definition）。希望解决跨平台的解决方案。

UMD先判断是否支持Node.js的模块（exports）是否存在，存在则使用Node.js模块模式。
在判断是否支持AMD（define是否存在），存在则使用AMD方式加载模块。

(function (window, factory) {
    if (typeof exports === 'object') {
     
        module.exports = factory();
    } else if (typeof define === 'function' && define.amd) {
     
        define(factory);
    } else {
     
        window.eventUtil = factory();
    }
})(this, function () {
    //module ...
});

作者：LomoTony
链接：https://www.jianshu.com/p/bd4585b737d7
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

---
在 Vuex 中，mutation 都是同步事务：

