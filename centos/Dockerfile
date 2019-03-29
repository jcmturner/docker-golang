FROM centos:latest

ENV GOBASE /usr/local
ENV GOROOT ${GOBASE}/go
ENV GOPATH /go
ENV PATH ${GOPATH}/bin:${GOROOT}/bin:$PATH
ENV GOOS linux
ENV GOARCH amd64

RUN for d in src pkg bin; do mkdir -p ${GOPATH}/$d; done; chmod -R 777 "$GOPATH"
WORKDIR $GOPATH
ADD getgo $GOPATH/bin/getgo
RUN GOTAR=$(getgo -path=/tmp | grep "Downloading to:" | sed 's/Downloading to: //') && \
  tar -C ${GOBASE} -xzf ${GOTAR} && \
  rm -f ${GOTAR}

RUN yum install -y \
  wget \
  rpm-build \
  git \
  gcc \
  && yum upgrade -y && yum clean all
