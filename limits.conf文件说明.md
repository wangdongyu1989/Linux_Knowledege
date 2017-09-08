
## 背景

在测试机器上用odin用户起key-value数据库，需要先申请一定的内存空间，启动时报：Cannot allocate memory错误。

## 尝试

* 开始以为内存不足，无法分配足够内存，就停掉了其他程序，但是启动时还是报相同的错误。

* 用root用户启动key-value数据库，可以启动。怀疑是不是启动用户权限导致报错。

## 方法

修改limits.conf配置文件：

odin    hard    memlock  79223827

odin    soft    memlock  79223827

## 说明

limits.conf文件实际是linux PAM(插入式认证模块，Pluggable Authentication Modules)中pam_limits.so的配置文件，而且只针对单个会话。

limits.conf的格式如下：

username|@groupname type resource limit

username|@groupname：设置需要被限制的用户名，组名前面加@和用户名区别。也可以用通配符*来做所有用户的限制。

type：有 soft，hard 和 -，soft 指的是当前系统生效的设置值。hard 表明系统中所能设定的最大值。soft 的限制不能比har 限制高。用 - 就表明同时设置了 soft 
和 hard 的值。

resource：

core - 限制内核文件的大小

date - 最大数据大小

fsize - 最大文件大小

memlock - 最大锁定内存地址空间

nofile - 打开文件的最大数目

rss - 最大持久设置大小

stack - 最大栈大小

cpu - 以分钟为单位的最多 CPU 时间

noproc - 进程的最大数目

as - 地址空间限制

maxlogins - 此用户允许登录的最大数目
