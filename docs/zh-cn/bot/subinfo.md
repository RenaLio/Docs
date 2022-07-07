# 订阅信息查询 Telegram Bot

## DEMO

[@Thesubinfo2_bot](https://t.me/Thesubinfo2_bot)

## 安装教程

先去botfather获取bot token，然后在vps内使用一下命令安装bot

```
git clone https://github.com/RenaLio/SubinfoChecker
```


### Debian | Ubuntu:

```
apt-get upgrade -y 
apt install -y python3 python3-pip 
pip3 install -r requirements.txt
```

### CentOS 

```
yum update -y
yun install -y python3 python3-pip
pip3 install -r requirements.txt
```

### 运行方式

直接使用Python命令调用Bot即可

```
python3 subinfo2.py
```

建议使用`screen`、`systemd`、`PM2`等工具将Bot挂在后台运行。

## 其他

### subinfo.py

> 推荐个人使用，直接发送`订阅链接`就可以返回结果

### subinfo2.py

> `/subinfo URL`

## 后台保活

创建`screen`_`mybot`运行.py文件

当多人同时使用时，可能导致bot无法继续运行，使用crontab每隔一段时间中止原来的进程，然后重新激活。使用以下shell脚本。

`mybot.sh`，需要首先创建`screen`_`xx`，依据名称和文件路径对shell脚本进行具体修改。

```shell
#!/usr/bin/env bash

red() {
    echo -e "\033[31m\033[01m$1\033[0m"
}

green() {
    echo -e "\033[32m\033[01m$1\033[0m"
}

yellow() {
    echo -e "\033[33m\033[01m$1\033[0m"
}

screenName="mybot"
# 退出screen中原来的bot.py，向screen中输入`Ctrl+c`
screen -S mybot -X stuff  `echo -e '\003'`
# 在screen存在的基础上输入命令
screen -S $screenName -X stuff 'cd /root/SubinfoChecker &&python3 mybot.py'`echo -ne '\015'`
# 删除旧的screen
# screen -S $screenName -X quit || red "没有找到 $screenName 的会话"
```

Crontab示例

```
[root@localhost ！]# crontab -e
#进入 crontab 编辑界面。会打开Vim编辑你的任务
15 * * * * bash x/bot.sh
```

## 感谢

subinfo的主要代码来源自`telegram-PGM`模块