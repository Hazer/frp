FROM golang:alpine AS builder

ENV FRP_VERSION=0.61.0

RUN mkdir /workspace

WORKDIR /workspace

RUN apk add --no-cache make \
    && wget -c https://github.com/fatedier/frp/archive/refs/tags/v${FRP_VERSION}.tar.gz \
    && tar zxvf v${FRP_VERSION}.tar.gz \
    && cd frp-${FRP_VERSION} \
    && make \
    && cp -rfv bin conf /workspace/ 


FROM alpine:latest

# OCI annotations to image
LABEL org.opencontainers.image.authors="Hazer" \
    org.opencontainers.image.title="Frps Image Based On Alpine" \
    org.opencontainers.image.description="Docker Images for Frps on Alpine. (i386, amd64, arm32v6, arm32v7, arm64, ppc64le,riscv64, s390x)" \
    org.opencontainers.image.documentation="https://hub.docker.com/r/hazertothepast/frps" \
    org.opencontainers.image.base.name="hazertothepast/frps:alpine" \
    org.opencontainers.image.licenses="MIT" \
    org.opencontainers.image.source="https://github.com/hazertothepast/frp" \
    org.opencontainers.image.vendor="Hazer" \
    org.opencontainers.image.version="0.61.0" \
    org.opencontainers.image.url="https://github.com/hazertothepast/frp"

COPY --from=builder /workspace/bin/frps /usr/bin/
COPY --from=builder /workspace/conf/frps.toml /etc/frp/

ENTRYPOINT ["/usr/bin/frps"]

CMD ["-c", "/etc/frp/frps.toml"]
