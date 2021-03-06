FROM docker.io/bitnami/minideb:buster
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV OS_ARCH="amd64" \
    OS_FLAVOUR="debian-10" \
    OS_NAME="linux"

COPY prebuildfs /
# Install required system packages and dependencies
RUN install_packages build-essential ca-certificates curl git gzip libbz2-1.0 libc6 libcom-err2 libcurl4 libexpat1 libffi6 libgcc1 libgcrypt20 libgmp10 libgnutls30 libgpg-error0 libgssapi-krb5-2 libhogweed4 libidn2-0 libk5crypto3 libkeyutils1 libkrb5-3 libkrb5support0 libldap-2.4-2 liblzma5 libncursesw6 libnettle6 libnghttp2-14 libp11-kit0 libpsl5 libreadline7 librtmp1 libsasl2-2 libsqlite3-0 libsqlite3-dev libssh2-1 libssl-dev libssl1.1 libstdc++6 libtasn1-6 libtinfo6 libunistring2 pkg-config procps sqlite3 tar unzip wget zlib1g
RUN wget -nc -P /tmp/bitnami/pkg/cache/ https://downloads.bitnami.com/files/stacksmith/python-3.8.11-0-linux-amd64-debian-10.tar.gz && \
    echo "28b91ef5db9ad93e704881400703e4085bd82f016be15e3cf8760df044da9490  /tmp/bitnami/pkg/cache/python-3.8.11-0-linux-amd64-debian-10.tar.gz" | sha256sum -c - && \
    tar -zxf /tmp/bitnami/pkg/cache/python-3.8.11-0-linux-amd64-debian-10.tar.gz -P --transform 's|^[^/]*/files|/opt/bitnami|' --wildcards '*/files' && \
    rm -rf /tmp/bitnami/pkg/cache/python-3.8.11-0-linux-amd64-debian-10.tar.gz
RUN wget -nc -P /tmp/bitnami/pkg/cache/ https://downloads.bitnami.com/files/stacksmith/node-14.17.3-2-linux-amd64-debian-10.tar.gz && \
    echo "c47c559cc4696938d59b58806bcd2c41a665646d89b7fe3c16a7674badc2cacd  /tmp/bitnami/pkg/cache/node-14.17.3-2-linux-amd64-debian-10.tar.gz" | sha256sum -c - && \
    tar -zxf /tmp/bitnami/pkg/cache/node-14.17.3-2-linux-amd64-debian-10.tar.gz -P --transform 's|^[^/]*/files|/opt/bitnami|' --wildcards '*/files' && \
    rm -rf /tmp/bitnami/pkg/cache/node-14.17.3-2-linux-amd64-debian-10.tar.gz
RUN wget -nc -P /tmp/bitnami/pkg/cache/ https://downloads.bitnami.com/files/stacksmith/java-11.0.11-0-linux-amd64-debian-10.tar.gz && \
    echo "8cf28afc1090b0fec1ad841012ead25b59d2d5f4212742c3d62e6007ef57850b  /tmp/bitnami/pkg/cache/java-11.0.11-0-linux-amd64-debian-10.tar.gz" | sha256sum -c - && \
    tar -zxf /tmp/bitnami/pkg/cache/java-11.0.11-0-linux-amd64-debian-10.tar.gz -P --transform 's|^[^/]*/files|/opt/bitnami|' --wildcards '*/files' && \
    rm -rf /tmp/bitnami/pkg/cache/java-11.0.11-0-linux-amd64-debian-10.tar.gz
RUN wget -nc -P /tmp/bitnami/pkg/cache/ https://downloads.bitnami.com/files/stacksmith/jruby-9.2.19-0-2-linux-amd64-debian-10.tar.gz && \
    echo "bd295449ca8764e2151bf23aad32254ed5dfe9d423f79cec00cb6635b9bd0111  /tmp/bitnami/pkg/cache/jruby-9.2.19-0-2-linux-amd64-debian-10.tar.gz" | sha256sum -c - && \
    tar -zxf /tmp/bitnami/pkg/cache/jruby-9.2.19-0-2-linux-amd64-debian-10.tar.gz -P --transform 's|^[^/]*/files|/opt/bitnami|' --wildcards '*/files' && \
    rm -rf /tmp/bitnami/pkg/cache/jruby-9.2.19-0-2-linux-amd64-debian-10.tar.gz
RUN sed -i 's/^PASS_MAX_DAYS.*/PASS_MAX_DAYS    90/' /etc/login.defs && \
    sed -i 's/^PASS_MIN_DAYS.*/PASS_MIN_DAYS    0/' /etc/login.defs && \
    sed -i 's/sha512/sha512 minlen=8/' /etc/pam.d/common-password

ENV BITNAMI_APP_NAME="jruby" \
    BITNAMI_IMAGE_VERSION="9.2.19-0-debian-10-r27" \
    PATH="/opt/bitnami/python/bin:/opt/bitnami/node/bin:/opt/bitnami/java/bin:/opt/bitnami/jruby/bin:$PATH"

EXPOSE 3000

WORKDIR /app
CMD [ "irb" ]
