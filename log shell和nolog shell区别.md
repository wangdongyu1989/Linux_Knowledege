

# login shell

##介绍
login shell:取得bash时需要完整登入流程，就称为login shell。举例来说，同tty1~tty6登入时，需要输入用户名和密码，此时取的bash就称为log shell。

log shell 登入读入配置文件顺序：

* /etc/profile, 处在shell配置文件的最顶端。这是系统shell环境的全局设定，例如PATH，MAIL很多环境变量。然后设置你的umask的值，然后读
取/etc/profile.d/*.sh中的一系列文件。这个目录下主要规定了语系，颜色，vi的命令别名等。有的说还会读取/etc/inputrc,/etc/sysconfig/i18n等，对它的修改，会影响到所有用户。不建议修改。

* /.bash_profile或~/.bash_login或~/.profile 其实这三个文件只会读取一个的，如果存在~/.bash_profile就不会读取后两个；如果不存在，则读取~/.bash_login，如果~/.bash_login存在的话，就不会读取~/.profile。不同的系统，这三个文件的存在情况不一样。

* 上面那三个文件其实只做了一件事判断~/.bashrc这个文件是否存在，如果存在的话，读取这个文件。打开~/.bashrc，在~/.bashrc中，只是判断/etc/bashrc是否存在，存在的话读取/etc/bashrc。/etc/bashrc中帮我们做了几件事情，设置umask,设置PS1,读取/etc/profile.d/*.sh。是不是和/etc/profile做的事情差不多。

## login shell 流程图
  ![image](https://github.com/wangdongyu1989/Linux_Knowledege/blob/master/image/20170908094045.jpg)
# non-login shell

non-login shell:以X windows登入linux后，再以X的图形化界面启动终端机，此时那个终端机并不需要再次输入用户名和密码，那个bash的环境就称为non-login shell
