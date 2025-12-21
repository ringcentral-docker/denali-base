# Denali Docker Images

Multi-platform Python Docker images for Denali projects.

## Supported Platforms

- linux/amd64
- linux/arm64

## Base Images (denali-base)

| Python | OS | Docker Hub | GitHub Package |
|--------|-------|------------|----------------|
| 3.13 | bookworm | `ringcentral/denali-base:3.13-bookworm` | `ghcr.io/ringcentral-docker/denali-base:3.13-bookworm` |
| 3.13 | trixie | `ringcentral/denali-base:3.13-trixie` | `ghcr.io/ringcentral-docker/denali-base:3.13-trixie` |
| 3.14 | bookworm | `ringcentral/denali-base:3.14-bookworm` | `ghcr.io/ringcentral-docker/denali-base:3.14-bookworm` |
| 3.14 | trixie | `ringcentral/denali-base:3.14-trixie` | `ghcr.io/ringcentral-docker/denali-base:3.14-trixie` |

## Packages Images (denali-packages)

| Python | OS | Poetry | Docker Hub | GitHub Package |
|--------|-------|--------|------------|----------------|
| 3.13 | bookworm | 2.2.1 | `ringcentral/denali-packages:3.13-bookworm` | `ghcr.io/ringcentral-docker/denali-packages:3.13-bookworm` |
| 3.13 | trixie | 2.2.1 | `ringcentral/denali-packages:3.13-trixie` | `ghcr.io/ringcentral-docker/denali-packages:3.13-trixie` |
| 3.14 | bookworm | 2.2.1 | `ringcentral/denali-packages:3.14-bookworm` | `ghcr.io/ringcentral-docker/denali-packages:3.14-bookworm` |
| 3.14 | trixie | 2.2.1 | `ringcentral/denali-packages:3.14-trixie` | `ghcr.io/ringcentral-docker/denali-packages:3.14-trixie` |

## Usage

```bash
# Pull base image
docker pull ringcentral/denali-base:3.11-bookworm

# Pull packages image (with Poetry)
docker pull ringcentral/denali-packages:3.11-bookworm
```

## Build Locally

```bash
# Build base image
docker build --build-arg BASE_IMAGE_TAG=3.12-bookworm \
  -f base/Dockerfile -t denali-base:3.12-bookworm .

# Build packages image
docker build --build-arg BASE_IMAGE_TAG=3.12-bookworm \
  --build-arg POETRY_VERSION=2.0.1 \
  -f packages/Dockerfile -t denali-packages:3.12-bookworm .
```

## License

MIT License
