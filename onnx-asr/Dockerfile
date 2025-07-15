ARG BUILD_FROM=ghcr.io/hassio-addons/debian-base:7.8.3
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install ONNX ASR
WORKDIR /usr/src
ARG WYOMING_ONNX_ASR_VERSION

RUN \
    apk add --no-cache git=2.49.1-r0 \
    \
    && curl -LsSf https://astral.sh/uv/install.sh | sh \
    && source "$HOME/.local/bin/env" \
    \
    && uv venv \
    && uv pip install "git+https://github.com/tboby/wyoming-onnx-asr@v${WYOMING_ONNX_ASR_VERSION}[cpu]"

WORKDIR /
COPY rootfs /
