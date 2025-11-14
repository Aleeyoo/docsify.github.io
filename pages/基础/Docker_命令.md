## **Docker 常用命令**

<!-- tabs:start -->
#### **镜像管理**

+ 查看本地所有镜像 +

  语法格式：<br> `docker images`

  > 同类：<br>
  > `docker image ls`

+ 从仓库下载镜像 +

  语法格式： `docker pull <镜像名>:<标签>`
  <br>（如果不指定标签，默认下载最新版本）

  > 示例：<br>
  > docker pull nginx:latest

+ 用当前目录的 `Dockerfile` 构建镜像 +

  语法格式： `docker build -t <名称:标签> .`
  <br> （`.` 表示当前目录）

  > 示例：<br>
  > docker build -t my-nginx:1.0 .

  > 说明：<br>
  > *`Dockerfile` 是一个文本文件，用于定义如何构建 Docker 镜像。*<br>
  > *它包含了一系列的指令，用于指定基础镜像、复制文件、安装依赖、设置环境变量等。*<br>
  > *构建镜像时，Docker 会根据 `Dockerfile` 中的指令执行相应的操作，最终生成一个新的镜像。*

+ 查看镜像构建历史 +

  语法格式： `docker history <镜像ID或名称>`

  > 示例：<br>
  > docker history my-nginx:1.0

+ 删除一个镜像 +

  语法格式： `docker rmi <镜像ID或名称>`

  > 示例：<br>
  > docker rmi my-nginx:1.0

+ ⚠️ 删除所有未使用的镜像 ⚠️ +

  语法格式： `docker rmi $(docker images -q)`

  > 说明：<br>
  > *`docker images -q` 命令用于列出所有镜像的 ID。*<br>
  > *`$()` 是 Bash 中的命令替换语法，用于将命令的输出作为参数传递给另一个命令。*<br>
  > *Docker 不允许删除正在被使用的镜像。*

+ 清理悬空镜像（build 失败残留） +

  语法格式： `docker image prune`

  > 说明：<br>
  > *悬空镜像是指那些没有被任何容器使用，也没有被任何标签引用的镜像。*<br>
  > *清理悬空镜像可以释放磁盘空间，避免镜像占用过多的空间。*

+ 导出 / 导入镜像（离线传输） +

  语法格式： `docker save -o <导出文件路径> <镜像ID或名称>`
  <br>（`-o` 表示输出到文件）

  > 示例：<br>
  > docker save -o my-nginx.tar my-nginx:1.0

  语法格式： `docker load -i <导入文件路径>`
  <br>（`-i` 表示输入文件）

  > 示例：<br>
  > docker load -i my-nginx.tar

+ 给镜像打多个标签 +

  语法格式： `docker tag <镜像ID或名称> <新标签>`

  > 示例：<br>
  > docker tag my-nginx:1.0 my-nginx:latest

+ 🛠️ 可能报错 +

  **提示权限错误，请检查 Docker 是否运行**

#### **容器管理**

+ 创建并启动一个容器 +

  语法格式： `docker run [选项] <镜像名>`<br>
  root 权限：`docker run --privileged -it <镜像名> bash`

  > 示例：<br>
  > docker pull nginx:latest

+ 启动已停止的容器 +

  语法格式： `docker start <容器ID或名称>`

  > 示例：<br>
  > docker start my-nginx
  
+ 停止正在运行的容器（优雅关闭） +

  语法格式： `docker stop <容器ID或名称>`

  > 示例：<br>
  > docker stop my-nginx

+ 重启容器 +

  语法格式： `docker restart <容器ID或名称>`

  > 示例：<br>
  > docker restart my-nginx

+ 删除已停止的容器 +

  语法格式： `docker rm <容器ID或名称>`<br>
  （可选参数：`-f` 强制删除正在运行的容器）

  > 示例：<br>
  > docker rm my-nginx
  
+ 暂停 / 恢复容器 +

  语法格式： `docker pause/unpause <容器ID或名称>`<br>
  （可选参数：`-a` 暂停所有容器）

  > 示例：<br>
  > docker pause my-nginx

+ 查看正在运行的容器 +

  语法格式： `docker ps`<br>
  （可选参数：`-a` 显示所有容器，包括已停止的容器）

  > 示例：<br>
  > docker ps

+ 检查容器内进程 +

  语法格式： `docker top <容器ID或名称>`

  > 示例：<br>
  > docker top my-nginx

+ 查看容器挂载的卷详情 +

  语法格式： `docker inspect <容器ID或名称>`

  > 示例：<br>
  > docker inspect my-nginx

+ 查看容器使用的网络 +

  语法格式： `docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' <容器ID或名称>`

  > 示例：<br>
  > docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' my-nginx

+ 查看容器健康状态 +

  语法格式： `docker inspect -f '{{.State.Health.Status}}' <容器ID或名称>`

  > 示例：<br>
  > docker inspect -f '{{.State.Health.Status}}' my-nginx

+ 查看容器输出日志 +

  语法格式： `docker logs <容器ID或名称>`<br>
  （可选参数：`-f` 实时查看日志，`--tail <行数>` 查看最后几行日志, `--since <时间>` 查看指定时间后的日志）

  > 示例：<br>
  > docker logs my-nginx

+ 进入容器内部执行命令（常用） +

  语法格式： `docker exec -it <容器ID或名称> <命令>`

  > 示例：<br>
  > docker exec -it my-nginx /bin/bash

+ 重命名容器 +

  语法格式： `docker rename <旧容器ID或名称> <新容器名称>`

  > 示例：<br>
  > docker rename my-nginx my-nginx-2

#### **数据卷与挂载**

+ 创建一个数据卷 +

  语法格式： `docker volume create <数据卷名称>`

  > 示例：<br>
  > docker volume create my-vol

+ 查看所有数据卷 +

  语法格式： `docker volume ls`

  > 说明：<br>
  > 数据卷是 Docker 用于存储容器数据的特殊目录，它独立于容器的生命周期，容器可以挂载数据卷到指定的目录，实现数据的持久化存储。

+ 删除数据卷 +

  语法格式： `docker volume rm <数据卷名称>`

  > 示例：<br>
  > docker volume rm my-vol

+ 删除所有未使用的卷 +

  语法格式： `docker volume prune`

  > 说明：<br>
  > *未使用的卷是指那些没有被任何容器挂载的卷。*<br>
  > *删除未使用的卷可以释放磁盘空间，避免卷占用过多的空间。*

+ 💡 技巧 +

  1. Windows 用户路径写法：C:\data → /c/data
  2. 将项目放在 WSL 文件系统中（如 ~/project）避免性能问题

#### **网络管理**

+ 查看所有网络 +

  语法格式： `docker network ls`

  > 说明：<br>
  > 网络是 Docker 用于容器之间通信的机制，它可以是桥接网络、主机网络、Overlay 网络等。

+ 创建自定义网络 +

  语法格式： `docker network create <网络名称>`

  > 示例：<br>
  > docker network create my-network

+ 将容器加入网络 +

  语法格式： `docker network connect <网络名称> <容器ID或名称>`

  > 示例：<br>
  > docker network connect my-network my-nginx

+ 将容器移出网络 +

  语法格式： `docker network disconnect <网络名称> <容器ID或名称>`

  > 示例：<br>
  > docker network disconnect my-network my-nginx

+ 删除网络 +

  语法格式： `docker network rm <网络名称>`

  > 示例：<br>
  > docker network rm my-network

#### **Docker Compose**

+ Docker Compose 介绍 +

  > **Docker Compose 是 Docker 官方提供的一个工具，用于定义和运行多个容器的应用。**<br>
  > **它使用 YAML 文件来配置应用的服务、网络和数据卷，简化了容器化应用的部署和管理。**<br>

  **示例：docker-compose.yml 文件**
  ```
  version: '3.8'
  services:
    web:
      image: nginx:latest
      ports:
        - "80:80"
      volumes:
        - ./html:/usr/share/nginx/html
    db:
      image: redis:alpine
      volumes:
        - dbdata:/data
  volumes:
  dbdata:
  ```

+ 启动所有服务 +

  语法格式： `docker-compose up`<br>
  （`-d` 表示在后台运行容器，不阻塞当前终端会话，常用于启动服务类容器（如数据库、消息队列等））

+ 停止并删除所有服务 +

  语法格式： `docker-compose down`

  > 说明：<br>
  > *停止并删除所有服务会停止所有正在运行的容器，并删除所有数据卷和镜像。*

+ 查看服务状态 +

  语法格式： `docker-compose ps`

  > 说明：<br>
  > *查看服务状态会显示所有服务的状态，包括容器 ID、名称、状态、端口映射等。*

+ 查看所有服务日志 +

  语法格式： `docker-compose logs`

  > 说明：<br>
  > *查看所有服务日志会显示所有服务的日志输出，包括容器的标准输出和标准错误输出。*

+ 重新构建服务镜像 +

  语法格式： `docker-compose build`

  > 说明：<br>
  > *重新构建服务镜像会根据 `docker-compose.yml` 文件中的配置，重新构建所有服务的镜像。*

#### **清理与维护**

+ 查看 Docker 磁盘使用情况 +

  语法格式： `docker system df`

  > 说明：<br>
  > *查看 Docker 磁盘使用情况会显示 Docker 占用的磁盘空间，包括镜像、容器、数据卷等。*

+ 清理所有未使用的资源（容器、网络、镜像、构建缓存） +

  语法格式： `docker system prune`

+ ⚠️ 清理所有未使用的镜像（包括未被引用的）⚠️ +

  语法格式： `docker system prune -a`

+ 清理构建缓存 +

  语法格式： `docker builder prune`

<!-- tabs:end -->

#### **创建并启动时可选**

<!-- tabs:start -->
#### ** `-d` **
  表示在后台运行容器，不阻塞当前终端会话，常用于启动服务类容器（如数据库、消息队列等）

#### ** `-p` **
  表示映射端口，格式为 `<主机端口>:<容器端口>`，用于将容器的端口映射到主机的端口，实现外部访问容器的服务

#### ** `--name` **
  表示指定容器的名称，用于方便管理和识别容器

#### ** `-v` 或 `--env` **
  表示挂载卷，格式为 `<主机目录>:<容器目录>`，用于将主机的目录挂载到容器的目录，实现数据持久化

#### ** `--rm` **
   表示在容器退出时自动删除容器，常用于临时容器（如测试容器、构建容器等）

#### ** `--it` **
   表示在容器中以交互模式运行，同时分配一个伪终端，常用于调试容器中的应用程序
   
#### ** `--network` **
  表示指定网络，用于将容器连接到指定的网络，实现容器之间的通信（如数据库密码、服务端口等）

#### ** `--env` **
  表示指定环境变量，格式为 `<键>=<值>`，用于在容器中设置环境变量（如数据库密码、服务端口等）

#### ** `--restart` **
  表示指定重启策略，用于在容器退出时自动重启容器，可选值为 `no`（不重启）、`always`（总是重启）、`on-failure`（仅在退出码非 0 时重启），常用于服务稳定性保障

#### ** `--link` **
  表示链接其他容器，格式为 `<容器名或ID>:<别名>`，用于在容器之间建立链接关系

#### ** `--env-file` **
  表示指定环境变量文件，用于从文件中加载环境变量，格式为 `<文件路径>`，常用于将敏感信息（如数据库密码、服务端口等）从文件中加载到容器中

#### ** `--user` **
  表示指定用户，格式为 `<用户名或 UID>`，用于在容器中以指定用户身份运行进程，常用于权限控制

#### ** `--group-add` **
   表示添加用户组，格式为 `<用户组名或 GID>`，用于在容器中添加指定的用户组，常用于权限控制

#### ** `--cap-add` **
   表示添加能力，格式为 `<能力名>`，用于在容器中添加指定的能力，常用于权限控制

#### ** `--cap-drop` **
   表示删除能力，格式为 `<能力名>`，用于在容器中删除指定的能力，常用于权限控制

#### ** `--security-opt` **
   表示指定安全选项，格式为 `<选项名>=<选项值>`，用于在容器中指定安全选项，常用于权限控制

#### ** `--sysctl` **
   表示指定系统参数，格式为 `<参数名>=<参数值>`，用于在容器中指定系统参数，常用于权限控制

#### ** `--ulimit` **
   表示指定资源限制，格式为 `<资源名>=<资源值>`，用于在容器中指定资源限制，常用于权限控制

<!-- tabs:end -->

## **实用技巧**

<!-- tabs:start -->
#### **查看容器 IP**
  `docker inspect <容器ID> | grep "IPAddress"`<br>
  `docker ps --format "ID: {{.ID}}, 名称: {{.Names}}, 状态: {{.Status}}, 端口: {{.Ports}}"`
#### ** 复制文件到容器**
  `docker cp /host/file.txt container_id:/container/path/`
#### **查看容器资源占用**
  `docker stats`
#### **构建时跳过缓存**
  `docker build --no-cache -t myapp:v1 .`
#### **进入运行中容器的终端**
  `docker exec -it <容器名/ID> bash  # 适用于有 bash 的容器`<br>
  `docker exec -it <容器名/ID> sh   # 适用于轻量容器（如 Alpine）`
#### **启动容器时自动创建目录挂载**
  `docker run -v /宿主机/newdir:/container/path --mount type=bind,source=/宿主机/newdir,target=/container/path,create=true <镜像名>`
#### **临时运行容器并执行单条命令（不进入终端）**
  `docker run --rm <镜像名> <命令>`
<!-- tabs:end -->

#### 来源

1. 感谢 Docker 官方文档 [🔗](https://docs.docker.com/) 
2. 感谢大佬的文章 [🔗](https://blog.csdn.net/y_wu794/article/details/150124009)
3. 使用 AI 进行补充

---


<!-- 统一容器样式，增加上下间距避免内容拥挤 -->

<div style="display:flex; gap:12px; flex-wrap:wrap; align-items:center; justify-content:center; margin:20px auto; padding:0 15px;">
  <!-- 优化跳动动画：增加缓动效果，让跳动更自然 -->
  <a href="https://www.ifdian.net/a/leoowa" target="_blank" rel="noopener noreferrer" 
     style="text-decoration:none; display:inline-block; animation: bounce 1.2s infinite ease-in-out; transition: transform 0.2s;">
    <img src="https://raw.github.com/Aleeyoo/note-gen-image-sync/main/b608f211-4aec-4994-9d43-8f80c150c21d.gif"  alt="爱发电"
         style="width:32px; height:32px; border:0; border-radius:4px; transition: opacity 0.3s;">
  </a>

<!-- 其他图标添加hover效果，提升交互感 -->

<a href="https://github.com/Aleeyoo" target="_blank" rel="noopener noreferrer" style="text-decoration:none; transition: transform 0.2s;">
    <img src="https://img.shields.io/badge/Aleeyoo-3498db?style=for-the-badge&logo=blogger&logoColor=white"  alt="GitHub"
         style="height:32px; width:auto; border:0; border-radius:4px; transition: opacity 0.3s;">
  </a>
  <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/" target="_blank" rel="noopener noreferrer" style="text-decoration:none; transition: transform 0.2s;">
    <img src="https://img.shields.io/badge/CC%20BY--NC--SA%204.0-9b59b6?style=for-the-badge&logo=creative-commons&logoColor=white"  alt="BY--NC--SA"
         style="height:32px; width:auto; border:0; border-radius:4px; transition: opacity 0.3s;">
  </a>
</div>

<style>
  /* 优化跳动动画：调整幅度和节奏，避免过于生硬 */
  @keyframes bounce {
    0%, 100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-8px); /* 减小跳动幅度，更显精致 */
    }
  }
  
  /* 统一hover效果：所有图标hover时轻微放大+提升透明度 */
  a:hover {
    transform: scale(1.05);
  }
  a:hover img {
    opacity: 0.9;
  }
