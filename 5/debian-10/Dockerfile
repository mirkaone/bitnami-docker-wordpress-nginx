FROM docker.io/bitnami/minideb:buster
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV HOME="/" \
    OS_ARCH="amd64" \
    OS_FLAVOUR="debian-10" \
    OS_NAME="linux"

COPY prebuildfs /
# Install required system packages and dependencies
RUN install_packages vim acl ca-certificates curl gzip less libaudit1 libbsd0 libbz2-1.0 libc6 libcap-ng0 libcom-err2 libcurl4 libexpat1 libffi6 libfftw3-double3 libfontconfig1 libfreetype6 libgcc1 libgcrypt20 libgeoip1 libglib2.0-0 libgmp10 libgnutls30 libgomp1 libgpg-error0 libgssapi-krb5-2 libhogweed4 libicu63 libidn2-0 libjemalloc2 libjpeg62-turbo libk5crypto3 libkeyutils1 libkrb5-3 libkrb5support0 liblcms2-2 libldap-2.4-2 liblqr-1-0 libltdl7 liblzma5 libmagickcore-6.q16-6 libmagickwand-6.q16-6 libmcrypt4 libmemcached11 libmemcachedutil2 libncurses6 libnettle6 libnghttp2-14 libonig5 libp11-kit0 libpam0g libpcre3 libpng16-16 libpq5 libpsl5 libreadline7 librtmp1 libsasl2-2 libsodium23 libsqlite3-0 libssh2-1 libssl1.1 libstdc++6 libsybdb5 libtasn1-6 libtidy5deb1 libtinfo6 libunistring2 libuuid1 libwebp6 libx11-6 libxau6 libxcb1 libxdmcp6 libxext6 libxml2 libxslt1.1 libzip4 procps tar zlib1g
RUN . /opt/bitnami/scripts/libcomponent.sh && component_unpack "php" "7.4.22-2" --checksum 0e54327672e6a12d6b5af92fcefaeacc7ec149d9a9433d6ab08796ffdcf32a43
RUN . /opt/bitnami/scripts/libcomponent.sh && component_unpack "wp-cli" "2.5.0-0" --checksum b2be17e2065fc8d9d1a175e1dbc689e8f6a5543bb3b6a6f5470bc987b7c396ce
RUN . /opt/bitnami/scripts/libcomponent.sh && component_unpack "nginx" "1.21.1-0" --checksum 34775d31ba2edb6bf4e84e049ac932017713a310e69905858cd1e0f3ad4f4947
RUN . /opt/bitnami/scripts/libcomponent.sh && component_unpack "mysql-client" "10.3.31-0" --checksum 92b99c64a3ffe10fd94ef9ecd94d2dd65a172404c726093eb50b3b293523559d
RUN . /opt/bitnami/scripts/libcomponent.sh && component_unpack "wordpress" "5.8.0-5" --checksum 1f6f177bdba5f7bd309999e830177553afb886f1b8346681cf78ff4ac71a7e9e
RUN . /opt/bitnami/scripts/libcomponent.sh && component_unpack "render-template" "1.0.0-3" --checksum 8179ad1371c9a7d897fe3b1bf53bbe763f94edafef19acad2498dd48b3674efe
RUN . /opt/bitnami/scripts/libcomponent.sh && component_unpack "gosu" "1.14.0-0" --checksum 3e6fc37ca073b10a73a804d39c2f0c028947a1a596382a4f8ebe43dfbaa3a25e
RUN chmod g+rwX /opt/bitnami

COPY rootfs /
RUN /opt/bitnami/scripts/mysql-client/postunpack.sh
RUN /opt/bitnami/scripts/nginx/postunpack.sh
RUN /opt/bitnami/scripts/php/postunpack.sh
RUN /opt/bitnami/scripts/nginx-php-fpm/postunpack.sh
RUN /opt/bitnami/scripts/wordpress/postunpack.sh
ENV ALLOW_EMPTY_PASSWORD="no" \
    BITNAMI_APP_NAME="wordpress-nginx" \
    BITNAMI_IMAGE_VERSION="5.8.0-debian-10-r19" \
    MYSQL_CLIENT_FLAVOR="mysql" \
    MYSQL_CLIENT_DATABASE_HOST="sqlfmg.mysql.database.azure.com" \
    MYSQL_CLIENT_DATABASE_PORT_NUMBER="3306" \
    MYSQL_CLIENT_DATABASE_ROOT_USER="mirkaone@sqlfmg" \
    MYSQL_CLIENT_DATABASE_ROOT_PASSWORD="Pinguino1" \
    MYSQL_CLIENT_CREATE_DATABASE_NAME="bitnami_wordpress" \
    MYSQL_CLIENT_CREATE_DATABASE_PASSWORD="Pinguino1" \
    MYSQL_CLIENT_CREATE_DATABASE_PRIVILEGES="ALL" \
    MYSQL_CLIENT_CREATE_DATABASE_USER="bn_wordpress" \
    MYSQL_CLIENT_ENABLE_SSL="no" \
    MYSQL_CLIENT_SSL_CA_FILE="" \
    NGINX_ENABLE_CUSTOM_PORTS="no" \
    NGINX_HTTPS_PORT_NUMBER="" \
    NGINX_HTTP_PORT_NUMBER="" \
    WORDPRESS_DATABASE_HOST="sqlfmg.mysql.database.azure.com" \
    WORDPRESS_DATABASE_USER="bn_wordpress" \
    WORDPRESS_DATABASE_PASSWORD="Pinguino1" \
    WORDPRESS_DATABASE_NAME="bitnami_wordpress" \
    PATH="/opt/bitnami/php/bin:/opt/bitnami/php/sbin:/opt/bitnami/wp-cli/bin:/opt/bitnami/nginx/sbin:/opt/bitnami/mysql/bin:/opt/bitnami/common/bin:$PATH"

EXPOSE 8080 8443

USER 1001
ENTRYPOINT [ "/opt/bitnami/scripts/wordpress/entrypoint.sh" ]
CMD [ "/opt/bitnami/scripts/nginx-php-fpm/run.sh" ]
