

# 教你用 Web Speech API 和 Node.js 来创建一个简单的 AI 聊天机器人


> 简评：使用语音命令在今天变得非常普遍，许多手机用户使用像 Siri 和 Cortana 这样的语音助手，我们的卧室也被亚马逊的 Echo 和 Google Home 这样的设备“入侵”了。这些系统都离不开语音识别软件，现在，我们的浏览器也友好支持了 Web Speech API，可以让用户在 Web 应用中集成语音功能。

这篇文章将介绍如何使用 API 来在浏览器中创建人工智能语音聊天界面。这个应用会识别用户的声音，并且用一个合成的声音来回答用户。因为 Web Speech API 还处在试验阶段，这个应用只在[支持的浏览器](http://caniuse.com/#search=speech)上可用。这篇文章使用的语音识别和语音合成功能，目前仅在基于 Chromium 的浏览器上支持，包括 Chrome 25+ 和 Opera 27+，目前 Firefox，Edge 和 Safari 仅支持语音合成。


要完成这个 Web 应用，我们需要完成下面三个主要的步骤：

1.  使用 Web Speech API 的 _SpeechRecognition_ 接口来识别用户的声音；
2.  将用户的消息作为文本字符串发送到商业的自然语言处理 API；
3.  一旦 [API.AI](https://api.ai/) 返回了响应文本，使用 _SpeechSynthesis_ 接口来合成语音。

<div class="image-package">![](//upload-images.jianshu.io/upload_images/1908904-c0d027ce532848dd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
</div>

这篇文章使用的[完整源代码](https://github.com/girliemac/web-speech-ai)在 GitHub 上。（先帮妹子赞一个）

### 开始你的 Node.js 应用

首先，我们要用 Node.js 搭建一个 Web 应用框架。创建你的应用目录，就像这样：

    .
    ├── index.js
    ├── public
    │   ├── css
    │   │   └── style.css
    │   └── js
    │       └── script.js
    └── views
        └── index.html

然后，执行下面的命令来初始化你的 Node.js 应用：

    $ npm init -f

**-f** 命令表示接受默认的配置（你也可以去掉，然后手动配置你的应用），这样会生成一个 _package.json_文件，包含一些基本信息。

现在，安装下面的依赖库：

    $ npm install express socket.io apiai --save

**--save** 命令将会在_package.json_ 中自动更新依赖。

我们将要使用 [Express](https://expressjs.com/) 库，一个 Node.js 写的 Web 应用服务框架，可以在本地运行服务器。为了实现在浏览器和服务器之间实时双向交流，我们将会使用 [Socket.IO](https://socket.io/)。同时，我们将会安装自然语音处理服务工具，API.AI用来构建一个 AI 聊天机器人。

[Socket.IO](https://socket.io/) 是一个在 Node.js 中轻松使用 WebSocket 的库。通过在客户端和服务端建立 socket 连接，只要 Web Speech API（语音消息）或者 [API.AI](https://api.ai/) API （AI 消息）返回了文本数据，我们的聊天信息就能在浏览器和服务器之间往返。

现在，让我们创建_index.js_ 文件，并实例化 Express 以及监听服务器：

    const express = require('express');
    const app = express();

    app.use(express.static(__dirname + '/views')); // html
    app.use(express.static(__dirname + '/public')); // js, css, images

    const server = app.listen(5000);
    app.get('/', (req, res) => {
      res.sendFile('index.html');
    });

下一步，我们将使用 Web Speech API 集成前端代码。

### 用 SpeechRecognition 接口接收语音

Web Speech API 有一个主要的控制接口，叫 [SpeechRecognition](https://developer.mozilla.org/en-US/docs/Web/API/SpeechRecognition)，从麦克风接收用户的语音并加以识别。

**创建用户界面**

这个应用的 UI 很简单：一个打开语音识别的按钮。打开_index.html_，将前端的 JavaScript 文件（_script.js_）和 [Socket.IO](https://socket.io/) 包含进去。

    <html lang="en">
      <head>…</head>
      <body>
        …
        <script src="https://cdnjs.cloudflare.com/ajax/libs/socket.io/2.0.1/socket.io.js"></script>
        <script src="js/script.js"></script>
      </body>
    </html>

然后，我们在 body 中添加一个按钮：

    <button>Talk</button>

为了让我们的按钮看起来像 demo 中的那样，我们需要在[源代码](https://github.com/girliemac/web-speech-ai)中引用_style.css_文件。

### 用 JavaScript 捕捉声音

在 _script.js_中，调用 [SpeechRecognition](https://developer.mozilla.org/en-US/docs/Web/API/SpeechRecognition) 的实例，Web Speech API 的控制接口：

    const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
    const recognition = new SpeechRecognition();

我们同时使用了有前缀和没有前缀的对象，因为 Chrome 目前支持 API 的前缀属性。

同时，我们使用了 ECMAScript6 语法，因为 ES6，_const_ 关键字和箭头函数以及 Speech API 接口 _SpeechRecognition_ 和 _SpeechSynthesis_ 都在浏览器中支持。

你可以随意地设置一些[属性](https://developer.mozilla.org/en-US/docs/Web/API/SpeechRecognition)变量来自定义语音识别：

    recognition.lang = 'en-US';
    recognition.interimResults = false;

然后，拿到按钮的 DOM 引用，监听点击事件来初始化语音识别：

    document.querySelector('button').addEventListener('click', () => {
     recognition.start();
    });

一旦开始语音识别，就能用 result 事件将刚刚说的话转成文本：

    recognition.addEventListener('result', (e) => {
      let last = e.results.length - 1;
      let text = e.results[last][0].transcript;

      console.log('Confidence: ' + e.results[0][0].confidence);

      // We will use the Socket.IO here later…
    });

这将返回 _SpeechRecognitionResultList_ 对象，你可以在这个对象的数组中得到文本结果。同时，你可以看到上面代码中返回的 _confidence_ 转录。

现在，是时候使用 [Socket.IO](https://socket.io/) 来向服务端发送文本了。

### 用 [Socket.IO](https://socket.io/) 实时交互

你可能会好奇为什么我们不用简单的 HTTP 或者 AJAX 来代替。你可以通过 POST 方法向服务端发送数据，但是，通过 [Socket.IO](https://socket.io/)，我们使用 WebSocket 发送数据，因为 socket 是双向交流的最佳解决方案，尤其是当我们从服务端向浏览器推送事件时。通过持续的 socket 连接，我们不用重新加载浏览器或者频繁地持续发送 AJAX 请求。

<div class="image-package">![](//upload-images.jianshu.io/upload_images/1908904-4136b0549eef7db4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
</div>

在 _script.js_中实例化 [http://Socket.IO](https://socket.io/)：

    const socket = io();

然后插入你监听 SpeechRecognition 的 result 事件代码：

    socket.emit('chat message', text);

现在重新回到 Node.js 代码，接收这条文本，然后使用 AI 响应用户。

### 从 AI 中得到答复

许多平台和服务都能够让你在应用中用语音-文本自然语言处理来集成 AI 系统，包括 IBM 的 [Watson](https://www.ibm.com/watson/)，微软的 [LUIS](https://www.luis.ai/) 和 脸书的 [Wit.a](https://wit.ai/)。为了快速构建对话界面，我们将使用 API.AI，因为它提供了免费的开发者账户，让我们可以使它的 Web 接口和 Node.js 库快速地建立一个小型对话系统。

**设置**[API.AI](https://api.ai/)  
创建一个账户后，你就创建了一个“代理”。参考[文档指南](https://api.ai/docs/getting-started/basics)的第一步。

接着，点击左边菜单的 “Small Talk”，然后开启启用服务选项。

<div class="image-package">![](//upload-images.jianshu.io/upload_images/1908904-6a0a3b07daea94a6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
</div>

用 [API.AI](https://api.ai/) 界面自定义你的 small-talk 代理。

点击菜单中你的代理名字旁边的齿轮图标，回到 “基本设置” 页面，拿到 API 密钥。你将会在 Node.js SDK 中使用“客户端访问令牌”。

**使用**[API.AI](https://api.ai/)  
我们将使用 Node.js SDK 来将我们的 Node.js 应用连接到 [API.AI](https://api.ai/)。回到 _index.js_，用你的访问令牌初始化 API.AI：

    const apiai = require('apiai')(APIAI_TOKEN);

如果你只想在本地运行，你可以在这里硬编码你的 API 密钥。这里有几种方式来设置环境变量，但我通常使用 _.env_ 文件来声明变量。在 GitHub 中的源码中，我用 _.gitignore_ 隐藏了我的证书文件。但是你可以参考 [.env-test](https://github.com/girliemac/web-speech-ai/blob/master/.env_test) 文件看看它是如何设置的。

现在我们要用服务端的 [Socket.IO](https://socket.io/) 来接收浏览器的数据。

一旦建立连接收到消息，使用 [API.AI](https://api.ai/) 的接口来响应用户：

    io.on('connection', function(socket) {
      socket.on('chat message', (text) => {

        // Get a reply from API.AI

        let apiaiReq = apiai.textRequest(text, {
          sessionId: APIAI_SESSION_ID
        });

        apiaiReq.on('response', (response) => {
          let aiText = response.result.fulfillment.speech;
          socket.emit('bot reply', aiText); // Send the result back to the browser!
        });

        apiaiReq.on('error', (error) => {
          console.log(error);
        });

        apiaiReq.end();

      });
    });


当 [API.AI](https://api.ai/) 返回结果后，用 [Socket.IO](https://socket.io/) 的 _socket.emit()_方法发送到客户端。

### 用 SpeechSynthesis 接口让 AI 发出声音

回到 _script.js_，用 Web Speech API 的 _SpeechSynthesis_ 控制器接口创建一个合成声音的函数。这个函数接收一个字符串参数，让浏览器读出文本：

    function synthVoice(text) {
      const synth = window.speechSynthesis;
      const utterance = new SpeechSynthesisUtterance();
      utterance.text = text;
      synth.speak(utterance);
    }

上面的代码首先创建了一个 _window.speechSynthesis_ 这个 API 接入点，你可能会注意到这次是没有前缀属性的，这个 API 比 _SpeechRecognition_ 更广泛地被支持，所有的浏览器都弃用了 _SpeechSysthesis_ 的前缀。

接着创建了一个 [SpeechSynthesisUtterance()](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesisUtterance) ，然后设置要被合成声音的文本。你可以设置其他的[属性](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesisUtterance)，比如 _voice_，来选择浏览器和操作系统支持的声音类型。最终调用 SpeechSynthesis.speak() 来发出声音。

现在再次用 [Socket.IO](https://socket.io/) 来获得服务端响应，一旦消息收到了，就调用上面的函数。

    socket.on('bot reply', function(replyText) {
     synthVoice(replyText);
    });

让我们来试试我们的 AI 机器人吧！

<div class="image-package">![](//upload-images.jianshu.io/upload_images/1908904-df1bb9d197aff38d.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
</div>


参考文章：

*   “[Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API),” Mozilla Developer Network
*   “[Web Speech API Specification](https://dvcs.w3.org/hg/speech-api/raw-file/tip/speechapi.html),” W3C
*   “[Web Speech API: Speech Synthesis](https://docs.microsoft.com/en-us/microsoft-edge/dev-guide/multimedia/web-speech-api)” (Microsoft Edge documentation) Microsoft
*   [Guide](https://nodejs.org/en/docs/guides/), Node.js
*   [Documentation](https://docs.npmjs.com/), npm
*   “[Hello world example](https://expressjs.com/en/starter/hello-world.html),” Express
*   “[Get Started](http://link.zhihu.com/?target=https%3A//socket.io/get-started/),” [Socket.IO](http://link.zhihu.com/?target=http%3A//Socket.IO)

还可以试试不同的自然语言处理工具：

*   [API.AI](http://link.zhihu.com/?target=https%3A//api.ai/), Google
*   [Wit.ai](http://link.zhihu.com/?target=https%3A//wit.ai/), Facebook
*   [LUIS](http://link.zhihu.com/?target=https%3A//www.luis.ai/), Microsoft
*   [Watson](http://link.zhihu.com/?target=https%3A//www.ibm.com/watson/), IBM
*   [Lex](http://link.zhihu.com/?target=https%3A//aws.amazon.com/lex/), Amazon

原文链接：[Building A Simple AI Chatbot With Web Speech API And Node.js](http://link.zhihu.com/?target=https%3A//www.smashingmagazine.com/2017/08/ai-chatbot-web-speech-api-node-js/)  

http://cdn2.jianshu.io/p/bb163ae5a279



