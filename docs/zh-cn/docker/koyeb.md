# Koyeb容器

## 安装aapanel

**docker images**

地址：https://hub.docker.com/r/aapanel/aapanel

```
docker.io/aapanel/aapanel
```

![image-20220711220600814](https://cdn.jsdelivr.net/gh/RenaLio/images/imgs/202207112206049.png)

Default installation entry:`aapanel`
Default username:`aapanel`
Default password:`aapanel123`
Default root password:`aapanel123`

#### Port usage analysis

Control Panel : 7800
Phpmyadmin : 888

#### Dir usage analysis

Website data : /www/wwwroot
Mysql data : /www/server/data
Vhost file : /www/server/panel/vhost

## 安装哪吒探针

```shell
wget -N --no-check-certificate  https://raw.githubusercontent.com/rea-tool/nezhascript/main/wula.sh && bash wula.sh
```

- `systemctl`在docker中无法使用，对哪吒探针的脚本做了部分修改

- 只采用了agent部分

- 支持`ipv4`和`ipv6`

