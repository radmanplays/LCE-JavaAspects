FROM debian:bookworm-slim

ARG DEBIAN_FRONTEND=noninteractive
# Build the server with CMake first (see COMPILE.md). The build context is
# the repo root, and MC_RUNTIME_DIR should point at a Release output that
# contains Minecraft.Server.exe, iggy_w64.dll, Common/, and Windows64/. For
# the FourKit flavour the same directory will also contain runtime/ and
# plugins/; the wildcard COPY below picks them up automatically.
ARG MC_RUNTIME_DIR=build/windows64/Minecraft.Server/Release

RUN dpkg --add-architecture i386 \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
    ca-certificates \
    wine \
    wine64 \
    wine32:i386 \
    xvfb \
    tini \
    && rm -rf /var/lib/apt/lists/*

ENV WINEARCH=win64
ENV WINEPREFIX=/var/opt/wineprefix64

WORKDIR /srv/mc

COPY ${MC_RUNTIME_DIR}/ /srv/mc/
COPY docker/dedicated-server/entrypoint.sh /usr/local/bin/entrypoint.sh

RUN chmod 0755 /usr/local/bin/entrypoint.sh \
    && mkdir -p /var/opt/wineprefix64 /srv/mc \
    && test -f /srv/mc/Minecraft.Server.exe

ENTRYPOINT ["/usr/bin/tini", "--", "/usr/local/bin/entrypoint.sh"]
