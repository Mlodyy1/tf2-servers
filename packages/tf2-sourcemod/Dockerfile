ARG REGISTRY=ghcr.io
ARG TF2_BASE_TAG=latest
FROM ${REGISTRY}/mlodyy1/tf2-base:${TF2_BASE_TAG}
LABEL maintainer="jmlodojewski@gmail.com"

COPY checksum.md5 .

ARG METAMOD_TARBALL_FILE_NAME=mmsource-1.11.0-git1148-linux.tar.gz
ARG METAMOD_MAJOR_VERSION=1.11
ARG METAMOD_TARBALL_URL=https://mms.alliedmods.net/mmsdrop/${METAMOD_MAJOR_VERSION}/${METAMOD_TARBALL_FILE_NAME}

ARG SOURCEMOD_TARBALL_FILE_NAME=sourcemod-1.11.0-git6939-linux.tar.gz
ARG SOURCEMOD_MAJOR_VERSION=1.11
ARG SOURCEMOD_TARBALL_URL=https://sm.alliedmods.net/smdrop/${SOURCEMOD_MAJOR_VERSION}/${SOURCEMOD_TARBALL_FILE_NAME}

RUN wget -nv "${METAMOD_TARBALL_URL}" \
  && wget -nv "${SOURCEMOD_TARBALL_URL}" \
  && md5sum -c checksum.md5 \
  && tar xf "${METAMOD_TARBALL_FILE_NAME}" -C "${SERVER_DIR}/tf" \
  && tar xf "${SOURCEMOD_TARBALL_FILE_NAME}" -C "${SERVER_DIR}/tf" \
  && rm "${METAMOD_TARBALL_FILE_NAME}" \
  && rm "${SOURCEMOD_TARBALL_FILE_NAME}" \
  && rm checksum.md5
