
# im service学习笔记
1. 支持点对点消息, 群组消息, 聊天室消息
2. 支持集群部署
3. 单机支持50w用户在线
4. 单机处理消息5000条/s
5. 支持超大群组(3000人)

*服务器硬件指标：32g 16核*

## 编译运行

1. 安装go编译环境

   参考链接:https://golang.org/doc/install

2. 下载im_service代码

   cd $GOPATH/src/github.com/GoBelieveIO

   git clone https://github.com/GoBelieveIO/im_service.git

3. 安装依赖

   cd im_service

   dep ensure

4. 编译

   cd im_service
    
   mkdir bin
    
   make install
    
   可执行程序在bin目录下

5. 安装mysql数据库, redis, 并导入db.sql

6. 配置程序
   配置项的说明参考ims.cfg.sample, imr.cfg.sample, im.cfg.sample

7. 启动程序

  * 创建配置文件中配置的im&ims消息存放路径

    mkdir /tmp/im

    mkdir /tmp/impending

  * 创建日志文件路径
    
    mkdir /data/logs/ims

    mkdir /data/logs/imr

    mkdir /data/logs/im

  * 启动im服务

    pushd \`dirname $0\` > /dev/null

    BASEDIR=\`pwd\`

    nohup $BASEDIR/ims -log_dir=/data/logs/ims ims.cfg >/data/logs/ims/ims.log 2>&1 &

    nohup $BASEDIR/imr -log_dir=/data/logs/imr imr.cfg >/data/logs/imr/imr.log 2>&1 &

    nohup $BASEDIR/im -log_dir=/data/logs/im im.cfg >/data/logs/im/im.log 2>&1 &



## 官方网站
   https://developer.gobelieve.io/

