---
layout: storage
description: "Storing user data with Blockstack"
permalink: /:collection/:path.html
---
# 一个去中心化存储架构

Blockstack网络使用名为Gaia的存储系统存储应用程序的数据。事务性的元数据存储在Blockstack区块链上，而用户应用程序数据存储在Gaia存储中。 在区块链之外存储数据可确保Blockstack应用程序可以为用户提供高性能和高可用性的数据读写，而无需引入中央信任方。

* TOC
{:toc}

##  了解Blockstack架构中的Gaia

下图描述了Blockstack架构及其在Gaia中的位置：

{% include architecture.md %}

## 用户所有权或Gaia如何是去中心化的？

Gaia Hub 作为写入数据存储的服务运行。 Hub服务通过要求来自请求者的有效身份验证令牌来写入数据存储。 通常情况下，Hub服务在计算资源上运行，而存储本身在单独的专用存储资源上运行。 通常情况下，两个资源都属于同一个云计算提供商。

![Gaiastorage](/storage/images/gaia-storage.png)

Gaia的分散管理方法关注在用户对数据及其存储的控制。 如果用户可以选择要使用的Gaia hub提供商，则该选择就是启用用户控制的应用程序所需的所有去中心化操作。

用户数据的控制在于访问用户数据的方式。
当应用程序为给定用户`alice.id` 获取文件 `data.txt` 时，查找将遵循以下步骤：

1. 为 `alice.id` 获取 `zonefile`。
2. 从她的`zonefile`中读取她的个人资料网址。
3. 获取 Alice's 资料
4.  _验证_ 这个资料是用 `alice.id` 的密钥签名的
5. 从资料里面读 `gaiaHubUrl`  (例如 `https://gaia.alice.org/`)
6. 从`https://gaia.alice.org/data.txt`获取文件


因为`alice.id`可以访问她的zonefile，所以她可以更改配置文件的存储位置。 例如，如果当前配置文件的服务或存储受到损害，她可能会这样做。 为了更改个人资料的存储位置，她将自己的Gaia hub的URL从其他hub提供商更改为另一个Gaia hub的URL。 如果Alice自己有足够的计算和存储资源，则可以运行自己的Gaia存储系统，并绕开商业Gaia hub提供商。

{% include note.html content="已经有身份的用户尚无法将其数据从一个gaia hub迁移到另一个gaia hub。" %}

直接代表Alice的应用程序不需要执行查找操作。 相反，Blockstack的<a
href="http://blockstack.github.io/blockstack.js/index.html"
target="\_blank">身份验证流程</a>向应用程序提供了Alice选择的应用程序根URL。 由于Alice的浏览器必须生成身份验证响应，因此该身份验证流程也处于Alice的控制范围内。


## 了解数据存储

Gaia hub 按给定的写入信息明文存储。 它提供有关数据的最小保证。 它不能确保数据被有效格式化，也不能确保包含有效签名或被加密。其设计理念是这些数据的存储方式应该是是客户端的关注点。

客户端库（例如`blockstack.js`）能够提供这些保证。 Blockstack使用了<a href="https://en.wikipedia.org/wiki/End-to-end_principle" target="\_blank">端到端原理</a>的自由定义来指导这种设计的决策。

## Gaia与其他存储系统相比

Gaia与其他去中心化存储系统的技术栈如下。为简洁起见，所有存储系统共有的功能都将省略。

<table class="uk-table uk-table-striped">
<thead>
  <tr>
    <th>Features</th>
    <th>Gaia</th>
    <th><a href="https://sia.tech/" target="\_blank">Sia</a></th>
    <th><a href="https://storj.io/" target="\_blank">Storj</a></th>
    <th><a href="https://ipfs.io/" target="\_blank">IPFS</a></th>
    <th><a href="https://datproject.org/" target="\_blank">DAT</a></th>
    <th><a href="https://www.scuttlebutt.nz/" target="\_blank">SSB</a></th>
  </tr>
  </thead>
  <tr>
    <td>用户控制数据的托管位置</td>
    <td>X</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>可以在普通的Web浏览器中查看数据</td>
    <td>X</td>
    <td></td>
    <td></td>
    <td>X</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>数据读/写</td>
    <td>X</td>
    <td></td>
    <td></td>
    <td></td>
    <td>X</td>
    <td>X</td>
  </tr>
  <tr>
    <td>数据可以删除</td>
    <td>X</td>
    <td></td>
    <td></td>
    <td></td>
    <td>X</td>
    <td>X</td>
  </tr>
  <tr>
    <td>数据可以列出</td>
    <td>X</td>
    <td>X</td>
    <td>X</td>
    <td></td>
    <td>X</td>
    <td>X</td>
  </tr>
  <tr>
    <td>回收已删除的数据空间</td>
    <td>X</td>
    <td>X</td>
    <td>X</td>
    <td>X</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>数据查询具有可预测的性能</td>
    <td>X</td>
    <td></td>
    <td>X</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>可以委托写权限</td>
    <td>X</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>可以委托列表权限</td>
    <td>X</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>本机支持多个后端</td>
    <td>X</td>
    <td></td>
    <td>X</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>数据可全局寻址</td>
    <td>X</td>
    <td>X</td>
    <td>X</td>
    <td>X</td>
    <td>X</td>
    <td></td>
  </tr>
  <tr>
    <td>需要一种加密货币才能工作</td>
    <td></td>
    <td>X</td>
    <td>X</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>数据是内容寻址的</td>
    <td></td>
    <td>X</td>
    <td>X</td>
    <td>X</td>
    <td>X</td>
    <td>X</td>
  </tr>
</table>
