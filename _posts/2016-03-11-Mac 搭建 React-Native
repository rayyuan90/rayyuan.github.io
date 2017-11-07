

# Mac搭建 React Native 工具篇Atom＋Nuclide



*   标签：
*   [atom](http://so.csdn.net/so/search/s.do?q=atom&t=blog) <span>/</span>
*   [mac](http://so.csdn.net/so/search/s.do?q=mac&t=blog) <span>/</span>
*   [native](http://so.csdn.net/so/search/s.do?q=native&t=blog) <span>/</span>

*   <button class="btn-noborder"><span class="txt">2944</span></button>
*   <a class="btn-noborder" href=""><span class="txt">编辑</span></a>
*   <a class="btn-noborder" onclick="javascript:deleteArticle(fileName);return false;"><span class="txt">删除</span></a>




关于如何在mac下搭建React环境这里就不详细介绍了，有兴趣的朋友可以看：[在Mac上搭建RN基础环境](http://blog.csdn.net/xiangzhihong8/article/details/53914336)，今天要说的是如何在mac下使用Atom＋Nuclide组合环境来开发项目。

## 安装Atom

如果没有的大家可以到官网下载：[https://atom.io/](https://atom.io/)，也可以到国内的镜像地址下载：[https://npm.taobao.org/mirrors/atom/1.7.2/](https://npm.taobao.org/mirrors/atom/1.7.2/)  
![这里写图片描述](http://img.blog.csdn.net/20170315223415570?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhbmd6aGlob25nOA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

解压atom，打开atom，你看到的界面应该是这样的 。

![这里写图片描述](http://img.blog.csdn.net/20170315223817447?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhbmd6aGlob25nOA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

## 安装Nuclide

安装Nuclide插件有两种方式。

### 1.图形化安装：

点击菜单栏：Atom->Preferences,或者可以”Command+,”，或者快捷键打开。然后，在Install Packets的输入框中，输入nuclide，出现的第一个就是我们想要安装的，点击install 。  
![这里写图片描述](http://img.blog.csdn.net/20170315224248480?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhbmd6aGlob25nOA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

安装完成之后，在工具栏多了一个Nuclide栏。

![这里写图片描述](http://img.blog.csdn.net/20170315224439168?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhbmd6aGlob25nOA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

默认安装nuclide之后，会安装一大堆的依赖包，如果没有默认安装这些依赖包，可以选中,Packages->Settings View->Manage Packets

![这里写图片描述](http://img.blog.csdn.net/20170315224730935?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhbmd6aGlob25nOA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

搜索nuclide，再nuclide package上双击，进入设置，勾选Install recommended packets on startup 。

![这里写图片描述](http://img.blog.csdn.net/20170315224859682?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhbmd6aGlob25nOA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

最后重启atom，就可以看到nuclide插件了。

### 命令行安装：

安装命令，对应的git[https://github.com/atom/apm](https://github.com/atom/apm)：

    apm install nuclide

命令行安装完成后，打开Atom，选择Packages->Settings View->Manage Packets ， 然后选择Packages，Nuclide中点击Settings。

![这里写图片描述](http://img.blog.csdn.net/20170315225127922?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhbmd6aGlob25nOA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

勾选Install recommended packets on startup 。

![这里写图片描述](http://img.blog.csdn.net/20170315225206063?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhbmd6aGlob25nOA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

## 在Nuclide运行项目

第一步，运行react native packager。点击 command + shift + p打开command palette（打开终端选项），然后输入：

    react native start

![这里写图片描述](http://img.blog.csdn.net/20170316123216148?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhbmd6aGlob25nOA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

选择Nuclide React Native :Start packager。

当然我们也可以使用Nuclide的图形化界面。

![这里写图片描述](http://img.blog.csdn.net/20170317142213762?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhbmd6aGlob25nOA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

注：常见错误：

    /Users/huangwenchen/Desktop/Demo/node_modules/react-native/local-cli/cli.js:123
    class CreateSuppressingTerminalAdapter extends TerminalAdapter {
    ^^^^^
    SyntaxError: Unexpected reserved word
        at exports.runInThisContext (vm.js:73:16)
        at Module._compile (module.js:443:25)
        at Object.Module._extensions..js (module.js:478:10)
        at Module.load (module.js:355:32)
        at Function.Module._load (module.js:310:12)
        at Function.Module.runMain (module.js:501:10)
        at startup (node.js:129:16)
        at node.js:814:3

说明你node的版本太低,运行以下命令更新。

    sudo npm cache clean -f
    sudo npm install -g n
    sudo n stable

第二步，终端运行项目 。  
cd到项目目录，执行。

    $ react-native run-ios
    $ react-native run-android

![这里写图片描述](http://img.blog.csdn.net/20170316125157928?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhbmd6aGlob25nOA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

## navigator实例

首先先来看一下效果图。  
![这里写图片描述](http://img.blog.csdn.net/20170317142755904?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhbmd6aGlob25nOA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

导入react-native-tab-navigator框架，在项目目录下：

    npm install react-native-tab-navigator –save

然后在项目中引入：

    import TabNavigator from 'react-native-tab-navigator';

完整代码：

    /**
     * Sample React Native App
     * https://github.com/facebook/react-native
     * @flow
     */

    import React, { Component } from 'react';
    import {
      AppRegistry,
      StyleSheet,
      Text,
      View,
      Image
    } from 'react-native';

    import TabNavigator from 'react-native-tab-navigator';

    export default class Shop extends Component {

      constructor(props) {
              super(props);
              this.state={
                  selectedTab:'home'//默认选中home
              }
          }

      render() {

        var homeView=(
                    <View style={[styles.flex,styles.center,{backgroundColor: '#ffff0044'}]}>
                        <Text style={{fontSize: 30}}>首页</Text>
                    </View>
                );
                var settingView=(
                    <View style={[styles.flex,styles.center,{backgroundColor: '#ffff0044'}]}>
                        <Text style={{fontSize: 30}}>设置</Text>
                    </View>
                );

        return (

             <TabNavigator
                   tabBarStyle={{ height: 70 }}
               >
                   <TabNavigator.Item
                       selected={this.state.selectedTab === 'home'}
                       title="首页" //Tab文字
                       renderIcon={() => <Image style={styles.img} source={require('./image/tab_message_n.png') }/>}//默认图标
                       renderSelectedIcon={() => <Image style={styles.img} source={require('./image/tab_message_n.png') }/>}//选中图标
                       badgeText="9+"//消息数目
                       onPress={() => this.setState({ selectedTab: 'home' })}
                   >
                       {homeView}
                   </TabNavigator.Item>
                   <TabNavigator.Item
                       selected={this.state.selectedTab === 'setting'}
                       title="设置"
                       renderIcon={() => <Image style={styles.img} source={require('./image/tab_mine_n.png') }/>}
                       renderSelectedIcon={() => <Image style={styles.img} source={require('./image/tab_mine_p.png') }/>}
                       onPress={() => this.setState({ selectedTab: 'setting' })}
                   >
                       {settingView}
                   </TabNavigator.Item>
               </TabNavigator>
        );
      }
    }

    const styles = StyleSheet.create({
      flex:{
            flex:1,
        },
        center:{
            justifyContent:'center',
            alignItems:'center'
        },
        img: {
            width: 45,
                height: 35,
        },
    });

    AppRegistry.registerComponent('Shop', () => Shop);

注：项目所用的图片放在image/*下。

<link rel="stylesheet" href="http://static.blog.csdn.net/public/res-min/markdown_views.css?v=2.0"></div>

<link rel="stylesheet" href="http://static.blog.csdn.net/public/res-min/markdown_views.css?v=2.0"></div>

</article>

<div class="readall_box csdn-tracking-statistics" data-mod="popu_376"><a class="btn btn-large btn-gray-fred read_more_btn" target="_self">阅读全文</a></div>

<div class="article_copyright">版权声明：本文为博主原创文章，未经博主允许不得转载。</div>

*   本文已收录于以下专栏：
*   [React Native](http://blog.csdn.net/column/details/reactnative-android.html)

<div class="comment_box clearfix">

<div id="comment_form">

<div id="commentsbmitarear">

<div class="comment_area clearfix">

<div class="userimg">[](http://my.csdn.net/)</div>

<form action="/xiangzhihong8/comment/submit?id=62246950" method="post" onsubmit="return subform(this);" id="commentform"><textarea class="comment_content" name="comment_content" id="comment_content" placeholder="发表你的评论"></textarea>

<div class="bot_bar clearfix">

<div id="ubbtools" class="add_code">[](#insertcode)</div>

<input type="hidden" id="comment_replyId" name="comment_replyId"> <input type="hidden" id="comment_userId" name="comment_userId" value=""> <input type="hidden" id="commentId" name="commentId" value=""> <input type="submit" class="btn btn-redborder" value="发表评论"> <span id="tip_comment" class="tip">

<div style="display: none;" class="csdn-tracking-statistics" data-mod="popu_384">[发表评论](#)</div>

<div id="lang_list" code="code">[HTML/XML](#html) [objective-c](#objc) [Delphi](#delphi) [Ruby](#ruby) [PHP](#php) [C#](#csharp) [C++](#cpp) [JavaScript](#javascript) [Visual Basic](#vb) [Python](#python) [Java](#java) [CSS](#css) [SQL](#sql) [其它](#plain)<span class="arrb"></span></div>

</span></div>

</form>

</div>

</div>

</div>

</div>

### 相关文章推荐

<div class="recommend_list clearfix">

<dl class="clearfix csdn-tracking-statistics" data-mod="popu_387" data-poputype="feed" data-feed-show="false" data-dsm="post">

<dd>

## [React Native开发之IDE（Atom+Nuclide）安装，运行，调试](/hello_hwc/article/details/51612139)

<div class="summary">欢迎Follow我的Github，博客会同步在Github的Blog仓库更新。也可以关注CSDN博客的React Native分类 LeoMobileDeveloper 前言 工欲善其事，必先利...</div>

*   [![Hello_Hwc](http://avatar.csdn.net/C/3/C/2_hello_hwc.jpg "Hello_Hwc")](http://blog.csdn.net/Hello_Hwc)
*   [Hello_Hwc](http://blog.csdn.net/Hello_Hwc)
*   2016-06-08 13:32
*   <span>43651</span>

</dd>

</dl>

<dl class="clearfix csdn-tracking-statistics" data-mod="popu_387" data-poputype="feed" data-feed-show="false" data-dsm="post">

<dd>

## [xcode 也有atom 装逼插件activate-power-mode](/ruglcc/article/details/50175105)

<div class="summary">引言 上一篇   装逼文本编辑器Atom + activate-power-mode插件 后，博主也发现在xcode下也有这么一个插件。 让我们在xcode下一起装逼吧~~ xcode 下 ...</div>

*   [![ruglcc](http://avatar.csdn.net/D/F/4/2_ruglcc.jpg "ruglcc")](http://blog.csdn.net/ruglcc)
*   [ruglcc](http://blog.csdn.net/ruglcc)
*   2015-12-04 15:06
*   <span>6486</span>

</dd>

</dl>

<script>(function() { var s = "_" + Math.random().toString(36).slice(2); document.write('<div id="' + s + '"></div>'); (window.slotbydup=window.slotbydup || []).push({ id: '4765209', container: s, size: '808,120', display: 'inlay-fix' }); })();</script>

<dl class="clearfix csdn-tracking-statistics" data-mod="popu_387" data-poputype="feed" data-feed-show="false" data-dsm="post">

<dd>

## [从零开始学React Native App开发](/chenbifeng/article/details/51496548)

<div class="summary">目录 1\. React Native简介      1.1 从何而来，背景介绍      1.2 为什么要使用React Native开发      1.3 环境搭建  ...</div>

*   [![chenbifeng](http://avatar.csdn.net/5/C/F/2_chenbifeng.jpg "chenbifeng")](http://blog.csdn.net/chenbifeng)
*   [chenbifeng](http://blog.csdn.net/chenbifeng)
*   2016-05-25 11:22
*   <span>12802</span>

</dd>

</dl>

<dl class="clearfix csdn-tracking-statistics" data-mod="popu_387" data-poputype="feed" data-feed-show="false" data-dsm="post">

<dd>

## [React Native Mac OS X 开发环境搭建](/u014484863/article/details/51550115)

<div class="summary">React Native Mac OS X 开发环境搭建(一)前言FaceBook早期开源发布了React Native For iOS,在2015年9月15日也发布了React Native For...</div>

*   [![u014484863](http://avatar.csdn.net/1/C/A/2_u014484863.jpg "u014484863")](http://blog.csdn.net/u014484863)
*   [u014484863](http://blog.csdn.net/u014484863)
*   2016-05-31 23:15
*   <span>1365</span>

</dd>

</dl>

<dl class="clearfix csdn-tracking-statistics" data-mod="popu_387" data-poputype="feed" data-feed-show="false" data-dsm="post">

<dd>

## [React Native常用IDE推荐与安装配置](/u014484863/article/details/51554428)

<div class="summary">React Native常用IDE推荐与安装配置（一）前言 上一讲提到了React Native框架安装和运行,以及创建了一个项目并介绍这个项目结构。这样介绍项目项目结构其实极其不方便，这一节将介绍...</div>

*   [![u014484863](http://avatar.csdn.net/1/C/A/2_u014484863.jpg "u014484863")](http://blog.csdn.net/u014484863)
*   [u014484863](http://blog.csdn.net/u014484863)
*   2016-06-01 11:05
*   <span>17168</span>

</dd>

</dl>

<dl class="clearfix csdn-tracking-statistics" data-mod="popu_387" data-poputype="feed" data-feed-show="false" data-dsm="post">

<dd>

## [Atom编辑器入门到精通(五) Git支持](/u010494080/article/details/51229211)

<div class="summary">版本控制对于开发来说非常重要,Atom当然也提供了很好的支持,本文将介绍如何在Atom中集成使用Git和GitHub</div>

*   [![u010494080](http://avatar.csdn.net/C/4/9/2_u010494080.jpg "u010494080")](http://blog.csdn.net/u010494080)
*   [u010494080](http://blog.csdn.net/u010494080)
*   2016-04-23 23:58
*   <span>14688</span>

</dd>

</dl>

<dl class="clearfix csdn-tracking-statistics" data-mod="popu_387" data-poputype="feed" data-feed-show="false" data-dsm="post">

<dd>

## [Atom编辑器入门到精通(二) 插件的安装和管理](/u010494080/article/details/50605654)

<div class="summary">在本节中我们会学习如果安装和使用插件 插件是Atom中一个非常重要的组成部分,很多功能都是以插件形式存在的,比如上篇文章中提到的目录树窗口和设置窗口都是利用默认安装的插件来实现的</div>

*   [![u010494080](http://avatar.csdn.net/C/4/9/2_u010494080.jpg "u010494080")](http://blog.csdn.net/u010494080)
*   [u010494080](http://blog.csdn.net/u010494080)
*   2016-01-29 10:35
*   <span>21871</span>

</dd>

</dl>

<dl class="clearfix csdn-tracking-statistics" data-mod="popu_387" data-poputype="feed" data-feed-show="false" data-dsm="post">

<dd>

## [mac osx 下 安装atom github官方出品的开发工具](/baidu_16051437/article/details/51204772)

<div class="summary">MAC OSX 下安装官方GITHUB地址国内镜像下载更快下载安装好 开始配置包管理器apm使用apm install --check检测安装源是否正常Checking for native buil...</div>

*   [![baidu_16051437](http://avatar.csdn.net/F/4/A/2_baidu_16051437.jpg "baidu_16051437")](http://blog.csdn.net/baidu_16051437)
*   [baidu_16051437](http://blog.csdn.net/baidu_16051437)
*   2016-04-20 23:01
*   <span>4589</span>

</dd>

</dl>

<dl class="clearfix csdn-tracking-statistics" data-mod="popu_387" data-poputype="feed" data-feed-show="false" data-dsm="post">

<dd>

## [Emmet for Dreamweaver：HTML/CSS代码快速编写神器](/ys743276112/article/details/38133995)

<div class="summary">Emmet的前身是大名鼎鼎的Zen coding，如果你从事Web前端开发的话，对该插件一定不会陌生。它使用仿CSS选择器的语法来生成代码，大大提高了HTML/CSS代码编写的速度，比如下面的演示： ...</div>

*   [![ys743276112](http://avatar.csdn.net/8/3/1/2_ys743276112.jpg "ys743276112")](http://blog.csdn.net/ys743276112)
*   [ys743276112](http://blog.csdn.net/ys743276112)
*   2014-07-26 00:17
*   <span>9679</span>

</dd>

</dl>

</div>

</main>

<aside>

<div class="right_box user_info">

<dl class="inf_bar clearfix">

<dt class="csdn-tracking-statistics" data-mod="popu_381">[![](http://avatar.csdn.net/E/D/2/1_xiangzhihong8.jpg) ](http://blog.csdn.net/xiangzhihong8) <span class="medals" title=""></span> </dt>

<dd>

### [xiangzhihong8](http://blog.csdn.net/xiangzhihong8)

<span class="csdn-tracking-statistics" data-mod="popu_379"><a class="btn btn-redborder-small " id="span_add_follow" target="_self">＋关注</a></span></dd>

</dl>

<div class="inf_number_box clearfix">

<dl>

<dt>原创</dt>

<dd>725</dd>

</dl>

<dl>

<dt>粉丝</dt>

<dd id="fan">1417</dd>

</dl>

<dl>

<dt>喜欢</dt>

<dd>0</dd>

</dl>

<dl>

<dt>码云</dt>

</dl>

</div>

<div class="writings">

<div class="public_signal clearfix">

### 他的最新文章

[<span>更多文章</span>](http://blog.csdn.net/xiangzhihong8)</div>

*   [一个ClassLoader引起的JNI链接错误](/xiangzhihong8/article/details/78455515)
*   [腾讯前端面试题集锦](/xiangzhihong8/article/details/78441626)
*   [mac环境下mongodb的安装和使用](/xiangzhihong8/article/details/78423983)
*   [HTTPS加密协议详解](/xiangzhihong8/article/details/78418226)

</div>

</div>

<div class="extension_other csdn-tracking-statistics" data-mod="popu_389">

<div class="flashrecommend"><script>(function() { var s = "_" + Math.random().toString(36).slice(2); document.write('<div id="' + s + '"></div>'); (window.slotbydup=window.slotbydup || []).push({ id: '4770930', container: s, size: '300,250', display: 'inlay-fix' }); })();</script></div>

</div>

<div class="host-column">

### 博主专栏

*   <div class="img list-left">[![](http://img.blog.csdn.net/20161125211524891)

    <div>12</div>

    ](http://blog.csdn.net/column/details/13695.html)</div>

    <div class="content list-left">

    #### [大数据](http://blog.csdn.net/column/details/13695.html)

    <div class="read list-left"><span>77661</span></div>

    </div>

*   <div class="img list-left">[![](http://img.blog.csdn.net/20161107200646656)

    <div>28</div>

    ](http://blog.csdn.net/column/details/13460.html)</div>

    <div class="content list-left">

    #### [ios开发大揭秘](http://blog.csdn.net/column/details/13460.html)

    <div class="read list-left"><span>55278</span></div>

    </div>

*   <div class="img list-left">[![](http://img.blog.csdn.net/20161013090412178)

    <div>30</div>

    ](http://blog.csdn.net/column/details/13180.html)</div>

    <div class="content list-left">

    #### [前端](http://blog.csdn.net/column/details/13180.html)

    <div class="read list-left"><span>116384</span></div>

    </div>

*   <div class="img list-left">[![](http://img.blog.csdn.net/20160724093143731)

    <div>31</div>

    ](http://blog.csdn.net/column/details/framwork.html)</div>

    <div class="content list-left">

    #### [深入Android Framwork](http://blog.csdn.net/column/details/framwork.html)

    <div class="read list-left"><span>103684</span></div>

    </div>

*   <div class="img list-left">[![](http://img.blog.csdn.net/20160724094135635)

    <div>86</div>

    ](http://blog.csdn.net/column/details/reactnative-android.html)</div>

    <div class="content list-left">

    #### [React Native](http://blog.csdn.net/column/details/reactnative-android.html)

    <div class="read list-left"><span>280006</span></div>

    </div>

*   <div class="img list-left">[![](http://img.blog.csdn.net/20160614090418838)

    <div>25</div>

    ](http://blog.csdn.net/column/details/design-mode.html)</div>

    <div class="content list-left">

    #### [设计模式](http://blog.csdn.net/column/details/design-mode.html)

    <div class="read list-left"><span>36165</span></div>

    </div>

*   <div class="img list-left">[![](http://img.blog.csdn.net/20160605192107879)

    <div>24</div>

    ](http://blog.csdn.net/column/details/java88.html)</div>

    <div class="content list-left">

    #### [开发语言系列](http://blog.csdn.net/column/details/java88.html)

    <div class="read list-left"><span>51538</span></div>

    </div>

*   <div class="img list-left">[![](http://img.blog.csdn.net/20170929103257931)

    <div>14</div>

    ](http://blog.csdn.net/column/details/myelicpse.html)</div>

    <div class="content list-left">

    #### [Weex和Vue](http://blog.csdn.net/column/details/myelicpse.html)

    <div class="read list-left"><span>44121</span></div>

    </div>

*   <div class="img list-left">[![](http://img.blog.csdn.net/20160531115534529)

    <div>22</div>

    ](http://blog.csdn.net/column/details/algorithm-struct.html)</div>

    <div class="content list-left">

    #### [数据结构与算法](http://blog.csdn.net/column/details/algorithm-struct.html)

    <div class="read list-left"><span>73955</span></div>

    </div>

*   <div class="img list-left">[![](http://img.blog.csdn.net/20160531112801863)

    <div>100</div>

    ](http://blog.csdn.net/column/details/laoshiji.html)</div>

    <div class="content list-left">

    #### [android开发大揭秘](http://blog.csdn.net/column/details/laoshiji.html)

    <div class="read list-left"><span>270751</span></div>

    </div>

<div class="unfold-btn"><span>展开</span></div>

</div>

<div class="fixRight">

<div class="right_box padb0 csdn-tracking-statistics" data-mod="popu_391">

### <span>_在线课程_</span>

*   <div>[![免费直播 神经网络的原理及结构设计](http://img.bss.csdn.net/201711061712351663.png "免费直播 神经网络的原理及结构设计")](http://edu.csdn.net/huiyiCourse/detail/596?utm_source=blog7) </div>

    <div>

    [免费直播 神经网络的原理及结构设计](http://edu.csdn.net/huiyiCourse/detail/596?utm_source=blog7)

    讲师：何宇健

    </div>

*   <div>[![Apache Weex：移动研发的进阶之路](http://img.bss.csdn.net/201711061707038235.png "Apache Weex：移动研发的进阶之路")](http://edu.csdn.net/huiyiCourse/detail/602?utm_source=blog7) </div>

    <div>

    [Apache Weex：移动研发的进阶之路](http://edu.csdn.net/huiyiCourse/detail/602?utm_source=blog7)

    讲师：董岩

    </div>

</div>

</div>

<div class="user-hotArticle">

### 热门文章

*   [“区块链”究竟是什么鬼](/xiangzhihong8/article/details/53312278)

    <div class="read list-left"><span>20090</span></div>

*   [React Native运行原理解析](/xiangzhihong8/article/details/52623852)

    <div class="read list-left"><span>18204</span></div>

*   [android 仿音悦台页面交互效果](/xiangzhihong8/article/details/54098508)

    <div class="read list-left"><span>17921</span></div>

*   [在Windows下搭建Gitlab服务器](/xiangzhihong8/article/details/52098015)

    <div class="read list-left"><span>15791</span></div>

*   [WebStorm开发工具设置React Native智能提示](/xiangzhihong8/article/details/52224527)

    <div class="read list-left"><span>15703</span></div>

</div>

</aside>

</div>

<div class="left_fixed">

<div class="left_show_button"><span></span></div>

*   <button class="left-fixed-btn btn-like csdn-tracking-statistics" data-mod="popu_373" target="_self"><span class="iconbox border_red"></span><span class="txt">1</span></button>
*   <button class="left-fixed-btn left_menu_btn csdn-tracking-statistics" data-mod="popu_372" target="_self"><span class="iconbox border_black"></span></button>

*   <button class="left-fixed-btn csdn-tracking-statistics" data-mod="popu_374" id="com-quick-collect" target="_self"><span class="iconbox border_purple"></span></button>
*   <button class="left-fixed-btn btn-pinglun"><span class="iconbox border_purple"></span></button>
*   <button class="left-fixed-btn  csdn-tracking-statistics" data-mod="popu_375" target="_self"><span class="iconbox border_orange"></span></button>

    <div class="bdsharebuttonbox csdn-tracking-statistics" data-mod="popu_172">

    <div class="outside"><span class="iconbox border_red2"></span>[](# "分享到新浪微博")</div>

    <div class="outside"><span class="iconbox border_green"></span>[](# "分享到微信")</div>

    <div class="outside"><span class="iconbox border_blue"></span>[](# "分享到QQ空间")</div>

    </div>

</div>

<div class="right_fixed">

<div class="r_ico"><span class="txt" id="reportBtn">内容举报</span></div>

<div class="returnTop"><span>返回顶部</span></div>

</div>

<div class="pop pop_CA">

<div class="CA_header">收藏助手<span class="cancel_icon" id="fapancle"></span></div>

<iframe src="" id="collectIframe" frameborder="0" width="100%" height="360" scrolling="no"></iframe></div>

<div id="report_dialog" style="top: 250px; left: 343.5px;">

<div id="panel_report">

<div class="panel_head">不良信息举报</div>

<form method="post" id="frmReport" class="panel_body">

<table border="0" cellpadding="0" cellspacing="4" class="pop_table">

<tbody>

<tr>

<td colspan="2">您举报文章：[深度学习：神经网络中的前向传播和反向传播算法推导](http://blog.csdn.net/raintungli/article/details/76583070)</td>

</tr>

<tr>

<th style="width:60px;">举报原因：</th>

<td id="panel_reporttype"><label><input type="radio" class="report_type" id="report_sex" name="report_type" value="1">色情</label> <label><input type="radio" class="report_type" id="report_Politics" name="report_type" value="2">政治</label> <label><input type="radio" class="report_type" id="report_copy" name="report_type" value="3">抄袭</label> <label><input type="radio" class="report_type" id="report_ad" name="report_type" value="4">广告</label> <label><input type="radio" class="report_type" id="report_want" name="report_type" value="5">招聘</label> <label><input type="radio" class="report_type" id="report_call" name="report_type" value="6">骂人</label>  
<label><input type="radio" class="report_type" id="report_other" name="report_type" value="7">其他</label> <input type="text" name="report_other_content" id="report_other_content" maxlength="30" style="display: none;"></td>

</tr>

<tr id="panel_originalurl" style="display: none;">

<th>原文地址：</th>

<td><input id="originalurl" value="http://" name="originalurl" type="text" style="width: 90%;"></td>

</tr>

<tr>

<th id="sp_reason">原因补充：</th>

<td><textarea id="report_description" style="width: 300px;" rows="3" name="report_description"></textarea>

(最多只允许输入30个字)

</td>

</tr>

<tr>

<td><input id="btnSubmitReport" name="submit" type="image" align="middle" class="btn_1" src="http://static.blog.csdn.net/images/btn_submit.jpg"> <span style="padding-left:20px;"></span> ![](http://static.blog.csdn.net/images/btn_cancel.jpg)</td>

</tr>

</tbody>

</table>

</form>

</div>

<script language="javascript" type="text/javascript">var isComment=0; //显示隐藏地址 $(function () { if(isComment){ $("#report_description").attr("disabled",true); $("#sp_n").hide(); $("#sp_reason").html("评论内容："); } $(".report_type").click(function () { $("#panel_originalurl,#report_other_content").hide(); switch ($(this).val()) { case '3': $("#panel_originalurl").show(); $("#originalurl").focus(); break; case '7': if(isComment){ $("#report_other_content").show().focus(); } break; } }); $("#frmReport").submit(function () { if (!currentUserName) { if (confirm("您的操作必须登录，是否登录？")) { location.href = "http://passport.csdn.net/account/login?from=" + encodeURIComponent(location.href); return false; } return false; } var reportType = $("input[name=report_type]:checked").val(); if(!reportType){ alert("请选择举报原因！"); return false; } var otherInfo = ""; switch (reportType) { case '3': otherInfo = $("#originalurl").val(); if (otherInfo == ""||otherInfo=="http://") { alert("举报抄袭必须提供原创文章地址！"); $("#originalurl").focus(); return false; } else if(!checkeURL(otherInfo)) { alert("请输入正确的原创文章地址！"); $("#originalurl").focus(); return false; } break; case '7': otherInfo = $("#report_other_content").val(); if (isComment && !otherInfo) { alert("请填写举报的具体原因！"); $("#report_other_content").focus(); return false; } if(!isComment){ if(!$("#report_description").val()){ alert("请填写举报的具体原因！"); $("#report_description").focus(); return false; } } break; } if(!isComment){ if($("#report_description").val().length>30){ alert("举报原因最多只允许输入30个字！"); return false; } } nowTime = { year: new Date().getFullYear(), month: parseInt(new Date().getMonth())+1, day: new Date().getDate(), hours: parseInt(new Date().getHours()), minutes: parseInt(new Date().getMinutes()), seconds: parseInt(new Date().getSeconds()) } var data = { articleId: fileName, commentId: 0, reportType: reportType, originalurl: $("#originalurl").val(), report_other_content: $("#report_other_content").val(), report_description: $("#report_description").val(), currentUserName: currentUserName, updatetime: nowTime.year+'/'+nowTime.month+'/'+nowTime.day+' '+ nowTime.hours+':'+nowTime.minutes+':'+seconds, blogUser: username }; if(!isComment){//如果是举报文章 data.report_other_content = data.report_description; // data.report_description = "1\. 神经网络这是一个常见的神经网络的图：这是一个常见的三层神经网络的基本构成，Layer L1是输入层，Layer L2是隐含层"; } $.post(blog_address + "/common/report?id="+fileName+"&t=2", data, function (data) { if (data.result == 1){ SetError("感谢您的举报，我们会尽快审核！"); }else{ if (data.content) alert(data.content); } }); return false; }); $("#btnCloseReportDialog").click(function () { CloseDiv(); }); }); //提示后关闭方法 function SetError(error) { $("#btnCloseReportDialog").trigger("click"); alert(error); CloseDiv(); } //关闭方法 function CloseDiv() { $.removeMask(); $("#report_dialog").hide(); return false; } //验证url function checkeURL(url){ return /^http(s)?:\/\/([\w-]+\.)+[\w-]+/i.test(url); }</script></div>

<script>window._bd_share_config = { "common": { "bdSnsKey": {}, "bdText": "", "bdMini": "1", "bdMiniList": false, "bdPic": "", "bdStyle": "0", "bdSize": "16" }, "share": {} }; with (document) 0[(getElementsByTagName('head')[0] || body).appendChild(createElement('script')).src = 'http://bdimg.share.baidu.com/static/api/js/share.js?v=89860593.js?cdnversion=' + ~(-new Date() / 36e5)];</script> <script type="text/javascript">if($(".article_collect li").length==1){$(".article_collect").hide();} if($(".article_tags li").length==1){$(".article_tags").hide();} $(".edit a").attr("href","http://write.blog.csdn.net/postedit/"+fileName); $.each($(".edu_li a"),function(){$(this).attr("href",$(this).attr("href").replace("blog7","blog9"))}); new CNick('#uid').showNickname(); if($("#fan").html()=="") { $("#fan").html(0); } var blogCustomType ='{customtype}'; $("#custom"+blogCustomType).show();</script> <script type="text/javascript">var fromjs=$("#fromjs"); if(fromjs.length>0) { $("#fromjs .markdown_views pre").addClass("prettyprint"); prettyPrint(); $('pre.prettyprint code').each(function () { var lines = $(this).text().split('\n').length; var $numbering = $('<ul/>').addClass('pre-numbering').hide(); $(this).addClass('has-numbering').parent().append($numbering); for (i = 1; i <= lines; i++) { $numbering.append($('<li/>').text(i)); }; $numbering.fadeIn(1700); }); $('.pre-numbering li').css("color","#999"); } $(function(){ setTimeout(function(){ $(".math").each(function(index,value){$(this).find("span").last().css("color","#fff"); }) },500); }); setTimeout(function () { $(".toc a[target='_blank']").attr("target", ""); }, 500);</script>
