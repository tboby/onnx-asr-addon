ARG BUILD_FROM=ghcr.io/hassio-addons/debian-base:7.8.3
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install ONNX ASR
WORKDIR /usr/src
ARG WYOMING_ONNX_ASR_VERSION="0.3.3"

RUN \
    apt-get update \
    && apt-get install -y --no-install-recommends git=1:2.39.5-0+deb12u2 \
    && apt-get autoclean \
    && apt-get purge \
    && rm -rf /var/lib/apt/lists/* \
    \
    && curl -LsSf https://astral.sh/uv/install.sh | sh \
    && source "$HOME/.local/bin/env" \
    \
    && uv venv \
    && uv pip install "git+https://github.com/tboby/wyoming-onnx-asr@v${WYOMING_ONNX_ASR_VERSION}[cpu]"

WORKDIR /
COPY rootfs /
