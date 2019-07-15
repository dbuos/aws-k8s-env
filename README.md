# aws-k8s-env
Dockerfile to build a developer env for k8s (eks) and aws tools

Example usage:

```
FROM dboss/aws-k8s-env

ADD fluxctl /usr/local/bin/fluxctl
RUN chmod +x /usr/local/bin/fluxctl

ADD helm /usr/local/bin/
RUN chmod +x /usr/local/bin/helm

ADD terraform_0.12.4_linux_amd64.zip ./
RUN unzip terraform_0.12.4_linux_amd64.zip && mv terraform /usr/local/bin/terraform && \
  rm terraform_0.12.4_linux_amd64.zip

ADD .terraformrc /root/.terraformrc
ADD credentials /root/.aws/credentials
ADD config /root/.aws/config
ENV HISTFILE=/workshop/env/zsh_history

WORKDIR /workshop
VOLUME /workshop

```
