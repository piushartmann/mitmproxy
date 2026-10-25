ARG BUILD_FROM
FROM $BUILD_FROM

RUN apk add --no-cache \
        ca-certificates \
        haproxy \
        libstdc++ \
        python3 \
    && apk add --no-cache --virtual .build-deps \
        build-base \
        cargo \
        libffi-dev \
        openssl-dev \
        py3-pip \
        python3-dev \
        llvm-dev \
    && ln -sf /usr/lib/libLLVM.so.22.1 /usr/lib/libLLVM.so \
    && cargo install --locked bpf-linker \
    && PATH="/root/.cargo/bin:${PATH}" pip3 install --break-system-packages --no-cache-dir mitmproxy==12.3.0 \
    && apk del .build-deps \
    && rm -rf /root/.cache /tmp/*

ENTRYPOINT [ "/init" ]
CMD []
COPY root /
