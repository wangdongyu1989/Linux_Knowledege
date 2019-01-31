
### 1: 下载pcstat

git clone https://github.com/tobert/pcstat

### 2: 安装go

yum install go

### 3: 设置路径并安装

$ export GOPATH=~/go

$ export PATH=~/go/bin:$PATH

$ go get golang.org/x/sys/unix

$ go get github.com/tobert/pcstat/pcstat
