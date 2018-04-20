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





#References  
[基于 CentOS 搭建 FTP 文件服务](https://www.linuxidc.com/Linux/2017-11/148518.htm)  
[Linux云主机服务器安全策略设置](https://help.aliyun.com/knowledge_detail/51062.html)  
[安全组设置](https://help.aliyun.com/document_detail/25833.html)  
[使用 FTP 上传或下载文件](https://helpcdn.aliyun.com/document_detail/58746.html?spm=a2c4g.11186623.2.26.eV9Wur#ftp)  
[使用 ECS 实例创建 FTP 站点](https://helpcdn.aliyun.com/document_detail/51998.html?spm=a2c4g.11186623.2.13.nFE0qu)
