# 后端基础服务镜像

---

## 基本编译配置项

* `--disable-session`禁用`session`
* `--enable-zip`
* `-enable-pcntl` 启用进程, 后端需要
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