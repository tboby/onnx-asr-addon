ARG BUILD_FROM=ghcr.io/hassio-addons/base-debian:bookworm
FROM ${BUILD_FROM}

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install ONNX ASR
WORKDIR /usr/src
ARG WYOMING_ONNX_ASR_VERSION

RUN \
    apt-get update \
    && apt-get install -y --no-install-recommends git \
    && apt-get autoclean \
    && apt-get purge \
    && rm -rf /var/lib/apt/lists/* \
    \
    && curl -LsSf https://astral.sh/uv/install.sh | sh \
    && source $HOME/.local/bin/env \
    \
    && uv venv \
    && uv pip install "git+https://github.com/tboby/wyoming-onnx-asr@v${WYOMING_ONNX_ASR_VERSION}[cpu]"

WORKDIR /
COPY rootfs /