ARG BUILD_FROM=ghcr.io/hassio-addons/base:17.2.1
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

# Set shell
SHELL ["/bin/ash", "-o", "pipefail", "-c"]

# Add env
ENV TERM="xterm-256color"

# Setup base
# hadolint ignore=DL3018
RUN apk add --no-cache \
    nano=8.2-r0 \
    sane=1.3.1-r0 \
    sane-saned=1.3.1-r0 \
    sane-utils=1.3.1-r0 \
    sane-backend-net=1.3.1-r0 \
    sane-backend-hpljm1005=1.3.1-r0 \ 
    sane-backend-pixma=1.3.1-r0

# Copy root filesystem
COPY rootfs /

RUN chmod a+x /run.sh

CMD ["/run.sh"]

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_DESCRIPTION
ARG BUILD_NAME
ARG BUILD_REF
ARG BUILD_REPOSITORY
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="${BUILD_NAME}" \
    io.hass.description="${BUILD_DESCRIPTION}" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Jochen Schalanda <jochen+home-assistant@schalanda.name>" \
    org.opencontainers.image.title="${BUILD_NAME}" \
    org.opencontainers.image.description="${BUILD_DESCRIPTION}" \
    org.opencontainers.image.authors="Jochen Schalanda <jochen+home-assistant@schalanda.name>" \
    org.opencontainers.image.licenses="MIT" \
    org.opencontainers.image.url="https://addons.community" \
    org.opencontainers.image.source="https://github.com/${BUILD_REPOSITORY}" \
    org.opencontainers.image.documentation="https://github.com/${BUILD_REPOSITORY}/blob/main/README.md" \
    org.opencontainers.image.created=${BUILD_DATE} \
    org.opencontainers.image.revision=${BUILD_REF} \
    org.opencontainers.image.version=${BUILD_VERSION}
