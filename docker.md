### 一、Docker命令

#### 命令大全

``` shell
docker version # 版本信息
docker --help  # 帮助命令
docker info    # 显示docker的系统信息，包括镜像核容器的数量
```



#### 镜像命令

``` shell
[root@iZuf64cki7jj44bn4pr5upZ ~]# docker images
REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
hello-world   latest    d1165f221234   4 months ago   13.3kB

# 解释
REPOSITORY # 镜像仓库源
TAG		   # 镜像标签
IMAGE ID   # 镜像id
CREATED    # 镜像创建时间
SIZE       # 镜像大小

# 可选项 docker images --help
Options:
  -a, --all             Show all images (default hides intermediate images)
  -q, --quiet           只显示id



```

**docker search搜索镜像**

```shell
[root@iZuf64cki7jj44bn4pr5upZ ~]# docker search mysql --filter=STARS=3000
NAME      DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
mysql     MySQL is a widely used, open-source relation…   11142     [OK]       
mariadb   MariaDB Server is a high performing open sou…   4224      [OK] 
```

**docker pull**

```shell
#下载镜像
[root@iZuf64cki7jj44bn4pr5upZ ~]# docker pull mysql
Using default tag: latest                  # 没有tag的话使用最新版
latest: Pulling from library/mysql
b4d181a07f80: Pull complete 			   # 分层下载，docker iamges的核心，联合文件系统
a462b60610f5: Pull complete 
578fafb77ab8: Pull complete 
524046006037: Pull complete 
d0cbe54c8855: Pull complete 
aa18e05cc46d: Pull complete 
32ca814c833f: Pull complete 
9ecc8abdb7f5: Pull complete 
ad042b682e0f: Pull complete 
71d327c6bb78: Pull complete 
165d1d10a3fa: Pull complete 
2f40c47d0626: Pull complete 
Digest: sha256:52b8406e4c32b8cf0557f1b74517e14c5393aff5cf0384eff62d9e81f4985d4b
Status: Downloaded newer image for mysql:latest
docker.io/library/mysql:latest              # 真实地址

# 上面的命令等价于
docker pull mysql
docker pull docker.io/library/mysql.latest

# 指定版本
docker pull mysql:5.7

```



**删除命令**

```shell
[root@iZuf64cki7jj44bn4pr5upZ ~]# docker images
REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
mysql         5.7       09361feeb475   3 weeks ago    447MB
mysql         latest    5c62e459e087   3 weeks ago    556MB
hello-world   latest    d1165f221234   4 months ago   13.3kB
[root@iZuf64cki7jj44bn4pr5upZ ~]# docker rmi -f 5c62e459e087    # 删除单个
Untagged: mysql:latest
# 删除单个
docker rmi -f 镜像ID

# 删除多个
docker rmi -f 镜像ID1 镜像ID2

# 删除全部
docker rmi -f $(docker images -aq)
```

####  容器命令

**下载一个centos用来学习**

```shell
# 下载一个centos虚拟机
docker pull centos
```

**新建容器并启动**

```shell
docker run [可选参数] image

# 参数说明
--name=“Name”				容器名字 tomcat01 tomcat02 用来区分
-d							后台方式运行
-it							使用交互方式运行，进入容器查看内容
-p							制定容器的端口 -p 8080:8080
	-p ip：主机端口：容器端口
	-p 主机端口：容器端口（常用）
	-p 容器端口
	容器端口
	-p 随机制定端口

```

