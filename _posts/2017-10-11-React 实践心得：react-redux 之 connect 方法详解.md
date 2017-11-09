![React 实践心得：react-redux 之 connect 方法详解](//img.alicdn.com/tfs/TB1fYYeLpXXXXbtXFXXXXXXXXXX-900-500.jpg)

Redux 是「React 全家桶」中极为重要的一员，它试图为 React 应用提供「可预测化的状态管理」机制。Redux 本身足够简单，除了 React，它还能够支持其他界面框架。所以如果要将 Redux 和 React 结合起来使用，就还需要一些额外的工具，其中最重要的莫过于 react-redux 了。

react-redux 提供了两个重要的对象，`Provider` 和 `connect`，前者使 React 组件可被连接（connectable），后者把 React 组件和 Redux 的 store 真正连接起来。react-redux 的文档中，对 `connect` 的描述是一段晦涩难懂的英文，在初学 redux 的时候，我对着这段文档阅读了很久，都没有全部弄明白其中的意思（大概就是，单词我都认识，连起来啥意思就不明白了的感觉吧）。

在使用了一段时间 redux 后，本文尝试再次回到这里，给[这段文档](https://github.com/reactjs/react-redux/blob/master/docs/api.md#connectmapstatetoprops-mapdispatchtoprops-mergeprops-options)（同时摘抄在附录中）一个靠谱的解读。

## [](#预备知识 "预备知识")预备知识

首先回顾一下 redux 的基本用法。如果你还没有阅读过 redux 的文档，你一定要先去[阅读一下](https://github.com/reactjs/redux/blob/master/docs/README.md)。

<figure class="highlight jsx">

<table>

<tbody>

<tr>

<td class="gutter">

<pre><span class="line">1</span>  
<span class="line">2</span>  
<span class="line">3</span>  
<span class="line">4</span>  
<span class="line">5</span>  
<span class="line">6</span>  
<span class="line">7</span>  
<span class="line">8</span>  
<span class="line">9</span>  
<span class="line">10</span>  
<span class="line">11</span>  
<span class="line">12</span>  
<span class="line">13</span>  
<span class="line">14</span>  
<span class="line">15</span>  
<span class="line">16</span>  
<span class="line">17</span>  
<span class="line">18</span>  
<span class="line">19</span>  
<span class="line">20</span>  
<span class="line">21</span>  
<span class="line">22</span>  
</pre>

</td>

<td class="code">

<pre><span class="line"><span class="keyword">const</span> reducer = (state = {count: <span class="number">0</span>}, action) => {</span>  
 <span class="line"><span class="keyword">switch</span> (action.type){</span>  
 <span class="line"><span class="keyword">case</span> <span class="string">'INCREASE'</span>: <span class="keyword">return</span> {count: state.count + <span class="number">1</span>};</span>  
 <span class="line"><span class="keyword">case</span> <span class="string">'DECREASE'</span>: <span class="keyword">return</span> {count: state.count - <span class="number">1</span>};</span>  
 <span class="line"><span class="keyword">default</span>: <span class="keyword">return</span> state;</span>  
 <span class="line">}</span>  
<span class="line">}</span>  
<span class="line"></span>  
<span class="line"><span class="keyword">const</span> actions = {</span>  
 <span class="line">increase: () => ({type: <span class="string">'INCREASE'</span>}),</span>  
 <span class="line">decrease: () => ({type: <span class="string">'DECREASE'</span>})</span>  
<span class="line">}</span>  
<span class="line"></span>  
<span class="line"><span class="keyword">const</span> store = createStore(reducer);</span>  
<span class="line"></span>  
<span class="line">store.subscribe(() =></span>  
 <span class="line"><span class="built_in">console</span>.log(store.getState())</span>  
<span class="line">);</span>  
<span class="line"></span>  
<span class="line">store.dispatch(actions.increase()) <span class="comment">// {count: 1}</span></span>  
<span class="line">store.dispatch(actions.increase()) <span class="comment">// {count: 2}</span></span>  
<span class="line">store.dispatch(actions.increase()) <span class="comment">// {count: 3}</span></span>  
</pre>

</td>

</tr>

</tbody>

</table>

</figure>

通过 `reducer` 创建一个 `store`，每当我们在 `store` 上 `dispatch` 一个 `action`，`store` 内的数据就会相应地发生变化。

我们当然可以**直接**在 React 中使用 Redux：在最外层容器组件中初始化 `store`，然后将 `state` 上的属性作为 `props` 层层传递下去。

<figure class="highlight jsx">

<table>

<tbody>

<tr>

<td class="gutter">

<pre><span class="line">1</span>  
<span class="line">2</span>  
<span class="line">3</span>  
<span class="line">4</span>  
<span class="line">5</span>  
<span class="line">6</span>  
<span class="line">7</span>  
<span class="line">8</span>  
<span class="line">9</span>  
<span class="line">10</span>  
<span class="line">11</span>  
<span class="line">12</span>  
<span class="line">13</span>  
</pre>

</td>

<td class="code">

<pre><span class="line"><span class="class"><span class="keyword">class</span> <span class="title">App</span> <span class="keyword">extends</span> <span class="title">Component</span></span>{</span>  
<span class="line"></span>  
 <span class="line">componentWillMount(){</span>  
 <span class="line">store.subscribe((state)=><span class="keyword">this</span>.setState(state))</span>  
 <span class="line">}</span>  
<span class="line"></span>  
 <span class="line">render(){</span>  
 <span class="line"><span class="keyword">return</span> <span class="xml"><span class="tag"><<span class="name">Comp</span> <span class="attr">state</span>=<span class="string">{this.state}</span></span>  
 <span class="line"><span class="attr">onIncrease</span>=<span class="string">{()</span>=></span>store.dispatch(actions.increase())}</span>  
 <span class="line">onDecrease={()=>store.dispatch(actions.decrease())}</span>  
 <span class="line">/></span>  
 <span class="line">}</span>  
<span class="line">}</span></span>  
</pre>

</td>

</tr>

</tbody>

</table>

</figure>

但这并不是最佳的方式。最佳的方式是使用 react-redux 提供的 `Provider` 和 `connect` 方法。

## [](#使用-react-redux "使用 react-redux")使用 react-redux

首先在最外层容器中，把所有内容包裹在 `Provider` 组件中，将之前创建的 `store` 作为 `prop` 传给 `Provider`。

<figure class="highlight jsx">

<table>

<tbody>

<tr>

<td class="gutter">

<pre><span class="line">1</span>  
<span class="line">2</span>  
<span class="line">3</span>  
<span class="line">4</span>  
<span class="line">5</span>  
<span class="line">6</span>  
<span class="line">7</span>  
</pre>

</td>

<td class="code">

<pre><span class="line"><span class="keyword">const</span> App = () => {</span>  
 <span class="line"><span class="keyword">return</span> (</span>  
 <span class="line"><span class="xml"><span class="tag"><<span class="name">Provider</span> <span class="attr">store</span>=<span class="string">{store}</span>></span></span>  
 <span class="line"><span class="tag"><<span class="name">Comp</span>/></span></span>  
 <span class="line"><span class="tag"></<span class="name">Provider</span>></span></span></span>  
 <span class="line">)</span>  
<span class="line">};</span>  
</pre>

</td>

</tr>

</tbody>

</table>

</figure>

`Provider` 内的任何一个组件（比如这里的 `Comp`），如果需要使用 `state` 中的数据，就必须是「被 connect 过的」组件——使用 `connect` 方法对「你编写的组件（`MyComp`）」进行包装后的产物。

<figure class="highlight jsx">

<table>

<tbody>

<tr>

<td class="gutter">

<pre><span class="line">1</span>  
<span class="line">2</span>  
<span class="line">3</span>  
<span class="line">4</span>  
<span class="line">5</span>  
</pre>

</td>

<td class="code">

<pre><span class="line"><span class="class"><span class="keyword">class</span> <span class="title">MyComp</span> <span class="keyword">extends</span> <span class="title">Component</span></span> {</span>  
 <span class="line"><span class="comment">// content...</span></span>  
<span class="line">}</span>  
<span class="line"></span>  
<span class="line"><span class="keyword">const</span> Comp = connect(...args)(MyComp);</span>  
</pre>

</td>

</tr>

</tbody>

</table>

</figure>

可见，`connect` 方法是重中之重。

## [](#connect-详解 "connect 详解")`connect` 详解

究竟 `connect` 方法到底做了什么，我们来一探究竟。

首先看下函数的签名：

> connect([mapStateToProps], [mapDispatchToProps], [mergeProps], [options])

`connect()` 接收四个参数，它们分别是 `mapStateToProps`，`mapDispatchToProps`，`mergeProps`和`options`。

### [](#mapStateToProps-state-ownProps-stateProps "mapStateToProps(state, ownProps) : stateProps")`mapStateToProps(state, ownProps) : stateProps`

这个函数允许我们将 `store` 中的数据作为 `props` 绑定到组件上。

<figure class="highlight jsx">

<table>

<tbody>

<tr>

<td class="gutter">

<pre><span class="line">1</span>  
<span class="line">2</span>  
<span class="line">3</span>  
<span class="line">4</span>  
<span class="line">5</span>  
</pre>

</td>

<td class="code">

<pre><span class="line"><span class="keyword">const</span> mapStateToProps = (state) => {</span>  
 <span class="line"><span class="keyword">return</span> {</span>  
 <span class="line">count: state.count</span>  
 <span class="line">}</span>  
<span class="line">}</span>  
</pre>

</td>

</tr>

</tbody>

</table>

</figure>

这个函数的第一个参数就是 Redux 的 `store`，我们从中摘取了 `count` 属性。因为返回了具有 `count` 属性的对象，所以 `MyComp` 会有名为 `count` 的 `props` 字段。

<figure class="highlight jsx">

<table>

<tbody>

<tr>

<td class="gutter">

<pre><span class="line">1</span>  
<span class="line">2</span>  
<span class="line">3</span>  
<span class="line">4</span>  
<span class="line">5</span>  
<span class="line">6</span>  
<span class="line">7</span>  
</pre>

</td>

<td class="code">

<pre><span class="line"><span class="class"><span class="keyword">class</span> <span class="title">MyComp</span> <span class="keyword">extends</span> <span class="title">Component</span></span> {</span>  
 <span class="line">render(){</span>  
 <span class="line"><span class="keyword">return</span> <span class="xml"><span class="tag"><<span class="name">div</span>></span>计数：{this.props.count}次<span class="tag"></<span class="name">div</span>></span></span></span>  
 <span class="line">}</span>  
<span class="line">}</span>  
<span class="line"></span>  
<span class="line"><span class="keyword">const</span> Comp = connect(...args)(MyComp);</span>  
</pre>

</td>

</tr>

</tbody>

</table>

</figure>

当然，你不必将 `state` 中的数据原封不动地传入组件，可以根据 `state` 中的数据，动态地输出组件需要的（最小）属性。

<figure class="highlight jsx">

<table>

<tbody>

<tr>

<td class="gutter">

<pre><span class="line">1</span>  
<span class="line">2</span>  
<span class="line">3</span>  
<span class="line">4</span>  
<span class="line">5</span>  
</pre>

</td>

<td class="code">

<pre><span class="line"><span class="keyword">const</span> mapStateToProps = (state) => {</span>  
 <span class="line"><span class="keyword">return</span> {</span>  
 <span class="line">greaterThanFive: state.count > <span class="number">5</span></span>  
 <span class="line">}</span>  
<span class="line">}</span>  
</pre>

</td>

</tr>

</tbody>

</table>

</figure>

函数的第二个参数 `ownProps`，是 `MyComp` 自己的 `props`。有的时候，`ownProps` 也会对其产生影响。比如，当你在 `store` 中维护了一个用户列表，而你的组件 `MyComp` 只关心一个用户（通过 `props` 中的 `userId` 体现）。

<figure class="highlight jsx">

<table>

<tbody>

<tr>

<td class="gutter">

<pre><span class="line">1</span>  
<span class="line">2</span>  
<span class="line">3</span>  
<span class="line">4</span>  
<span class="line">5</span>  
<span class="line">6</span>  
<span class="line">7</span>  
<span class="line">8</span>  
<span class="line">9</span>  
<span class="line">10</span>  
<span class="line">11</span>  
<span class="line">12</span>  
<span class="line">13</span>  
<span class="line">14</span>  
<span class="line">15</span>  
<span class="line">16</span>  
<span class="line">17</span>  
<span class="line">18</span>  
<span class="line">19</span>  
<span class="line">20</span>  
</pre>

</td>

<td class="code">

<pre><span class="line"><span class="keyword">const</span> mapStateToProps = (state, ownProps) => {</span>  
 <span class="line"><span class="comment">// state 是 {userList: [{id: 0, name: '王二'}]}</span></span>  
 <span class="line"><span class="keyword">return</span> {</span>  
 <span class="line">user: _.find(state.userList, {id: ownProps.userId})</span>  
 <span class="line">}</span>  
<span class="line">}</span>  
<span class="line"></span>  
<span class="line"><span class="class"><span class="keyword">class</span> <span class="title">MyComp</span> <span class="keyword">extends</span> <span class="title">Component</span></span> {</span>  
 <span class="line"></span>   
 <span class="line"><span class="keyword">static</span> PropTypes = {</span>  
 <span class="line">userId: PropTypes.string.isRequired,</span>  
 <span class="line">user: PropTypes.object</span>  
 <span class="line">};</span>  
 <span class="line"></span>   
 <span class="line">render(){</span>  
 <span class="line"><span class="keyword">return</span> <span class="xml"><span class="tag"><<span class="name">div</span>></span>用户名：{this.props.user.name}<span class="tag"></<span class="name">div</span>></span></span></span>  
 <span class="line">}</span>  
<span class="line">}</span>  
<span class="line"></span>  
<span class="line"><span class="keyword">const</span> Comp = connect(mapStateToProps)(MyComp);</span>  
</pre>

</td>

</tr>

</tbody>

</table>

</figure>

当 `state` 变化，或者 `ownProps` 变化的时候，`mapStateToProps` 都会被调用，计算出一个新的 `stateProps`，（在与 `ownProps` merge 后）更新给 `MyComp`。

这就是将 Redux `store` 中的数据连接到组件的基本方式。

### [](#mapDispatchToProps-dispatch-ownProps-dispatchProps "mapDispatchToProps(dispatch, ownProps): dispatchProps")`mapDispatchToProps(dispatch, ownProps): dispatchProps`

`connect` 的第二个参数是 `mapDispatchToProps`，它的功能是，将 action 作为 `props` 绑定到 `MyComp` 上。

<figure class="highlight jsx">

<table>

<tbody>

<tr>

<td class="gutter">

<pre><span class="line">1</span>  
<span class="line">2</span>  
<span class="line">3</span>  
<span class="line">4</span>  
<span class="line">5</span>  
<span class="line">6</span>  
<span class="line">7</span>  
<span class="line">8</span>  
<span class="line">9</span>  
<span class="line">10</span>  
<span class="line">11</span>  
<span class="line">12</span>  
<span class="line">13</span>  
<span class="line">14</span>  
<span class="line">15</span>  
<span class="line">16</span>  
<span class="line">17</span>  
<span class="line">18</span>  
<span class="line">19</span>  
</pre>

</td>

<td class="code">

<pre><span class="line"><span class="keyword">const</span> mapDispatchToProps = (dispatch, ownProps) => {</span>  
 <span class="line"><span class="keyword">return</span> {</span>  
 <span class="line">increase: (...args) => dispatch(actions.increase(...args)),</span>  
 <span class="line">decrease: (...args) => dispatch(actions.decrease(...args))</span>  
 <span class="line">}</span>  
<span class="line">}</span>  
<span class="line"></span>  
<span class="line"><span class="class"><span class="keyword">class</span> <span class="title">MyComp</span> <span class="keyword">extends</span> <span class="title">Component</span></span> {</span>  
 <span class="line">render(){</span>  
 <span class="line"><span class="keyword">const</span> {count, increase, decrease} = <span class="keyword">this</span>.props;</span>  
 <span class="line"><span class="keyword">return</span> (<span class="xml"><span class="tag"><<span class="name">div</span>></span></span>  
 <span class="line"><span class="tag"><<span class="name">div</span>></span>计数：{this.props.count}次<span class="tag"></<span class="name">div</span>></span></span>  
 <span class="line"><span class="tag"><<span class="name">button</span> <span class="attr">onClick</span>=<span class="string">{increase}</span>></span>增加<span class="tag"></<span class="name">button</span>></span></span>  
 <span class="line"><span class="tag"><<span class="name">button</span> <span class="attr">onClick</span>=<span class="string">{decrease}</span>></span>减少<span class="tag"></<span class="name">button</span>></span></span>  
 <span class="line"><span class="tag"></<span class="name">div</span>></span></span>)</span>  
 <span class="line">}</span>  
<span class="line">}</span>  
<span class="line"></span>  
<span class="line"><span class="keyword">const</span> Comp = connect(mapStateToProps， mapDispatchToProps)(MyComp);</span>  
</pre>

</td>

</tr>

</tbody>

</table>

</figure>

由于 `mapDispatchToProps` 方法返回了具有 `increase` 属性和 `decrease` 属性的对象，这两个属性也会成为 `MyComp` 的 `props`。

如上所示，调用 `actions.increase()` 只能得到一个 `action` 对象 `{type:'INCREASE'}`，要触发这个 `action` 必须在 `store` 上调用 `dispatch` 方法。`diapatch` 正是 `mapDispatchToProps` 的第一个参数。但是，为了不让 `MyComp` 组件感知到 `dispatch` 的存在，我们需要将 `increase` 和 `decrease` 两个函数包装一下，使之成为直接可被调用的函数（即，调用该方法就会触发 `dispatch`）。

Redux 本身提供了 `bindActionCreators` 函数，来将 action 包装成直接可被调用的函数。

<figure class="highlight jsx">

<table>

<tbody>

<tr>

<td class="gutter">

<pre><span class="line">1</span>  
<span class="line">2</span>  
<span class="line">3</span>  
<span class="line">4</span>  
<span class="line">5</span>  
<span class="line">6</span>  
<span class="line">7</span>  
<span class="line">8</span>  
</pre>

</td>

<td class="code">

<pre><span class="line"><span class="keyword">import</span> {bindActionCreators} <span class="keyword">from</span> <span class="string">'redux'</span>;</span>  
<span class="line"></span>  
<span class="line"><span class="keyword">const</span> mapDispatchToProps = (dispatch, ownProps) => {</span>  
 <span class="line"><span class="keyword">return</span> bindActionCreators({</span>  
 <span class="line">increase: action.increase,</span>  
 <span class="line">decrease: action.decrease</span>  
 <span class="line">});</span>  
<span class="line">}</span>  
</pre>

</td>

</tr>

</tbody>

</table>

</figure>

同样，当 `ownProps` 变化的时候，该函数也会被调用，生成一个新的 `dispatchProps`，（在与 `statePrope` 和 `ownProps` merge 后）更新给 `MyComp`。注意，`action` 的变化不会引起上述过程，默认 `action` 在组件的生命周期中是固定的。

### [](#mergeProps-stateProps-dispatchProps-ownProps-props "[mergeProps(stateProps, dispatchProps, ownProps): props]")`[mergeProps(stateProps, dispatchProps, ownProps): props]`

之前说过，不管是 `stateProps` 还是 `dispatchProps`，都需要和 `ownProps` merge 之后才会被赋给 `MyComp`。`connect` 的第三个参数就是用来做这件事。通常情况下，你可以不传这个参数，`connect` 就会使用 `Object.assign` 替代该方法。

### [](#其他 "其他")其他

最后还有一个 `options` 选项，比较简单，基本上也不大会用到（尤其是你遵循了其他的一些 React 的「最佳实践」的时候），本文就略过了。希望了解的同学可以直接看文档。

（完）

## [](#附：connect-方法的官方英文文档 "附：connect 方法的官方英文文档")附：connect 方法的官方英文文档

> #### [](#connect-mapStateToProps-mapDispatchToProps-mergeProps-options "connect([mapStateToProps], [mapDispatchToProps], [mergeProps], [options])")`connect([mapStateToProps], [mapDispatchToProps], [mergeProps], [options])`
> 
> Connects a React component to a Redux store.
> 
> It does not modify the component class passed to it. Instead, it returns a new, connected component class, for you to use.
> 
> #### [](#Arguments "Arguments")Arguments
> 
> *   [mapStateToProps(state, [ownProps]): stateProps] (Function): If specified, the component will subscribe to Redux store updates. Any time it updates, mapStateToProps will be called. Its result must be a plain object*, and it will be merged into the component’s props. If you omit it, the component will not be subscribed to the Redux store. If ownProps is specified as a second argument, its value will be the props passed to your component, and mapStateToProps will be additionally re-invoked whenever the component receives new props (e.g. if props received from a parent component have shallowly changed, and you use the ownProps argument, mapStateToProps is re-evaluated).
>     
>     
> *   [mapDispatchToProps(dispatch, [ownProps]): dispatchProps] (Object or Function): If an object is passed, each function inside it will be assumed to be a Redux action creator. An object with the same function names, but with every action creator wrapped into a dispatch call so they may be invoked directly, will be merged into the component’s props. If a function is passed, it will be given dispatch. It’s up to you to return an object that somehow uses dispatch to bind action creators in your own way. (Tip: you may use the bindActionCreators() helper from Redux.) If you omit it, the default implementation just injects dispatch into your component’s props. If ownProps is specified as a second argument, its value will be the props passed to your component, and mapDispatchToProps will be re-invoked whenever the component receives new props.
>     
>     
> *   [mergeProps(stateProps, dispatchProps, ownProps): props] (Function): If specified, it is passed the result of mapStateToProps(), mapDispatchToProps(), and the parent props. The plain object you return from it will be passed as props to the wrapped component. You may specify this function to select a slice of the state based on props, or to bind action creators to a particular variable from props. If you omit it, Object.assign({}, ownProps, stateProps, dispatchProps) is used by default.
>     
>     
> *   [options] (Object) If specified, further customizes the behavior of the connector.
>     
>     
>     *   [pure = true] (Boolean): If true, implements shouldComponentUpdate and shallowly compares the result of mergeProps, preventing unnecessary updates, assuming that the component is a “pure” component and does not rely on any input or state other than its props and the selected Redux store’s state. Defaults to true.
>     *   [withRef = false] (Boolean): If true, stores a ref to the wrapped component instance and makes it available via getWrappedInstance() method. Defaults to false.

