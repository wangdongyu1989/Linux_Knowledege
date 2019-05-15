1，iterm2终端编码设置成utf-8，Preferences->Profiles->Terminal->Character encoding, Report terminal type选择xterm-256color。

2，在~/.bashr配置文件中添加如下，是为了设置locale

```c
export LANG=en_US.UTF-8
```

3，在~/.vimrc配置文件中添加

```c
set fileencodings=utf-8,cp936,gb18030,big5,euc-jp,euc-kr,latin1,gb2312
set termencoding=utf-8
set encoding=utf-8
set fileencoding=gb18030
```
