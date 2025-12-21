# Parameterized Denali Base Dockerfile
#
# Build example:
#   docker build --build-arg BASE_IMAGE_TAG=3.12-bookworm -t ringcentral/denali-base:3.12-bookworm .

ARG BASE_IMAGE_TAG=3.11-bookworm

FROM public.ecr.aws/docker/library/python:${BASE_IMAGE_TAG}

LABEL maintainer="john.lin@ringcentral.com"

RUN apt-get update \
    # Install dependencies
    && apt-get install -y --no-install-recommends \
        # basic environment
        curl nodejs libgmp-dev libmpfr-dev libmpc-dev \
        # For Security
        expat libldap-2.5-0 perl libsqlite3-0 zlib1g \
        # install a chinese font to support the use of tools like matplotlib
        fonts-noto-cjk \
        # install libmagic to support the use of python-magic guess MIMETYPE
        libmagic1 \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*

# Verify installation
RUN echo "=== Version Summary ===" \
    && python --version \
    && pip --version \
    && node --version \
    && curl --version | head -1
