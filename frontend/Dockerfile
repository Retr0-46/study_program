# 1. Используем официальный образ Dart/Flutter
FROM cirrusci/flutter:latest

# 2. Устанавливаем рабочую директорию
WORKDIR /app

# 3. Копируем pubspec и устанавливаем зависимости
COPY pubspec.* ./
RUN flutter pub get

# 4. Копируем остальной код
COPY . .

# 5. Собираем Web-версию
RUN flutter build web

# 6. Используем nginx для сервировки статики
FROM nginx:alpine
COPY --from=0 /app/build/web /usr/share/nginx/html
