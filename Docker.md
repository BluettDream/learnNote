# 安装docker

## 卸载旧版本

> 无论之前有没有下载过皆可执行

```shell
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

## 设置yum库

```shell
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

## 安装最新版本docker引擎

```shell
sudo yum install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## 启动docker

```shell
sudo systemctl start docker
```

## 测试docker

```shell
sudo docker run hello-world
```

<img src="https://raw.githubusercontent.com/BluettDream/ImgBed01/master/learn/docker%E5%90%AF%E5%8A%A8%E6%88%90%E5%8A%9F.png" style="zoom:67%;" />

> 出现上述界面代表安装成功

## 删除下载的镜像

```shell
docker ps -a
找到hello wolrd容器对应的id
docker rm 容器ID
docker images
找到hello world镜像的id
docker rmi 镜像ID
```

<img src="https://raw.githubusercontent.com/BluettDream/ImgBed01/master/learn/docker%E5%88%A0%E9%99%A4%E9%95%9C%E5%83%8F.png" style="zoom:67%;" />

> 出现上述界面代表删除成功

## 测试docker compose

```shell
docker compose version
```

> 出现docker compose版本号即为成功