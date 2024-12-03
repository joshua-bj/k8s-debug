FROM ubuntu:22.04 AS build-stage

FROM ubuntu:22.04
# install the network utils (for debug)
RUN apt-get update && apt-get install -y net-tools iputils-ping iproute2 dnsutils \
    && apt-get -y upgrade wget \
    && apt-get install -y curl && apt-get -y upgrade curl && apt-get -y upgrade libcurl3-gnutls libc6 \
    # install kubectl
    && apt-get install -y --no-install-recommends apt-utils  \
    && apt-get install -y apt-transport-https ca-certificates gnupg
RUN curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.31/deb/Release.key | \
    gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg \
    && chmod 644 /etc/apt/keyrings/kubernetes-apt-keyring.gpg \
    && echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.31/deb/ /' | \
    tee /etc/apt/sources.list.d/kubernetes.list \
    && chmod 644 /etc/apt/sources.list.d/kubernetes.list \
    && apt-get update \
    && apt-get install -y kubectl
RUN apt-get install -y iperf
RUN apt-get install -y fio
RUN apt-get install -y postgresql-client
RUN unset http_proxy && unset https_proxy && unset HTTP_PROXY && unset HTTPS_PROXY

CMD ["tail", "-f", "/dev/null"]