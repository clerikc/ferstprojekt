# Этап сборки с подробным выводом
FROM golang:1.22-alpine AS builder

WORKDIR /app

# Копируем исходный код
COPY . .

# Собираем приложение с подробным выводом
RUN go build my-go-app/main.go
RUN pwd
# Этап запуска
FROM alpine:latest
COPY --from=builder main /hello-world
EXPOSE 9090
CMD ["/hello-world"]