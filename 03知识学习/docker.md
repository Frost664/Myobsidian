## docker 架构
镜像 Image
容器 Container
仓库 Repository

镜像 相当于环境
容器 类似于启动的案例

一个镜像可以 有好几个容器
镜像是创建docker容器的模板

容器独立运行
docker registry  仓库

## Ubuntu  docker 安装
```shell
# 自动安装
 curl -fsSL https://test.docker.com -o test-docker.sh
 sudo sh test-docker.sh

# 手动安装
sudo apt-get remove docker docker-engine docker.io containerd runc

$ sudo apt-get update
$ curl -fsSL https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu/gpg | sudo apt-key add -

$ sudo apt-key fingerprint 0EBFCD88
    
pub   rsa4096 2017-02-22 [SCEA]
      9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
sub   rsa4096 2017-02-22 [S]
```

```
docker ps
# 查看当前运行的容器
```