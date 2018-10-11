# redis
## 安装
### yum 安装
   1. 下载fedora的epel仓库: yum install epel-release
   2. 安装redis数据库:yum install redis
   3. 启动redis:service redis start
   4. 设置redis为开机自动启动:chkconfig redis on
### 下载软件包安装
   1. wget http://download.redis.io/releases/redis-4.0.11.tar.gz
   2. $ tar -zxvf redis-4.0.11.tar.gz
   3. cd redis-4.0.11
   4. make
   5. 后台启动：修改conf文件中*daemonize no*的值为*yes*
   6. copy redis安装目录下的 /utils/redis_init_script 至 _/etc/init.d/redis_
   7. 修改/etc/init.d/redis 文件中的配置：
> \#!/bin/sh
> \### chkconfig: 2345 10 90
> \# Simple Redis init.d script conceived to work on Linux systems
> \# as it does use of the /proc filesystem.

> \### BEGIN INIT INFO
> \# Provides:     redis_6379
> \# Default-Start:        2 3 4 5
> \# Default-Stop:         0 1 6
> \# Short-Description:    Redis data structure server
> \# Description:          Redis data structure server. See https://redis.io
> \### END INIT INFO

> REDISPORT=6379
> EXEC=/etc/redis/src/redis-server
> CLIEXEC=/etc/redis/src/redis-cli

> PIDFILE=/var/run/redis_${REDISPORT}.pid
> CONF="/etc/redis/redis.conf"
> ...
> esac

## 基本命令
