# Используем официальный образ Go для сборки
FROM golang:1.22-alpine AS builder

# Устанавливаем рабочую директорию
WORKDIR /app

# Копируем файлы go.mod и go.sum (если есть)
COPY go.mod go.sum ./

# Скачиваем зависимости
RUN go mod download

# Копируем исходный код
COPY . .

# Собираем приложение
RUN CGO_ENABLED=0 GOOS=linux go build -o /hello-world

# Используем минимальный образ для запуска
FROM alpine:latest

# Копируем бинарник из builder
COPY --from=builder /hello-world /hello-world

# Открываем порт, который использует приложение
EXPOSE 9090

# Запускаем приложение
CMD ["/hello-world"]