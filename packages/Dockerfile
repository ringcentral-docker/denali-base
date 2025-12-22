# Parameterized Denali Packages Dockerfile
#
# Build example:
#   docker build \
#     --build-arg BASE_IMAGE_TAG=3.14-trixie \
#     --build-arg POETRY_VERSION=2.0.1 \
#     -t ringcentral/denali-packages:3.14-trixie .

ARG BASE_IMAGE_TAG=3.14-trixie

FROM public.ecr.aws/docker/library/python:${BASE_IMAGE_TAG}

LABEL maintainer="john.lin@ringcentral.com"

ARG POETRY_VERSION=2.0.1

WORKDIR /app/api

# Install Poetry
ENV POETRY_VERSION=${POETRY_VERSION}
RUN pip install --no-cache-dir poetry==${POETRY_VERSION}

# Configure Poetry
ENV POETRY_CACHE_DIR=/tmp/poetry_cache \
    POETRY_NO_INTERACTION=1 \
    POETRY_VIRTUALENVS_IN_PROJECT=true \
    POETRY_VIRTUALENVS_CREATE=true \
    POETRY_REQUESTS_TIMEOUT=15

# Install build dependencies
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        gcc g++ libc-dev libffi-dev libgmp-dev libmpfr-dev libmpc-dev \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*

# Verify installation
RUN echo "=== Version Summary ===" \
    && python --version \
    && pip --version \
    && poetry --version
