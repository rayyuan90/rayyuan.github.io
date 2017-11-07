
<html>
<body>
    <div class="yq-main">
    <div class="yq-main-left yq-blog-detail" data-spm="blogcont57996">
        <h1 class="blog-title">
            weex vs react-native
</h1>

<p class="blog-summary">
    <em>摘要：</em>
    # 前言
weex的思想是多个平台，只写一套代码，而react-native的思想是多个平台可以写多套代码，但其使用的是同一套语言框架。
weex的目标在于抹平各个平台的差异性，从而简化应用开发。而react-native承认了各个平台之间的差异，退而求其次，在语言和框架层面对平台进行抽象，从方法论的角度去解决多平台开发的问题。

进一步浏览weex和react-native的代码之后，可
</p>
<div class="content-detail">
            
<h1>前言</h1>
<p>weex的思想是多个平台，只写一套代码，而react-native的思想是多个平台可以写多套代码，但其使用的是同一套语言框架。<br>
weex的目标在于抹平各个平台的差异性，从而简化应用开发。而react-native承认了各个平台之间的差异，退而求其次，在语言和框架层面对平台进行抽象，从方法论的角度去解决多平台开发的问题。</p>
<p>进一步浏览weex和react-native的代码之后，可以得出如下的公式。</p>
<pre><code data-language="">weex = Vue.js + H5/Native
react-native = React + Native
</code></pre>
<p>总的来说，其差异性如下表格所示。</p>
<table>
<thead><tr>
<th>dimension</th>
<th>weex</th>
<th>react-native</th>
</tr></thead>
<tbody>
<tr>
<td>js framework</td>
<td>Vue.js</td>
<td>React</td>
</tr>
<tr>
<td>principle</td>
<td>write once, run anywhere</td>
<td>learn once, write anywhere</td>
</tr>
</tbody>
</table>
<p>个人观点，weex和react-native最核心的区别就是这两个。然而就只这两个维度的同步，导致了weex和react-native完全不一样的发展方向。</p>
<h2>Vue.js vs React</h2>
<table>
<thead><tr>
<th>维度</th>
<th>Vue.js</th>
<th>React</th>
</tr></thead>
<tbody>
<tr>
<td>定位</td>
<td>UI框架</td>
<td>UI框架</td>
</tr>
<tr>
<td>目标平台</td>
<td>Web</td>
<td>多平台</td>
</tr>
<tr>
<td>架构</td>
<td>MVVM</td>
<td>React</td>
</tr>
<tr>
<td>数据流</td>
<td>数据绑定</td>
<td>单向数据流动</td>
</tr>
<tr>
<td>组件系统</td>
<td>有</td>
<td>有</td>
</tr>
<tr>
<td>响应式</td>
<td>是</td>
<td>否</td>
</tr>
<tr>
<td>开发语言</td>
<td>html/css/js</td>
<td>all in js</td>
</tr>
<tr>
<td>flexbox</td>
<td>支持</td>
<td>支持</td>
</tr>
<tr>
<td>外围框架</td>
<td>能和其他js框架整合使用</td>
<td>能和其他js框架整合使用</td>
</tr>
<tr>
<td>渲染机制</td>
<td>real DOM</td>
<td>Virtual DOM</td>
</tr>
<tr>
<td>动画</td>
<td>支持</td>
<td>支持</td>
</tr>
<tr>
<td>级别</td>
<td>轻量级</td>
<td>重量级</td>
</tr>
</tbody>
</table>
<h2>weex vs react-native</h2>
<table>
<thead><tr>
<th>维度</th>
<th>weex</th>
<th>react-native</th>
</tr></thead>
<tbody>
<tr>
<td>思想</td>
<td>write once, run anywhere</td>
<td>learn once, write anywhere</td>
</tr>
<tr>
<td>试用场景</td>
<td>简单明了</td>
<td>难易双修</td>
</tr>
<tr>
<td>扩展</td>
<td>为了保证各平台的一致性，一次扩展得在各个平台都实现</td>
<td>不同平台可自由扩展</td>
</tr>
<tr>
<td>社区</td>
<td>内测开源</td>
<td>15年3月开源，社区非常活跃</td>
</tr>
<tr>
<td>支持</td>
<td>alibaba支持</td>
<td>facebook支持</td>
</tr>
<tr>
<td>组件丰富程度</td>
<td>基本只有自带的10余种</td>
<td>除了自带的，还有js.coach上社区贡献的，还是比较丰富的</td>
</tr>
<tr>
<td>上手难度</td>
<td>容易</td>
<td>困难</td>
</tr>
<tr>
<td>调式</td>
<td>暂时log调试</td>
<td>有专门的调试工具，chrome调试，较为完善</td>
</tr>
<tr>
<td>IDE</td>
<td>文本编辑器</td>
<td>Nuclide/文本编辑器</td>
</tr>
</tbody>
</table>
<h1>Vue.js</h1>
<p>Vue.js虽然是Evan You个人开发的开源项目，其社区活跃度以及代码质量还是值得一提的。在写此文章之际，Vue.js在Github上的Star达到了21099，Fork达到了2186。虽然相比于react的Star数44108，Fork数7610还有一定距离，但考虑到作为个人开发者能有如此多的人关注参与，该框架的优秀程度恐怕不会低于React。</p>
<p>Vue.js的文档资料非常齐全，而且其本身的设计非常简洁，因此绝大部分开发者只要花费少量的时间就能快速上手Vue.js。其中<a href="http://blog.evanyou.me/2015/10/25/vuejs-re-introduction/">VUE.JS: A (RE)INTRODUCTION</a>是 Vue.js的作者Evan You对Vue.js的介绍，非常值得一看。我想这可能也是weex团队选择Vue.js入手的原因之一吧。对Vue.js有兴趣的同学可以移步<a href="https://vuejs.org/guide/">Vue.js Guide</a>自行学习。</p>
<p>Vue.js用来构建交互式web界面的，其主要的关注点和React是一样的，都是立足于View层。<br>
Vue.js最核心的部分是两个Reactive Data Binding以及Composable View Components。还值得特别关注的是，其保留了html、css、js分离的写法，使得现有的前端开发者在开发的时候能保持原有的习惯。</p>
<h2>响应式数据绑定</h2>
<p>Vue.js将界面开发分成了三个部分，分别是View、ViewModel和Model，这种划分在客户端开发看来是非常合理的，也经过了实际的检验。以HelloWorld为例来说明，示例来源<a href="https://vuejs.org/guide/">Vue.js Guide</a>。</p>
<pre><code data-language="js">&lt;!-- this is our View --&gt;
&lt;div id="example-1"&gt;
  Hello {{ name }}!
&lt;/div&gt;

&lt;!-- this is our Model --&gt;
var exampleData = {
  name: 'Vue.js'
}

&lt;!-- this is our ViewModel --&gt;
var exampleVM = new Vue({
  el: '#example-1',
  data: exampleData
})
</code></pre>
<p>这就是经典的MVVM模式，Vue.js通过极简的API，将数据和视图绑定在一起，也就是所谓的Data-Binding。<br>
这样，当数据变化的时候，界面就能变化，实现了数据驱动的响应式变成。</p>
<h2>组件化</h2>
<p>当我们在写网页的时候，本质上就是构造DOM树，DOM树则是由div、span等元素组成的。div、span这样的元素是构建大型应用的基础。其实Vue.js或者其他的UI框架基本也是一样的，他们都会提供自己的组件系统。这些组件就类似div元素，一般具有一下特征：</p>
<ul>
<li>小巧精致</li>
<li>能重用</li>
<li>自包含，高内聚</li>
</ul>
<p>当我们使用Vue.js开发应用的时候，就是搭建特定的组件树。这些组件可以是Vue.js定义的，也可以是开发者自己定义的，这非常重要。</p>
<p>看个组件化的例子。</p>
<pre><code data-language="js">// example组件定义
var Example = Vue.extend({
  template: '&lt;div&gt;{{ message }}&lt;/div&gt;',
  data: function () {
    return {
      message: 'Hello Vue.js!'
    }
  }
})

// register it with the tag &lt;example&gt;
Vue.component('example', Example)

// example组件使用
&lt;example&gt;&lt;/example&gt;
</code></pre>
<h3>组件间数据传递</h3>
<p>Vue.js的组件都是有自己独立的scope的，因此子组件是不能直接访问到父组件的数据的。数据一般都是通过props来传递的，示例说明。</p>
<pre><code data-language="js">// define component
Vue.component('child', {
  // declare the props
  props: ['msg'],
  // the prop can be used inside templates, and will also
  // be set as `this.msg`
  template: '&lt;span&gt;{{ msg }}&lt;/span&gt;'
})

// usage
&lt;child msg="hello!"&gt;&lt;/child&gt;
</code></pre>
<p>上述方式只能实现组件树从上往下传递数据，在Vue.js中，会有大量的场景需要子组件向父组件传输数据，甚至兄弟组件之间传递数据，一般这种时候就需要使用以下几种能力。</p>
<ul>
<li>子组件获取父组件的能力（<code>this.$parent</code>）</li>
<li>自定义事件的能力 (<code>$on, $emit, $dispatch, $broadcast</code>)</li>
</ul>
<p>想要了解详情，请移步<a href="http://vuejs.org/guide/components.html#Parent-Child-Communication">Parent-Child Communication</a>。</p>
<h2>样式、逻辑和界面的分离</h2>
<p>前端开发经过这么多年的发展，html、css和js的分开编写应当是顺理成章的，Vue.js没有打破这个规则，通过 <strong>style</strong> 、 <strong>template</strong> 、 <strong>script</strong> 将样式、视图和数据逻辑进行了分离。详见下面示例，来源于<a href="http://blog.evanyou.me/2015/10/25/vuejs-re-introduction/">VUE.JS: A (RE)INTRODUCTION</a>。</p>
<pre><code data-language="js">&lt;!-- css --&gt;
&lt;style&gt;
.message {
  color: red;
}
&lt;/style&gt;

&lt;!-- template --&gt;
&lt;template&gt;
  &lt;div class="message"&gt;{{ message }}&lt;/div&gt;
&lt;/template&gt;

&lt;!-- js --&gt;
&lt;script&gt;
export default {
  props: ['message'],
  created() {
    console.log('MyComponent created!')
  }
}
&lt;/script&gt;
</code></pre>
<h1>React</h1>
<p>React可能是现在前端开发中最炙手可热的UI框架了。在React的<a href="https://facebook.github.io/react/">首页</a>最明显的位置上展示者关于React的最核心的三个思想，它们分别是：</p>
<ul>
<li>Declarative(声明式)</li>
<li>Component-Based（组件化）</li>
<li>Learn Once, Write AnyWhere（一学多写）</li>
</ul>
<h2>声明式</h2>
<p>React和Vue.js的组件的使用都是声明式的，声明式的编写方式会比命令式的编写更加的直观。关于声明式和命令式的区别，可以参考<a href="https://en.wikipedia.org/wiki/Declarative_programming">Declarative programming</a>和<a href="https://en.wikipedia.org/wiki/Imperative_programming">Imperative programming</a>，这里就不加详述了。</p>
<h2>组件化</h2>
<p>诚然React和Vue.js在编写大型程序的时候都是构建一颗组件树，但React和Vue.js的组件却有着不小的差异。先来看一个React组件的示例（来源React官网）。</p>
<pre><code data-language="js">var HelloMessage = React.createClass({
  render: function() {
    return &lt;div style={divStyle}&gt;Hello {this.props.name}&lt;/div&gt;;
  }

  // style
  var divStyle = {
    color: 'white',
    backgroundImage: 'url(' + imgUrl + ')',
    WebkitTransition: 'all', // note the capital 'W' here
    msTransition: 'all' // 'ms' is the only lowercase vendor prefix
  };
});

ReactDOM.render(&lt;HelloMessage name="John" /&gt;, mountNode);
</code></pre>
<p>在React中，一切都是js，视图、逻辑和样式都是通过js来写的。通过js来统一颠覆了html、css和js分离的原则，当然是褒贬不一了。在Vue.js中，分离带来了清晰度，逻辑、视图、样式和数据可以分别处理，但在React中，一切都需要重新组织，甚至需要新的配套框架和设计模式，比如新的语言JSX就是用来简化js带来的麻烦的。但all in js让很多事情变得简单，js的快速发展也让React脱离了css和html发展限制，可以实现更多的可能性，优化、扩展以及其他很多事情，就只要单纯考虑js就可以了，而不必收到css和html的限制。</p>
<p>当然，这样带来的后果就是学习曲线的陡然增加，React甚至带来了新的JSX语法，同时考虑到React全新的React思想，开发者想要开发生产环境的app，尤其是在将现有app用React重写的时候，成本是要比Vue.js高出不止一个数量级的。</p>
<h3>组件间数据传递</h3>
<p>React推崇的是单向数据流动，也就是说，数据最好是从组件树的顶端往叶子节点流动，尽量少的出现反向流动的情况。<br>
用另外一种方式来说，React希望实现的immutable data，数据的不变性。只读的数据能给我们带来非常多的好处，并发、简化逻辑、数据统一管理等等。</p>
<p>React提供了props和state两种数据类型，props是实现数据从父组件往子组件传递的机制，而state则是提供了一种机制来实现组件的自更新，facebook是建议尽量少用该特性，因为其违反了immutable data和单向数据流动的设定。</p>
<p>因为React的数据设定让其数据管理成为一个问题，业界出现了一些解决方案，其中最为著名的应该就是redux/flux了，有兴趣的同学可以上github搜搜，都是开源的。</p>
<h2>一学多写</h2>
<p>React背后是强大的facebook在开发维护，其目的不是要简单的创建一种新的js的UI框架，相反，其想要让React成为平台无感知的UI开发思想。什么意思呢？就是本节要说的learn once，write anywhere。facebook认为每个平台不可能完全一样，Web、Android、iOS、Windows Phone甚至Xbox，以及未来会出现的各种平台，他们都会有自己的发展理念和发展路劲，不可能做到完全一样，但不管平台如何变化，基于平台之上，创建Virtual DOM，React通过控制Virtual DOM来实现界面变化。<br>
也就是说Virtual DOM相当于是一个中间层，隔离平台的差异，从而实现统一的开发方式。</p>
<p>不敢说这样的想法一定能成功，但就现在的发展势头来看，机会还是非常大的。尤其对于开发者来说极具吸引力，如果这一想法成为现实，以后React就可能像DOM一样成为业界统一的标准。那对于iOS开发者来说，在Android上面开发会跟在iOS上开发一样，不需要学习全新的Java语言，Android系统，更不要说各种Java特有的艰深复杂的工具了。</p>
<h1>Native</h1>
<p>个人感觉weex和react-native最大的不同是在Vue.js和React层面。这一点在react-native的命名上就非常容易看出来。在react-native刚出来的时候，其和React的关系是react-native依赖React。</p>
<pre><code data-language="">"dependencies": {
  "react": "~14.0.0"
}
</code></pre>
<p>而现在react-native和react则是同级别的。</p>
<pre><code data-language="">"peerDependencies": {
  "react": "~15.1.0"
}
</code></pre>
<p>react-native中最重要的文件名字也是Library，主要提供了一系列Native的能力。</p>
<p>查看weex的源码，native部分的作用几乎是一样的，主要就是提供了一些列Native的组件，以及其他的一些能力。</p>
<p>这也就是为什么本文将两者的Native合为一谈的原因，他们的本质是差不多的。</p>
<ul>
<li>提供了js和native交互的桥梁Bridge</li>
<li>提供了一系列组件</li>
<li>提供了flexbox布局支持</li>
<li>提供了事件支持</li>
<li>……</li>
</ul>
<p>当然，因为weex和react-native的设计思想的差异，在native部分也存在差异，但我觉得这是因为js需要导致的，仅就native而言，两者并没有特别大的不一样。</p>
<p>也许在不远的将来，native部分会出来一个比较核心的框架，抽象出在构建App时js和native交互所需要的基本能力，同时提供扩展方式，让各种类似react-native\weex这样的框架可以专注于js层的设计。也许react-native就走在这条路上，谁知道呢？</p>
<h1>展望</h1>
<p>动态化的世界越来越精彩，对于weex和react-native的了解才刚刚入门，需要更多实操经验来深刻体会到两者的博大精深。weex和react-native各有千秋，开源的魅力也正是在此。</p>

    
    <!-- 登录查看 begin -->
        <!-- 登录查看 end -->
</div>
    <div class="content-detail yq-blog-sem-remove" style="text-decoration:underline;padding-top:0 !important;">
        版权声明：本文内容由互联网用户自发贡献，本社区不拥有所有权，也不承担相关法律责任。如果您发现本社区中有涉嫌抄袭的内容，欢迎发送邮件至：<a href="mailto:yqgroup@service.aliyun.com">yqgroup@service.aliyun.com</a> 进行举报，并提供相关证据，一经查实，本社区将立刻删除涉嫌侵权内容。
    </div>

    




<div class="footer-detail yq-blog-sem-remove">
 </div>
<div class="about-content yq-blog-sem-remove">
</div>
    <div class="about-content yq-blog-sem-remove">
        <h3 class="title-info">相关文章</h3>
        <ul class="about-c-list">
                            <li>
                    <a href="/articles/57995">
                                                    关于Weex，你想了解的一切都在这里
                                            </a>
                </li>
                            <li>
                    <a href="/articles/226375">
                                                    初识weex与rax
                                            </a>
                </li>
                            <li>
                    <a href="/articles/66570">
                                                    weex高性能list解析
                                            </a>
                </li>
                            <li>
                    <a href="/articles/63540">
                                                    React Native学习指南
                                            </a>
                </li>
                            <li>
                    <a href="/articles/226298">
                                                    [译] 原生 iOS(Swift) 和 React-Na…
                                            </a>
                </li>
                            <li>
                    <a href="/articles/174042">
                                                    《React Native移动开发实战》一一1.1  看…
                                            </a>
                </li>
                            <li>
                    <a href="/articles/57992">
                                                    Weex&amp;ReactNative对比
                                            </a>
                </li>
                            <li>
                    <a href="/articles/111499">
                                                    微软发招，苹果发飙，React Native 躺枪
                                            </a>
                </li>
                            <li>
                    <a href="/articles/57888">
                                                    ReactNative动画研究与实践
                                            </a>
                </li>
                            <li>
                    <a href="/articles/12413">
                                                    react-native开发  react-native…
                                            </a>
                </li>
                    </ul>
    </div>



</body>
</html>

