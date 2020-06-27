#**`Linux环境下安装Python3`**

###1.安装依赖环境
	yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel
###2.wget下载安装包(cd /opt): 
    wget https://www.python.org/ftp/python/3.7.1/Python-3.7.1.tgz
	注:如果出现wget not found: yum -y install wget  安装wget即可
###3.mkdir -p /usr/local/python3 
###4.解压： tar -zxvf Python-3.7.1.tgz
###5.编译安装
	安装编译器：yum install gcc
	注:3.7版本后需要一个新的包：libffi-devel
		安装：yum install libffi-devel -y
###6.进入python文件夹，生成编译脚本(指定安装目录):
    cd Python-3.7.1
	./configure --prefix=/usr/local/python3
###7.编译：make
###8.编译安装：make install
###9.检查python3.7的编译器：/usr/local/python3/bin/python3.7
###10.建立Python3和pip3的软链：
	ln -s /usr/local/python3/bin/python3 /usr/bin/python3
	ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
###11.添加环境变量
	vim /etc/profile  进入编辑后，将以下信息添加至配置文件
	
	# vim ~/.bash_profile
	# .bash_profile
	# Get the aliases and functions
	if [ -f ~/.bashrc ]; then
	. ~/.bashrc
	fi
	# User specific environment and startup programs
	PATH=$PATH:$HOME/bin:/usr/local/python3/bin
	export PATH
	
###12.重启配置信息：source ~/.bash_profile
###13.检查：python3 -V   pip3 -V