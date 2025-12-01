# TG-mtproxy
## 🚀 快速开始 (Quick Start)
MTProxyTLS一键安装绿色脚本
```bash
rm -rf /home/mtproxy && mkdir /home/mtproxy && cd /home/mtproxy
curl -fsSL -o mtproxy.sh https://github.com/ellermister/mtproxy/raw/master/mtproxy.sh
bash mtproxy.sh
```

## 使用方式

配置文件 `config`，如果你想手动修改密钥或者参数请注意格式。

运行服务

```bash
bash mtproxy.sh start
```

调试运行

```bash
bash mtproxy.sh debug
```

停止服务

```bash
bash mtproxy.sh stop
```

重启服务

```bash
bash mtproxy.sh restart
```

重新安装/重新配置

```bash
bash mtproxy.sh reinstall
```

## 卸载安装

因为是绿色版卸载极其简单，直接删除所在目录即可。

```bash
rm -rf /home/mtproxy
```

## 开机启动

> 该脚本没有配置为系统服务的方式，你可以将其添加到开机启动脚本中。

开机启动脚本，如果你的 rc.local 文件不存在请检查开机自启服务。

通过编辑文件`/etc/rc.local`将如下代码加入到开机自启脚本中：

```bash
cd /home/mtproxy && bash mtproxy.sh start > /dev/null 2>&1 &
```

## 计划任务守护

由于默认官方的 mtproxy 程序存在BUG，在 pid 大于 65535 时进程处理存在问题，进程容易坏死和异常退出。

因此建议通过计划任务去守护进程 `crontab -e` ：

每分钟检测进程并启动

```bash
* * * * * cd /home/mtproxy && bash mtproxy.sh start > /dev/null 2>&1 &
```
