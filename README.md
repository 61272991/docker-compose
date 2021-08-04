docker-compose.yml 配置指令参考

🔗：https://www.runoob.com/docker/docker-dockerfile.html
🔗：https://www.runoob.com/docker/docker-compose.html

version
指定本 yml 依从的 compose 哪个版本制定的。

build
指定为构建镜像上下文路径。

command
覆盖容器启动的默认命令。

container_name
指定自定义容器名称，而不是生成的默认名称。

depends_on
设置依赖关系。


示例/模板：

# docker-compose版本号
version: '3'  
# 定义服务配置信息
services:
  # 容器名称
  redis:
    # 镜像
    image: redis:latest
    # 重启策略
    restart: "no"
    # 别名
    container_name: redis
    # 文件映射
    volumes:
      - ./docker-conf/nginx/redis.conf:/etc/redis/redis.conf
      - ./docker-conf/nginx/data:/data
    # 覆盖容器启动默认指令
    command:
    ["redis-server", "--appendonly no", "--requirepass redis"]
    /bin/bash -c "redis-server /etc/redis/redis.conf"
    # 端口映射
    ports:
      - 6379:6379
      
      



docker-compose 命令详解

1.docker-compose的使用非常类似于docker命令的使用，但是需要注意的是大部分的compose命令都需要到docker-compose.yml文件所在的目录下才能执行。

2.【Linux命令】docker-compose up【命令解释】 命令聚合每个容器的输出，命令退出时，所有容器都将停止。

3.【Linux命令】docker-compose up -d【命令解释】 在后台启动容器并使它们保持运行。

4.【Linux命令】docker-compose logs -f【命令解释】 查看该容器的启动的日志打印(日志从头打印)。

5.【Linux命令】docker logs -f container_id【命令解释】 查看某一容器的启动的日志打印(日志从头打印)。 

6.【Linux命令】docker logs -f --tail 数量词 container_id【命令解释】 查看某一容器的启动的日志打印(查看最后n条日志打印)。 例：docker logs -f --tail 50 44b 

7.【Linux命令】docker-compose stop【命令解释】 停止compose服务。

8.【Linux命令】docker-compose restart【命令解释】 重启compose服务。

9.【Linux命令】docker-compose kill【命令解释】 kill compose服务。

10.【Linux命令】docker-compose ps【命令解释】查看compose服务状态。

11.【Linux命令】docker-compose rm【命令解释】删除compose服务。
