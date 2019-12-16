
![Blockstack Architecture](/common/images/architecture.png)

区块链需要大量人之间的共识，因此会很慢。 此外，区块链设计的初衷并不是要去容纳大量数据。 这意味着对于用户而言在区块链上写入和存储的每一位数据都非常昂贵。 例如，设想一个应用程序在链中存储了所有tweet。

Blockstack使用分层方法解决了区块链性能问题。 该系统的基础是区块链和Blockstack 域名系统（BNS）。 区块链控制系统中域名（身份）的所有权，域名包含子域名、用户域名、与应用程序域名。

Blockstack中的域名与OSI（Open Systems Interconnection）中的路由数据相对应。 路由数据存储在第二层Atlas节点网络中。 加入Blockstack网络的每个核心节点都可以获取此路由数据的完整副本。 Blockstack使用路由数据将域名（用户域名，子域名和应用程序域名）与特定的存储位置相关联。

最后一层是Gaia存储系统。 Gaia系统由hub服务和云服务提供商（例如Azure，DigitalOcean，Amazon EC2等）上的存储资源组成。 通常，计算资源和存储资源属于同一云供应商。 Gaia当前具有对S3和Azure Blob存储的驱动程序支持，但该驱动程序模型还允许其他后端支持。

由于Gaia将应用程序和用户数据存储在区块链之外，因此Blockstack DApp通常比在其他区块链上创建的DApp具有更高的性能。 此外，用户可以选择数据的存储位置，Gaia使应用程序可以通过统一的API访问该用户数据。 当用户登录时，身份验证过程将为应用程序提供Gaia hub的URL，然后该hub将代表该用户写入存储。
