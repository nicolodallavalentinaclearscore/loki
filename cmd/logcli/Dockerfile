FROM golang:1.20.3 as build

COPY . /src/loki
WORKDIR /src/loki
RUN make clean && make BUILD_IN_CONTAINER=false logcli

FROM alpine:3.16.4

RUN apk add --no-cache ca-certificates

COPY --from=build /src/loki/cmd/logcli/logcli /usr/bin/logcli

ENTRYPOINT [ "/usr/bin/logcli" ]
