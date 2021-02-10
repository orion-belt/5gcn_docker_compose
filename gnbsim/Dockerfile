FROM ubuntu:bionic

RUN apt-get update
RUN apt-get install git wget make build-essential -y

# Installing go 1.13 for pfcp session injector
RUN wget https://dl.google.com/go/go1.13.3.linux-amd64.tar.gz && tar -xvf go1.13.3.linux-amd64.tar.gz && mv go /usr/local
ENV GOROOT=/usr/local/go
RUN mkdir goproject
ENV GOPATH=/goproject
ENV PATH=$GOPATH/bin:$GOROOT/bin:$PATH

RUN git clone https://github.com/hhorai/gnbsim.git
RUN cd gnbsim && make test && make

COPY example.json /gnbsim/examples/
RUN rm *.gz

ENTRYPOINT /bin/bash
