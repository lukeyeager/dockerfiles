FROM golang:1.15-buster AS build
RUN go get github.com/lukeyeager/lustre_exporter

FROM debian:buster-slim
COPY --from=build /go/bin/lustre_exporter /usr/local/bin/
