---
title: "yum安装docker"
slug: "yum-install-docker"
thumbnailImagePosition: left
thumbnailImage: images/docker.png
date: 2023-01-01
categories:
- 云原生
tags:
- 云原生
showSocial: false
---



Docker是一个开源的应用容器引擎，让开发者可以打包他们的应用以及依赖包到一个可移植的镜像中，然后发布到任何流行的Linux或Windows操作系统的机器上，也可以实现虚拟化。容器是完全使用沙箱机制，相互之间不会有任何接口。

<!--more-->



## 主要步骤

- 1.更新yum
- 2.设置稳定的docker来源仓库
- 3.安装Docker
- 4.启动Docker
- 5.验证Docker
- 6.卸载Docker



## 安装说明



#### 1. 更新Yum

```shell
yum update
```



#### 2. 设置稳定的docker来源仓库

```sh
-- 官网源仓库，在国外，因此下载会比较慢

sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

-- 阿里云
sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```



#### 3. 安装docker

```sh
-- 安装Docker所需的软件包
sudo yum install -y yum-utils device-mapper-persistent-data lvm2

-- 安装最新版本的Docker
sudo yum install docker-ce docker-ce-cli containerd.io


-- 安装特定版本的Docker

---- 获取Docker版本
yum list docker-ce --showduplicates | sort -r

-- 指定安Docker版本命令
yum install docker-ce-20.10.9 docker-ce-cli-20.10.9 containerd.io

yum install docker-ce-20.10.5 docker-ce-cli-20.10.5 containerd.io
```



#### 4. 启动docker

```sh
systemctl start docker

-- 开机自启动docker
systemctl enable docker


systemctl restart docker
systemctl stop docker

docker pull harbor.biz.com:8443/kubernetes/pause:latest
```



#### 5. 验证docker

```sh
docker version
```



#### 6. 卸载docker

```sh
-- 较新版本的docker
yum remove docker-ce containerd.io docker-ce-cli docker-scan-plugin

-- 旧版本docker
sudo yum remove docker docker-client docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine

-- 删除卸载Docker后系统内部的镜像、容器、配置文件
sudo rm -rf /var/lib/docker
```
