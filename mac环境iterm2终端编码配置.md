1，iterm2终端编码设置成gb18030，Preferences->Profiles->Terminal->Character encoding, Report terminal type选择xterm-256color。

2，在~/.bashr配置文件中添加如下，是为了设置locale

```c
export LANG=en_US.UTF-8
export LC_CTYPE=en_US
```

3，在~/.vimrc配置文件中添加

```c
set fileencodings=gb18030,utf-8,cp936,big5,euc-jp,euc-kr,latin1,gb2312
set termencoding=gb18030
set encoding=utf-8
set fileencoding=gb18030
```

linux相应编码知识总结：

locale命令是根据计算机用户所使用的语言，所在国家或者地区，以及当地文化传统定义的一个软件运行时的语言环境。

