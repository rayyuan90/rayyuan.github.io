
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

### 原文地址 
http://blog.csdn.net/xiangzhihong8/article/details/62246950
