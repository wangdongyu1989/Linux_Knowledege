
## 背景

hadoop升级到Hadoop 2.6.0-cdh5.10.0，导致提交任务的客户端无法使用，如图：

![image](https://github.com/wangdongyu1989/Linux_Knowledege/blob/master/image/20170908113926.jpg)

## 原因

java1.7无法支持新版hadoop集群

## 方法

安装java1.8 并在hadoop的配置环境脚本里配置：

/etc/hadoop/hadoop-env.sh增加：

export JAVA_HOME=/usr/lib/jvm/jre-1.8.0-openjdk
