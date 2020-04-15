# 如何在Windows和Linux系统之间进行文件共享（以Ubuntu为例）？

## 01. 什么是samba？

废话少说，甩给你俩个网址：

[Samba](https://www.samba.org/samba/)

[维基百科](https://zh.wikipedia.org/wiki/Samba)

## 02. 操作步骤

### 2.1 安装Samba

`sudo apt install samba`

### 2.2 创建共享目录

```
mkdir /home/xxx(你的用户名)/share(名字自己定)
sudo chmod 777 /home/xxx/share
```

### 2.3 修改配置文件

```
# 先备份一个原件
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
# 默认安装了vim，如果没有可以其他方式打开这个文件，带上权限sudo命令
sudo vim /etc/samba/smb.conf
# 添加以下内容,可以根据自己实际情况设置
[share]
comment = share for users
path = /home/xxx/share
available = yes
browseable = yes
writable = yes
public = no
```

### 2.4 设置登录samba密码

```
sudo touch /etc/samba/smbpasswd
sudo smbpasswd -a xxx
```

### 2.5 重启samba

`sudo /etc/init.d/smbd restart`

### 2.6 Linux下测试

```
 # 如果smbclient未安装
 sudo apt install smbclient
 # 该命令回车后提示输入密码则表示成功
 smbclient -L //localhost/share
```

### 2.7 Windows下测试

打开文件管理器，输入`\\linux ip address\share`回车

按提示输入用户名和密码，*then just enjoy it !*

> 键入命令`hostname -I`查看Linux ip

## 03. 参考资料

[Linux与Windows共享文件夹之samba的安装与使用（Ubuntu为例）](https://www.cnblogs.com/gzdaijie/p/5194033.html)

[Ubuntu下配置samba实现文件夹共享](https://www.cnblogs.com/phinecos/archive/2009/06/06/1497717.html)

[配置samba服务器](https://wiki.jikexueyuan.com/project/linux/samba.html)

[Linux chmod命令](https://www.runoob.com/linux/linux-comm-chmod.html)

[如何在Linux系统这查看IP地址](https://zh.wikihow.com/在Linux系统中查看IP地址)