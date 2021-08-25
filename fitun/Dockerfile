FROM bitnami/wordpress-nginx
## Change user to perform privileged actions
USER 0
## Install 'vim'
RUN install_packages vim
## Revert to the original non-root user
USER 1001

ENV NGINX_HTTPS_PORT_NUMBER=443 \
ALLOW_EMPTY_PASSWORD=yes \
WORDPRESS_DATABASE_HOST=mariadb \
WORDPRESS_DATABASE_PORT_NUMBER=3306 \
WORDPRESS_DATABASE_USER=bn_wordpress \
WORDPRESS_DATABASE_NAME=bitnami_wordpress  \
WORDPRESS_DATABASE_NAME=bitnami_wordpress 

EXPOSE 8080 443
