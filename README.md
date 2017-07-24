# Claymore-NoFee
完美屏蔽Claymore 9.X的手续费。Removes Claymore's 9.x 1-2% mining fee using Stratum Proxy。开发测试环境Ubuntu 16.04 、 Windows 10 和 Claymore 9.7原版


## 工作机制
此协议用于 Claymore 和公网连接之间抓取mining fee数据包替换devfee地址为自己钱包地址. 重定向速度很快不需要重启挖矿终端 。

## 环境配置方法
在 Windows
### Python
安装Python 2.7 Windows10安装Python2.7 http://blog.csdn.net/u011781521/article/details/53909151

### 虚拟一个Wan口
可以参考教程[Windows](http://www.qukuai.top/d/53-wan-win)
补充: DNS 重定向不再需要 (除非挖矿 ETH分支如ETC).

## 运行
第一次运行代理要注意把如下矿池地址改成自己实际使用的地址
```
./stratum_proxy.py 127.0.0.1 8008 eth-eu2.nanopool.org 9999 0xB7716d5A768Bc0d5bc5c216cF2d85023a697D04D
```
通过虚拟WAN口的ip运行挖矿软件
```
./ethdcrminer64 -epool 194.12.12.2:8008 ....
```
## 已知问题
- 不支持所有分叉币.
- 本代只理适配 ESM mode 0 & 1

## 特性
- 重定向 DevFee 到自己钱包
- 监测网络中断
- 极简
- 探测不同用户名
- 自定义矿工名

## 问答

### 可以用在其他矿池吗?
Claymore 试图从你挖矿的池子获取手续费. 所以你只要在代理参数中改成自己的池子即可.

### 这个软件是轻量化的么?
我们努力把占用做到最少化, 这个stratum 代理进程占用 130MB RAM 少量的cpu占用. 功耗可以忽略不计.

### 如何保证这是 100% 安全不是抽水?
这是一个开源项目,本身就是避免抽水的，你可以检查源代码. 也欢迎提供改进意见。

### 我需要在每个矿机上运行吗?
是的, 我建议在每台上运行代理.

### 能适配所有的币吗?
此代理用于Claymore ETH 单.如果打算挖 ETH分支, 你需要在claymore定义 `-allcoins 1`更改host 文件为h正确的池子. [Windows](http://www.qukuai.top/d/54-redirecting-all-devfee-domains) [Linux](http://www.qukuai.top/d/55-redirecting-all-domains-linux)
自从Claymore 9.6 对于 ETC 设置更简单, 使用 `-allcoins etc` 参数(可以跳过上面教程).
只有当 Claymore不能挖同一个池子才要重置host文件强制更改dns.
Zcash version in the futur?  

### 双挖可以吗?
当然.

### 如何更改用户名 ?
查找编辑 `worker_name`参数， 默认矿工名是 _rekt_. .

### 如何判断正在工作?
你可以在挖矿软件窗口看到 (1分钟 devfee每小时). 也可以检查矿池, 但有的矿池会忽略没有share的小段时间. 但所有的都能挖到自己钱包!

### Claymore 客户端对于本地代理的警告...
Claymore 通过检查狂吃 IP 来避免本地代理,如果你收到警告可以参考: [Fake WAN For Windows](http://www.qukuai.top/d/53-wan-win)


## 感谢原作者 thk original author
如果觉得有用请支持原作者
- 0xfeE03fB214Dc0EeDc925687D3DC9cdaa1260e7EF
- Drdada - 0xB7716d5A768Bc0d5bc5c216cF2d85023a697D04D (ethermine)
