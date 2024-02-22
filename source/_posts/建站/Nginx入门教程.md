---
title: Nginx入门教程
tags: 网站部署
date: 2024-01-30 23:27:19
categories: 建站
cover: https://www.vectorlogo.zone/logos/nginx/nginx-ar21.svg
---

# Nginx入门教程

## 一、简介

### 1. 介绍

Nginx（发音为"engine x"）是一个高性能的开源 Web 服务器，也可以用作反向代理服务器、负载均衡器和 HTTP 缓存。它的设计目标是处理高并发的网络流量，同时保持低内存使用。

### 2. 主要用途和功能

当你在浏览器中输入一个网址，比如`www.example.com`，想象一下这个网址就像是一家商店的门面。而 Nginx 就是像一位聪明的门卫，它帮助你把进出商店的人和物品都组织得井井有条。

1. **反向代理（Reverse Proxy）：** Nginx 就像是商店的门卫，它接受你的访问请求，然后帮你转发到商店里真正的服务员，比如一个网站或应用。这样，商店的内部结构对于外部人是不可见的。

2. **负载均衡（Load Balancer）：** 如果商店很大，有很多服务员，Nginx 就像是一个智能的服务员调度员。当很多人同时想进入商店时，Nginx 会把他们分配给不同的服务员，确保每个服务员的工作负担都差不多，不至于有人忙碌而有人闲置。

3. **静态文件服务：** 想象商店的门卫会直接告诉你哪里有你要的商品，而不是让你找到商品的仓库。Nginx 也可以直接提供一些不需要特别处理的文件，比如图片、样式表等，让网站更快地加载。

4. **HTTP代理：** 就像门卫可以帮你筛查进出的人一样，Nginx 也可以过滤和修改请求，增加一些额外的安全措施。

5. **灵活配置：** 商店的门卫能够根据需要调整自己的工作方式，Nginx 的配置也是非常灵活的，管理员可以根据实际情况调整 Nginx 的行为，以适应不同的需求。

总之，Nginx 就像是网络世界中的门卫和服务员调度员，它在你和网站之间起到了桥梁的作用，使得网站更安全、更快速地为你提供服务。

## 二、Nginx安装（包管理器）

### 1. 在 Ubuntu、Debian 上安装 Nginx：

在终端中运行以下命令：

```bash
sudo apt update
sudo apt install nginx
```

安装完成后，可以使用以下命令启动 Nginx：

```bash
sudo systemctl start nginx
```

设置开机自启动：

```bash
sudo systemctl enable nginx
```

### 2. 在 CentOS/RHEL 上使用包管理器安装 Nginx：

在终端中运行以下命令：

```bash
sudo yum install epel-release
sudo yum install nginx
```

启动 Nginx：

```bash
sudo systemctl start nginx
```

设置开机自启动：

```bash
sudo systemctl enable nginx
```

### 3. 在 macOS 上使用 Homebrew 包管理器安装 Nginx：

如果未安装 Homebrew，请先安装 Homebrew。然后在终端中运行以下命令：

```bash
brew install nginx
```

启动 Nginx：

```bash
brew services start nginx
```

### 4. 在 Windows 上使用 Chocolatey 包管理器安装 Nginx：

在命令提示符中运行以下命令（请以管理员身份运行）：

```bash
choco install nginx
```

安装完成后，你可以在服务管理器中启动 Nginx 服务。

以上命令和步骤是基于一些常见的包管理器，具体情况可能因操作系统版本、发行版或个人需求而有所不同。安装完成后，你可以通过访问 `http://localhost` 来验证 Nginx 是否成功安装并运行。ubantu或debian等系统也可以使用`ps -ef | grep nginx`来查看服务运行进程。
> 此时会有master进程和worker进程两种，master为主进程，读取配置文件，worker进程完成具体任务。


## 三、静态站点部署
找到nginx的配置文件， `使用nginx -V` 查看配置文件路径,得到各个配置文件的位置信息（也可以使用`nginx -t`来查看,该命令用来检查配置文件的正确性 ）：
```bash 

hexo init
hexo generate
hexo server
hexo d

```

## 四、配置文件

```nginx

# 以下是一个简单的 Nginx 配置文件示例

# 设置运行的用户和组
user www-data;

# 定义工作进程的数量
worker_processes auto;

# 设置运行的日志文件路径及级别
error_log /var/log/nginx/error.log warn;
pid /run/nginx.pid;

# 事件处理模块配置
events {
    # 设置每个工作进程可以处理的最大连接数
    worker_connections 1024;
}

# HTTP 服务配置
http {
    # 设置 HTTP 请求头中的服务器名称
    server_tokens off;

    # MIME 类型映射
    include /etc/nginx/mime.types;

    # 默认文件类型
    default_type application/octet-stream;

    # 定义日志格式
    log_format main '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    # 访问日志配置
    access_log /var/log/nginx/access.log main;

    # Gzip 压缩配置
    gzip on;
    gzip_disable "msie6";
    gzip_comp_level 6;
    gzip_min_length 1100;
    gzip_buffers 16 8k;
    gzip_proxied any;
    gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

    # 包含的虚拟主机配置文件
    include /etc/nginx/conf.d/*.conf;

    # 包含的站点配置文件
    include /etc/nginx/sites-enabled/*;
}


```

### 配置文件结构

* 全局块
* events块：事件处理模块配置
* http块
  * server块（虚拟主机）



## 五、反向代理和负载均衡

### 反向代理
> 正向代理代理客户端，反向代理代理服务端。代理哪端令一端不知道（透明）

在 Nginx 中配置反向代理有两种常见的方式：直接在 `location` 块中使用 `proxy_pass` 指令，或者使用 `upstream` 模块配合 `proxy_pass` 指令。

1. **直接在 `location` 块中使用 `proxy_pass`：**

```nginx
server {
    listen 80;
    server_name your_domain.com;

    location / {
        proxy_pass http://backend_server;
        # 其他代理请求头设置...
    }
}
```

2. **使用 `upstream` 模块配合 `proxy_pass` 指令：**

```nginx
upstream backend {
    ip_hash;  # 根据哈希，绑定客户端和服务器，解决session问题 
    server backend_server;  # 可以设置多个服务器目标和端口，默认以轮询方式代理，使用weight调整权重
}

server {
    listen 80;
    server_name your_domain.com;

    location / {
        proxy_pass http://backend;
        # 其他代理请求头设置...
    }
}
```

区别在于：

- **配置结构：** 使用 `upstream` 模块可以将后端服务器的定义和具体的 `proxy_pass` 配置分离开来，使得配置更具可维护性。`upstream` 块中定义了后端服务器的集群或池，并可以包含多个服务器，而 `proxy_pass` 则直接指定了反向代理的目标地址。

- **可维护性：** 使用 `upstream` 模块可以更灵活地管理后端服务器的列表，例如可以动态地添加或移除服务器，而不需要修改 `server` 块中的配置。这对于负载均衡和高可用性非常有用。

- **性能影响：** 从性能角度来看，两种方式的性能影响不大。`upstream` 模块可能会稍微增加一些内存消耗，但对于大多数情况来说，性能差异很小。

总的来说，使用 `upstream` 模块配合 `proxy_pass` 指令可以提高配置的灵活性和可维护性，尤其适用于需要负载均衡或高可用性的场景。
 

## 六、HTTPS配置

### 配置ssl证书
```nginx
server {
    listen 443 ssl;
    server_name your_domain.com;

    ssl_certificate /path/to/your_domain.crt;
    ssl_certificate_key /path/to/your_domain.key;

    # 可选：配置 SSL 会话缓存
    ssl_session_cache shared:SSL:10m;
    ssl_session_timeout 10m;

    # 可选：配置 SSL 协商参数
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_prefer_server_ciphers on;
    ssl_ciphers 'EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH';

    location / {
        # 其他反向代理或静态文件服务配置...
    }
}

```
### 配置重定向
```nginx

server {
    listen 80;
    server_name your_domain.com;

    # 重定向所有 HTTP 请求到 HTTPS
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl;
    server_name your_domain.com;

    # SSL 配置
    ssl_certificate /path/to/your/ssl_certificate.crt;
    ssl_certificate_key /path/to/your/ssl_certificate_key.key;

    # 其他 SSL 配置项...

    # 其余的 HTTPS 配置
    # ...
}

```

## 七、虚拟主机

Nginx 虚拟主机是一种配置方式，允许在单个服务器上托管多个域名或网站。每个虚拟主机可以有自己独立的配置，可以根据不同的域名或请求来提供不同的内容。虚拟主机使得在单个服务器上托管多个网站变得容易且高效。

在nginx目录中新建server文件夹，新建配置文件（conf）将server模块放进去，可以实现在一台服务器上部署多个站点的功能。

## 附：常用nginx终端操作指令


| 指令                            | 描述                                             |
|---------------------------------|--------------------------------------------------|
| `nginx -t`                      | 检查 Nginx 配置文件语法是否正确                 |
| `nginx -s reload`               | 重新加载配置文件，以应用新的配置               |
| `nginx -s stop`                 | 停止运行中的 Nginx 服务                          |
| `nginx -s quit`                 | 安全停止 Nginx 服务，等待当前连接关闭后退出     |
| `nginx -s reopen`               | 重新打开日志文件                                 |
| `nginx -V`                      | 显示 Nginx 编译时的版本和配置信息               |
| `nginx -h`                      | 显示 Nginx 的帮助信息                             |
| `nginx -s signal`               | 向正在运行的 Nginx 服务器发送信号                |

这些指令可以通过终端直接在命令行中执行，用于管理和操作 Nginx 服务器。