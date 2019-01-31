### 1:  bcc-tools 需要内核版本为 4.1 或者更新的版本，我们首先需要升级内核

yum update -y

### 2: 安装elrepo内核，最好能访问外网

rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org

rpm -Uvh http://www.elrepo.org/elrepo-release-7.0-2.el7.elrepo.noarch.rpm

### 3: 先卸载旧的 kernel-headers，kernel-tools, kernel-tools-libs，只保留内核，然后
yum --enablerepo=elrepo-kernel install kernel-ml   kernel-ml-devel.x86_64
注意，这里是下载内核和驱动，如果不下载驱动，到后面bcc软件链接的文件就没有，在/usr/src/kernels下4.20.0-1.el7.elrepo.x86_64目录

yum remove -y kernel-headers kernel-tools kernel-tools-libs

yum --enablerepo="elrepo-kernel" install -y kernel-ml kernel-ml-devel kernel-ml

### 4: 然后设置：grub2-mkconfig -o /boot/grub2/grub.cfg 生成启动菜单,把kernel-ml 4.9设为默认,重启

grub2-mkconfig -o /boot/grub2/grub.cfg

grub2-set-default 0

reboot

### 5: 安装gcc

yum install gcc-c++

wget https://cmake.org/files/v3.7/cmake-3.7.0.tar.gz

tar xf cmake-3.7.0.tar.gz

cd cmake-3.7.0

./configure

make -j $THREADS

make install

### 6: 安装bison

curl -OL https://ftp.gnu.org/gnu/bison/bison-3.0.tar.xz

tar -xf bison-3.0.tar.xz

cd bison-3.0

./configure

make -j $THREADS  注意多线程太多 容易耗尽内存


make install

### 7: 安装clang

curl -LO http://releases.llvm.org/3.9.1/cfe-3.9.1.src.tar.xz

curl -LO http://releases.llvm.org/3.9.1/llvm-3.9.1.src.tar.xz

tar -xf cfe-3.9.1.src.tar.xz

tar -xf llvm-3.9.1.src.tar.xz

mkdir clang-build

mkdir llvm-build

cd llvm-build

cmake -G "Unix Makefiles" -DLLVM_TARGETS_TO_BUILD="BPF;X86" \

  -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr ../llvm-3.9.1.src
  
make -j $THREADS

sudo make install


cd ../clang-build

cmake -G "Unix Makefiles" -DLLVM_TARGETS_TO_BUILD="BPF;X86" \

  -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr ../cfe-3.9.1.src

make -j $THREADS

sudo make install

### 8: 下载BCC的依赖

yum install -y elfutils-libelf-devel flex

### 9: 下载BCC

git clone https://github.com/iovisor/bcc.git

export CFLAGS=-I${HOME}/build/linux-4.9.71/usr/include

mkdir bcc-build

cd bcc-build

cmake -G "Unix Makefiles" -DCMAKE_INSTALL_PREFIX=/usr ../bcc

make -j $THREADS

make install

### 10: 测试

cachestat


参考：

     1：https://www.jianshu.com/p/997e0a6d8e09

     2：https://github.com/iovisor/bcc/issues/462
