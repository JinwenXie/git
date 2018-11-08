## 使用git上遇到的一些问题<br>

### 一、github连接超时<br>
检查连接github是否成功  
在命令行输入：   `ssh -T git@github.com`  
如果出现：You've successfully authenticated，那么连接成功可以使用了；  
如果出现：ssh: connect to host github.com port 22: Connection timed out，很遗憾连接超时；  

**解决方法：**  
首先我们得要找到git的安装目录，找到/etc/ssh/ssh_config文件*（如果忘记了自己git的安装目录，我们可以在命令行输入：`where git`就可以打印出git的安装目录）*;<br>
![](https://i.imgur.com/XmVFspc.png)  

然后在ssh_config文件末尾处添加：  
	`Host github.com `
	`User git`  
	`Hostname ssh.github.com`  
	`PreferredAuthentications publickey`  
	`IdentityFile ~/.ssh/id_rsa`  
	`Port 443`  
保存后，命令行重跑 `ssh -T git@github.com`  
出现如下图情况：  
![](https://i.imgur.com/VdlicvC.png)  
输入： `yes` 即可  
出现如下图文字，即表示连接成功  
![](https://i.imgur.com/JqMRAAr.png)

