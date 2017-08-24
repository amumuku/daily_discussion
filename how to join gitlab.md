---
title: how to join gitlab 
---
# 生成一个公钥

*windows用户*

		1）首先需要下载一个windows下得git bash工具，它是一个运行在windows下模拟linux bash环境的一个终端，大概长这个样子

		2）然后就可以在bash环境下，类似linux一样生成公钥，应该是执行这个命令ssh-keygen.exe，然后一直按回车即可
		
*linux和mac用户*

		先用ssh-keygen程序生成自己的公钥
		
# 将公钥注册到gitlab上

	1）公钥一般在 ~/.ssh/id_rsa.pub，然后可以cat一下就输出公钥了（cat ~/.ssh/id_rsa.pub）
	2）将公钥注册到gitlab上
	3）进入http://gitlab.flyfire.com/profile/keys(对应项目链接)，上面选择Add SSH Key
	4）将公钥粘贴进去，然后点Add Key 即可
	
## 注册完后，就可以使用git clone gitlab下有权限的代码了
	
