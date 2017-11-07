
<!DOCTYPE html>
<html lang="zh-cn">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>js模块化编程之彻底弄懂CommonJS和AMD/CMD！ - 方便以后复习 - 博客园</title>
<link type="text/css" rel="stylesheet" href="/bundles/blog-common.css?v=ChDk9h03-S75WEqNhGvXkWireJ5cCWdK1xRM9NIXfnM1"/>
<link id="MainCss" type="text/css" rel="stylesheet" href="/skins/CodingLife/bundle-CodingLife.css?v=Kn6KiDd259SBCz5TLORaQ9SBElF985T0TAIl-BjTtws1"/>
<link type="text/css" rel="stylesheet" href="/blog/customcss/301310.css?v=Ww6FXdN3llQuFaWeoxTXuWnA03k%3d"/>
<link id="mobile-style" media="only screen and (max-width: 768px)" type="text/css" rel="stylesheet" href="/skins/CodingLife/bundle-CodingLife-mobile.css?v=Xay8b9tTSw814nBzbOgvS6rrbcxrobMhvHJHdZAO9vI1"/>
<link title="RSS" type="application/rss+xml" rel="alternate" href="http://www.cnblogs.com/chenguangliang/rss"/>
<link title="RSD" type="application/rsd+xml" rel="EditURI" href="http://www.cnblogs.com/chenguangliang/rsd.xml"/>
<link type="application/wlwmanifest+xml" rel="wlwmanifest" href="http://www.cnblogs.com/chenguangliang/wlwmanifest.xml"/>
<script src="//common.cnblogs.com/script/jquery.js" type="text/javascript"></script>  
<script type="text/javascript">var currentBlogApp = 'chenguangliang', cb_enable_mathjax=false;var isLogined=false;</script>
<script src="/bundles/blog-common.js?v=DRleNSOp-2-RdlbwNt69QQ4yKTISMA1DSih-VNOSd9w1" type="text/javascript"></script>
</head>
<body>
<a name="top"></a>

<!--done-->
<div id="home">
<div id="header">
	<div id="blogTitle">
	<a id="lnkBlogLogo" href="http://www.cnblogs.com/chenguangliang/"><img id="blogLogo" src="/Skins/custom/images/logo.gif" alt="返回主页" /></a>			
		
<!--done-->
<h1><a id="Header1_HeaderTitle" class="headermaintitle" href="http://www.cnblogs.com/chenguangliang/">方便以后复习</a></h1>
<h2>把一件事，重复做，重复做，重复做，你就成功了。</h2>



		
	</div><!--end: blogTitle 博客的标题和副标题 -->
	<div id="navigator">
		
<ul id="navList">
<li><a id="blog_nav_sitehome" class="menu" href="http://www.cnblogs.com/">博客园</a></li>
<li><a id="blog_nav_myhome" class="menu" href="http://www.cnblogs.com/chenguangliang/">首页</a></li>
<li><a id="blog_nav_newpost" class="menu" rel="nofollow" href="https://i.cnblogs.com/EditPosts.aspx?opt=1">新随笔</a></li>
<li><a id="blog_nav_contact" class="menu" rel="nofollow" href="https://msg.cnblogs.com/send/%E6%96%B9%E4%BE%BF%E4%BB%A5%E5%90%8E%E5%A4%8D%E4%B9%A0">联系</a></li>
<li><a id="blog_nav_rss" class="menu" href="http://www.cnblogs.com/chenguangliang/rss">订阅</a>
<!--<a id="blog_nav_rss_image" class="aHeaderXML" href="http://www.cnblogs.com/chenguangliang/rss"><img src="//www.cnblogs.com/images/xml.gif" alt="订阅" /></a>--></li>
<li><a id="blog_nav_admin" class="menu" rel="nofollow" href="https://i.cnblogs.com/">管理</a></li>
</ul>
		<div class="blogStats">
			
			<div id="blog_stats">
<span id="stats_post_count">随笔 - 25&nbsp; </span>
<span id="stats_article_count">文章 - 0&nbsp; </span>
<span id="stats-comment_count">评论 - 4</span>
</div>
			
		</div><!--end: blogStats -->
	</div><!--end: navigator 博客导航栏 -->
</div><!--end: header 头部 -->

<div id="main">
	<div id="mainContent">
	<div class="forFlow">
		
<div id="post_detail">
<!--done-->
<div id="topics">
	<div class = "post">
		<h1 class = "postTitle">
			<a id="cb_post_title_url" class="postTitle2" href="http://www.cnblogs.com/chenguangliang/p/5856701.html">js模块化编程之彻底弄懂CommonJS和AMD/CMD！</a>
		</h1>
		<div class="clear"></div>
		<div class="postBody">
			<div id="cnblogs_post_body"><p><span style="font-family: 'Microsoft YaHei';"><span style="font-size: 16px; line-height: 24px;">先回答我：为什么模块很重要？</span></span></p>
<p>&nbsp;</p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">答：因为有了模块，我们就可以更方便地使用别人的代码，想要什么功能，就加载什么模块。</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">但是，这样做有一个前提，那就是大家必须以同样的方式编写模块，否则你有你的写法，我有我的写法，岂不是乱了套！</span></p>
<p><span style="font-family: 'Microsoft YaHei';"><span style="font-size: 16px; line-height: 24px;">于是下面三个模块规范出来了，这篇文章也出来了（拼出来的 {捂脸笑}）。</span></span></p>
<p>&nbsp;</p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">JS中的模块规范（CommonJS，AMD，CMD），如果你听过js模块化这个东西，那么你就应该听过或CommonJS或AMD甚至是CMD这些规范咯，我也听过，但之前也真的是听听而已。<span style="line-height: 1.5;">&nbsp;现在就看看吧，这些规范到底是啥东西，干嘛的。本文包括这三个规范的来源及对应的产物的原理。</span></span></p>
<p><span style="font-family: 'Microsoft YaHei';">&nbsp;</span></p>
<p><strong><span style="font-family: 'Microsoft YaHei'; font-size: 18pt;">一、CommonJS</span></strong></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">1.一开始大家都认为JS是辣鸡，没什么用，官方定义的API只能构建基于浏览器的应用程序，逗我呢，这太狭隘了吧(用了个高端词，嘎嘎)，CommonJS就按耐不住了，CommonJS API定义很多普通应用程序（主要指非浏览器的应用）使用的API，从而填补了这个空白。它的终极目标是提供一个类似Python，Ruby和Java标准库。这样的话，开发者可以使用CommonJS API编写应用程序，然后这些应用可以运行在不同的JavaScript解释器和不同的主机环境中。</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">在兼容CommonJS的系统中，你可以使用JavaScript开发以下程序：</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">(1).服务器端JavaScript应用程序</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">(2).命令行工具</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">(3).图形界面应用程序</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">(4).混合应用程序（如，Titanium或Adobe AIR）</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">2009年，美国程序员Ryan Dahl创造了<a href="http://nodejs.org/" target="_blank">node.js</a>项目，将javascript语言用于服务器端编程。这标志"Javascript模块化编程"正式诞生。因为老实说，在浏览器环境下，没有模块也不是特别大的问题，毕竟网页程序的复杂性有限；但是在服务器端，一定要有模块，与操作系统和其他应用程序互动，否则根本没法编程。NodeJS是CommonJS规范的实现，webpack 也是以CommonJS的形式来书写。</span></p>
<div>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">node.js的<a href="http://nodejs.org/docs/latest/api/modules.html" target="_blank">模块系统</a>，就是参照<a href="http://wiki.commonjs.org/wiki/Modules/1.1" target="_blank">CommonJS</a>规范实现的。在CommonJS中，有一个全局性方法require()，用于加载模块。假定有一个数学模块math.js，就可以像下面这样加载。</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">var math = require('math');</span></p>








</blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">然后，就可以调用模块提供的方法：</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　var math = require('math');</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">&nbsp; &nbsp; &nbsp; math.add(2,3); // 5</span></p>








</blockquote>








</div>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">CommonJS定义的模块分为:{模块引用(require)} {模块定义(exports)} {模块标识(module)}</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">require()用来引入外部模块；exports对象用于导出当前模块的方法或变量，唯一的导出口；module对象就代表模块本身。</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">虽说Node遵循CommonJS的规范，但是相比也是做了一些取舍，填了一些新东西的。</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">不过，说了CommonJS也说了Node，那么我觉得也得先了解下NPM了。NPM作为Node的包管理器，不是为了帮助Node解决依赖包的安装问题嘛，那它肯定也要遵循CommonJS规范啦，它遵循包规范（还是理论）的。<a href="http://en.wikipedia.org/wiki/CommonJS" target="_blank">CommonJS WIKI</a>讲了它的历史，还介绍了modules和packages等。</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">下面讲讲commonJS的原理以及简易实现：</span></p>
<h2><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">1、原理</span></h2>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">浏览器不兼容CommonJS的根本原因，在于缺少四个Node.js环境的变量。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<ul>
<li><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">module</span></li>
<li><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">exports</span></li>
<li><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">require</span></li>
<li><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">global</span></li>








</ul>








</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">只要能够提供这四个变量，浏览器就能加载 CommonJS 模块。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">下面是一个简单的示例。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<pre class=" language-javascript"><span style="font-family: 'Microsoft YaHei'; font-size: 16px;"><code class=" language-javascript">
<span class="token keyword">var module <span class="token operator">= <span class="token punctuation">{
  exports<span class="token punctuation">: <span class="token punctuation">{<span class="token punctuation">}
<span class="token punctuation">}<span class="token punctuation">;

<span class="token punctuation">(<span class="token keyword">function<span class="token punctuation">(module<span class="token punctuation">, exports<span class="token punctuation">) <span class="token punctuation">{
  exports<span class="token punctuation">.multiply <span class="token operator">= <span class="token keyword">function <span class="token punctuation">(n<span class="token punctuation">) <span class="token punctuation">{ <span class="token keyword">return n <span class="token operator">* <span class="token number">1000 <span class="token punctuation">}<span class="token punctuation">;
<span class="token punctuation">}<span class="token punctuation">(module<span class="token punctuation">, module<span class="token punctuation">.exports<span class="token punctuation">)<span class="token punctuation">)

<span class="token keyword">var f <span class="token operator">= module<span class="token punctuation">.exports<span class="token punctuation">.multiply<span class="token punctuation">;
<span class="token function">f<span class="token punctuation">(<span class="token number">5<span class="token punctuation">)<span class="token comment"> // 5000 
</span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></span></pre>
</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">上面代码向一个立即执行函数提供 module 和 exports 两个外部变量，模块就放在这个立即执行函数里面。模块的输出值放在 module.exports 之中，这样就实现了模块的加载。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<h2><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">2、Browserify 的实现</span></h2>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">知道了原理，就能做出工具了。<a href="http://browserify.org/" target="_blank">Browserify</a>&nbsp;是目前最常用的 CommonJS 格式转换的工具。</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">请看一个例子，main.js 模块加载 foo.js 模块。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<pre class=" language-javascript"><span style="font-family: 'Microsoft YaHei'; font-size: 16px;"><code class=" language-javascript"><span class="token comment">
// foo.js
module<span class="token punctuation">.exports <span class="token operator">= <span class="token keyword">function<span class="token punctuation">(x<span class="token punctuation">) <span class="token punctuation">{
  console<span class="token punctuation">.<span class="token function">log<span class="token punctuation">(x<span class="token punctuation">)<span class="token punctuation">;
<span class="token punctuation">}<span class="token punctuation">;
<span class="token comment">
// main.js
<span class="token keyword">var foo <span class="token operator">= <span class="token function">require<span class="token punctuation">(<span class="token string">"./foo"<span class="token punctuation">)<span class="token punctuation">;
<span class="token function">foo<span class="token punctuation">(<span class="token string">"Hi"<span class="token punctuation">)<span class="token punctuation">;
</span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></span></pre>
</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">使用下面的命令，就能将main.js转为浏览器可用的格式。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<pre class=" language-bash"><span style="font-family: 'Microsoft YaHei'; font-size: 16px;"><code class=" language-bash">
$ browserify main<span class="token punctuation">.js <span class="token operator">&gt; compiled<span class="token punctuation">.js
</span></span></span></code></span></pre>
</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">Browserify到底做了什么？安装一下<a href="https://www.npmjs.com/package/browser-unpack" target="_blank">browser-unpack</a>，就能看清楚了。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<pre class=" language-bash"><span style="font-family: 'Microsoft YaHei'; font-size: 16px;"><code class=" language-bash">
$ npm install browser<span class="token operator">-unpack <span class="token operator">-g
</span></span></code></span></pre>
</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">然后，将前面生成的compile.js解包。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<pre class=" language-bash"><span style="font-family: 'Microsoft YaHei'; font-size: 16px;"><code class=" language-bash">
$ browser<span class="token operator">-unpack <span class="token operator">&lt; compiled<span class="token punctuation">.js

<span class="token punctuation">[
  <span class="token punctuation">{
    <span class="token string">"id"<span class="token punctuation">:<span class="token number">1<span class="token punctuation">,
    <span class="token string">"source"<span class="token punctuation">:<span class="token string">"module.exports = function(x) {\n  console.log(x);\n};"<span class="token punctuation">,
    <span class="token string">"deps"<span class="token punctuation">:<span class="token punctuation">{<span class="token punctuation">}
  <span class="token punctuation">}<span class="token punctuation">,
  <span class="token punctuation">{
    <span class="token string">"id"<span class="token punctuation">:<span class="token number">2<span class="token punctuation">,
    <span class="token string">"source"<span class="token punctuation">:<span class="token string">"var foo = require(\"./foo\");\nfoo(\"Hi\");"<span class="token punctuation">,
    <span class="token string">"deps"<span class="token punctuation">:<span class="token punctuation">{<span class="token string">"./foo"<span class="token punctuation">:<span class="token number">1<span class="token punctuation">}<span class="token punctuation">,
    <span class="token string">"entry"<span class="token punctuation">:<span class="token boolean">true
  <span class="token punctuation">}
<span class="token punctuation">]
</span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></span></pre>
</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">可以看到，browerify 将所有模块放入一个数组，id 属性是模块的编号，source 属性是模块的源码，deps 属性是模块的依赖。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">因为 main.js 里面加载了 foo.js，所以 deps 属性就指定 ./foo 对应1号模块。执行的时候，浏览器遇到 require('./foo') 语句，就自动执行1号模块的 source 属性，并将执行后的 module.exports 属性值输出。</span></p>
<p>&nbsp;</p>
<h2><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">3、Tiny Browser Require</span></h2>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">虽然 Browserify 很强大，但不能在浏览器里操作，有时就很不方便。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">我根据&nbsp;<a href="https://github.com/mochajs/mocha" target="_blank">mocha</a>&nbsp;的内部实现，做了一个纯浏览器的 CommonJS 模块加载器&nbsp;<a href="https://github.com/ruanyf/tiny-browser-require" target="_blank">tiny-browser-require</a>&nbsp;。完全不需要命令行，直接放进浏览器即可，所有代码只有30多行。</span></p>
<p>&nbsp;</p>
<p><span style="font-family: 'Microsoft YaHei';"><a href="https://github.com/ruanyf/tiny-browser-require" target="_blank"><img title="" src="http://image.beekka.com/blog/2015/bg2015052203.png" alt="" /></a></span></p>
<p>&nbsp;</p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">它的逻辑非常简单，就是把模块读入数组，加载路径就是模块的id。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<pre class=" language-javascript"><span style="font-family: 'Microsoft YaHei'; font-size: 16px;"><code class=" language-javascript">
<span class="token keyword">function <span class="token function">require<span class="token punctuation">(p<span class="token punctuation">)<span class="token punctuation">{
  <span class="token keyword">var path <span class="token operator">= require<span class="token punctuation">.<span class="token function">resolve<span class="token punctuation">(p<span class="token punctuation">)<span class="token punctuation">;
  <span class="token keyword">var mod <span class="token operator">= require<span class="token punctuation">.modules<span class="token punctuation">[path<span class="token punctuation">]<span class="token punctuation">;
  <span class="token keyword">if <span class="token punctuation">(<span class="token operator">!mod<span class="token punctuation">) <span class="token keyword">throw <span class="token keyword">new <span class="token class-name">Error<span class="token punctuation">(<span class="token string">'failed to require "' <span class="token operator">+ p <span class="token operator">+ <span class="token string">'"'<span class="token punctuation">)<span class="token punctuation">;
  <span class="token keyword">if <span class="token punctuation">(<span class="token operator">!mod<span class="token punctuation">.exports<span class="token punctuation">) <span class="token punctuation">{
    mod<span class="token punctuation">.exports <span class="token operator">= <span class="token punctuation">{<span class="token punctuation">}<span class="token punctuation">;
    mod<span class="token punctuation">.<span class="token function">call<span class="token punctuation">(mod<span class="token punctuation">.exports<span class="token punctuation">, mod<span class="token punctuation">, mod<span class="token punctuation">.exports<span class="token punctuation">, require<span class="token punctuation">.<span class="token function">relative<span class="token punctuation">(path<span class="token punctuation">)<span class="token punctuation">)<span class="token punctuation">;
  <span class="token punctuation">}
  <span class="token keyword">return mod<span class="token punctuation">.exports<span class="token punctuation">;
<span class="token punctuation">}

require<span class="token punctuation">.modules <span class="token operator">= <span class="token punctuation">{<span class="token punctuation">}<span class="token punctuation">;

require<span class="token punctuation">.resolve <span class="token operator">= <span class="token keyword">function <span class="token punctuation">(path<span class="token punctuation">)<span class="token punctuation">{
  <span class="token keyword">var orig <span class="token operator">= path<span class="token punctuation">;
  <span class="token keyword">var reg <span class="token operator">= path <span class="token operator">+ <span class="token string">'.js'<span class="token punctuation">;
  <span class="token keyword">var index <span class="token operator">= path <span class="token operator">+ <span class="token string">'/index.js'<span class="token punctuation">;
  <span class="token keyword">return require<span class="token punctuation">.modules<span class="token punctuation">[reg<span class="token punctuation">] <span class="token operator">&amp;&amp; reg
    <span class="token operator">|| require<span class="token punctuation">.modules<span class="token punctuation">[index<span class="token punctuation">] <span class="token operator">&amp;&amp; index
    <span class="token operator">|| orig<span class="token punctuation">;
<span class="token punctuation">}<span class="token punctuation">;

require<span class="token punctuation">.register <span class="token operator">= <span class="token keyword">function <span class="token punctuation">(path<span class="token punctuation">, fn<span class="token punctuation">)<span class="token punctuation">{
  require<span class="token punctuation">.modules<span class="token punctuation">[path<span class="token punctuation">] <span class="token operator">= fn<span class="token punctuation">;
<span class="token punctuation">}<span class="token punctuation">;

require<span class="token punctuation">.relative <span class="token operator">= <span class="token keyword">function <span class="token punctuation">(parent<span class="token punctuation">) <span class="token punctuation">{
  <span class="token keyword">return <span class="token keyword">function<span class="token punctuation">(p<span class="token punctuation">)<span class="token punctuation">{
    <span class="token keyword">if <span class="token punctuation">(<span class="token string">'.' <span class="token operator">!<span class="token operator">= p<span class="token punctuation">.<span class="token function">charAt<span class="token punctuation">(<span class="token number">0<span class="token punctuation">)<span class="token punctuation">) <span class="token keyword">return <span class="token function">require<span class="token punctuation">(p<span class="token punctuation">)<span class="token punctuation">;
    <span class="token keyword">var path <span class="token operator">= parent<span class="token punctuation">.<span class="token function">split<span class="token punctuation">(<span class="token string">'/'<span class="token punctuation">)<span class="token punctuation">;
    <span class="token keyword">var segs <span class="token operator">= p<span class="token punctuation">.<span class="token function">split<span class="token punctuation">(<span class="token string">'/'<span class="token punctuation">)<span class="token punctuation">;
    path<span class="token punctuation">.<span class="token function">pop<span class="token punctuation">(<span class="token punctuation">)<span class="token punctuation">;

    <span class="token keyword">for <span class="token punctuation">(<span class="token keyword">var i <span class="token operator">= <span class="token number">0<span class="token punctuation">; i <span class="token operator">&lt; segs<span class="token punctuation">.length<span class="token punctuation">; i<span class="token operator">++<span class="token punctuation">) <span class="token punctuation">{
      <span class="token keyword">var seg <span class="token operator">= segs<span class="token punctuation">[i<span class="token punctuation">]<span class="token punctuation">;
      <span class="token keyword">if <span class="token punctuation">(<span class="token string">'..' <span class="token operator">== seg<span class="token punctuation">) path<span class="token punctuation">.<span class="token function">pop<span class="token punctuation">(<span class="token punctuation">)<span class="token punctuation">;
      <span class="token keyword">else <span class="token keyword">if <span class="token punctuation">(<span class="token string">'.' <span class="token operator">!<span class="token operator">= seg<span class="token punctuation">) path<span class="token punctuation">.<span class="token function">push<span class="token punctuation">(seg<span class="token punctuation">)<span class="token punctuation">;
    <span class="token punctuation">}

    <span class="token keyword">return <span class="token function">require<span class="token punctuation">(path<span class="token punctuation">.<span class="token function">join<span class="token punctuation">(<span class="token string">'/'<span class="token punctuation">)<span class="token punctuation">)<span class="token punctuation">;
  <span class="token punctuation">}<span class="token punctuation">;
<span class="token punctuation">}<span class="token punctuation">;
</span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></span></pre>
</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">使用的时候，先将上面的代码放入页面。然后，将模块放在如下的立即执行函数里面，就可以调用了。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<pre><span style="font-family: 'Microsoft YaHei'; font-size: 16px;"><code class="language-html">
&lt;script src="require.js" /&gt;

&lt;script&gt;
require.register("moduleId", function(module, exports, require){
  // Module code goes here
});
var result = require("moduleId");
&lt;/script&gt;
</code></span></pre>
</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">还是以前面的 main.js 加载 foo.js 为例。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<pre class=" language-javascript"><span style="font-family: 'Microsoft YaHei'; font-size: 16px;"><code class=" language-javascript">
require<span class="token punctuation">.<span class="token function">register<span class="token punctuation">(<span class="token string">"./foo.js"<span class="token punctuation">, <span class="token keyword">function<span class="token punctuation">(module<span class="token punctuation">, exports<span class="token punctuation">, require<span class="token punctuation">)<span class="token punctuation">{
  module<span class="token punctuation">.exports <span class="token operator">= <span class="token keyword">function<span class="token punctuation">(x<span class="token punctuation">) <span class="token punctuation">{
    console<span class="token punctuation">.<span class="token function">log<span class="token punctuation">(x<span class="token punctuation">)<span class="token punctuation">;
  <span class="token punctuation">}<span class="token punctuation">;
<span class="token punctuation">}<span class="token punctuation">)<span class="token punctuation">;

<span class="token keyword">var foo <span class="token operator">= <span class="token function">require<span class="token punctuation">(<span class="token string">"./foo.js"<span class="token punctuation">)<span class="token punctuation">;
<span class="token function">foo<span class="token punctuation">(<span class="token string">"Hi"<span class="token punctuation">)<span class="token punctuation">;
</span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></span></pre>
</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">注意，这个库只模拟了 require 、module 、exports 三个变量，如果模块还用到了 global 或者其他 Node 专有变量（比如 process），就通过立即执行函数提供即可。</span></p>
<p><strong><span style="font-family: 'Microsoft YaHei'; font-size: 18pt;">二、AMD</span></strong></p>
<p><span style="font-size: 16px;"><span style="font-family: 'Microsoft YaHei';">基于commonJS规范的nodeJS出来以后，服务端的模块概念已经形成<span style="font-family: 'Microsoft YaHei';">，</span></span><span style="font-family: 'Microsoft YaHei';">很自然地，大家就想要客户端模块。而且最好两者能够兼容，一个模块不用修改，在服务器和浏览器都可以运行。</span><span style="font-family: 'Microsoft YaHei';">但是，由于一个重大的局限，使得CommonJS规范不适用于浏览器环境。还是上面的代码，如果在浏览器中运行，会有一个很大的问题，你能看出来吗？</span></span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　var math = require('math');</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　math.add(2, 3);</span></p>
</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">第二行math.add(2, 3)，在第一行require('math')之后运行，因此必须等math.js加载完成。也就是说，如果加载时间很长，整个应用就会停在那里等。<span style="color: #ff0000;"><strong><span style="font-family: 'Microsoft YaHei';">您会注意到&nbsp;<code>require</code>&nbsp;是同步的。</span></strong></span></span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">这对服务器端不是一个问题，因为所有的模块都存放在本地硬盘，可以同步加载完成，等待时间就是硬盘的读取时间。但是，对于浏览器，这却是一个大问题，因为模块都放在服务器端，等待时间取决于网速的快慢，可能要等很长时间，浏览器处于"假死"状态。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">因此，浏览器端的模块，不能采用"同步加载"（synchronous），只能采用"异步加载"（asynchronous）。这就是AMD规范诞生的背景。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-size: 16px;"><span style="font-family: 'Microsoft YaHei';">CommonJS是主要为了JS在后端的表现制定的，他是不适合前端的</span><span style="font-family: 'Microsoft YaHei'; line-height: 1.5;">，AMD(异步模块定义)出现了，它就主要为前端JS的表现制定规范。</span></span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;"><a href="https://github.com/amdjs/amdjs-api/wiki/AMD" target="_blank">AMD</a>是"Asynchronous Module Definition"的缩写，意思就是"异步模块定义"。它采用异步方式加载模块，模块的加载不影响它后面语句的运行。所有依赖这个模块的语句，都定义在一个回调函数中，等到加载完成之后，这个回调函数才会运行。</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">AMD也采用require()语句加载模块，但是不同于CommonJS，它要求两个参数：</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　require([module], callback);</span></p>
</blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">第一个参数[module]，是一个数组，里面的成员就是要加载的模块；第二个参数callback，则是加载成功之后的回调函数。如果将前面的代码改写成AMD形式，就是下面这样：</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　require(['math'], function (math) {</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　math.add(2, 3);</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　});</span></p>
</blockquote>
<p><span style="font-size: 16px;"><span style="font-family: 'Microsoft YaHei';">math.add()与math模块加载不是同步的，浏览器不会发生假死。所以很显然，AMD比较适合浏览器环境。</span><span style="font-family: 'Microsoft YaHei';">目前，主要有两个Javascript库实现了AMD规范：<a href="http://requirejs.org/" target="_blank">require.js</a>和<a href="https://github.com/cujojs/curl" target="_blank">curl.js</a>。</span></span></p>
<p><span style="color: #ff0000; font-family: 'Microsoft YaHei'; font-size: 16px;"><strong>RequireJS就是实现了AMD规范的呢。</strong></span></p>
<p><span style="color: #000000; font-family: 'Microsoft YaHei'; font-size: 16px;"><strong>详细概括：下面以RequireJS为例说明AMD规范</strong></span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">一、为什么要用require.js？</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">最早的时候，所有Javascript代码都写在一个文件里面，只要加载这一个文件就够了。后来，代码越来越多，一个文件不够了，必须分成多个文件，依次加载。下面的网页代码，相信很多人都见过。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　&lt;script src="1.js"&gt;&lt;/script&gt;</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　&lt;script src="2.js"&gt;&lt;/script&gt;</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　&lt;script src="3.js"&gt;&lt;/script&gt;</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　&lt;script src="4.js"&gt;&lt;/script&gt;</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　&lt;script src="5.js"&gt;&lt;/script&gt;</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　&lt;script src="6.js"&gt;&lt;/script&gt;</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">这段代码依次加载多个js文件。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">这样的写法有很大的缺点。首先，加载的时候，浏览器会停止网页渲染，加载文件越多，网页失去响应的时间就会越长；其次，由于js文件之间存在依赖关系，因此必须严格保证加载顺序（比如上例的1.js要在2.js的前面），依赖性最大的模块一定要放到最后加载，当依赖关系很复杂的时候，代码的编写和维护都会变得困难。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">require.js的诞生，就是为了解决这两个问题：</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei';">　　<img src="http://image.beekka.com/blog/201211/bg2012110701.png" alt="" /></span></p>
<p><span style="font-family: 'Microsoft YaHei';">　　<span style="font-size: 16px;">（1）实现js文件的异步加载，避免网页失去响应；</span></span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　（2）管理模块之间的依赖性，便于代码的编写和维护。</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">二、require.js的加载</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">使用require.js的第一步，是先去官方网站<a href="http://requirejs.org/docs/download.html" target="_blank">下载</a>最新版本。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">下载后，假定把它放在js子目录下面，就可以加载了。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　&lt;script src="js/require.js"&gt;&lt;/script&gt;</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">有人可能会想到，加载这个文件，也可能造成网页失去响应。解决办法有两个，一个是把它放在网页底部加载，另一个是写成下面这样：</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　&lt;script src="js/require.js"&nbsp;defer async="true"&nbsp;&gt;&lt;/script&gt;</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">async属性表明这个文件需要异步加载，避免网页失去响应。IE不支持这个属性，只支持defer，所以把defer也写上。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">加载require.js以后，下一步就要加载我们自己的代码了。假定我们自己的代码文件是main.js，也放在js目录下面。那么，只需要写成下面这样就行了：</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　&lt;script src="js/require.js"&nbsp;data-main="js/main"&gt;&lt;/script&gt;</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">data-main属性的作用是，指定网页程序的主模块。在上例中，就是js目录下面的main.js，这个文件会第一个被require.js加载。由于require.js默认的文件后缀名是js，所以可以把main.js简写成main。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">三、主模块的写法</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">上一节的main.js，我把它称为"主模块"，意思是整个网页的入口代码。它有点像C语言的main()函数，所有代码都从这儿开始运行。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">下面就来看，怎么写main.js。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">如果我们的代码不依赖任何其他模块，那么可以直接写入javascript代码。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　// main.js</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　alert("加载成功！");</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">但这样的话，就没必要使用require.js了。真正常见的情况是，主模块依赖于其他模块，这时就要使用AMD规范定义的的require()函数。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　// main.js</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　require(['moduleA', 'moduleB', 'moduleC'], function (moduleA, moduleB, moduleC){</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　// some code here</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　});</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">require()函数接受两个参数。第一个参数是一个数组，表示所依赖的模块，上例就是['moduleA', 'moduleB', 'moduleC']，即主模块依赖这三个模块；第二个参数是一个回调函数，当前面指定的模块都加载成功后，它将被调用。加载的模块会以参数形式传入该函数，从而在回调函数内部就可以使用这些模块。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">require()异步加载moduleA，moduleB和moduleC，浏览器不会失去响应；它指定的回调函数，只有前面的模块都加载成功后，才会运行，解决了依赖性的问题。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">下面，我们看一个实际的例子。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">假定主模块依赖jquery、underscore和backbone这三个模块，main.js就可以这样写：</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　require(['jquery', 'underscore', 'backbone'], function ($, _, Backbone){</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　// some code here</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　});</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">require.js会先加载jQuery、underscore和backbone，然后再运行回调函数。主模块的代码就写在回调函数中。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">四、模块的加载</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">上一节最后的示例中，主模块的依赖模块是['jquery', 'underscore', 'backbone']。默认情况下，require.js假定这三个模块与main.js在同一个目录，文件名分别为jquery.js，underscore.js和backbone.js，然后自动加载。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">使用require.config()方法，我们可以对模块的加载行为进行自定义。require.config()就写在主模块（main.js）的头部。参数就是一个对象，这个对象的paths属性指定各个模块的加载路径。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　require.config({</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　paths: {</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　"jquery": "jquery.min",</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　"underscore": "underscore.min",</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　"backbone": "backbone.min"</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　}</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　});</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">上面的代码给出了三个模块的文件名，路径默认与main.js在同一个目录（js子目录）。如果这些模块在其他目录，比如js/lib目录，则有两种写法。一种是逐一指定路径。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　require.config({</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　paths: {</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　"jquery": "lib/jquery.min",</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　"underscore": "lib/underscore.min",</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　"backbone": "lib/backbone.min"</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　}</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　});</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">另一种则是直接改变基目录（baseUrl）。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　require.config({</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　baseUrl: "js/lib",</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　paths: {</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　"jquery": "jquery.min",</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　"underscore": "underscore.min",</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　"backbone": "backbone.min"</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　}</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　});</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">如果某个模块在另一台主机上，也可以直接指定它的网址，比如：</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　require.config({</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　paths: {</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　"jquery": "https://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min"</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　}</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　});</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">require.js要求，每个模块是一个单独的js文件。这样的话，如果加载多个模块，就会发出多次HTTP请求，会影响网页的加载速度。因此，require.js提供了一个<a href="http://requirejs.org/docs/optimization.html" target="_blank">优化工具</a>，当模块部署完毕以后，可以用这个工具将多个模块合并在一个文件中，减少HTTP请求数。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">五、AMD模块的写法</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">require.js加载的模块，采用AMD规范。也就是说，模块必须按照AMD的规定来写。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">具体来说，就是模块必须采用特定的define()函数来定义。如果一个模块不依赖其他模块，那么可以直接定义在define()函数之中。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">假定现在有一个math.js文件，它定义了一个math模块。那么，math.js就要这样写：</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　// math.js</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　define(function (){</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　var add = function (x,y){</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　return x+y;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　};</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　return {</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　add: add</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　};</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　});</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">加载方法如下：</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　// main.js</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　require(['math'], function (math){</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　alert(math.add(1,1));</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　});</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">如果这个模块还依赖其他模块，那么define()函数的第一个参数，必须是一个数组，指明该模块的依赖性。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　define(['myLib'], function(myLib){</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　function foo(){</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　myLib.doSomething();</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　}</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　return {</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　foo : foo</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　};</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　});</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">当require()函数加载上面这个模块的时候，就会先加载myLib.js文件。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">六、加载非规范的模块</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">理论上，require.js加载的模块，必须是按照AMD规范、用define()函数定义的模块。但是实际上，虽然已经有一部分流行的函数库（比如jQuery）符合AMD规范，更多的库并不符合。那么，require.js是否能够加载非规范的模块呢？</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">回答是可以的。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">这样的模块在用require()加载之前，要先用require.config()方法，定义它们的一些特征。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">举例来说，underscore和backbone这两个库，都没有采用AMD规范编写。如果要加载它们的话，必须先定义它们的特征。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　require.config({</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　shim: {</span><br /><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　'underscore':{</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　　　exports: '_'</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　},</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　'backbone': {</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　　　deps: ['underscore', 'jquery'],</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　　　exports: 'Backbone'</span><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　}</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　}</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　});</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">require.config()接受一个配置对象，这个对象除了有前面说过的paths属性之外，还有一个shim属性，专门用来配置不兼容的模块。具体来说，每个模块要定义（1）exports值（输出的变量名），表明这个模块外部调用时的名称；（2）deps数组，表明该模块的依赖性。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">比如，jQuery的插件可以这样定义：</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　shim: {</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　'jquery.scroll': {</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　deps: ['jquery'],</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　exports: 'jQuery.fn.scroll'</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　}</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　}</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">七、require.js插件</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">require.js还提供一系列<a href="https://github.com/jrburke/requirejs/wiki/Plugins" target="_blank">插件</a>，实现一些特定的功能。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">domready插件，可以让回调函数在页面DOM结构加载完成后再运行。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　require(['domready!'], function (doc){</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　// called once the DOM is ready</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　});</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">text和image插件，则是允许require.js加载文本和图片文件。</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<blockquote>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　define([</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　'text!review.txt',</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　'image!cat.jpg'</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　],</span><br /><br /><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　function(review,cat){</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　console.log(review);</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　　　document.body.appendChild(cat);</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　　　}</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">　　);</span></p>







</blockquote>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">类似的插件还有json和mdown，用于加载json文件和markdown文件。（完）</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 幼圆; font-size: 16px;">另一个人的概括(有点简单)：</span></p>
<p><span style="font-family: 幼圆; font-size: 16px;">AMD就只有一个接口：define(id?,dependencies?,factory);</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 幼圆; font-size: 16px;">它要在声明模块的时候制定所有的依赖(dep)，并且还要当做形参传到factory中，像这样：</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<div class="cnblogs_code">
<pre><span style="font-family: 幼圆; font-size: 16px;">1 define(['dep1','dep2'],function(dep1,dep2){...});</span></pre>
</div>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 幼圆; font-size: 16px;">要是没什么依赖，就定义简单的模块，下面这样就可以啦：</span></p>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<div class="cnblogs_code">
<pre><span style="font-family: 幼圆; font-size: 16px;">1 define(function(){
2     var exports = {};
3     exports.method = function(){...};
4     return exports;
5 });</span></pre>
</div>
<p><span style="font-size: 16px;">&nbsp;</span></p>
<p><span style="font-family: 幼圆; font-size: 16px;">咦，这里有define，把东西包装起来啦，那Node实现中怎么没看到有define关键字呢，它也要把东西包装起来呀，其实吧，只是Node隐式包装了而已.....</span></p>
<p><span style="font-family: 幼圆; font-size: 16px;">这有AMD的WIKI中文版，讲了很多蛮详细的东西，用到的时候可以查看：<a href="https://github.com/amdjs/amdjs-api/wiki/AMD-(%E4%B8%AD%E6%96%87%E7%89%88)" target="_blank">AMD的WIKI中文版</a></span></p>
<p><span style="font-size: 18pt;"><strong><span style="font-family: 'Microsoft YaHei';">三、CMD</span></strong></span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">大名远扬的玉伯写了seajs，就是遵循他提出的CMD规范，与AMD蛮相近的，不过用起来感觉更加方便些，最重要的是中文版，应有尽有：<a href="http://seajs.org/docs/#docs" target="_blank">seajs官方doc</a></span></p>
<div class="cnblogs_code">
<pre><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">1 define(function(require,exports,module){...});</span></pre>
</div>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">用过seajs吧，这个不陌生吧，对吧。</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">前面说AMD，说RequireJS实现了AMD，CMD看起来与AMD好像呀，那RequireJS与SeaJS像不像呢？</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">虽然CMD与AMD蛮像的，但区别还是挺明显的，官方非官方都有阐述和理解，我觉得吧，说的都挺好：</span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;"><a href="https://github.com/seajs/seajs/issues/277" target="_blank">官方阐述SeaJS与RequireJS异同</a></span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;"><a href="http://www.douban.com/note/283566440/" target="_blank">SeaJS与RequireJS的最大异同（这个说的也挺好）</a></span></p>
<p><span style="font-family: 'Microsoft YaHei'; font-size: 16px;">&nbsp;</span></p></div><div id="MySignature"></div>
<div class="clear"></div>
<div id="blog_post_info_block">
<div id="BlogPostCategory"></div>
<div id="EntryTag"></div>
<div id="blog_post_info">
</div>
<div class="clear"></div>
<div id="post_next_prev"></div>
</div>


		</div>
		<div class = "postDesc">posted @ <span id="post-date">2016-09-09 15:07</span> <a href='http://www.cnblogs.com/chenguangliang/'>方便以后复习</a> 阅读(<span id="post_view_count">...</span>) 评论(<span id="post_comment_count">...</span>)  <a href ="https://i.cnblogs.com/EditPosts.aspx?postid=5856701" rel="nofollow">编辑</a> <a href="#" onclick="AddToWz(5856701);return false;">收藏</a></div>
	</div>
	<script type="text/javascript">var allowComments=true,cb_blogId=301310,cb_entryId=5856701,cb_blogApp=currentBlogApp,cb_blogUserGuid='3c728f1c-3139-e611-9fc1-ac853d9f53cc',cb_entryCreatedDate='2016/9/9 15:07:00';loadViewCount(cb_entryId);var cb_postType=1;</script>
	
</div><!--end: topics 文章、评论容器-->
</div><a name="!comments"></a><div id="blog-comments-placeholder"></div><script type="text/javascript">var commentManager = new blogCommentManager();commentManager.renderComments(0);</script>
<div id='comment_form' class='commentform'>
<a name='commentform'></a>
<div id='divCommentShow'></div>
<div id='comment_nav'><span id='span_refresh_tips'></span><a href='javascript:void(0);' onclick='return RefreshCommentList();' id='lnk_RefreshComments' runat='server' clientidmode='Static'>刷新评论</a><a href='#' onclick='return RefreshPage();'>刷新页面</a><a href='#top'>返回顶部</a></div>
<div id='comment_form_container'></div>
<div class='ad_text_commentbox' id='ad_text_under_commentbox'></div>
<div id='ad_t2'></div>
<div id='opt_under_post'></div>
<div id='cnblogs_c1' class='c_ad_block'></div>
<div id='under_post_news'></div>
<div id='cnblogs_c2' class='c_ad_block'></div>
<div id='under_post_kb'></div>
<div id='HistoryToday' class='c_ad_block'></div>
<script type='text/javascript'>
    fixPostBody();
    setTimeout(function () { incrementViewCount(cb_entryId); }, 50);
    deliverAdT2();
    deliverAdC1();
    deliverAdC2();    
    loadNewsAndKb();
    loadBlogSignature();
    LoadPostInfoBlock(cb_blogId, cb_entryId, cb_blogApp, cb_blogUserGuid);
    GetPrevNextPost(cb_entryId, cb_blogId, cb_entryCreatedDate, cb_postType);
    loadOptUnderPost();
    GetHistoryToday(cb_blogId, cb_blogApp, cb_entryCreatedDate);   
</script>
</div>


	</div><!--end: forFlow -->
	</div><!--end: mainContent 主体内容容器-->

	<div id="sideBar">
		<div id="sideBarMain">
			
<!--done-->
<div class="newsItem">
<h3 class="catListTitle">公告</h3>
	<div id="blog-news"></div><script type="text/javascript">loadBlogNews();</script>
</div>

			<div id="blog-calendar" style="display:none"></div><script type="text/javascript">loadBlogDefaultCalendar();</script>
			
			<div id="leftcontentcontainer">
				<div id="blog-sidecolumn"></div><script type="text/javascript">loadBlogSideColumn();</script>
			</div>
			
		</div><!--end: sideBarMain -->
	</div><!--end: sideBar 侧边栏容器 -->
	<div class="clear"></div>
	</div><!--end: main -->
	<div class="clear"></div>
	<div id="footer">
		
<!--done-->
Copyright &copy;2017 方便以后复习
	</div><!--end: footer -->
</div><!--end: home 自定义的最大容器 -->
</body>
</html>
