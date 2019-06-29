# base image
FROM alpine:3.10

RUN echo $ALPINEVER \
    && echo '# Aliyun Repo ' > /etc/apk/repositories \
    && echo https://mirrors.aliyun.com/alpine/v3.10/main/ >> /etc/apk/repositories \
    && echo https://mirrors.aliyun.com/alpine/v3.10/community/ >> /etc/apk/repositories