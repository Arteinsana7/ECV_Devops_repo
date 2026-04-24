FROM jenkins/jenkins:lts-jdk17

USER root

# Node.js
RUN curl -fsSL https://nodejs.org/dist/v20.11.0/node-v20.11.0-linux-arm64.tar.gz \
    | tar xz --strip-components=1 -C /usr/local

# Docker
RUN curl -fsSL https://download.docker.com/linux/static/stable/aarch64/docker-27.3.1.tgz \
    | tar xz --strip-components=1 -C /usr/local/bin docker/docker \
    && chmod +x /usr/local/bin/docker

USER jenkins