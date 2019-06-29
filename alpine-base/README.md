# alpine-base
Docker Build DockerFile,Useable And Developer Enviroment.

使用基础镜像alpine,减少基础镜像包大小。
Use the base image alpine to reduce the size of the base image package.

因为默认的镜像下载安装包地址在国外，比较缓慢,之前一直因为这个而怀疑人生。
Because the default image download installation package address is abroad, it is relatively slow, and I have been suspected of life because of this.

变更点：
Change point

更换apk包Repo源为阿里云，提升包编译速度。
Replace the apo package Repo source for Alibaba Cloud to improve the package compilation speed.

当然，也可以切换为不同的源，只需要按照Dockerfile里面的方法。
Of course, you can also switch to a different source, just follow the method in the Dockerfile.

变更Repo源方法
Change Repo source method
`cat /etc/apk/repositories`
`echo https://mirrors.aliyun.com/alpine/v3.10/main/ >> /etc/apk/repositories`
`echo https://mirrors.aliyun.com/alpine/v3.10/community/ >> /etc/apk/repositories`

