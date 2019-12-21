
使用下面的表格来回答关于密钥/短语/值(keys/phrases/values)的问题，您可以与他人共享这些密钥/短语/值(`可共享的`)，以及一些您不应该与他人共享、而应该保存在安全位置(`受保护`)的密钥/短语/值。

<table class="uk-table-small uk-table-striped uk-overflow-auto">
   <tr valign="top">
      <th class="uk-width-large">Phrase/Key/Value</th>
      <th>Security</th>
      <th class="uk-width-medium">Description</th>
   </tr>
   <tr valign="top">
      <td>
         <p>Secret Recovery Key</p>
      </td>
      <td><p>PROTECT</p></td>
      <td>
         <p>用于访问Blockstack区块链上的标识。一个24字的单词序列，例如: </p>
         <p><code>applied binge crisp pictorial fiery</code>
         </p><p><code> dancing agreeable frogs light finish ping apple</code></p>
         <p>早期的Blockstack恢复Key是12个单词的序列。</p>
      </td>
   </tr>
   <tr valign="top">
      <td>
         <p>identity</p>
         <p>Blockstack identity</p>
         <p>Blockstack ID</p>
         </td>
      <td><p>SHAREABLE</p></td>
      <td>
         <p>一种在Blockstack网络上识别个人或组织的方法。一个身份标示是唯一的， <code>meepers.id.blockstack</code> 或者 <code>chad.id</code> 是2个IDs例子.</p>
      </td>
   </tr>
   <tr valign="top">
      <td>Magic Recovery Code</td>
      <td><p>PROTECT</p></td>
      <td><p>一个长的加密字符串，例如:</p> <p> <code>36mWivFdy0YPH2z31EflpQz/Y0UMrOrJ++lH=0EI7c3mop2JuRBm5WXxSTazJsUjOA...</code></p> <p>也不要分享你的恢复码附带的二维码。这是一个二维码:</p> <img src="/org/images/qr-code.png"/>
      </td>
   </tr>
   <tr valign="top">
      <td>Blockstack Owner Address</td>
      <td><p>SHAREABLE</p></td>
      <td>
      <p>看起来像一个比特币地址，但以 <code>ID</code> 开头，例如:</p> <p><code>ID-1J3PUxY5uDShUnHRrMyU6yKtoHEUPhKULs</code></p>
       </td>
   </tr>
   <tr valign="top">
      <td>Bitcoin address
         BTC Address
      </td>
      <td><p>SHAREABLE</p></td>
      <td><p>一串字母和数字。</p>
    <p><code>3E53XjqK4Cxt71BGeP2VhpcotM8LZ853C8</code></p>
        <p>分享这个地址允许任何人将比特币发送到该地址。</p>
      </td>
   </tr>
   <tr valign="top">
      <td><p>Stacks address or STX address</p>
      </td>
      <td><p>SHAREABLE</p></td>
      <td>
       <p>一串字母和数字。</p> <p><code>3E53XjqK4Cxt71BGeP2VhpcotM8LZ853C8</code></p> <p>分享这个地址允许任何人将STX发送到该地址。</p>
      </td>
   </tr>
   <tr valign="top">
      <td>public key</td>
      <td><p>SHAREABLE</p></td>
      <td><p>公钥和私钥对由两个唯一相关的加密密钥组成。它看起来像一长串随机的字母和数字:</p>
         <p><code>3048 0241 00C9 18FA CF8D EB2D EFD5 FD37 89B9 E069 EA97 FC20 …</code></p>
      <p>公钥和私钥的确切格式取决于创建它们所用的软件。</p>
      </td>
   </tr>
   <tr valign="top">
      <td>private key</td>
      <td>PROTECT</td>
      <td><p>私钥与对应的公钥匹配。公钥看起来也像一串字母和数字:</p>
      <img src="/org/images/private.png"/>
         <p>公钥和私钥的确切格式取决于创建它们所用的软件。</p>
      </td>
   </tr>
   <tr valign="top">
      <td>
         <p>seed phrase</p>
      </td>
      <td><p>PROTECT</p></td>
      <td>
         <p>用于访问Stacks钱包软件。 种子短语由24个单词组成。<em>单词及其位置顺序</em>都很重要。</p><p>写下你的种子短语，并把它储存在一个安全的地方，比如一个保险箱。当你写下种子短语时，包括它的位置，例如，<code>1-frog, 2-horse, 3-building</code> 等等，直到你到达最后一个位置， <code>24-ocean</code>.</p>
      </td>
   </tr>
      <tr valign="top">
      <td>
         <p>wallet address</p>
      </td>
      <td><p>SHAREABLE</p></td>
      <td>
       <p>
         如果您使用Stacks钱包软件创建了一个纯软件钱包，该钱包有一个单独的STX地址，有时也称为<em>Stacks (STX) 地址。</em>。用<em>种子短语</em>您访问一个软件钱包。
       </p>
      </td>
   </tr>
</table>
