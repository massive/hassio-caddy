ARG BUILD_FROM=hassioaddons/base:5.0.1
FROM ${BUILD_FROM}

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

ENV LANG C.UTF-8

USER root

ARG BUILD_ARCH

RUN apk add --no-cache \
        caddy=1.0.0-r0 jq 

# Copy root file system
COPY rootfs /

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

ENV CADDYPATH /ssl

COPY run.sh /

CMD [ "/run.sh" ]

# Labels
LABEL \
    io.hass.name="Caddy" \
    io.hass.description="HTTP server to act as SSL Proxy" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Matias Käkelä" \
    org.label-schema.description="HTTP server to act as SSL Proxy" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="Caddy" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.usage="https://github.com/massive/hassio-caddy/blob/master/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/massive/hassio-caddy.git" \
    org.label-schema.vendor="Community Hass.io Addons"