ARG BUILD_FROM
FROM $BUILD_FROM

RUN apk add --no-cache \
        ca-certificates \
        haproxy \
        libstdc++ \
        python3 \
    && apk add --no-cache --virtual .build-deps \
        build-base \
        libffi-dev \
        openssl-dev \
        py3-pip \
        python3-dev \
    && pip3 install --break-system-packages --no-cache-dir mitmproxy==12.3.0 \
    && apk del .build-deps \
    && rm -rf /root/.cache /tmp/*

ENTRYPOINT [ "/init" ]
CMD []
COPY root /
