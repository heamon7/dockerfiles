## 使用指南
- docker login xxx
- docker-compose up -d
- docker exec zmirror service apache2 restart

## 重置安装
如果想重新使用 docker 安装 zmirror，可以使用下面的方法

- 用 docker-compose 启动下面 docker-compose.yml 描述的容器

```
zmirror:
  container_name: zmirror
  image: ubuntu:16.04
  restart: unless-stopped
  stdin_open: true
  tty: true
  ports:
    - "80:80"
    - "443:443"
```
- docker exec -it zmirror bash 之后，按照[官方文档](https://github.com/aploium/zmirror-onekey)步骤安装

cp /etc/apt/sources.list /etc/apt/sources.list.bakcup && echo """
deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse 
""">/etc/apt/sources.list && apt update
