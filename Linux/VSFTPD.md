# Install FTP Service  

使用 yum 安装 vsftpd  
``` 
yum install -y vsftpd
```

# Start FTP Service  
安装完成后，启动 FTP 服务：  
~~service vsftpd start  【slashed】~~  
```
/bin/systemctl start vsftpd.service  
```  
启动后，可以看到系统已经监听了 21 端口：
```  
netstat -nltp | grep 21  
```  
此时，访问 ftp://192.168.1.170 可浏览机器上的 /var/ftp目录了。
  
```
如果不能访问，要关闭本机的防火墙  
如果关了防火墙还不能访问，要看云服务提供商是不是有安全策略，如阿里云的安全组设置(20/21端口)。
```  

如果要设置ftp开机启动，需要设置
```
# systemctl enable vsftpd.service
Created symlink from /etc/systemd/system/multi-user.target.wants/vsftpd.service to /usr/lib/systemd/system/vsftpd.service.

```

# 设置登录用户  
运行以下命令创建 ftptest 用户。    
```
useradd ftptest

```

运行以下命令修改 ftptest 用户密码。

```
passwd ftptest

```

修改/etc/vsftpd/vsftpd.conf：  

```
anonymous enable=NO
local_enable=YES
```
修改ftp目录权限，重启ftp服务
```
chmod o+w /var/ftp/pub/
systemctl restart vsftpd.service
```





# 其他问题
[在阿里云“专有网络”网络类型中配置vsftpd](https://bbs.aliyun.com/read/534639.html?spm=a2c4e.11155515.0.0.XBhKe5)  
[阿里云FTP：“服务器发回了不可路由的地址。使用服务器地址代替。”](https://bbs.aliyun.com/read/539360.html?page=e)  
[http://bbs.51cto.com/thread-1156344-1.html](vsftp 无法启动 在线等)

#References  
[基于 CentOS 搭建 FTP 文件服务](https://www.linuxidc.com/Linux/2017-11/148518.htm)  
[Linux云主机服务器安全策略设置](https://help.aliyun.com/knowledge_detail/51062.html)  
[安全组设置](https://help.aliyun.com/document_detail/25833.html)  
[使用 FTP 上传或下载文件](https://helpcdn.aliyun.com/document_detail/58746.html?spm=a2c4g.11186623.2.26.eV9Wur#ftp)  
[使用 ECS 实例创建 FTP 站点](https://helpcdn.aliyun.com/document_detail/51998.html?spm=a2c4g.11186623.2.13.nFE0qu)
