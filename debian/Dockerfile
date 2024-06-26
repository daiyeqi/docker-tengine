FROM debian:bookworm-slim
LABEL maintainer="Dai Yeqi <daiyeqi@nichijou.com>"

ENV TONGSUO_VERSION 8.4.0
ENV TENGINE_VERSION 3.1.0

RUN set -x \
    && groupadd --system --gid 101 nginx \
    && useradd --system --gid nginx --no-create-home --home /nonexistent --comment "nginx user" --shell /bin/false --uid 101 nginx \
    && dpkgArch="$(dpkg --print-architecture)" \
    && case "$dpkgArch" in \
         amd64) \
           tongsuo_opt="-march=native no-rc5 no-zlib no-ssl3 no-ssl3-method enable-cms no-capieng no-rdrand enable-ec_sm2p_64_gcc_128 enable-cert-compression enable-ntls --api=1.1.1"; \
           ;; \
         arm64) \
           tongsuo_opt="no-rc5 no-zlib no-ssl3 no-ssl3-method enable-cms no-capieng no-rdrand enable-ec_sm2p_64_gcc_128 enable-cert-compression enable-ntls --api=1.1.1"; \
           ;; \
         armhf) \
           tongsuo_opt="linux-armv4 no-rc5 no-zlib no-ssl3 no-ssl3-method enable-cms no-capieng no-rdrand enable-cert-compression enable-ntls --api=1.1.1"; \
           ;; \
       esac \
    && apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests -y \
        curl ca-certificates lsb-release g++ gcc make libpcre2-8-0 libpcre2-dev zlib1g zlib1g-dev perl \
    && export TEMP_HOME="$(mktemp -d)" && cd $TEMP_HOME \
    && curl -L -o $TEMP_HOME/tongsuo.tar.gz https://github.com/Tongsuo-Project/Tongsuo/archive/refs/tags/$TONGSUO_VERSION.tar.gz && tar -zxf tongsuo.tar.gz \
    && curl -L -o $TEMP_HOME/tengine.tar.gz https://github.com/alibaba/tengine/archive/refs/tags/$TENGINE_VERSION.tar.gz && tar -zxf tengine.tar.gz \
    && cd $TEMP_HOME/tengine-$TENGINE_VERSION/ \
    && mkdir /var/lib/nginx && chown nginx:nginx /var/lib/nginx \
    && ./configure \
        --prefix=/etc/nginx \
        --sbin-path=/usr/sbin/nginx \
        --modules-path=/usr/lib/nginx/modules \
        --conf-path=/etc/nginx/nginx.conf \
        --error-log-path=/var/log/nginx/error.log \
        --http-log-path=/var/log/nginx/access.log \
        --http-client-body-temp-path=/var/lib/nginx/body \
        --http-fastcgi-temp-path=/var/lib/nginx/fastcgi \
        --http-proxy-temp-path=/var/lib/nginx/proxy \
        --http-scgi-temp-path=/var/lib/nginx/scgi \
        --http-uwsgi-temp-path=/var/lib/nginx/uwsgi \
        --user=nginx \
        --group=nginx \
        --pid-path=/var/run/nginx.pid \
        --lock-path=/var/run/nginx.lock \
        --with-compat \
        --with-pcre-jit \
        --with-http_ssl_module \
        --with-http_stub_status_module \
        --with-http_realip_module \
        --with-http_auth_request_module \
        --with-http_v2_module \
        --with-http_slice_module \
        --with-threads \
        --with-http_addition_module \
        --with-http_gunzip_module \
        --with-http_gzip_static_module \
        --with-http_mp4_module \
        --with-http_random_index_module \
        --with-http_secure_link_module \
        --with-http_sub_module \
        --with-stream_realip_module \
        --with-stream_ssl_module \
        --with-stream_sni \
        --with-stream_ssl_preread_module \
        --with-stream_realip_module \
        --with-stream=dynamic \
        --add-module=./modules/ngx_tongsuo_ntls \
        --with-openssl=$TEMP_HOME/Tongsuo-$TONGSUO_VERSION \
        --with-openssl-opt="$tongsuo_opt" \
    && make -j4 && make install \
    && rm -rf $TEMP_HOME \
    && apt-get remove --purge --auto-remove -y curl g++ gcc make lsb-release libpcre2-dev zlib1g-dev perl && apt-get autoclean \
    && rm -rf /var/lib/apt/lists/* \
    && echo "Container for $(uname -m) CPU architecture." > /opt/architecture \
    && ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf /dev/stderr /var/log/nginx/error.log

EXPOSE 80

STOPSIGNAL SIGQUIT

CMD ["nginx", "-g", "daemon off;"]
