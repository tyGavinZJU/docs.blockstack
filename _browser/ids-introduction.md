---
layout: usenew
description: Use a Blockstack ID with a DApp
permalink: /:collection/:path.html
---
# 获取和使用 Blockstack ID
{:.no_toc}

通过Blockstack浏览器，您可以创建一个身份标识。你可以使用唯一的身份标识登录到允许使用**Blockstack 登录**的应用。当你通过DApps与他人互动时，你的身份标识是一个接触点。其他人可能是个人用户、公司或软件。除非您允许，否则这些其他任何人都不能访问身份标识以外的任何东西，例如`moxiegirl.id.blockstack`。通常情况下，别人必须要求更多地了解你，你可以选择分享 &ndash; 或者不分享。

本文档解释了免费的Blockstack ID，尽管你可以通过付费获得其他的。您将了解如何创建一个Blockstack ID，如何使用ID进行登录，以及如何删除ID关联的数据。它包括以下部分:

* TOC
{:toc}

## 了解身份标识如何在blockstack生态系统中发挥作用

在本节中，您将学习有关身份标识的知识，以便安全地使用它。

### 为什么身份标示不是帐户

在今天的互联网上，你为一个应用程序创建的帐户将保留在提供该应用程序的公司。该公司保存你输入的关于你自己的数据和收集你如何使用他们的应用程序的数据。这些数据都是有价值的公里利用你的数据去吸引广告商，当你停止使用应用并且关闭账户时，公司会保留这些数据因为就数据也是有价值的。

公司将您访问的不同应用程序的数据组合在一起，以构建您的个人资料。这个资料让他们针对你的特定信息和构建你的经验。例如，广告商可以确定你是否对某个产品感兴趣，以及他们可以向你收取多少费用。作为允许这种微妙的消息传递给您和隐私缺失的回报，您将收到一个免费的应用程序或服务。

去中心化身份是一种使用应用程序而不需要提供数据的新方法。一个去中心化身份是用户名和密钥的组合。与该身份相关的数据将保留在其中，这意味着大公司、它们的应用程序或中央机构无法建立关于您的个人资料。你仍然是有隐私的。

Blockstack ID是一个去中心化的身份。您可以使用这个单一身份登录到带有**用Blockstack登录**按钮的去中心化的应用程序(DApps)，单一身份允许您访问100多个应用程序。当您登录到DApp时，您将创建数据，但这些数据将使用您的身份进行加密和存储。当您退出应用程序时，应用程序将无法读取这些数据，因此它无法利用这些数据来建立您的个人资料或将您的数据出售给其他公司。您的隐私将得到保护。

### 如何获得Blockstack身份标识

将ID看作一种身份验证的形式，就像驾照一样。每个身份标识都是唯一的，但是这个驾照可以在虚拟的互联网高速公路上识别你。一个身份标识是通过一个注册商创建的，注册商有很多。当你创建了一个Blockstack ID时，注册商将在Stacks区块链上记录你的身份创建。

Blockstack浏览器允许新用户创建免费IDs。这些免费的IDs在ID中包含了单词`blockstack` ，比如`meepers.id.blockstack`。名称的附加`blockstack`部分称为命名空间。它只是意味着所有的名字都属于一个特定的实体。您不必使用免费的`id.blockstack` 标识。您还可以购买一个只有惟一名称和.id部分的标识。

创建的第一个Blockstack ID是主ID。一旦创建了主标识，就可以向其添加其他子标识。子标识可以使用`id.blockstack`或`.id`格式。您可能创建子标识的原因与您拥有工作和家庭电子邮件的原因相同。

如果你想要一个没有`blockstack`命名空间的主标识，你可以买一个。例如购买的一个ID例子是`larry.id`。`.id`指定是必需的，`larry`部分是唯一的字符串。

### 什么是钥匙?

Blockstack IDs有密钥。这些钥匙解锁你的身份，就像打开一扇私人家的门。你应该把你的身份密钥并放在安全的地方。Blocktack会为你创建你的身份密钥。有两个和key关联的重要信息:

* 密钥本身也称为_magic recovery key_，它是一个单词序列 `applied binge crisp pictorial fiery dancing agreeable frogs light finish ping apple`
* _secret recovery code_ 是一个加密的字符串, `36mWivFdy0YPH2z31EflpQz/Y0UMrOrJ++lH=0EI7c3mop2JuRBm5W1P0BwXxSTazJsUjOAmC55rFUWINqDqGccLio0iwzGclAhaHGZQ5M52`

当你创建Blockstack ID时，Blockstack会向您发送一封电子邮件，其中包含可以用来查看密钥的恢复代码。您只接收一次恢复代码。当你收到这封邮件时，你应该**立即查看密钥恢复key**并保存到安全位置，如密码管理器。

<div class="uk-card uk-card-default uk-card-body">
<p>当使用Blockstack注册可读的ID和恢复key，您必须记录如下内容：
</p>
<ul>
<li>secret recovery key</li>
<li>magic recovery code (按单词出现的顺序排列)</li>
<li>初始化密码 (密码将被保留到浏览器直到你 <strong>重置</strong> 浏览器)</li>
</ul>
<p>Blockstack 不存储密钥或恢复代码，所以如果您丢失了密钥或恢复代码，它就不能在以后将它们提供给您。</p>
</div>

### 在哪里可以使用Blockstack ID

您可以对Blockstack生态系统中的每个DApp使用您的Blockstack ID。要创建ID，可以使用名为Blockstack Browser的DApp。您创建的任何DApp数据都链接到这个ID。

例如，如果您向DApp添加一张图片，该图片将出现在DApp中，但是图片的大小和字节存储在您的个人存储中。当您使用ID登录到另一个DApp时，该应用程序可以请求访问您的存储。

访问 <a href="https://app.co/" target="_blank">App.co, 通用的DApp商店</a> 查找您可以使用Blockstack ID的应用程序。

## 创建一个初始Blockstack ID

{% include create_id.md %}

## 使用存在的Blockstack ID登录

当您返回到Blockstack浏览器时，浏览器提示您创建一个新的Blockstack ID或使用现有的Blockstack ID登录。

![](images/existing-id.png)

在这个对话框中，你可以选择这两种方法:

* 方法1:提供一个单词序列的secret recovery key (`applied binge ...`)
* 方法2:提供您创建身份时使用的magic recovery code (' 36mWivFdy0YPH2z31E…')和密码

如果您丢失了magic recovery code或您在丢失了初始化创建您的身份时提供的密码，您不能再使用方法1登录你的身份。如果您丢失了secret recovery key，您将不能再使用方法2。一旦你不能再使用任何一种方法，你的身份就会被疏远任何人都无法访问，甚至是Blockstack。

### 使用secret recovery key登录

1. 在浏览器中打开[Blockstack web应用程序](https://browser.blockstack.org/sign-up?redirect=%2F).

2. 选择 **使用现有的ID登录**.

   系统将显示一个对话框，您可以在其中输入recovery code或recovery key。

3. 输入 recovery key.

   recovery key是一个单词序列。

   ![](images/recovery-key.png)

4. 点解 **下一步**.

   系统提示您输入电子邮件地址。这封邮件可以是你的以前输入的或新的。Blockstack不会存储这个邮件地址; 邮件只是在Blockstack Browser和你进行重要信息交互的时候使用。

5. 输入邮件点击 **下一步**.

   系统提示您输入密码并进行确认。这个密码可以是你以前输入的，也可以是一个全新的。记录下这个密码下来。您可以在当前的Blockstack浏览器中使用密码交互以显示您的密钥链或更改您的密码。Blockstack不会将此信息存储到会话之后。

6. 输入密码点击 **下一步**.

   系统欢迎你回来。

   ![](images/welcome-back.png)

   此时，您可以使用DApps继续工作，或者查看您的recovery key。

### 使用agic recovery code和原始密码登录

1. .在浏览器中打开[Blockstack web应用程序](https://browser.blockstack.org/sign-up?redirect=%2F).

2. 选择 **Sign in with an existing ID**.

   系统将显示一个对话框，您可以在其中输入recovery code或recovery key。

3. 输入magic recovery code.

  recovery code是一个加密的字符串。

  ![](images/recovery-code.png)

4. 点击 **下一步**.

   系统提示您输入电子邮件地址。这封邮件可以是你的以前输入的或新的。Blockstack不存储这个邮件地址;它将在您当前的Blockstack浏览器交互期间使用与你交流重要的信息。

5. 输入邮件地址点击 **下一步**.

   系统提示您输入密码。**这一定是当你第一次创建你的身份时输入的密码。**如果你忘记了这个密码，Blockstack不能提供给你。相反，你必须切换到使用你的recovery key而不是您的代码来登录到您的身份。

6. 输入你的原始密码点击 **下一步**.

   系统欢迎你回来。

   ![](images/welcome-back.png)

  此时，您可以使用DApps工作，或者查看您的recovery key。

## 能删除一个Blockstack ID吗?

ID被记录在Blockstack的区块链上;因此，一旦创建了身份，就不能删除它。您可以放弃或停止使用您的ID。像这样的脱离的身份不能被其他个人或组织使用，因为只有你可以访问ID的12个字的恢复短语。

但是，您**可以删除**与您的ID关联的数据。如果您将该ID与默认的Blockstack Gaia存储中心一起使用，那么删除存储只能是*可能的*。如果您的ID使用您自己的或另一个Gaia存储中心，Blockstack不能删除数据，相反，您应该联系您的存储中心提供商的服务。

执行以下操作删除与您的ID一起提供的默认存储。

1. 登录到Blockstack浏览器。
2. 选择 <a href="https://browser.blockstack.org/profiles/i/all" target="_blank"><strong>Identity > More page</strong></a>.

   此页面列出您的**默认ID**和与之相关的任何其他ID。每个ID都有一个与之关联的Gaia存储位置。您可能只有一个ID，这是典型的情况。

3. 确定你在使用 <a hreg="https://browser.blockstack.org/account/storage" target="_blank">默认存储hub</a>.

   如果你使用默认的hub，页面看起来是这样的:

   ![](images/defaultstorage.png)

4. 访问 <a href="https://browser.blockstack.org/profiles" target="_blank"><strong>Identity</strong></a> 页.

5. 输入 `Delete Me` 和请求 **Full Name** 和 **Short Bio**的日期。

   ![](images/deleteme.png)

6. 点击 **保存**.

7. 将id列表发送到 <a href='mailto:support@blockstack.com'>support@blockstack.com</a>, 您的电子邮件内容应该包含以下详细信息:

   ```txt
   请删除与下列id相关的Gaia存储:
   - user1.id.blockstack
   - user2.id
   - user3.id.blockstack
   所有这些id使用的Gaia默认存储。
   ```

   支持团队将回复一封电子邮件，确认您的数据已被删除。
  
8. 要确认您的数据已被删除，请导航到 <a href="https://explorer.blockstack.org/" target="_blank">the Blockstack Explorer</a> 然后在搜索栏中输入你的ID。

   你应该看到类似的东西如下:

   ![](images/deletedprofile.png)