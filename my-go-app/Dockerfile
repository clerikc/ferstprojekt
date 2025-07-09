FROM golang:1.22-alpine AS builder

WORKDIR /app

COPY . .

RUN go mod init hello-world && \
    go mod tidy && \
    CGO_ENABLED=0 GOOS=linux go build -o /hello-world

FROM alpine:latest
COPY --from=builder /hello-world /hello-world
EXPOSE 9090
CMD ["/hello-world"]