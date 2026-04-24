FROM jenkins/jenkins:lts-jdk17

USER root

RUN curl -fsSL https://download.docker.com/linux/static/stable/aarch64/docker-27.3.1.tgz \
    | tar xz --strip-components=1 -C /usr/local/bin docker/docker \
    && chmod +x /usr/local/bin/docker

USER jenkins