---
layout: learn
description: Blockstack Zero-to-DApp tutorial
permalink: /:collection/:path.html
image: /assets/img/zero-to-dapp.png
---
# 1 - About DApps and App Mining
{:.no_toc}

**Zero-to-DApp 1 of 4**

欢迎来到Blockstack Zero-to-DApp教程。本教程使用Blockstack平台向您介绍区块链技术和Blockstack生态系统。本教程将向您介绍DApp与传统应用程序的不同之处。您将构建并运行一个DApp。您还将了解Blockstack应用程序挖掘项目，该项目每月向DApp开发人员提供资金奖励。

本教程分为四个部分，这是第一部分，它包含以下主题:

* TOC
{:toc}

您可以在45分钟内完成整个Zero-to-DApp教程。如果您喜欢10分钟Hello-world代码示例，请参阅[Hello, Blockstack教程](/browser/hello-blockstack)。

### 学习本教程所需的技能
{:.no_toc}

本教程是为开发人员和其他想了解DApps以及Blockstack生态系统如何支持它们的开发。因此，目标受众是广泛的。任何能够使用Windows、Mac或Linux计算机并熟悉命令行的人都应该能够使用本教程。

如果您擅长以下方向，即使您没有编程经验，也有可能完成本教程。知识渊博的开发人员应该能够轻松地在一个小时内完成本教程。

如果您是一名超强的开发人员，您可能希望略读或快速浏览页面，这也没有问题。

{% include note.html content="为了获得最佳效果，请使用Chrome浏览器。 目前，Blockstack浏览器在Chrome中运行得最好，在使用Safari或Firefox等浏览器时可能会遇到问题。目前不支持IE和Edge浏览器。" %}


## 传统应用程序和去中心化应用程序有何不同

在本教程中，您将构建、运行、修改和部署一个名为Animal Kingdom的去中心化应用程序(DApp)。DApp使用区块链技术对应用程序平台的身份验证和数据存储组件进行验证。区块链应用程序是去中心化的应用程序，这意味着它们将数据控制和身份管理从中央机构和组织转移到个人用户。

因数据泄露而导致身份被盗或丢失的人都明白，集中式应用程序会带来个人风险。曾在国外生活或访问过外国，但由于政府审查而无法访问网站、服务或信息的人，都知道集中化如何影响人们的生活。

用户和企业认为DApps很有价值，因为它们解决了传统应用程序的中心化问题。下表描述了传统应用和区块链应用各自的特点:

<table class="uk-table uk-table-small uk-table-divider">
  <tr>
    <th>传统应用程序</th>
    <th>去中心化应用程序</th>
  </tr>
  <tr>
    <td>用户必须为每个服务或应用程序创建许多用户名和密码组合。必须管理和维护每个组合。而且，每次创建都需要用户向第三方提供重要的或唯一的信息。</td>
    <td>用户创建并拥有一个或多个身份。他们在所有应用程序和服务中使用自己的身份。例如，用户可以使用与社交媒体相同的身份在线购买书籍。</td>
  </tr>
  <tr>
    <td>多个第三方应用程序和服务在后端服务器中存储来自单个用户的个人数据。这些后端服务器由应用程序或服务控制。离开应用程序的用户会留下他们的数据。</td>
    <td>个人信息和数据是加密的，并在用户的控制下。用户离开应用程序时没有留下任何数据，因为应用程序没有存储任何数据。</td>
  </tr>
  <tr>
    <td>跨许多服务器的多个帐户使个人数据容易受到攻击、误用和不受控制的收集。</td>
    <td>用户可以审计对其数据的访问，并知道谁访问了其数据以及访问了哪些数据。</td>    
  </tr>
  <tr>
    <td>中央当局和中间人控制网络访问，使他们能够审查应用程序和/或使用它们的用户。</td>
    <td>一些公司正在开发基于点对点网络的区块链。这些未来的网络可能使关闭或完全阻塞去中心化的应用程序变得几乎不可能。</td>    
  </tr>
</table>

构建DApp时使用的区块链技术决定了应用程序可用的特性。

## 创建一个身份来尝试您的第一个DApp

Blockstack Web浏览器是一个Web的DApp。用户可以使用它在Blockstack生态系统中创建和管理身份。使用Blockstack平台构建的DApps，使用浏览器提供给用户的登录序列。目前，用户可以免费创建Blockstack ID或购买自己的ID。

如果您还没有创建自己的Blockstack ID，那么现在就创建它。在创建ID时，请考虑传统应用程序中哪些交互是您熟悉的，哪些不是。

{% include create_id.md %}

如果您已经有了一个Blockstack ID，那么启动浏览器并尝试重新设置它。或者尝试使用以前从未使用过的设备或浏览器软件登录。

## 使用App Mining开拓DApp市场

区块链应用程序对于应用程序开发人员和应用程序用户来说都是一个新的范例。任何市场的新范式，比如太阳能或电动汽车，都需要公共和私人联盟来发展。被称为云计算的集中式主机和服务曾经是新的范例。推动云计算市场增长的，是来自政府和私营企业的数十亿美元资金投资和激励措施。

<div class="uk-card uk-card-default uk-card-body">
<h5>App Mining资格要求</h5>
<p>符合应用程序挖掘条件的DApps必须:</p>

<ul>
<li>实现Blockstack身份验证</li>
<li>邀请公众注册和使用</li>
</ul>

<p>在Gaia存储中心存储数据是可选的。将来可能会需要它。</p>

<p>在学习这个Zero-to-DApp教程时，您将构建和部署一个示例
满足这些要求的应用程序。虽然您构建的应用程序不适合应用程序挖掘，完成教程后，你就有资格获得免费的限量版t-shirt:</p>

<p><img class="uk-align-center" src="images/tshirt-blank.png" alt=""></p>

<p>在本教程的第4部分中，您将学习如何获得您的t-shirt。</p>

</div>

## 您将构建的DApp的概述

你要建立的是一个叫做动物王国（Animal Kingdom）的DApp。动物王国（Animal Kingdom）是一个Web DApp。用户登录它，可以创建一个动物角色，统治一个特定的领域。人物和地域的结合是一个王国。一旦你创建了一个王国，你可以添加其他王国的臣民。

动物王国与两个Blockstack服务交互，[Blockstack
Browser](https://browser.blockstack.org) 和 [Gaia data storage hub]
(https://hub.blockstack.org/). Blockstack浏览器本身是一个DApp。 存储中心纯粹是一个服务，没有面向用户的功能。

下表描述了DApp中的关键交互和截图。

<table class="uk-table uk-table-striped">
  <tr>
    <th>Click to enlarge</th>
    <th> Description</th>
  </tr>
  <tr>
    <td><div uk-lightbox="animation: slide">
         <a class="uk-inline" href="images/kingdom-enter.png" data-caption="Users must login with a Blockstack identity.">
             <img src="images/kingdom-enter.png" alt="">
         </a>
    </div>
    </td>
    <td><p>用户使用Blockstack身份进行登录(身份验证)。通过身份验证，用户赋予应用程序获取和将数据放入用户的Gaia存储中心的能力。</p></td>
  </tr>
  <tr>
    <td><div uk-lightbox="animation: slide">
          <a class="uk-inline" href="images/kingdom-signin.png" data-caption="Blockstack login dialogs.">
              <img src="images/kingdom-signin.png" alt="">
          </a>
     </div>
     </td>
    <td><p>Blockstack登录对话框是Blockstack浏览器的一部分，它本身就是一个DApp。一旦用户通过身份验证，DApp代码就会自动将他们返回到他们试图进入的王国。</p></td>
  </tr>
  <tr>
  <td><div uk-lightbox="animation: slide">
    <a class="uk-inline" href="images/kingdom-new.png" data-caption="Choose a persona and territory.">
        <img src="images/kingdom-new.png" alt="">
    </a>
    </div></td>
  <td><p>第一次到一个王国的游客会被提示创建一个动物角色和要统治的领土。 一旦他们做出选择，用户点击<strong>Done</strong> 来创建一个王国来统治。 关于用户选择的数据存储在用户的Gaia中心。</p>
  </td>
</tr>
<tr>
  <td> <div uk-lightbox="animation: slide">
     <a class="uk-inline" href="images/kingdom-choices.gif" data-caption="Choose a persona and territory.">
      <img src="images/kingdom-choices.gif" alt="">
    </a>
   </div></td>
  <td><p>每个王国都有动物和领地。用户可以编辑他们原来的角色/动物组合。您将学习如何修改动物王国代码来添加新的动物和领土。</p></td>
</tr>
<tr>
  <td><div uk-lightbox="animation: slide">
  <a class="uk-inline" href="images/kingdom-subjects.gif" data-caption="Adding subjects">
      <img src="images/kingdom-subjects.gif" alt="">
  </a>
  </div></td>
  <td>
  <p>用户可以添加来自他们自己的动物王国领土的主题。每当用户添加一个主题时，DApp都会更新用户的Gaia中心。用户还可以访问其他动物王国设置，以及从这些王国添加主题。您将了解如何修改安装中可用的其他王国。
  </p>
  </td>
</tr>
</table>

您可以使用您的Blockstack身份登录到<a href="https://animalkingdoms.netlify.com/" target="\_blank">Blockstack Animal Kingdom</a>尝试这个应用程序的完整版本。

## 接下来做什么？
{:.no_toc}

本节介绍了去中心化应用程序(DApp)的优点。您还了解到，与其他新范例类似，公共和私有公司都投入了大量资源来开发区块链技术。最后，您了解到，Blockstack的设计目的是让您能够快速构建一个DApp并进入这个新兴市场。

在下一节中，您将了解更多关于开发DApps的信息，以及它们与传统应用程序的不同之处。您还将了解Blockstack为DApp开发人员提供的资源，这些资源可以帮助您明确将精力放在何处以及如何为它们提供资金。

下一节 [2 of 4, Zero-to-DApp](zero_to_dapp_2.html).

