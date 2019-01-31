1:  bcc-tools 需要内核版本为 4.1 或者更新的版本，我们首先需要升级内核

yum update -y

2: 安装elrepo内核，最好能访问外网

rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org

rpm -Uvh http://www.elrepo.org/elrepo-release-7.0-2.el7.elrepo.noarch.rpm

3: 先卸载旧的 kernel-headers，kernel-tools, kernel-tools-libs，只保留内核，然后
yum --enablerepo=elrepo-kernel install kernel-ml   kernel-ml-devel.x86_64
注意，这里是下载内核和驱动，如果不下载驱动，到后面bcc软件链接的文件就没有，在/usr/src/kernels下4.20.0-1.el7.elrepo.x86_64目录

yum remove -y kernel-headers kernel-tools kernel-tools-libs

yum --enablerepo="elrepo-kernel" install -y kernel-ml kernel-ml-devel kernel-ml
