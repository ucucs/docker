# base image
FROM ucucs/alpine-base

# running required command

ARG NGINX_VERSION=1.16.0

# execute command 
RUN build_pkgs="gcc libc-dev make linux-headers openssl-dev pcre-dev zlib-dev tzdata" \
    && runtime_pkgs="curl ca-certificates openssl pcre zlib" \
	&& apk add --no-cache ${build_pkgs} ${runtime_pkgs} \
	&& cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
	&& echo "Asia/Shanghai" > /etc/timezone \
    && addgroup -S nginx \
	&& adduser -D -S -h /var/cache/nginx -s /sbin/nologin -G nginx nginx \
	&& curl -fSL -o - http://nginx.org/download/nginx-$NGINX_VERSION.tar.gz | tar xzf -  \
	&& cd nginx-$NGINX_VERSION \
	&& ./configure --prefix=/etc/nginx \
		--sbin-path=/usr/sbin/nginx \
		--modules-path=/usr/lib/nginx/modules \
		--conf-path=/etc/nginx/nginx.conf \
		--error-log-path=/var/log/nginx/error.log \
		--http-log-path=/var/log/nginx/access.log \
		--pid-path=/var/run/nginx.pid \
		--lock-path=/var/run/nginx.lock \
		--http-client-body-temp-path=/var/cache/nginx/client_temp \
		--http-proxy-temp-path=/var/cache/nginx/proxy_temp \
		--http-fastcgi-temp-path=/var/cache/nginx/fastcgi_temp \
		--http-uwsgi-temp-path=/var/cache/nginx/uwsgi_temp \
		--http-scgi-temp-path=/var/cache/nginx/scgi_temp \
		--user=nginx \
		--group=nginx \
		--with-http_ssl_module \
		--with-http_realip_module \
		--with-http_gunzip_module \
		--with-http_gzip_static_module \
		--with-threads \
		--with-stream \
		--with-stream_ssl_module \
		--with-stream_ssl_preread_module \
		--with-stream_realip_module \
		--with-file-aio \
		--with-http_v2_module \
		--with-http_stub_status_module \
		--without-http_memcached_module \
        --without-mail_pop3_module \
        --without-mail_imap_module \
        --without-mail_smtp_module \
        --without-http_geo_module \
		--with-ipv6 \
		--with-pcre-jit \
        --with-cc-opt='-g -O2 -fstack-protector-strong -Wformat -Werror=format-security' \
        --with-ld-opt='-Wl,-z,relro -Wl,--as-needed' \
	&& make -j$(getconf _NPROCESSORS_ONLN) \
	&& make install \
	&& mkdir /etc/nginx/conf.d \
	&& cd .. && rm -rf nginx-$NGINX_VERSION \
	&& apk del ${build_pkgs} \
	&& rm -rf /tmp/* /var/tmp/* /var/cache/apk/*

COPY nginx.conf /etc/nginx/nginx.conf
COPY nginx.vh.default.conf /etc/nginx/conf.d/default.conf

# Expose
EXPOSE 80
STOPSIGNAL SIGTERM
ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]