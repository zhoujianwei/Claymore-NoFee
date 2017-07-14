# Claymore-NoFee
完美屏蔽Claymore 9.X的手续费。Removes Claymore's 9.x 1-2% mining fee using Stratum Proxy
##工作机制
此协议用于 Claymore 和公网连接之间抓取mining fee数据包替换devfee地址为自己钱包地址. 重定向速度很快不需要重启挖矿终端 。

##环境配置方法
在 Windows

安装Python 2.7

在每台挖矿终端上修改host 文件. C:/Windows/System32/drivers/etc/hosts

替换手续费矿池名称，添加记录:

```
127.0.0.1   eth-eu.dwarfpool.com
```
##运行
第一次运行代理要注意把矿池地址改成自己实际使用的地址
```
./stratum_proxy.py 127.0.0.1 8008 eth-eu2.nanopool.org 9999 0xB7716d5A768Bc0d5bc5c216cF2d85023a697D04D
```

用手续费矿池运行挖矿软件
```
./ethdcrminer64 -epool eth-eu.dwarfpool.com:8008 ....
```
