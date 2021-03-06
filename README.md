# 后端基础服务镜像

---

## 基本编译配置项

* `--disable-session`禁用`session`
* `--enable-zip`
* `--enable-pcntl` 启用进程, 后端需要
* `--enable-sysvmsg`
* `--enable-sysvsem`
* `--enable-sysvshm`
* `--enable-bcmath` rabbitmq 需要

## 扩展安装

* inotify `2.0.0`
* memcached `3.0.3`
* mongo `1.2.10`
* redis `3.1.3`

### apt包

#### memcached

* `libmemcached-dev`
* `zlib1g-dev`

#### mongo

* `libssl-dev`

### 编译

#### memcached

因为在后端服务不使用`session`, 所以编译扩展不需要支持该项.

指定`--disable-memcache-session`, 否则会出现`Cannot find php_session.h`.

#### redis

因为在后端服务不使用`session`, 所以编译扩展不需要支持该项.

需要指定 `--disable-redis-session`, 否则会出现`Cannot find php_session.h`.

## 版本记录

* `1.0`: 初始化基础镜像
* `1.1`: 添加`inotify`
* `1.3`: 添加`--enable-soap`, 支持`soap`
	* 信用平台需要远程调用省信息中心接口, 目前暂时碰见使用`soap`居多, 编译到后端开发环境中
* `1.4`
	* 取消默认安装`confd`
	* 更新`composer 2.0.13`
	* 更新`memcached 3.1.5`
* `1.5`
	* 安装`inotify-tools`
* `1.6`
	* 安装`gd`库
	* 安装`unzip`