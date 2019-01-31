
### 1: 下载pcstat

$ git clone https://github.com/tobert/pcstat

### 2: 安装go

$ yum install go

### 3: 设置路径并安装

$ export GOPATH=~/go

$ export PATH=~/go/bin:$PATH

$ go get golang.org/x/sys/unix

$ go get github.com/tobert/pcstat/pcstat

### 4：测试

pcstat pcstat/README.md

+------------------+----------------+------------+-----------+---------+

| Name             | Size (bytes)   | Pages      | Cached    | Percent |

|------------------+----------------+------------+-----------+---------|

| pcstat/README.md | 7114           | 2          | 2         | 100.000 |

+------------------+----------------+------------+-----------+---------+
