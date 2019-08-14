#
# Build stage
#
FROM golang:1.11-stretch as build-env

WORKDIR /go/src/github.com/myspotontheweb/$NAME/
COPY .  /go/src/github.com/myspotontheweb/$NAME/

RUN cd /go/src/github.com/myspotontheweb/$NAME/cmd/$NAME; go build -ldflags="-w -s" -o app .

#
# Package stage
#
FROM bitnami/minideb:stretch

EXPOSE $PORT
WORKDIR /apps

RUN install_packages ca-certificates tzdata

COPY --from=build-env /go/src/github.com/myspotontheweb/$NAME/cmd/$NAME/app /usr/local/bin/$NAME

CMD ["$NAME"]
