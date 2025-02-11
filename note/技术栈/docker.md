设置镜像:`docker pull [image]`

参数为以命令行模式进入该容器:`docker run -i-t ubuntu /bin/bash`
其中-i：交互式操作，-t：终端，后续是镜像和命令
退出输入exit

## 启用已停止运行的容器
查看所有的容器：`docker ps -a`

启用一个停止的容器：`docker start [容器 ID]`

## 后台运行
-d可以指定容器的运行模式：`docker run -itd --name ubuntu-test ubuntu /bin/bash`

加了-d参数默认不会进入容器，想要进入容器需要使用指令 `docker exec`

## 停止一个容器
`docker stop <容器 ID>`
## 重启停止的容器
`docker restart <容器 ID>`

## 进入容器
使用 **-d** 参数时，容器启动后会进入后台，此时进入容器使用以下指令

`docker attach`<br> 
`docker exec`：推荐大家使用 docker exec 命令，因为此命令会退出容器终端，但不会导致容器的停止
例：`docker attach <容器 ID>`<br>
`docker exec -it <容器 ID> /bin/bash`


## 导出和导入容器快照
导出：`docker export <容器 ID> > <文件名称(ubuntu.tar)>`<br>
导入：`cat docker/buntu.tar | docker import - test/ubuntu:v1`<br>
`docker import <url>`

## 删除容器
`docker rm -f <容器 ID>`

## 运行web应用
`docker pull training/webapp  # 载入镜像`<br>
`docker run -d -P training/webapp python app.py`<br>
**-P:** 将容器内部使用的网络端口随机映射到我们使用的主机上。<br>
`docker run -d -p 5000:5000 training/webapp python app.py`