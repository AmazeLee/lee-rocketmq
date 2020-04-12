# RocketMQ是什么

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

- Consumer Group 一类Consmer的集合名称，这类Consumer通常消费一类消息，且消费逻辑一致

- Broker 消息中转角色，负责存储消息，转发消息，这里就是RocketMQ Server

- Topic 消息的主题，用于定义并在服务端配置，消费者可以按照主题进行订阅，也就是消息分类，通常一个系统一个Topic