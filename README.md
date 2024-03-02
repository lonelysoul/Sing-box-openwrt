# Sing-box在openwrt原版的使用方法（完整版）
## 1.准备工作及启动
更新配置文件
```
vim /etc/sing-box/config.json
```
## 2.新增接口
新增名称为```tun0```的接口，关联```tun0```的网络设备
## 3.设置防火墙
新增防火墙配置，在常规设置的区域中，新增一条，名称任意，入站、出站、转发全部允许，源区域、目标区域把lan和wan全部选择。
## 4.设置启动项
在系统-启动项-本地脚本中新增启动命令
```
sleep 5 && sing-box run -c /etc/sing-box/config.json &>/dev/null &
```
## 5.问题
>1）启动后未达到目的，可连接ssh后用top命令检查是否存在sing-box进程；没有再重新执行启动命令；核心问题可能是tun模式的不稳定；
>2）sing-box的版本是1.8.7（openwrt原版当前版本），在当前原版openwrt下运行下载到200M时，cpu占用70%，性能低；immortalwrt跑1000M时约为40%+。

