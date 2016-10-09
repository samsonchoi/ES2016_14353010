# Lab1:Dol开发环境配置



-------------------


## Description


The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.


## How to install


###1.安装VMWARE及Ubuntu

###2.安装一些必要的环境
`$	sudo apt-get update`
`$	sudo apt-get install ant`
`$ 	sudo apt-get install openjdk-7-jdk`
`$	sudo apt-get install unzip`

###3.下载文件
`$	sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz`
`$	sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip`

###4.解压文件
新建dol的文件夹 
`$	mkdir dol`
将dolethz.zip解压到 dol文件夹中
`$	unzip dol_ethz.zip -d dol`
解压systemc
`$	tar -zxvf systemc-2.3.1.tgz`

###5.编译systemc
解压后进入systemc-2.3.1的目录下
`$	cd systemc-2.3.1`
新建一个临时文件夹objdir
`$	mkdir objdir`
进入该文件夹objdir
`$	cd objdir`
运行configure(能根据系统的环境设置一下参数，用于编译)
`$	../configure CXX=g++ --disable-async-updates`
编译
`$	sudo make install`
编译完后文件目录如下
`$ cd ..        $ ls`
记录当前的工作路径
`$	pwd`

###6.编译dol
进入刚刚dol的文件夹
`$	cd ../dol`
修改build_zip.xml文件,编译
`$	ant -f build_zip.xml all`
接着运行第一个例子
进入build/bin/main路径下
`$	cd build/bin/main`
然后运行第一个例子
`$	ant -f runexample.xml -Dnumber=1`


## Experimental experience


本次实验虽然只是配置环境，但是在配置的过程中依然遇到一些问题。首先是下载dol_ethz和systemc-2.3.1时，我尝试直接从windows中通过拖动文件的方式将文件移入虚拟机的文件夹中。结果在解压文件的时候报错，显示该文件不是可解缩文件。重复尝试了几次还是不行，最后通过`$	sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz`和`$	sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip`指令在线下载文件，才成功解压文件。

在编译systemc时也遇到了一些问题，在运行configure时，命令行报错。我上网查了一下这个错误，发现是g++的库不完整，应该是前面步骤出现问题，或者是这个版本的ubantu的问题。运用网上的解决方法（即重新装这个库），在成功运行configure。

通过本次实验，我学会了在虚拟机的ubantu系统下配置dol文件，并能够在github上创建仓库并把虚拟机中的文件传到仓库中。
