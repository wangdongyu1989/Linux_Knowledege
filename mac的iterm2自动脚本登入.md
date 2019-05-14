```c
#!/usr/bin/expect -f
  
set user root
set host  [lindex $argv 0]
set password  [lindex $argv 1]
set myhome /root/

spawn -noecho ssh $user@$host
expect "*assword:*"
send "$password\r"
log_user 0
expect "#*"
send  "cd $myhome\r"
log_user 1
interact
expect eof
```

设置步骤1：

![image](https://github.com/wangdongyu1989/Linux_Knowledege/blob/master/image/expect1.png)

设置步骤2：auto_login.sh 第一个参数主机名 第二个参数密码

![image](https://github.com/wangdongyu1989/Linux_Knowledege/blob/master/image/expect2.png)
