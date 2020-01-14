# docker-compose-lamp
基于docker-compose构建LAMP运行环境
启动应用

1、安装docker环境。（参考docker文档 https://docs.docker.com/install/linux/docker-ee/centos/#install-docker-ee-1 ）

2、下载当前项目并解压，进入docker-compose.yml所在目录，执行docker-compose build构建镜像。

3、执行docker-compose up -d启动容器服务。

4、访问 http://localhost:8080 可看到phpinfo信息。
