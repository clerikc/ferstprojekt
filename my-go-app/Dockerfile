# Этап сборки с подробным выводом
FROM golang:1.22-alpine AS builder

WORKDIR /app

# Копируем исходный код
COPY . .

# Собираем приложение с подробным выводом
RUN cd my-go-app & go build main.go

# Этап запуска
FROM alpine:latest
COPY --from=builder /main /hello-world
EXPOSE 9090
CMD ["/hello-world"]