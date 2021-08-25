FROM bitnami/wordpress-nginx
## Change user to perform privileged actions
USER 0
## Install 'vim'
RUN install_packages vim
## Revert to the original non-root user
USER 1001

ENV ALLOW_EMPTY_PASSWORD="no" \
    BITNAMI_APP_NAME="wordpress-nginx" \
    BITNAMI_IMAGE_VERSION="5.8.0-debian-10-r19" \
    MARIADB_HOST="sqlfmg.mysql.database.azure.com" \
    MARIADB_PORT_NUMBER="3306" \
    MARIADB_ROOT_PASSWORD="Pinguino1" \
    MARIADB_ROOT_USER="mirkaone@sqlfmg" \
    MYSQL_CLIENT_CREATE_DATABASE_NAME="wordpress" \
    MYSQL_CLIENT_CREATE_DATABASE_PASSWORD="Pinguino1" \
    MYSQL_CLIENT_CREATE_DATABASE_PRIVILEGES="ALL" \
    MYSQL_CLIENT_CREATE_DATABASE_USER="" \
    MYSQL_CLIENT_ENABLE_SSL="no" \
    MYSQL_CLIENT_SSL_CA_FILE="" \
    NGINX_ENABLE_CUSTOM_PORTS="no" \
    NGINX_HTTPS_PORT_NUMBER=443 \
    NGINX_HTTP_PORT_NUMBER="" \
    WORDPRESS_DATABASE_USER="mirkaone@sqlfmg" \
    WORDPRESS_DATABASE_PASSWORD="Pinguino1" \
    WORDPRESS_DATABASE_NAME="wordpress"

EXPOSE 443 8080
