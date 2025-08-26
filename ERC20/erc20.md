### ERC20 Token
> ERC20 代币是以太坊上最广泛采用的通缩（可互换）代币标准，是无数去中心化应用（dApps）的基本构建模块。

ERC20 代币是在以太坊（或其他 EVM 兼容）区块链上部署的智能合约，它遵循特定的技术标准（ERC-20）。该标准定义了一组所有合规代币必须实现的通用规则和功能。

#### 常见用例
* 数字货币
* dApp实用代币
* DAO治理代币
* 质押与奖励

##### ERC20 标准定义的关键特性与功能
* `name()`（可选但推荐）：返回代币的可读名称
* `symbol()`（可选但推荐）：返回代币的交易代码
* `decimals()`（可选但推荐）：返回代币使用的十进制位数，通常为18
* `totalSupply()`：返回代币总供应量
* `balanceOf()`：返回指定`account`的代币余额
* `transfer(address recipient, uint256 amount)`：从调用者的`(msg.sender)`余额中转移`amount`个代币到`recipient`。必须发出一个`Transfer`事件。
* `approve(address spender, uint256 amount)`：允许代币持有者`(msg.sender)`授权`spender`（另一个地址或合约）从其账户中提取最多`amount`个代币。必须发出一个`Approval`事件。
* `allowance(address owner, address spender)`：返回`spender`仍可从`owner`处提取的剩余代币数量。
* `transferFrom(address sender, address recipient, uint256 amount)`：允许已经授权的`spender`从`sender`的账户向`recipient`转移`amount`个代币。这在approve调用之后使用，必须发出`Transfer`事件。

###### 事件
* `Transfer(address indexed from, address indexed to, uint256 value)`：在转移代币时（包括零值转移和铸造/销毁）发出
* `Approval(address indexed owner, address indexed spender, uint256 value)` ：在`approve`调用中设置允许值时发出


#### ERC20代币流程: 转账和授权是如何工作的
###### Transfer:转账
1. 用户调用`transfer(to, amount)`
2. 合约检查发送者的余额
3. 更新余额并发出`Transfer`事件

###### Approve/transferFrom:
1. `Owner`调用`approve(spender, amount)`
2. `Spender`调用`transferFrom(owner, to, amount)`
3. 合约检查允许值和余额，更新它们并发出事件
