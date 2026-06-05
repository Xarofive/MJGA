# Java Advanced Curriculum Proposal

Документ описывает Java Advanced как дополнительный курс после Java Pre-project.

Advanced не заменяет Pre-project. Он расширяет уже собранный Spring Boot CRUD/web/REST опыт до инфраструктуры, микросервисов, распределенных систем и современного production-adjacent стека.

## Входной профиль студента

Студент перед Advanced уже должен уметь:

- работать с Git и проходить ревью;
- писать Spring Boot CRUD-приложение;
- работать с PostgreSQL и JPA/Hibernate;
- понимать controller/service/repository слои;
- реализовывать REST API;
- добавлять базовую Spring Security модель;
- использовать Bootstrap и простой JavaScript для frontend-задач;
- читать логи приложения и диагностировать типовые ошибки запуска.

## Текущее содержание Advanced

### Модуль 1. Docker

- Что такое Docker
- Почему Docker легковесный и быстрый
- Установка Docker
- Практическое задание Docker
- Docker Compose
- Практическое задание Docker Compose
- Обратная связь по модулю

### Модуль 2. Знакомство с микросервисами

- Микросервисы vs монолит
- Что такое Spring Cloud
- Spring Cloud и Docker
- Обратная связь по модулю

### Модуль 3. Discovery Server

- Как работает Eureka
- Настройки для запуска Eureka Server
- Практическое задание: запуск Eureka Server
- Минимальные настройки Eureka Client
- Eureka Server, Eureka Service, Eureka Instance и Eureka Client
- Работа с Eureka: детальный разбор
- Взаимодействие клиента с сервером
- Взаимодействие нескольких Eureka Server
- Time Lag
- Режим самосохранения
- Безопасность
- Проверка состояния
- Клиенты в других зонах
- Практическая задача: работа с сервером
- Обратная связь по модулю

### Модуль 4. Configuration Server

- Что такое Config Server и зачем он нужен
- Создание Config Service и Config Client
- Обратная связь по модулю

### Модуль 5. Feign Client

- Feign Client и его аналоги
- RestTemplate
- WebClient
- Практическое задание
- Решение
- MongoDB: как скачать образ
- Обратная связь по модулю

### Модуль 6. Маршрутизация запросов

- API Gateway
- Spring Cloud Gateway
- Как устроен Gateway
- Маршрутизация на основе класса конфига
- Маршрутизация на основе property-файла
- Дополнительные возможности Spring Cloud Gateway
- Практическое задание: реализуем API Gateway
- Решение
- Обратная связь по модулю

### Модуль 7. Отказоустойчивость

- LoadBalancer
- Балансировка в Spring Cloud
- Circuit Breaker
- Обратная связь по модулю

### Модуль 8. Трассировка запросов

- Zipkin и Sleuth
- Как подключить Sleuth
- Добавление Zipkin
- Практическое задание Zipkin и Sleuth
- Обратная связь по модулю

### Модуль 9. Логирование

- ELK: Elasticsearch, Logstash, Kibana
- Практическое задание ELK
- Обратная связь по модулю

### Модуль 10. Spring Cloud Stream

- Spring Cloud Stream
- Kafka и RabbitMQ
- Отличия Kafka и RabbitMQ
- Практическое задание Spring Cloud Stream
- Решение
- Функциональный Spring Cloud Stream
- Работа в функциональном стиле
- Привязка и обязательные имена
- Практическое задание
- Обратная связь по модулю

### Модуль 11. Изменения свойств

- Spring Cloud Bus
- Добавление Spring Cloud Bus
- Зависимости в check-book-service
- Доработка store-book-service
- Файлы свойств
- Docker-образ с Kafka, Zookeeper и сопутствующими приложениями
- Обратная связь по модулю

### Модуль 12. Reactive

- Reactor
- Backpressure
- Как реактивность может помочь
- WebFlux
- Как работает Reactor
- Что такое реактивный поток
- Практические задания по Reactor/WebFlux
- Реализация реактивного подхода
- Решение
- Обратная связь по модулю

### Модуль 13. Kubernetes

- Kubernetes: что это такое и какие проблемы решает
- Основные понятия
- Deploy Spring Boot Application
- Решение
- Spring Cloud Kubernetes
- Обратная связь по модулю

## Методическая граница Advanced

Advanced должен начинаться только после Pre-project, потому что темы курса требуют уже готового Spring Boot опыта.

В Pre-project студент учится делать монолитное web/API-приложение. В Advanced он узнает, что происходит, когда таких приложений становится несколько:

- как их упаковывать и запускать в контейнерах;
- как сервисы находят друг друга;
- как выносить конфигурацию;
- как маршрутизировать запросы;
- как переживать сбои;
- как трассировать запрос через несколько сервисов;
- как собирать логи;
- как обмениваться событиями;
- как обновлять свойства;
- как работает reactive stack;
- как приложение деплоится в Kubernetes.

## Ожидаемый результат после Advanced

Студент после Advanced понимает:

- зачем нужен Docker и Docker Compose;
- чем микросервисная архитектура отличается от монолита;
- как работают Eureka, Config Server, Feign и API Gateway;
- зачем нужны LoadBalancer и Circuit Breaker;
- как устроены distributed tracing и централизованное логирование;
- как Spring Cloud Stream связывает сервисы через messaging;
- зачем нужны Spring Cloud Bus, Reactor/WebFlux и Kubernetes;
- какие риски появляются в распределенной backend-системе.
