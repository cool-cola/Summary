> 声明：本文主要是本人从网上参考学习后的一个简单总结

程序的运行要去加载所需要的dll文件，在程序运行的时候往往会遇到dll找不到的问题，或者不能确定所加载的dll文件是否是自己所需要的dll，遇到dll出问题的时候往往会不知所措，但是一旦知道了dll的加载顺序，按这个去查找解决就会方便很多。

###### 首先，搜索可执行文件所在路径，在搜索系统路径：%PATH%（环境变量所配置的路径）

> 一般path中的值为：%HIVE_ROOT%/lib/x86;(ps:这是我们实验室自己写的库的路径)

###### 然后，按照下列顺序搜索dll：

> - 当前进程的可执行模块所在的目录
> - 当前目录
> - windows系统目录。GetSystemDirectory函数检索此目录的路径。
> - windows目录。GetWindowsDirectory函数检索此目录的路径
> - Path环境变量中列出的目录


有时候确定了加载的dll文件确实是自己所想加载的dll文件，但是还会发生错误的可能原因，就是dll文件被损坏，此时需要重新替换现有的dll文件；或者dll文件和所用的头文件（.h文件）不匹配，即是头文件中的函数，在dll文件中没有实现，这样的话，找到对应的dll文件就ok了。