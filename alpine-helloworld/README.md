# alpine-helloworld
Docker Build DockerFile,Useable And Developer Enviroment.

这是个入门docker比较好的镜像，因为小而简单，容易学习相关的指令和降低复杂度。
This is a good image for getting started with docker, because it's small and simple, it's easy to learn related instructions and reduce complexity.

运行这个镜像有两种办法，一种是原生的docker指令，另外一种是使用docker-compose。
There are two ways to run this image, one is the native docker directive and the other is docker-compose.

需要进入Dockerfile目录
Need to enter the Dockerfile directory

使用docker指令进行构建如下：
Use the docker directive to build as follows:

`docker build -t ucucs/alpine-helloworld .`
"ucucs/alpine-helloworld" 可以替换成你想要的镜像名称

完成后，使用执行命令
Once you are done, you can execute the run command.

`docker run yourimagename`
示例：docker run ucucs/alpine-helloworld

使用docker-compose进行构建如下：
Use docker-compose to build as follows:

`docker-compose build`

完成后，使用执行命令
Once you are done, you can execute the run command.

`docker-compose up`

