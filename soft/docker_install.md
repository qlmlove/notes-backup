---
title: windows10下安装Docker
tags: Docker
date: 2017-11-08 00:16:15
---

## 1. 下载


1. 阿里云地址：

    `http://mirrors.aliyun.com/docker-toolbox/windows/docker-for-windows/`

2. 官方下载

    `https://www.docker.com`

## 2. 安装

双击安装包开始安装（如未开启Hyper-V,会弹出一个窗口，需要点击OK，系统会自动启用Hyper-V），重启若干次


## 3. 配置工作目录

在Docker 图标右键->Settings->Shared Driver，勾选上你工作区的目录，点击 Apply ，弹出框中输入当前电脑用户的用户密码

## 4. 设置加速器

1. 打开`https://cr.console.aliyun.com/#/imageList`，注册登录之后点击“Docker Hub 镜像站点”，然后复制右侧的您的专属加速器地址 :`https://zevxaccp.mirror.aliyuncs.com`(请自行申请)
2. 打开docker图标，setting，daemon，然后点击base滑块，修改下边内容（请自行更换专属加速器地址）：

```
{
  "registry-mirrors": [
    "https://zevxaccp.mirror.aliyuncs.com"
  ],
  "insecure-registries": [],
  "debug": true,
  "experimental": true
}
```

## 4. 获取devilbox，并且在`.env`文件中选择需要的软件版本，然后开始安装

```bash
# Get the devilbox
$ git clone https://github.com/cytopia/devilbox
$ cd devilbox

# Create docker-compose environment file
$ cp env-example .env

# Edit your configuration
$ vim .env

# Start all containers
$ docker-compose up
```

## 5. 配置PostgreSQL数据库的pgdata,解决pgdata启动不起来的问题

```bash
  pgsql:
    image: postgres:${PGSQL_SERVER:-9.6}

    environment:

      - POSTGRES_USER=${PGSQL_ROOT_USER}
      - POSTGRES_PASSWORD=${PGSQL_ROOT_PASSWORD}
      - PGDATA=./data/pgdata # 修改此处

    ports:
      # [local-machine:]local-port:docker-port
      - "${LOCAL_LISTEN_ADDR}${HOST_PORT_PGSQL}:5432"

    networks:
      app_net:
        ipv4_address: 172.16.238.13

    volumes:
      # ---- Format: ----
      # HOST-DIRECTORY : DOCKER-DIRECTORY

      # Mount logs
      - ${DEVILBOX_PATH}/log/pgsql-${PGSQL_SERVER}:/var/log/postgresql

      # Mount PostgreSQL Data directory
      - ${HOST_PATH_PGSQL_DATADIR}/${PGSQL_SERVER}:/var/lib/postgresql/data/pgdata

    depends_on:
      - bind
      - php
      - httpd

```

## 6. 配置MongoDB的DATADIR参数,解决mongo启动不了的问题

```bash
  mongo:
    image: mongo:${MONGO_SERVER:-latest}

    ports:
      # [local-machine:]local-port:docker-port
      - "${LOCAL_LISTEN_ADDR}${HOST_PORT_MONGO}:27017"

    networks:
      app_net:
        ipv4_address: 172.16.238.16

    volumes:
      # ---- Format: ----
      # HOST-DIRECTORY : DOCKER-DIRECTORY

      # Mount MongoDB Data directory
      - ${HOST_PATH_MONGO_DATADIR}/${MONGO_SERVER}:/h/data/db # 修改此处h为盘符,此处最好用绝对路径

    depends_on:
      - bind
      - php
      - httpd

```

(未完待续)