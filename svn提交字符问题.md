
正在发送       ×××.cpp

传输文件数据.svn: 提交失败(细节如下): 

svn: Commit blocked by pre-commit hook (exit code 1) with output:

/usr/bin/svnlook author -t170319-3nku /srv/svn/repos.d/websearch4

iconv: illegal input sequence at position 4817

file=×××.cpp is not a GBK file. plz check svn:mime-type properties.

mime-type= charset=GBK

for example:

  text/plain; charset=GBK

  text/plain; charset=BIG5
  
  text/plain; charset=utf-8
  
  text/plain; charset=utf-16
  
  text/plain; charset=unicode

文本类型转换： 
             
             iconv -f  utf-8 -t gbk xxx.cpp -o xxx.cp.bak
        
             rm -rf xxx.cp
             
             mv xxx.cp.bak xxx.cp
