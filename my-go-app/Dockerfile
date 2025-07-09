# Этап сборки с подробным выводом
FROM golang:1.22-alpine AS builder

WORKDIR /app

# Копируем файлы зависимостей
COPY my-go-app/go.mod my-go-app/go.sum ./

# Скачиваем зависимости с выводом логов
RUN go mod download -x 2>&1 | tee /tmp/go-mod.log

# Копируем исходный код
COPY . .

# Собираем приложение с подробным выводом
RUN CGO_ENABLED=0 GOOS=linux go build -v -x -o /hello-world 2>&1 | tee /tmp/go-build.log || \
    (cat /tmp/go-build.log && exit 1)

# Этап запуска
FROM alpine:latest
COPY --from=builder /hello-world /hello-world
EXPOSE 9090
CMD ["/hello-world"]