FROM golang:1.19-alpine AS build
RUN apk add --no-cache git
RUN git clone --depth 1 --branch RELEASE.2022-10-29T06-21-33Z https://github.com/minio/minio /src
WORKDIR /src
RUN CGO_ENABLED=0 go build -trimpath -o /minio .

FROM alpine:3.19
COPY --from=build /minio /usr/bin/minio
EXPOSE 9000
ENTRYPOINT ["/usr/bin/minio"]
