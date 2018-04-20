# 安装前准备工作  
## 下载压缩包（别看已经是下载地址，要先登录的）  
[http://download.oracle.com/otn/linux/oracle12c/122010/linuxx64_12201_database.zip](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index.html)

## 更新软件、安装jdk、安装oracle前置条件
```
# yum -y install java-1.8.0-openjdk*
#  yum -y install binutils compat-libstdc++ compat-libstdc++-33 elfutils-libelf-devel gcc gcc-c++ glibc-devel glibc-headers ksh libaio-devel libstdc++-devel make sysstat unixODBC-devel binutils-* compat-libstdc++* elfutils-libelf* glibc* gcc-* libaio* libgcc* libstdc++* make* sysstat* unixODBC* wget unzip

```

## 上传压缩包到服务器并解压  

```
# mkdir /data
# cd /home/ftpuser
# mv linuxx64_12201_database.zip /data
# cd /data
# unzip linuxx64_12201_database.zip
# ls 
```

# 安装  
## 创建用户和组    
```  
# groupadd oinstall  
# groupadd dba  
# useradd -g oinstall -G dba oracle  
# passwd oracle  
```  

## 创建Oracle安装目录    
```  
# mkdir -p /data/oracle  

# chown -R oracle:oinstall /data/oracle/  

# chmod -R 775 /data/oracle/  
```  

## 安装   
### 切换用户并安装。
```
# su oracle  

$ cd /data/database  

$ ls  
$ ./runInstaller
```


# 问题及处理  
[centos 安装oracle 报Checking swap space: 0 MB available, 150 MB required. Failed <<<<](https://www.cnblogs.com/a9999/p/6957280.html)  

# 参考文章：
[最小安装centos 7 无GUI静默安装 oracle 12c，打造轻量linux化服务器](https://www.cnblogs.com/mokeyish/p/5531769.html)
