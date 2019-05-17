
lib_LTLIBRARIES：用于生成动态库

lib_LIBRARIES：用于生产静态库

bin_PROGRAMS：用于生成可执行程序，程序会被安装到$(prefix)/bin目录下。

noinst_PROGRAMS/noinst_LIBRARIES：只编译，而不想安装到系统中。
