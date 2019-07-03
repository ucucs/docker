# alpine-nginx
Docker Build DockerFile,Useable And Developer Enviroment.

这个是构建基本的nginx镜像，基于alpine进行构建，并进行安全加固。

构建包含基本的nginx模块以及配置，另外，还提供生产级别优化的nginx配置示例文件。

## 开启模块
`--with-ipv6 `
`--with-pcre-jit `
`--with-http_v2_module `
`--with-file-aio `
`--with-threads `
`--with-stream `

## 屏蔽模块
`--without-http_memcached_module `
`--without-mail_pop3_module `
`--without-mail_imap_module `
`--without-mail_smtp_module `
`--without-http_geo_module `

## 编译优化
`--with-cc-opt='-g -O2 -fstack-protector-strong -Wformat -Werror=format-security' `
`--with-ld-opt='-Wl,-z,relro -Wl,--as-needed' `

