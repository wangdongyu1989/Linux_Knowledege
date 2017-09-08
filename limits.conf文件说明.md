
## 背景

在测试机器上用odin用户起key-value数据库，需要先申请一定的内存空间，启动时报：Cannot allocate memory错误。

## 尝试

* 开始以为内存不足，无法分配足够内存，就停掉了其他程序，但是启动时还是报相同的错误。

* 用root用户启动key-value数据库，可以启动。怀疑是不是启动用户权限导致报错。

## 方法

修改limits.conf配置文件：

odin    hard    memlock  79223827
odin    soft    memlock  79223827

