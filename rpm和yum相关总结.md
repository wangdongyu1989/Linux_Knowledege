## rpm（RedHat Package Manager）

rpm简单地说就是安装软件的命令，这些软件都是编译通过的，因为我们使用的linux操作环境和软件开发商是相同的，所以可以直接安装使用。

常用命令总结：

rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org 导入相关软件秘钥
rpm -Uvh https://www.elrepo.org/elrepo-release-7.0-3.el7.elrepo.noarch.rp 后面接的软件及时没有安装，则系统将予以安装；否则后面的软件有安装过旧版，则系统自动更新至新版


## yum
