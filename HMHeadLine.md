# 初始化项目

## Nacos:v2.3.0

### 拉取nacos：

```shell
docker pull nacos/nacos-server:v2.3.0
```

拉取成功后使用docker images查看nacos-server是否存在

### 启动nacos:

```shell
docker run --name nacos -e MODE=standalone -p 8848:8848 -d nacos/nacos-server:v2.3.0
```

--name：配置启动名称；-e：配置环境变量；mode配置单机模式；-p：配置端口；-d：以守护进程模式启动；最后的部分要和images查看的内容一一对应，启动成功会显示id

通过docker ps查看nacos是否启动成功

**注意：**v2.2.2版本之后的nacos默认不开启鉴权不打开登录页面，若开启鉴权即登录模式，需要在docker启动时在-e后面添加NACOS_AUTH_ENABLE=true，默认登录用户名和密码为nacos。官方文档： https://nacos.io/zh-cn/docs/v2/guide/user/auth.html

### centos7开启8848端口：

```sh
sudo firewall-cmd --permanent --zone=public --add-port=8848/tcp
sudo firewall-cmd --reload
```