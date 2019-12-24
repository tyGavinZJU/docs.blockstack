---
layout: learn
description: Blockstack Zero-to-DApp tutorial
permalink: /:collection/:path.html
image: /assets/img/zero-to-dapp.png
---
# 2 - 了解平台
{:.no_toc}

**Zero-to-DApp 2 of 4 for MacOS/Linux (or [Windows](zero_to_dapp_2_win.html))**

在本部分中，您将了解Blockstack平台如何降低使用区块链技术构建的门槛。您将设置构建典型web DApp所需的所有前提条件。最后，您将构建并运行[第1部分中](zero_to_dapp_1.html)中介绍的动物王国DApp。本部分的主题如下:

* TOC
{:toc}


## 1.一个没有痛点的区块链平台

Blockstack的任务是带来一个新的互联网，用户可以控制对他们的数据的访问和如何使用。基于这一使命，Blockstack
Public Benefit Corp. (PBC)于2017年开始开发Blockstack平台。

该平台的开发理念遵循两个简单的原则。首先，创建后端服务，使去中心化的应用程序具有性能和可伸缩性。其次，为区块链技术提供简单、熟悉的开发接口。这种理念的结果是一个技术平台，允许您:

* **在任何Javascript框架中构建应用程序。** 您可以使用区块链，而不需要学习新的编程语言或扩展应用程序栈。目前，Blockstack支持web应用程序的react生成器和iOS和Android的SDK。
* **使用定义良好的REST端点来简化和封装区块链后端。** Blockstack Javascript API将区块链操作简化为熟悉的GET和PUT操作。
* **可访问的Blockstack的命名系统(BNS)。** 系统有超过90K的用户可以立即开始使用您的应用程序。
* **快速扩展到大型、高性能的生产系统。** Blockstack的Gaia存储系统提供了与Amazon S3、Google Drive或Azure相当的快速、可伸缩的性能。

使用Blockstack的技术，您可以根据您已经拥有的知识立即开始在区块链上构建。您不需要花费时间或精力在专门语言或技术知识上。

## 获取前提条件并设置环境

要遵循本教程其余部分的步骤，您需要按照以下步骤:

* 一个用于测试您的动物王国的Blockstack ID (identity)。
* 访问终端窗口并熟悉它提供的命令行。
* 在Mac上，安装XCode命令行工具来支持Node包管理器(`npm`)。
* Node包管理器包管理器。

按照本节中的步骤安装这些组件。

{% include note.html content="为了获得最佳效果，请使用Chrome浏览器。目前，Blockstack浏览器在Chrome中运行得最好，在使用Safari或Firefox等浏览器时可能会遇到问题。我们正在努力解决这些问题。" %}

### 确认或获取Blockstack ID
{:.no_toc}

确认您有一个Blockstack ID，也称为标识；`joe.id.blockstack`是标识的一个例子。

* 如果您有一个ID, 在浏览器中访问 <a href="https://browser.blockstack.org/" target="\_blank">Blockstack Browser</a>。

   登录确认您拥有一个有效的ID，其中包含所需的密钥恢复key（_secret recovery key_）或恢复代码（_magic recovery code_）。密钥恢复key是在创建ID时记录的一个12或24个单词短语。恢复代码是在创建身份时Blockstack发送给您的一串字符。你可以用任何一个来确认你的身份。

* 如果您还没有Blockstack ID， <a href="https://browser.blockstack.org/" target="\_blank">可以通过blockstack浏览器创建一个</a>.

    创建ID的说明可以在 <a href="{{ site.baseurl
    }}/browser/ids-introduction.html#create-an-initial-blockstack-id"
    target="\_blank">本文档中获得</a>.


###  命令行访问
{:.no_toc}

如果您正在使用Mac, 你可以找到 **终端** 在 **Application >
Launchpad > Other** 文件夹中.

<img src="images/terminal.png" alt="">

如果您不经常使用命令行，请花点时间测试一些常见的命令。

<table class="uk-table uk-table-small uk-table-divider">
  <tr>
    <th>命令</th>
    <th>做什么</th>
  </tr>
  <tr>
    <td><code>pwd</code></td>
    <td> 打印工作命令行所在的当前目录的名称。</td>
  </tr>
  <tr>
    <td><code>ls</code></td>
    <td>列出当前目录中的文件和目录。</td>
  </tr>
  <tr>
    <td><code>cd</code></td>
    <td>更改目录导航到文件系统中的位置</td>
  </tr>
</table>

### 安装XCode命令行工具
{:.no_toc}

命令行工具包为Mac终端用户提供了许多常用的工具、实用程序和编译器。NPM安装的一些内容需要XCode。

1. 打开系统上的终端窗口。
2. 输入 `xcode-select` 命令:

   ```bash
   $ xcode-select --install
   ```

   <img src="images/install-command-line-tools-os-x.jpg" alt="">

   软件更新对话框显示:

   <img src="images/confirm-install-command-line-tools-mac-os-x.jpg" alt="">

3. 单击 **Install** 确认。

   您将被提示同意服务条款。

4. 同意服务条款。

   工具安装好了。这取决于您的连接速度。


### 安装Node包管理器(NPM)
{:.no_toc}

来自各个国家的开源开发人员都使用NPM来共享称为包的软件组件。动物王国使用React、Babel和许多其他组件。您将使用`npm`命令来安装这些打包的组件。

 1. 打开系统上的终端窗口。
 2. 使用`which`命令验证您已经安装了`npm`。

     <img src="images/command-line.png" alt="">

     如果安装了`npm`，`which`将返回命令在您的环境中的位置。

3. 如果`npm`命令不在您的系统中， <a href="https://www.npmjs.com/get-npm" target="\_blank">请根据操作系统的说明安装它。</a>.

   安装NPM工具可能需要几分钟，这取决于您的连接速度。

## 获取动物王国代码

在本节中，您将动物王国的代码复制到你的工作站上。

1. 在您的浏览器中(推荐使用Chrome)，<a href="https://github.com/blockstack/animal-kingdom" target="\_blank">打开动物王国代码库。</a>

   AnimalKingdom代码保存在公共GitHub存储库中。

2. 单击 **Clone 或者 download** 按钮。

   如果您有一个GitHub帐户，您可以选择克隆原始存储库，或者fork，然后克隆它。以下说明假定您正在下载代码。

3. 选择动物王国 **Download ZIP**。

   <img src="images/kingdom-copy.png" alt="">

4. 检查您的下载目录以获得`animal-kingdom-master.zip`文件。
5. 将下载的zip文件复制到保存代码项目的目录中。
6. 解压文件。

   <img src="images/kingdom-download.png" alt="">

   解压文件之后，查看`animal-kingdom-master` 目录。

7. 在您的终端中，通过输入改变目录:

   ```bash
   $ cd animal-kingdom-master
   ```

   使用`pwd`命令确认您在哪个目录中。

   ```bash
   $ pwd
   /Users/manthony/animal-kingdom-master
   ```

8. 花一分钟回顾一下动物王国项目中的文件和子目录。

   使用`ls`命令列出目录内容。

   <table class="uk-table uk-table-striped">
   <tr>
   <th><b>名称</b> </th>
   <th><b>描述</b></th>
   </tr>
   <tr>
   <td><code>README.md</code></td>
   <td>包含一个建立和运行动物王国的参考。 </td>
   </tr>
   <tr>
   <td><code>package.json</code></td>
   <td>一个NPM项目文件和一个相应的<code>.lock</code> 文件。</td>
   </tr>
   <tr>
   <td><code>public</code></td>
   <td>复制到正在构建的站点根目录中的文件。</td>
   </tr>
   <tr>
   <td><code>cors</code></td>
   <td>支持跨源请求配置的文件。</td>
   </tr>
   <tr>
   <td><code>src</code></td>
   <td>React网站源代码。&nbsp;&nbsp;这包含配置文件。</td>
   </tr>
   </table>

## 在开发模式中构建示例

您可以在本地工作站上构建和运行动物王国。在运行程序之前，使用NPM安装所有依赖的包。`npm`为您安装的一个关键包是Blockstack Javascript库。

1. 确保您在项目的根目录中。

    ```bash
    cd ~/animal-kingdom-master
    pwd
    /Users/manthony/animal-kingdom-master
    ```

2. 输入 `npm install` 获取动物王国所需的软件组件。

    ```bash
     $ npm install

     > fsevents@1.2.4 install /Users/manthony/animal-kingdom-master/node_modules/fsevents
     > node install

     node-pre-gyp WARN Tried to download(404): https://fsevents-binaries.s3-us-west-2.amazonaws.com/v1.2.4/fse-v1.2.4-node-v67-darwin-x64.tar.gz
     node-pre-gyp WARN Pre-built binaries not found for fsevents@1.2.4 and node@11.1.0 (node-v67 ABI, unknown) (falling back to source compile with node-gyp)
      SOLINK_MODULE(target) Release/.node
      CXX(target) Release/obj.target/fse/fsevents.o
     In file included from ../fsevents.cc:6:

      ...

     added 1390 packages from 766 contributors and audited 15238 packages in 16.11s
     found 1 high severity vulnerability
      run `npm audit fix` to fix them, or `npm audit` for details
     $
    ```

    该命令为项目代码创建一个 `node_modules` 子目录，并安装动物王国项目所需的所有代码库。

3. 输入 `ls` 命令，列出项目目录的内容，以验证是否正确安装了`npm` 。

    ```
    $ ls
    ```

    `node_modules`目录包含许多动物王国使用的核心库。例如，Blockstack Javascript库位于
    `nodule_modules/blockstack/lib` 子目录中。


## 启动你的动物王国DApp

1. 在您的工作站上启动动物王国DApp，输入:

   ```bash
   npm run start
   ```

   `npm` 程序使用`scripts/start.js` 文件来打包动物王国应用程序。一旦代码被打包，DApp就会在浏览器的`http://localhost:3000`中打开动物王国。

2. 从初始化的动物王国画面中，选择一个动物人和一个地域。

   <img src="images/initialkingdom.png" alt="">

3. 在页面的底部点击 **Done**。

   动物王国调用Gaia hub来存储您的选择。短暂的停顿之后，DApp会返回到您的**王国页面**。如果您有问题，刷新页面并单击菜单中的**王国**。

   <img src="images/kingdom-ruler.png" alt="">

4. 花点时间研究一下这个应用程序

   例如，您可以编辑您的动物或访问其他页面，如**Animals**或**Territories**。

5. 回到您启动应用程序运行的终端。
6. 按`CTRL-C`停止应用程序。

   <img src="images/kingdom-stop.png" alt="">

您可以使用`npm run start`命令重新启动应用程序，正如您将在本教程的后面所做的那样。

## blockstack开发人员的资源

Blockstack提供了一些资源来帮助开发人员在平台上进行构建。花点时间研究一下这些资源:

* 访问 <a href="https://forum.blockstack.org/" target="\_blank">Blockstack 论坛</a>。这是了解其他开发人员现在或过去遇到的问题的宝贵资源。
* 访问 <a href="https://community.blockstack.org/" target="\_blank">Blockstack 社区网站</a>了解您所在地方可能发生的事件。
* 加入 Blockstack <a href="https://slofile.com/slack/blockstack" target="\_blank"> Slack </a> 您可以通过填写以下<a href="https://docs.google.com/forms/d/e/1FAIpQLSed5Mnu0G5ZMJdWs6cTO_8sTJfUVfe1sYL6WFDcD51_XuQkZw/viewform">表单</a>加入该通道。


## 下一步
{:.no_toc}

在本节中，您了解了Blockstack平台，以及为什么它通过封装Blockstack后端的复杂性使区块链开发成为一个轻松的过程。您还为开发Blockstack web应用程序设置了一个典型的开发环境。最后，您启动并运行了本地的Animal Kingdom应用程序。

在下一节中，您将研究应用程序代码，并了解DApp中哪些记录的元素适合 App Mining。下一节 [Zero-to-DApp, 3 of 4](zero_to_dapp_3.html).
