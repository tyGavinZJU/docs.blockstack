---
layout: learn
description: Blockstack Zero-to-DApp tutorial
permalink: /:collection/:path.html
image: /assets/img/zero-to-dapp.png
---
# 3 - 定制化你的王国
{:.no_toc}

 **Zero to DAPP 3 of 4 for MacOS/Linux (or [Windows](zero_to_dapp_3_win.html))**

在这个页面中，您将检查和修改在[第2部分中](zero_to_dapp_2.html)构建的动物王国DApp。您将查看底层代码，并找到满足App Mining资格要求的部分。您将扩展对应用程序的知识。最后，您将学习如何部署DApp。

此页面包含以下课题

 * TOC
 {:toc}


### 在您开始之前
{:.no_toc}

在继续之前，请确保能够找到项目中的关键文件和目录(文件夹)。您需要确保已打开终端并将目录更改为动物王国项目的目录中。

<img src="images/project-prompt.png" alt="">

您也可以使用Finder，如果您发现它更容易导航。只需记住，您将需要命令行来运行您的项目。

## 了解动物王国应用程序代码

动物王国应用程序有两个主要组件，React和Blockstack。React用于构建所有web组件和交互。你可以用任何你喜欢的框架来替换React;Blockstack与web框架无关。本节不详细解释React;讨论的重点是Blockstack Javascript库代码。

<a href="https://blockstack.github.io/blockstack.js/"
target="\_blank">Blockstack Javascript 库是开发人员创建DApp所需要的全部。</a>它赋予应用程序验证Blockstack标识和读写存储在Gaia hub中的用户数据的能力。

### 验证用户身份

`src/App.js` 文件创建一个Blockstack的`UserSession`并使用该会话的`isUserSignedIn()`方法来确定用户是登录还是退出应用程序。根据这个方法的返回的结果。 应用程序重定向到`src/SignedIn`页面或`src/Landing.js` 页面。

```js
 import React, { Component } from 'react'
 import './App.css'
 import { UserSession } from 'blockstack'

 import Landing from './Landing'
 import SignedIn from './SignedIn'

 class App extends Component {

   constructor() {
     super()
     this.userSession = new UserSession()
   }

   componentWillMount() {
     const session = this.userSession
     if(!session.isUserSignedIn() && session.isSignInPending()) {
       session.handlePendingSignIn()
       .then((userData) => {
         if(!userData.username) {
           throw new Error('This app requires a username.')
         }
         window.location = `/kingdom/${userData.username}`
       })
     }
   }

   render() {
     return (
       <main role="main">
           {this.userSession.isUserSignedIn() ?
             <SignedIn />
           :
             <Landing />
           }
       </main>
     );
   }
 }

 export default App
```

第一次启动应用程序时，这段代码将确定用户是否以前已登录到DApp。如果没有，则打开`Landing.js`页面。这个页面为用户提供了一个**登录到Blockstack**的机会。

单击该按钮将调用`redirectToSignIn()`方法，该方法生成身份验证请求，并将用户重定向到Blockstack浏览器以批准登录请求。实际的Blockstack登录对话框取决于用户是否已经在Blockstack浏览器中拥有一个已经存在的会话。

<img src="images/kingdom_notin.png" alt="">

使用标识登录是用户授予DApp访问权限的方法。访问意味着DApp可以读取用户资料，并能为DApp读取/写入用户数据。数据加密存储在Gaia Hub上。

源代码从Blockstack库导入`UserSession`。与给定用户会话相关的数据封装在会话中。在web浏览器中，`UserSession`默认行为是将会话数据存储在浏览器的本地存储中。这意味着应用程序开发人员可以将会话状态的管理留给用户。在非web浏览器环境中，需要传入一个`AppConfig`实例，该实例定义了当前应用程序的参数。

<div class="uk-card uk-card-default uk-card-body">
<h5>App Mining 要求： Blockstack 身份验证</h5>
<p>要参与应用程序mining，您的应用程序必须集成Blockstack 身份验证。否则应用程序不合格。
</p>
</div>

### 获取并将用户数据放到Gaia Hub中

Gaia是Blockstack数据存储中心(https://hub.blockstack.org)。一旦用户进行了身份验证，应用程序就可以获取并将应用程序数据放入用户的存储中。在用户登录之后，`SignedIn.js`代码通过运行`loadMe()`方法检查用户的Gaia配置文件。

```js
loadMe() {
    const options = { decrypt: false }
    this.userSession.getFile(ME_FILENAME, options)
    .then((content) => {
      if(content) {
        const me = JSON.parse(content)
        this.setState({me, redirectToMe: false})
      } else {
        const me = null

        this.setState({me, redirectToMe: true})
      }
    })
  }
```

该文件中的大多数导入都是本地编码的React组件。例如,`Kingdom.js`, `EditMe.js`和`Card.js`。关键的Blockstack导入是`UserSession`和在`constants.js`文件中定义的`appConfig`。

`loadMe()`代码使用Blockstack的`UserSession.getFile()`方法从应用程序数据存储中获取指定的文件。如果用户在Gaia上的数据存储没有数据(新用户的情况就是如此)，Gaia hub将使用HTTP `404`代码进行响应，`getFile()`promise解析为null。如果您正在使用带DApp的Chrome开发工具，您将在浏览器的开发人员**控制台**中看到这些错误。

<img src="images/kingdom-errors.png" alt="">

在用户选择动物角色和领地之后，用户按**Done**，应用程序将用户数据存储在Gaia上。

```js
saveMe(me) {
  this.setState({me, savingMe: true})
  const options = { encrypt: false }
  this.userSession.putFile(ME_FILENAME, JSON.stringify(me), options)
  .finally(() => {
    this.setState({savingMe: false})
  })
}
```

Blockstack中的 <a href="https://blockstack.github.io/blockstack.js/#putfile"
target="\_blank"><code>putFile()</code></a> 存储用户的DApp数据存储中提供的数据。默认情况下， `putFile()`以加密格式存储数据，这意味着只有存储它的用户才能查看数据。 可以从用户配置文件中查看数据存储的URL。由于此应用程序希望其他用户查看角色和领地，因此数据未加密，因此 `encrypt` 选项被设置为 `false`.

如果你测试过你的动物王国，你可以在你的个人资料上看到。要查看您的个人资料，<a href="https://explorer.blockstack.org">Blockstack 资源管理器中</a> 搜索您的ID:

<img src="images/explorer.png" alt="">

<div class="uk-card uk-card-default uk-card-body">
<h5>App Mining 可选: Gaia Storage</h5>
<p>应用程序挖掘使用Gaia存储不是必须的。请记住，使用Gaia可能使数据存储更容易，因为它是为在Blockstack生态系统中工作而设计的。
</p>
</div>

### 应用配置

您的DApp包含三个页面**动物**、**领地**和**其他王国**，它们来自于三个代码元素:

 * `src/constants.js` 文件定义了应用程序的数据概要文件(`AppConfig`).
 * `public/animals` 目录包含图片。
 * `public/territories` 目录包含图片。

在下一节中，您将通过修改这些文件来扩展王国的配置。

## 添加一个领地

如果您的应用程序仍然在localhost中运行，请用键盘上的`CTRL-C`停止它。

1. 决定添加的领地类型; &&mdash;; 沙漠、海洋或城市!

   这个例子添加了虚构的领地维斯特洛。

2. 搜索代表您的新领地的图像。
   
   谷歌图像是查找 <a href="images/westeros.jpg" target="\_blank">维斯特洛JPEG图像</a>的好地方。

3. 将图像保存到“动物王国”项目代码中的 `public/territories`文件夹中。
 
   {% include warning.html content="领地文件名必须全部小写，扩展名为 <code>.jpg</code>。
   对于本例，领地图像保存在 <code>westeros.jpg</code> 文件中。" %}

4. 使用 `ls` 命令确认在文件`territories`目录中，并且名称正确。

   ```bash
   ls public/territories/
   forest.jpg   tundra.jpg   westeros.jpg
   ```

5. 在您喜欢的编辑器中打开 `src/constant.js`文件。
6. 向下滚动到定义**领地**的部分。

   ```js
   export const TERRITORIES = [
     {
       id: 'forest',
       name: 'Forest',
       superpower: 'Trees!'
     },
     {
       id: 'tundra',
       name: 'Tundra',
       superpower: 'Let it snow!'
     }
   ]
   ```

7. 添加您的新领地。

   ```js
   export const TERRITORIES = [
     {
       id: 'forest',
       name: 'Forest',
       superpower: 'Trees!'
     },
     {
       id: 'tundra',
       name: 'Tundra',
       superpower: 'Let it snow!'
     },
     {
       id: 'westeros',
       name: 'Westeros',
       superpower: 'The Iron Throne!'
     }
    ]
    ```
8. 保存并关闭 `constant.js` 文件。
9. 回到终端窗口，重新启动应用程序。

   ```bash
   $ npm run start
   ```
10. 应用程序启动后， 导航到 **领地** 页面并查找您的 `Westeros` 领地。

   <img src="images/kingdom-throne.png" alt="">

## 将Blockstack王国添加到其他王国

你的动物王国只能识别另外**两个王国**在本节中，您将添加第三个Blockstack王国(`https://animalkingdoms.netlify.com`).

1. 在您喜欢的编辑器中打开 `src/constant.js`文件。

   在Mac电脑上，你可以使用TextEdit或Vim。

2. 向下滚动到定义**其他王国**的部分。

   ```js
   export const OTHER_KINGDOMS = [
     {
       app: 'https://animal-kingdom-1.firebaseapp.com',
       ruler: 'larry.id'
     },
     {
       app: 'http://localhost:3001',
       ruler: 'larz.id'
     }
   ]
   ```

   要添加王国，您需要它的URL和所有者的ID。

3. 编辑文件并添加由`meepers.id.blockstack`拥有的`https://animalkingdoms.netlify.com`。

   当您完成时，文件将像这样。


   ```js
   export const OTHER_KINGDOMS = [
     {
       app: 'https://animal-kingdom-1.firebaseapp.com',
       ruler: 'larry.id'
     },
     {
       app: 'http://localhost:3001',
       ruler: 'larz.id'
     },
     {
       app: 'https://animalkingdoms.netlify.com',
       ruler: 'meepers.id.blockstack'
     }
   ]
   ```

4. 保存并关闭`constants.js` 文件。
5. 回到浏览器中，导航到**其他王国**页面。

   <img src="images/kingdom-meepers.png" alt="">

6. 点击他的王国进入`meepers`王国。
7. 尝试从meepers的王国添加一个主题到您的王国。


## 在web上部署您的DApp

到目前为止，您一直在本地运行应用程序。这意味着你是唯一可以用它来创造一个王国的人。您可以通过将应用程序托管在internet上，使其对其他人可用。你可以用Netlify帐户免费做这件事。

<div class="uk-card uk-card-default uk-card-body uk-section-muted">
<h5>App Mining 要求: 审查可访问性</h5>
<p>要参与应用程序挖掘，您的应用程序必须可用于审查。 开源项目必须提供其代码的URL。 带有私有存储库的项目可以以包形式提供其应用程序。
</p>
</div>

在开始之前，您需要构建一个可以部署的站点。

1. 在你的终端中，  按下`CTRL-C` 用来停止`npm run start` 运行。
2. 输入`npm run build`命令，用你的代码构建一个网站:

   ```bash
   npm run build
   ```

   <img src="images/run-build.png" alt="">

   当命令完成时，您的项目中应该有一个新的`build`子目录。

3. 在Finder中打开项目。
4. 找到新创建的 `build` 子文件夹。

   <img src="images/finder-build.png" alt="">

5. <a href="https://app.netlify.com/signup" target="\_blank">注册一个免费的Netlify帐户</a>

   本例假设您通过提供电子邮件和密码来创建帐户。

   <img src="images/netlify-account.gif" alt="">

6. 在您的电子邮件收件箱中，找到Netlify的欢迎邮件并验证您的帐户。

   <img src="images/netlify-verify.png" alt="">

7. 登录到 Netlify 并转到浏览器的 **Overview** 页面。
8. 将`build`子目录从Finder中拖到Netlify中的drop区域。

   <img src="images/netlify-deploy.gif" alt="">

   过一会儿，Netlify会构建你的代码并显示新网站的位置。

   <img src="images/kingdom-build.png" alt="">

9. 点击你的网站名称来显示网站。

   提示您使用Blockstack ID登录到这个新站点。

10. 单击 **使用Blockstack登录**.

    在您登录后，您的网站会向您显示以下信息:

    <img src="images/kingdom-failed.png" alt="">   

    您得到此消息是因为当您进行身份验证时，您在一个URL处的DApp向另一个DApp (Blockstack浏览器)请求资源(标识)。对源(您的新网站)之外的资源的请求称为跨源请求(CORs)。以这种方式获取数据可能有风险，因此必须配置网站安全性，以允许跨源交互。

    <div class="uk-inline">
    <button class="uk-button uk-button-primary" enter="button">点击我来学习CORS如何像借用梯子一样。</button>
    <div uk-dropdown>
    您可以将CORS交互视为具有安全性的公寓楼。例如，如果你需要借梯子，你可以问你楼里的邻居谁有梯子。安全性可能不会对这个请求有问题(即，同根同源，你的建筑)。但是，如果您需要某个特定的工具，并且您从在线五金店下订单(即，非同源，其他地点),保安人员在允许送货员进入公寓大楼前，可能会要求出示证件来源:

    <br>
    Credit: <a href="https://www.codecademy.com/articles/what-is-cors" target="\_blank">Codecademy</a>
    </div>
    </div>

    配置CORs的方式取决于为您的网站提供服务的公司。本例使用Netlify。

11. 定位项目中的`cors/_headers` 和 `cors/_redirects` 文件。

    您可以使用Finder或`ls`命令。

    <img src="images/finder.png" alt="">

12. 将它们复制到`build`目录中。

    要复制它们使用`ls`命令，请在`animal-kingdom-master`项目的根目录中输入以下内容。

    ```bash
    cp cors/_headers build
    cp cors/_redirects build
    ```

    每个文件的名称和下划线都是必不可少的。

13. 将`build`文件拖回Netlify drop区域。

    过一会儿，Netlify将发布您的站点。检查发布的位置，它可能已经更改。

14. 点击链接，进入你的动物王国。
15. 重建你的动物和领地。

    动物王国是由它在互联网上的位置来确定的，还记得吗?因此，您在本地工作站上创建的动物王国与您在Netlify上创建的动物王国是不同的。

## 把你的王国加入我们的家族

在这一点上，你的王国是孤立的。如果您知道另一个王国，您可以添加来自该王国的主题，但其他王国无法访问您的主题。在本节中，您将使用一个免费的GitHub帐户将您的王国添加到Blockstack王国。

1. 如果您有一个GitHub帐户，请转到步骤2，否则转到GitHub <a href="https://github.com/" target="\_blank">站点并创建一个新帐户</a>。
2. 转到Github上的 <a href="https://github.com/blockstack/animal-kingdom/issues" target="\_blank">https://github.com/blockstack/animal-kingdom/issues</a> 储存库。
2. 单击 **New Issue**.

   出现new issue对话框。

3. 使用来自Netlify的URL和您的Blockstack id填写。

   完成后，您的问题将如下所示:

   <img src="images/kingdom-issue.png" alt="">

4. 按 **Submit new issue**.

   Blockstack团队将把您的Netlify王国添加到我们的王国。当我们这样做的时候，我们会通知你，你也会收到一封电子邮件。

5. 当您收到电子邮件时，登录到Blockstack动物王国查看您在 **其他王国下**的王国。


## 下一步 (得到一个很Cool的tshirt!)
{:.no_toc}

在下一部分中，您将了解应用程序挖掘如何为DApp开发工作提供资金。您将花几分钟时间将您的动物王国DApp添加到[App.co - the Universal App store](zero_to_dapp_4.html)。完成这一步，你将获得一件限量版t-shirt。

如果你有一个twitter账号，为什么不告诉一些人你的进展呢?

<a href="https://twitter.com/share?ref_src=twsrc%5Etfw"
class="twitter-share-button" data-size="large" data-text="I just built a DApp
using @blockstack's  Zero-to-DApp tutorial! " data-hashtags="blockstack,
blockchain, blockchainnopain, blockchainnopainblockstack"
data-show-count="true">Tweet your work!</a><script async
src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
