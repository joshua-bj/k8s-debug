FROM ubuntu:22.04 AS build-stage

FROM ubuntu:22.04
# install the network utils (for debug)
RUN apt-get update && apt-get install -y net-tools iproute2 dnsutils && apt-get -y upgrade wget \
    && apt-get install -y curl && apt-get -y upgrade curl && apt-get -y upgrade libcurl3-gnutls libc6 \
    # install kubectl
    && apt-get install -y --no-install-recommends apt-utils  \
    && apt-get install -y apt-transport-https gnupg
# RUN curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - \
#    && echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | tee -a /etc/apt/sources.list.d/kubernetes.list \
#    && apt-get update && apt-get install -y kubectl
RUN apt-get install -y iperf
RUN apt-get install -y fio
RUN apt-get install -y postgresql-client
# install nginx for web server testing
RUN apt-get install -y nginx


CMD ["tail", "-f", "/dev/null"]