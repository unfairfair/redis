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
>
> \### BEGIN INIT INFO  
> \# Provides:     redis_6379 
> \# Default-Start:        2 3 4 5  
> \# Default-Stop:         0 1 6 
> \# Short-Description:    Redis data structure server   
> \# Description:          Redis data structure server. See https://redis.io  
> \### END INIT INFO 
>  
> REDISPORT=6379  
> EXEC=/etc/redis/src/redis-server  
> CLIEXEC=/etc/redis/src/redis-cli  
>  
> PIDFILE=/var/run/redis_${REDISPORT}.pid 
> CONF="/etc/redis/redis.conf"   
> ...    
> esac   

  配置文件中的①chkconfig: 2345 10 90，②Default-Start|Default-Stop 两种任选其一    
  8. 添加redis服务： chkconfig --add redis    
  9. 设置开机启动： chkconfig redis on    
  10. 每当修改redis启动配置时： chkconfig redis reset    
## 基本
### 数据结构
  * String: 字符串
    * set key "abc"
    * get key
  * Hash: 散列
    * hmset key field value [field value ...]
    * hget key field
  * List: 列表
    * rpush key value [value ...],lpush key value [value ...]
    * lrange key start stop,lpop key,rpop key
  * Set: 集合
    * SADD key member1 [member2] 向集合添加一个或多个成员
    * SRANDMEMBER key [count] 返回集合中一个或多个随机数
  * Sorted Set: 有序集合
### 常用命令
  * set key value [EX seconds] [PX milliseconds] [NX|XX]    
     set key value ex 10 = setex key 10 value 将key的有效期设置为10秒    
     NX:（if Not eXist）只有键key不存在的时候才会设置key的值，通常用于实现锁机制，*set key 123 ex 5 nx*    
     XX：只有键key存在的时候才会设置key的值  
  * GETSET key value ：给定 key 的值设为 value ，并返回 key 的旧值(old value)。    
  * MSET key value [key value ...],MGET key [key ...]    
  * incr key| incrby key increment| decrby key decrement|decr key    
