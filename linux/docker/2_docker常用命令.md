1. 镜像（Images）相关命令：
    • docker images：列出本地所有的镜像。
    • docker search [镜像名]：搜索镜像仓库中的镜像。
    • docker pull [镜像名]：从镜像仓库中拉取镜像到本地。
    • docker rmi [镜像ID]：删除指定的镜像。
2. 容器（Containers）相关命令：
    • docker ps：列出正在运行的容器。
    • docker ps -a：列出所有的容器，包括已经停止的。
    • docker run [选项] [镜像名] [命令]：创建并启动一个容器。
    • docker start [容器ID]：启动一个已经停止的容器。
    • docker stop [容器ID]：停止一个正在运行的容器。
    • docker rm [容器ID]：删除指定的容器。
    • docker exec -it [容器ID] [命令]：在运行的容器中执行命令。
3. 网络（Networking）相关命令：
    • docker network ls：列出所有的网络。
    • docker network inspect [网络名]：查看指定网络的详细信息。
    • docker network create [网络名]：创建一个新的网络。
4. 日志（Logging）相关命令：
    • docker logs [容器ID]：查看容器的日志。
    • docker logs -f [容器ID]：实时查看容器的日志。
5. 数据卷（Volumes）相关命令：
    • docker volume ls：列出所有的数据卷。
    • docker volume create [数据卷名]：创建一个新的数据卷。
    • docker volume inspect [数据卷名]：查看指定数据卷的详细信息。
6. 其他常用命令：
    • docker info：显示 Docker 系统信息，包括镜像和容器的数量等。
    • docker version：显示 Docker 版本信息。
    • docker-compose：用于管理多个容器的工具，可以通过编写 docker-compose.yml 文件来定义容器间的关系和配置。



docker查看运行过的容器
docker ps -a

查看容器日志
docker logs [镜像ID]
