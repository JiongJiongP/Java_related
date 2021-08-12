# Docker

## 容器技术

容器的目的是实现隔离，原有的隔离方式有虚拟机，但有几个缺点：内存占用、启动时间漫长；容器技术只隔离应用程序的运行时环境但容器之间可以共享一个操作系统。



## Docker

Docker是容器的一种实现，docker的优势是：屏蔽环境差异；快速部署。  

1. docker中的概念：

- dockerfile：
  - image的源码，dockerfile指定了需要哪些程序，依赖哪些配置，由docker进行编译，也就是docker build命令，build的结果是生成image

- image：
  - 可以理解为可执行程序，docker在编译dockerfile后生成可执行程序image，再执行docker run，运行起来之后生成的进程就是docker container

- container：
  - 可以理解为运行时的进程

2. docker是如何运行的

- docker build
  - dockerfile完成后进行build命令，client端收到命令后转发给docker daemon进程，由该进程创建image
- docker run
  - 执行docker run时，还是由docker daemon进程找到具体的执行的image，然后加载内run运行，image执行起来后就是container
- docker pull
  - docker registry是一个远程仓库，里面存储了大量的公共image方便调用，该命令通过daemon进程从docker hub中下载image

3. docker的底层实现

- Namespace：一种资源隔离方案，管理Linux中的公共资源如PID, IPC,网络等，使得这些资源不再是全局的，而是属于某个Namespace的
- Control groups：控制容器中的进程对资源的消耗，比如设置内存使用上限等





















