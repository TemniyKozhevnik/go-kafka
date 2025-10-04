# Go Kafka Project

Проект для работы с Apache Kafka на Go. Включает производителя (producer) и потребителя (consumer).

## Возможности

- 🚀 Производитель сообщений в Kafka
- 📨 Потребитель сообщений из Kafka
- 🐳 Docker контейнеризация

## Технологии

- **Язык**: Go 1.19+
- **Брокер сообщений**: Apache Kafka
- **Координация**: Zookeeper
- **Контейнеризация**: Docker, Docker Compose

## Быстрый старт

### 1. Клонирование репозитория
```bash
git clone https://github.com/TemniyKozhevnik/go-kafka.git
cd go-kafka
```

### 2. Создание переменных окружения
Создайте в корневой директории файл .env, включающий:
```env
PORT=:8000
HOST=localhost
KAFKA_PORT=:29092
```

### 3. Запуск проекта

#### 1) Создайте контейнеры

```bash
docker compose up
```

#### 2) Запустите продюсера

```bash
go run producer/producer.go 
```

#### 3) Запустите консюмера

```bash
go run consumer/worker.go
```

## API Endpoints

### Основные endpoints

#### 🔗 Отправка комментария в кафку
```http
POST /api/v1/comment
```

#### Пример запроса
Запрос
```json
{
    "text": "1234"
}
```

Ответ
```json
{
    "comment": {
        "text": "1234"
    },
    "message": "Comment pushed successfully",
    "success": true
}
```
Вывод продюсера:
```bash
Message is stored in topic(comments)/partition(0)/offset(0)
```

Вывод консюмера:
```bash
consumer started
Received message Count: 1: | Topic (comments) | Message({"text":"1234"})
```
