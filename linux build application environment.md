---
title: linux build application environment
grammar_cjkRuby: true
---
# 1.Linux 安装Tomcat

	tomcat只要解压就可以使用。
	1、	创建web目录
			mkdir /ucenter/web
	2、	上传apache-tomcat-7.0.57.tar.gz
	3、	解压
			tar -zxvf apache-tomcat-7.0.57.tar.gz
	4、	重命名
			mv apache-tomcat-7.0.57 tomcat
	5、	启动tomcat：
			cd  /ucenter/web/tomcat/bin/
			./startup.sh 或者 sh startup.sh
	6、	查看日志：
			tail -f /ucenter/web/tomcat/logs/catalina.out
	7、	查看效果 http://192.168.0.160:8080/
	发现无法访问：
	8、	防火墙打开 8080 端口
		1)单独打开8080端口
			vi /etc/sysconfig/iptables
			添加：
			-A INPUT -m state --state NEW -m tcp -p tcp --dport 8080 -j ACCEPT
			service iptables restart
		2）临时关闭防火墙
			service iptables stop
		3）永久关闭防火墙，需要重启
			chkconfig iptables off
		4)输入setup，去掉防火墙中的*
		5）查看防火墙状态
			chkconfig iptables –list
9、	安装成功
![enter description here][1]

# 2.Linux 安装mysql
*1.	卸载linux自带的mysql*

	1.1.	查看
			 rpm -qa | grep mysql
	1.2.	卸载
			rpm -e --nodeps 查看到的选项
*2.	安装mysql(使用yum安装)*
		
	2.1.	yum安装
			  yum install -y mysql-server mysql mysql-deve
	2.2.	启动mysql
			  service mysqld start
	2.3.	查看mysql服务
			  ps –ef | grep mysql
	2.4.	登陆
			  mysql –u root –p
			 无密码
	2.5.   修改root密码
			 mysqladmin -u root password 'root'

*3 （安装mysql）*[非yum安装参见jdk安装](https://github.com/amumuku/daily_discussion/blob/master/linux%20build%20jdk%20environment.md) 


*4.	开启远程连接*

	4.1.	开启端口
			  vi /etc/sysconfig/iptables
   			 添加防火墙信息(添加端口号)
			 重启防火墙：
			 service iptables restart
	4.2.	关闭selinux
			关闭：setenforce 0
			查看：getenforce
	4.3.	授权远程连接
			GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' 				IDENTIFIED BY 'root' WITH GRANT OPTION;
			flush privileges;
*5.	用sqlyong（或者其他工具）链接mysql服务器*

		进行链接
		
*6.	开机启动*

	6.1.	查看mysql是否开机启动
			  chkconfig --list | grep mysqld
	6.2.	开启mysql开机启动
			  chkconfig mysqld on



  [1]: ./images/tomcat-home.jpg "tomcat-home"
  
  