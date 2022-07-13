# linux 修改系统资源限制

**1：解除 Linux 系统的最大进程数和最大文件打开数限制**

```
vi /etc/security/limits.conf
 # 添加如下的行
*  soft  nproc  655350
*  hard  nproc  655350
*  soft  nofile 655350
*  hard  nofile 655350
说明：
* 代表针对所有用户
* noproc 是代表最大进程数
* nofile 是代表最大文件打开数
```

**2：修改用户最大连接数**

```
vim /etc/security/limits.d/20-nproc.conf
修改
*  soft  nproc  65535
```

**3：更改系统最大文件数永久生效**

```
vim /etc/sysctl.conf
添加
fs.file-max = 6815744
执行
sysctl -p
```

