

# loin shell

login shell:取得bash时需要完整登入流程，就称为login shell。举例来说，同tty1~tty6登入时，需要输入用户名和密码，此时取的bash就称为log shell。

log shell 登入读入配置文件顺序：

* /etc/profile, 处在shell配置文件的最顶端。这是系统shell环境的全局设定，例如PATH，MAIL很多环境变量。然后设置你的umask的值，然后读
取/etc/profile.d/*.sh中的一系列文件。这个目录下主要规定了语系，颜色，vi的命令别名等。有的说还会读取/etc/inputrc,/etc/sysconfig/i18n等，对它的修改，会影响到所有用户。不建议修改。





# non-login shell

non-login shell:以X windows登入linux后，再以X的图形化界面启动终端机，此时那个终端机并不需要再次输入用户名和密码，那个bash的环境就称为non-login shell
