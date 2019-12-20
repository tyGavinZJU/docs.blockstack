---
layout: usenew
description: Use a Blockstack ID with a DApp
permalink: /:collection/:path.html
---
# 如何控制你自己的数据

当您使用Blockstack的去中心化应用程序(DApp)时，您进入该应用程序的数据、照片、文档等都是您自己拥有和控制的。Instagram或PayPal等传统应用程序将您的数据存储在它们的公司服务器上。

Blockstack DApps不允许应用程序将您的数据存储在应用程序的公司服务器上。相反，您可以选择一个存储提供程序来存储数据。Gaia hub为您的应用程序数据提供了个人存储。

如果您想离开某个特定的DApp，甚至不需要导出数据。您只需停止使用DApp，它就不再能够读取或修改您的数据。如果您想开始使用具有相同数据的不同DApp，您可以这样做。

## 了解Gaia hub提供商

Blockstack生态系统提供了一种名为Gaia的数据存储技术。Gaia是用于存储应用程序数据的存储中心技术。存储提供程序只是实现Gaia并为用户提供存储中心的组织。任何组织或个人都可以创建Gaia存储系统并成为Gaia hub提供商。

这些提供者将数据驻留在他们选择的一个或多个现有存储系统中。这些存储系统通常是云存储系统，如Amazon、Dropbox、iCloud或Azure等。

在Blockstack浏览器中创建标识的用户可以选择使用哪个Gaia hub提供者。Blockstack本身运行一个Gaia hub并充当hub提供者。默认选择是Blockstack-run Gaia hub。

每个提供者都会将您的数据存储在特定的地址或URL。这些地址看起来与您在web浏览器中输入的任何地址相似。当您登录到DApp时，您就赋予了该应用程序代表您将数据保存到URL的行为。

## 数据存储的当前限制

以下是当前系统的局限性。

* 您不能将存储从一个提供程序移动到另一个提供程序。
* 您不能将数据存储在自己的计算机上。

Blockstack一直在寻求扩展Gaia的能力。随着Gaia新特性的出现，这些限制将会消失。