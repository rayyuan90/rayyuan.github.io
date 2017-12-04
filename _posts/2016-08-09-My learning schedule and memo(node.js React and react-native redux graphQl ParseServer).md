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

relational database(mySql and postgreSQL) and non-relational database noSQL (mongoDB) realtional dabase save data in different table and connect with relation like prime-key ID. save id in one table and use the id to find detail. non-relational database save all the data in one document. when save in the two table save it twice. 
