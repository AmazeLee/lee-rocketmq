- # RocketMQ是什么

  RocketMQ是由阿里捐赠给Apache的一款分布式、队列模型的开源消息中间件，经历了淘宝双十一的洗礼

  # RocketMQ的特性

  - 原生分布式

  - 两种消息拉取

  - 严格消息顺序

  - 特有的分布式协调器

  - 亿级消息堆积

  - 组（Group）

  # RocketMQ基本概念

  - Producer 

    消息生产者，负责产生消息，一般由业务系统负责产生消息

  - Consumer 

    消息消费者，负责消费消息，一般是后台系统负责异步消费

  - Push Consumer 

    封装消息拉取，消息进程和内部

  - Pull Consumer 

    主动拉取消息，一旦拉取到消息，应用的消费进程进行初始化

  - Produce Group 

    一类Producer的集合名称，这类Producer通常发送一类消息，并且发送逻辑一致

  - Consumer Group 

    一类Consmer的集合名称，这类Consumer通常消费一类消息，且消费逻辑一致

  - Broker 

    消息中转角色，负责存储消息，转发消息，这里就是RocketMQ Server

  - Topic 

    消息的主题，用于定义并在服务端配置，消费者可以按照主题进行订阅，也就是消息分类，通常一个系统一个Topic

  - Message 

    在生产者、消费者、服务器之间传递的消息，一个message必须属于一个Topic

  - Namesrv 

    一个无状态的名称服务，可以集群部署，每一个broker启动的时候都会向名称服务器注册，主要是接受broker的注册，接收客户端的路由请求并返回路由信息

  - Offset 

    偏移量，消费者拉取消息时需要知道上一次消费到了什么位置，这一次从哪里开始

  - Partition 

    分区，Topic物理上的分组，一个Topic可以分为多个区，每个分区是一个有序的队列。分区中的每条消息都会分配一个有序的ID，也就是偏移量

  - Tag 用于对消息进行过滤，理解为message的标记，同一业务不同目的的message可以用相同的topic但是可以用不同tag来区分

  - key 消息的KEY字段是为了唯一表示消息的，方便查问题，不是说必须设置，只是说设置为了方便开发和运维定位问题。比如：可以为订单ID

    # 下载安装

    1、下载

    ![image-20200412220434385](https://raw.githubusercontent.com/AmazeLee/images/master/img/image-20200412220434385.png)

    [**https://mirror.bit.edu.cn/apache/rocketmq/4.7.0/rocketmq-all-4.7.0-bin-release.zip**](https://mirror.bit.edu.cn/apache/rocketmq/4.7.0/rocketmq-all-4.7.0-bin-release.zip)

    2、解压

    `unzip -d/usr rocketmq-all-4.7.0-bin-release.zip`

    `mv /usr/rocketmq-all-4.7.0-bin-release/ /usr/rocketmq`

    3、启动NameServer

    `nohub sh bin/mqnamesrv>~/logs/rocketmqlogs/namesrv.log 2>&1&`

    4、启动Broker

    `nohub sh bin/mqbroker -n localhost:9876>~/logs/rocketmqlog/broker.log2>&1&`

    5、停止Broker

    `bin/mqshutdown broker`

    6、停止NameServer

    `bin/mqshutdown namesrv`

    7、发送消息

    `export NAMESRV_ADDR=localhost:9876`

    `bin/tools.sh org.apache.rocketmq.example.quickstart.Producer`

    8、接收消息

    `bin/tools.sh org.apache.rocketmq.example.quickstart.Consumer`

    

    

  