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
## 基本命令
