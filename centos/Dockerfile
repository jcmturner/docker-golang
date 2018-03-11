FROM centos:latest

ENV GOROOT /usr/local/go
ENV GOPATH /go
ENV PATH ${GOPATH}/bin:${GOROOT}/bin:$PATH

RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"
WORKDIR $GOPATH

RUN yum install -y \
  wget \
  rpm-build \
  git \
  docker

ENV GOLANG_VERSION 1.10
ENV goRelSha256 "b5a64335f1490277b585832d1f6c7f8c6c11206cba5cd3f771dcb87b98ad1a33"

ENV GOOS linux
ENV GOARCH amd64

RUN wget -nv -O go.tgz https://dl.google.com/go/go${GOLANG_VERSION}.${GOOS}-${GOARCH}.tar.gz && \
  echo "${goRelSha256} *go.tgz" | sha256sum -c - && \
  tar -C /usr/local -xzf go.tgz; rm -f go.tgz
