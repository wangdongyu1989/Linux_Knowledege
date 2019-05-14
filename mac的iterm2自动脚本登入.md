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
