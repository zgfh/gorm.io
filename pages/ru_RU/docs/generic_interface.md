---
title: Общий интерфейс базы данных sql.DB
layout: страница
---

GORM предоставляет метод `DB`, который возвращает общий интерфейс базы данных [\*sql.DB](https://pkg.go.dev/database/sql#DB) из текущего `*gorm.DB`

```go
// Получить объект sql.DB для использования его методов
sqlDB, err := db.DB()

// Ping
sqlDB.Ping()

// Закрыть
sqlDB.Close()

// Возвращает статистику БД
sqlDB.Stats()
```

{% note warn %}
**NOTE** If the underlying database connection is not a `*sql.DB`, like in a transaction, it will returns error
{% endnote %}

## Пул подключений

```go
// Получить объект sql.DB для использования его методов
sqlDB, err := db.DB()

// SetMaxIdleConns устанавливает максимальное количество соединений в пуле бездействия.
sqlDB.SetMaxIdleConns(10)

// SetMaxOpenConns устанавливает максимальное количество открытых соединений с БД.
sqlDB.SetMaxOpenConns(100)

// SetConnMaxLifetime устанавливает максимальное время повторного использования соединения.
sqlDB.SetConnMaxLifetime(time.Hour)
```
