## rpm（RedHat Package Manager）

rpm简单地说就是安装软件的命令，这些软件都是编译通过的，因为我们使用的linux操作环境和软件开发商是相同的，所以可以直接安装使用。

常用命令总结：

rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org 导入相关软件秘钥

注释：noarch.rpm可以在不同的cpu上使用，包有这么几种（后缀）：*.386.rpm,*.486.rpm,*.586. rpm,*.686.rpm，这是与CPU的指令集有关.

rpm -Uvh https://www.elrepo.org/elrepo-release-7.0-3.el7.elrepo.noarch.rpm 后面接的软件及时没有安装，则系统将予以安装；否则后面的软件有安装过旧版，则系统自动更新至新版

注释：会在/etc/yum.repos.d目录下面生成相应elrepo.repo配置文件

rpm -qa 列出所有的，已经安装在本机linux系统上面的所有软件名称

## yum

yum基于RPM包管理，能够从指定的服务器上自动下载rpm包并且安装，可以自动处理依赖性关系，并且一次解决所有依赖的软件包，无需繁琐地一次次下载，安装。

yum 的配置文件分为两部分：main 和repository:

main 部分定义了全局配置选项，整个yum 配置文件应该只有一个main。常位于/etc/yum.conf 中。
repository 部分定义了每个源/服务器的具体配置，可以有一到多个。常位于/etc/yum.repo.d 目录下的各文件中。

yum的配置软件仓库地址放到了/etc/yum.repos.d/目录下面 

注释：/etc/yum.conf中pkgpolicy选项，包的策略。一共有两个选项，newest 和last，这个作用是如果你设置了多个repository，而同一软件在不同的repository 中同时存在，yum 应该安装哪一个，如果是newest，则yum 会安装最新的那个版本。如果是last，则yum 会将服务器id 以字母表排序，并选择最后的那个服务器上的软件安装。一般都是选newest。
