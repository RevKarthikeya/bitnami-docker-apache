FROM bitnami/minideb-extras:stretch-r332
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV BITNAMI_PKG_CHMOD="-R g+rwX" \
    BITNAMI_PKG_EXTRA_DIRS="/bitnami/apache/conf /opt/bitnami/apache/tmp /opt/bitnami/apache/conf" \
    HOME="/"

# Install required system packages and dependencies
RUN install_packages libc6 libexpat1 libffi6 libgmp10 libgnutls30 libhogweed4 libidn11 libldap-2.4-2 libnettle6 libnghttp2-14 libp11-kit0 libpcre3 libsasl2-2 libssl1.1 libtasn1-6 zlib1g
RUN bitnami-pkg unpack apache-2.4.39-0 --checksum e6108f6ea91c18d8f5481a1015b301d17ea59ba9d641e1a06b3860d66ffa46b0
RUN ln -sf /opt/bitnami/apache/htdocs /app
RUN ln -sf /dev/stdout /opt/bitnami/apache/logs/access_log
RUN ln -sf /dev/stderr /opt/bitnami/apache/logs/error_log

COPY rootfs /
ENV APACHE_HTTPS_PORT_NUMBER="8443" \
    APACHE_HTTP_PORT_NUMBER="8080" \
    BITNAMI_APP_NAME="apache" \
    BITNAMI_IMAGE_VERSION="2.4.39-debian-9-r1" \
    NAMI_PREFIX="/.nami" \
    PATH="/opt/bitnami/apache/bin:$PATH"

EXPOSE 8080 8443

WORKDIR /app
USER 1001
ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "/run.sh" ]
