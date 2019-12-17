---
layout: usenew
description: Use a Blockstack ID with a DApp
permalink: /:collection/:path.html
---
# Install or uninstall the local browser
{:.no_toc}

如果您只想创建、管理和资助一个身份，然后与DApps交互，那么您应该使用[web 版本](browser-introduction.html)。如果您担心网络审查、高度安全问题，或者想自己开发一个DApp，您可能需要下载并安装浏览器的客户端版本;虽然这不是必需的。本页面解释如何在工作站上安装或卸载浏览器客户端.

* TOC
{:toc}


## 安装客户端版本

记住，对于大多数用户来说，blockstack浏览器web应用程序就足够了。只有当您对互联网或身份有额外的、高级的关注时，才需要安装客户端。虽然不是必需的，但是一些Dapp开发人员可能会发现安装客户端版本很有用。

blockstak浏览器安装程序是一个多上下文（_multiple-context_）的安装程序。如果您以用户身份运行它，则安装只对该用户有效。如果您以管理员身份安装，则安装适用于所有用户。要找到操作系统的安装程序，请访问[浏览器安装页面](https://blockstack.org/install)。

### On Mac

安装要求macOS High Sierra 10.12或更高版本。按以下步骤安装:

1. 从[浏览器安装页面](https://blockstack.org/install)下载OSX安装程序
2. 双击下载的DMG文件启动安装程序。

   ![](images/ubuntu-browser.png)

3. 将Blockstack应用程序拖动到应用程序文件夹。
4. 双击Blockstack应用程序启动它。

   打开文件时系统会显示一个通知:

   ![](images/dmg-notice.png)

5. 选择 **打开**.

   系统使用Blockstack浏览器应用程序打开默认浏览器，从您的机器(本地主机)运行。您还将在您的机器上看到blockstack图标

   ![](images/browser-on-mac.png)

   如果你已经通过Blockstack web应用程序加载了一个身份，你已经登录到本地应用程序:

   ![](images/browser-on-mac-1.png)


### On Windows

安装时需要Windows 10或更高版本。按以下步骤安装:

1. 从[浏览器安装页面](https://blockstack.org/install)下载Windows安装程序.
2. 双击安装程序包启动它.

   ![](images/windows-installer.png)

3. 打开windows **Start**菜单，并单击最近添加的**Blockstack浏览器**

   ![](images/windows-start.png)

   系统显示一个Windows安全警告.

   ![](images/windows-security.png)

4. 选择 **允许访问**.

   系统打开Blockstack浏览器应用程序

    ![](images/windows-browser.png)


### On Linux

在Linux上安装blockstack需要Docker。在安装Blockstack之前，安装适合您的操作系统的[Docker版本](https://docs.docker.com/install/).

>**注意**: 此过程中使用的blockstack脚本运行docker命令。根据在系统上安装和配置Dockered的方式，可能需要也可能不需要root或sudo权限。因此，下面的命令显示了sudo在与脚本或docker可执行文件交互时的用法。如果您的安装允许运行权限较低的Docker，则可以忽略它。

1. 从浏览器安装页面下载[Linux安装程序](https://blockstack.org/install)

   这将下载一个`Blockstack-for-Linux-v0.30.0.sh`脚本到本地.

2. 打开终端并导航到包含下载脚本的目录.

   当脚本下载完，它是不可执行的

3. 设置文件可执行

    ```bash
    $ chmod u+x Blockstack-for-Linux-v0.309.0.0.sh
    ```

4. 输入没有任何参数的命令来查看可用的子命令。

    ```bash
    $ sudo ./Blockstack-for-Linux-v0.309.0.0.sh
    blockstack docker launcher commands:
    Install-protocol-handler -> install a protocol handler for blockstack:// links
    ...
    ```

5. 使用`pull`获取所需的blockstack Docker镜像

    ```bash
    $ sudo ./Blockstack-for-Linux-v0.309.0.0.sh pull
    ```

    根据您的网络速度，这可能需要一些时间.

7. 使用`docker image ls`命令确认您拥有该镜像

    ```bash
    $ sudo docker image Is
    REPOSITORY  TAG IMAGE ID    CREATED
    quay.io/blockstack/blockstack-browser   v0.30.0 ad05fd844f59    2 days ago
    ```

8. 安装协议处理程序

    ```bash
    $  sudo ./Blockstack-for-Linux-vO.30.0.sh install-protocol-handler�
    Registering protocol handler
    ```

9. 启动blockstack容器.

    ```bash
    $ sudo ./Blockstack-for-Linux-vO.30.0.sh start
    c3092592e59abe3559fdb49d070a7aa5e99165c7d9f2flla20ecaf4e0dfc2f46�
    cd92f61ae473d54398da987f5023f5462b29c03f08584ebb3c9fIbb4cd790c69�
    Registering protocol handler
    ```

    系统将为您启动Blockstack浏览器应用程序.

    ![](images/ubuntu-browser.png)

在停止blockstack容器之前，应用程序将继续在系统上运行。要显示blockstack容器的状态，可以使用`docker container ls`命令

{% raw %}
```bash
$ sudo docker container ls --format '{{.ID}}\t{{.Image}}\t{{.Status}}\t{{.Ports}}\t{{.Names}}'
```
{% endraw %}

使用`./Blockstack-for-Linux-vO.30.0.sh stop`来停止blockstack浏览器及其容器.

## 卸载浏览器

如果您使用安装者安装浏览器，请遵循操作系统的说明.

### On Mac

1. 退出正在运行的blockstack应用程序.

   ![](images/quit-blockstack.png)

2. 检查是否有blockstack设备，如果有，则将其弹出.

   ![](images/eject-blockstack.png)

3. 使用Finder打开**Applications**文件夹.
4. 定位blockstack应用程序.
5. 打开`应用程序`文件夹，找到**Blockstack.app**.
6. 把应用程序拖到垃圾桶里.
7. 删除`/Users/USERNAME/Library/Application Support/Blockstack`文件夹.

   从命令行:

   ```bash
   $ rm -r /Users/moxiegirl/Library/Application\ Support/Blockstack
   ```

### On Windows

1. 打开**开始**菜单.
2. 点击 **Settings > System**.
3. 打开 **Apps & features** .

   ![](images/eject-blockstack.png)

4. 找到 **Blockstack Browser** 选择 **Uninstall**.

   ![](images/browser-uninstall.png)


### On Linux

blockstack安装依赖于Docker容器及其相关映像。它还包含一个必须删除的支持协议处理程序。如果您安装了Docker以便运行Blockstack，那么您也可以卸载Docker.

执行以下步骤卸载blockstack:

1. 如果Docker容器正在运行，停止并删除它们.

    ```bash
    $ sudo ./Blockstack-for-Linux-vO.30.0.sh stop
    stopping the running blockstack-browser containers
    69a686799d4f
    56fc6189ff97
    69a686799d4f
    56fc6189ff97
    ```

2. 删除关联的blockstack镜像.

    ```bash
    $ sudo docker image ls
    REPOSITORY                            TAG       IMAGE ID        CREATED
    quay.io/blockstack/blockstack-browser   v0.30.0 ad05fd844f59    3 days ago
    $ sudo docker image rm ad05fd844f59�
    Untagged : quay.io/blockstack/blockstack- browser :vO.30.0
    Untagged: quay.io/blockstack/blockstack-browser@sha256:b20c9514c56b99398fd4946af39e7537b807e85694943ac3b8807dlb3625833b
    Deleted: Sha256:ad05fd844f5948blee06a0a09228df946478393c0a7588cbc65dlb8817f5b34e
    Deleted: Sha256:7c3d0043f2ba01cf285f3fe09701b086c349b6380c2e42f25b31ac65c6626ec8
    Deleted: sha256:54ea2aa7d7d000e7483f299eeca9e5466fa86231f4cd4cld3c3096d97e61c5df
    Deleted: sha256:38e61054355adefc3c2de031462114a9946cfc0e44444a38a27d0f115aba0da2
    ....
    ```

3. 使用脚本删除协议处理程序

    ```bash
    $ sudo ./Blockstack-for-Linux-vO.30.0.sh remove-protocol-handler
    ```

4. 删除脚本.

    ```bash
    $ rm Blockstack-for-Linux-vO.30.0.sh
    ```
