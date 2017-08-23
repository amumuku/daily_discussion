---
title: linux build jdk environment
grammar_cjkRuby: true
---

# 1.1 切换到root用户：
 			su – root;
# 1.2 查看以前是不是安装了openjdk

		命令：rpm -qa | grep java
		显示如下：（有则卸载，没有就不用,下面是个显示的例子）
		tzdata-java-2013g-1.el6.noarch
	    java-1.7.0-openjdk-1.7.0.45-2.4.3.3.el6.x86_64
	    java-1.6.0-openjdk-1.6.0.0-1.66.1.13.0.el6.x86_64

# 1.3 卸载openjdk

	rpm -e --nodeps  tzdata-java-2013g-1.el6.noarch
	rpm -e --nodeps  java-1.7.0-openjdk-1.7.0.45-2.4.3.3.el6.x86_64
	rpm -e --nodeps  java-1.6.0-openjdk-1.6.0.0-1.66.1.13.0.el6.x86_64
	（其中参数“tzdata-java-2013g-1.el6.noarch”为上面查看中显示的结果，粘进来就行）


# 1.4 安装sunjdk：
		1、	切换到root用户，如果已经是root用户就不需要				切换了
				su - root
		2、	进入usr目录
				cd /usr
		3、	在usr目录下创建java文件夹
				mkdir java
		4、	将jdk-7u71-linux-x64.tar.gz拷贝到java目录下(用					工具)
				用rz或者工具（xftp）
		5、	进入/usr/java文件夹下
				 cd /usr/java
		6、	修改权限，参数“jdk-7u71-linux-x64.tar.gz”为你				自己上传的jdk安装文件
				chmod 755 jdk-7u71-linux-x64.tar.gz
		7、	解压
				tar -zxvf jdk-7u71-linux-x64.tar.gz
		8、	创建快捷方式 
				ln -s /usr/java/ jdk1.7.0_71/ /usr/jdk
				参数：
				“/usr/java/ jdk-7u71-linux-x64/”为你jdk安装的路					径
				“/usr/jdk”为你需要创建的jdk快捷方式的路径，				此“/usr/jdk”路径需要配置到环境变量。
		9、	配置环境变量
				vi /etc/profile
				添加内容：
				export JAVA_HOME=/usr/jdk
				export PATH=$PATH:$JAVA_HOME/bin
				export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
				export JAVA_HOME PATH CLASSPATH
		10、	重新编译环境变量
				source /etc/profile
				
	遇到jdk版本问题  linux-64位版本与linux操作系统不一致问题，可以用32位装一下linux i586版本，home路径配置问题


