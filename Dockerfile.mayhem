FROM --platform=linux/amd64 ubuntu:20.04 as builder

RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y qtcreator qt5-default build-essential

COPY . /repo
WORKDIR /repo
RUN qmake
RUN make -j8

FROM ubuntu:20.04 as package
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y qt5-default
COPY --from=builder /repo/cpi /
