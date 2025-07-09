ARG BUILD_FROM
FROM ${BUILD_FROM}

# Install ONNX ASR
WORKDIR /usr/src
ARG WYOMING_ONNX_ASR_VERSION
ENV PIP_BREAK_SYSTEM_PACKAGES=1

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