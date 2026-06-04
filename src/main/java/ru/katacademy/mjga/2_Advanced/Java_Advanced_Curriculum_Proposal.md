# Java Advanced Curriculum Proposal

Документ описывает курс Java Advanced как продолжение Java Core.

## Назначение курса

Java Advanced отвечает за переход от обычного Java-приложения без фреймворков к backend-сервису, который:

- принимает HTTP-запросы;
- работает с JSON;
- хранит данные в PostgreSQL;
- использует Spring Boot;
- имеет миграции БД;
- покрыт unit/integration-тестами;
- логирует важные события;
- имеет базовую observability;
- запускается в Docker;
- устойчивее относится к сетевым сбоям;
- готовит студента к предпроектной работе.

Advanced не должен заново учить Java-синтаксис. Он должен показывать, какие реальные задачи фреймворки и инфраструктурные инструменты решают поверх уже понятной Java.

## Входной профиль студента

Студент перед Advanced уже должен уметь:

- писать классы, методы, интерфейсы и enum;
- понимать инкапсуляцию, наследование, полиморфизм;
- пользоваться Collections Framework и generics;
- писать JUnit-тесты;
- работать с Maven/Gradle на базовом уровне;
- пользоваться Git;
- читать и писать файлы;
- работать с SQL, PostgreSQL и JDBC;
- понимать Repository pattern;
- разделять приложение на `model`, `service`, `repository`, `app`;
- пользоваться логированием на базовом уровне;
- понимать HTTP request/response, status codes, headers/body;
- делать HTTP-запросы через Java `HttpClient`;
- понимать базовые сетевые ошибки, timeout и retry;
- понимать базовую многопоточность: `ExecutorService`, `Future`, race condition, `synchronized`.

Если этих знаний нет, Advanced будет восприниматься как магия Spring и инфраструктуры.

## Главный методический принцип

Каждая новая технология вводится через проблему, которую студент уже видел в Core.

Примеры:

- Dependency Injection в Spring объясняется после ручной DI через конструкторы.
- Spring Data JPA объясняется после JDBC repository.
- REST controller объясняется после HTTP basics и Java `HttpClient`.
- Flyway/Liquibase объясняется после ручного создания таблиц.
- Docker объясняется после проблемы "у меня на компьютере работает, у другого нет".
- Observability объясняется после логирования и поиска ошибок в приложении.
- Retry/circuit breaker объясняются после сетевых timeout и ошибок HTTP-клиента.

Фреймворк не должен появляться раньше боли, которую он закрывает.

## Логичная последовательность модулей

### Модуль 1. Spring Core и Dependency Injection

**Цель:** показать, как Spring автоматизирует ручную сборку зависимостей, уже знакомую из Core.

**Из Core используется:** interfaces, service/repository, constructor injection руками, Maven/Gradle, JUnit.

**Новые знания:**

- IoC container;
- bean;
- application context;
- `@Component`, `@Service`, `@Repository`;
- constructor injection;
- configuration class;
- profiles на базовом уровне.

**Почему здесь:** Spring нельзя начинать с REST. Сначала студент должен понять, кто создает объекты и как зависимости попадают внутрь сервисов.

### Модуль 2. Spring Boot приложение

**Цель:** научить запускать Spring Boot-приложение и понимать его структуру.

**Из Core используется:** Maven/Gradle, packages, logging, application layers.

**Новые знания:**

- `@SpringBootApplication`;
- auto-configuration на уровне идеи;
- `application.yml`;
- external configuration;
- startup logs;
- dev/prod settings на базовом уровне.

**Почему здесь:** после Spring Core студент готов увидеть Boot как удобную сборку типового приложения.

### Модуль 3. REST API, JSON и Validation

**Цель:** научить делать HTTP API на Spring Boot.

**Из Core используется:** HTTP basics, JSON как формат обмена, DTO как идея, service layer, exceptions.

**Новые знания:**

- controller;
- `@RestController`;
- `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`;
- request body;
- response body;
- path/query params;
- status codes;
- DTO;
- Jackson;
- Bean Validation;
- global exception handler.

**Почему здесь:** студент уже знает HTTP как протокол. Теперь он учится принимать запросы, а не только отправлять их.

### Модуль 4. Spring Data JPA и Hibernate

**Цель:** заменить ручной JDBC repository на ORM, не потеряв понимание SQL и границ слоев.

**Из Core используется:** SQL, PostgreSQL, JDBC, Repository pattern, transactions базово, domain model.

**Новые знания:**

- entity;
- `@Entity`, `@Id`, `@GeneratedValue`;
- repository interfaces;
- Spring Data query methods;
- relationships: one-to-many, many-to-one на базовом уровне;
- lazy/eager loading как практический риск;
- transactions через `@Transactional`.

**Почему здесь:** ORM нельзя давать до JDBC. Студент должен понимать, что Hibernate не отменяет SQL, а генерирует и выполняет его.

### Модуль 5. Миграции базы данных

**Цель:** научить управлять схемой БД как частью приложения.

**Из Core используется:** SQL DDL basics, PostgreSQL, Git, Maven/Gradle.

**Новые знания:**

- проблема ручного изменения БД;
- migration file;
- versioned migrations;
- Flyway или Liquibase;
- rollback на уровне идеи;
- локальная и тестовая БД.

**Почему здесь:** миграции логично идут после JPA/JDBC, когда у приложения уже есть таблицы и schema evolution.

### Модуль 6. Security Basics

**Цель:** дать практическую базу аутентификации и авторизации.

**Из Core и Advanced используется:** HTTP, REST, PostgreSQL, service/repository, exceptions, validation.

**Новые знания:**

- authentication vs authorization;
- password hashing;
- bcrypt;
- role;
- JWT;
- login endpoint;
- secured endpoints;
- basic Spring Security flow.

**Почему здесь:** безопасность нельзя давать до REST API и хранения пользователей. Но перед предпроектом студент должен понимать хотя бы базовую модель доступа.

### Модуль 7. Integration Testing

**Цель:** научить проверять не только классы, но и связку Spring + HTTP + БД.

**Из Core используется:** JUnit, Maven/Gradle, repository/service tests.

**Новые знания:**

- Spring Boot tests;
- slice tests;
- MockMvc;
- integration tests;
- Testcontainers;
- test database;
- testing REST endpoints.

**Почему здесь:** после REST, DB и security появляются сценарии, которые unit-тестами уже не покрыть.

### Модуль 8. Observability

**Цель:** научить видеть, что происходит с приложением после запуска.

**Из Core используется:** logging basics, exceptions, HTTP, multithreading basics.

**Новые знания:**

- observability overview;
- structured logging;
- correlation id на базовом уровне;
- Spring Boot Actuator;
- health checks;
- readiness/liveness как идея;
- metrics;
- Prometheus basics;
- простая dashboard-ориентация.

**Почему здесь:** студент уже умеет писать сервис. Теперь он должен понимать, как сервис наблюдать в работе.

### Модуль 9. Resilience

**Цель:** научить проектировать приложение, которое не падает от первого сетевого сбоя.

**Из Core используется:** HTTP client, timeout, retry idea, exceptions, logging, ExecutorService.

**Новые знания:**

- network failures in distributed systems;
- timeout;
- retry;
- exponential backoff;
- idempotency на базовом уровне;
- circuit breaker;
- fallback;
- client pool на уровне идеи;
- Resilience4j basics.

**Почему здесь:** resilience без HTTP-интеграций и observability превращается в абстрактные паттерны. Здесь у студента уже есть сервис и внешние вызовы.

### Модуль 10. Docker и Docker Compose

**Цель:** научить запускать приложение и его зависимости воспроизводимо.

**Из Core и Advanced используется:** Maven/Gradle, Spring Boot jar, PostgreSQL, configuration.

**Новые знания:**

- image;
- container;
- Dockerfile;
- multi-stage Dockerfile;
- environment variables;
- Docker Compose;
- app + PostgreSQL;
- app + Redis на базовом уровне;
- logs в контейнере.

**Почему здесь:** контейнеризация полезна после появления реального сервиса с БД и конфигурацией.

### Модуль 11. Redis и Cache Basics

**Цель:** показать кэширование как прикладной инструмент ускорения чтения и снижения нагрузки.

**Из Core и Advanced используется:** HTTP service, repository/service, Docker Compose, serialization basics.

**Новые знания:**

- cache;
- cache invalidation на простом уровне;
- Redis;
- TTL;
- Spring Cache;
- cache key;
- когда кэш вреден.

**Почему здесь:** кэширование нельзя давать до БД и сервисной архитектуры. Иначе студент не понимает, какую проблему решает Redis.

### Модуль 12. Advanced Concurrency

**Цель:** расширить базовую многопоточность Core до практик, нужных backend-разработчику.

**Из Core используется:** `Thread`, `Runnable`, `ExecutorService`, `Future`, race condition, `synchronized`.

**Новые знания:**

- `CompletableFuture`;
- thread pools deeper;
- locks;
- atomics;
- `volatile`;
- Java Memory Model overview;
- concurrent collections deeper;
- async calls на прикладном уровне.

**Почему здесь:** глубокая concurrency слишком тяжела для Core, но нужна для понимания async-интеграций и производительности.

### Модуль 13. CI/CD Basics

**Цель:** показать путь кода от commit до запуска проверок и сборки.

**Из Core используется:** Git, Maven/Gradle, JUnit.

**Из Advanced используется:** Docker, integration tests.

**Новые знания:**

- pipeline;
- build step;
- test step;
- Docker build step;
- GitHub Actions или GitLab CI;
- artifacts;
- environment variables/secrets на уровне идеи.

**Почему здесь:** CI/CD логично давать после того, как приложение уже собирается, тестируется и контейнеризуется.

### Модуль 14. Предпроектная работа: Backend Service

**Цель:** собрать Advanced-навыки в сервис, близкий к реальной командной разработке.

**Проект должен включать:**

- Spring Boot REST API;
- PostgreSQL;
- migrations;
- service/repository layers;
- DTO и validation;
- authentication/authorization;
- logging;
- Actuator health checks;
- базовые metrics;
- integration tests;
- Docker Compose;
- README;
- Git workflow;
- code review checklist.

**Почему здесь:** финальный проект должен проверять не знание отдельных аннотаций, а способность собрать поддерживаемый backend-сервис.

## Итоговая программа курса

### Модуль 1. Spring Core и Dependency Injection

- Лекция 1. Зачем нужен Spring, если мы уже умеем DI руками
- Лекция 2. IoC container и bean
- Лекция 3. `@Component`, `@Service`, `@Repository`
- Лекция 4. Constructor injection
- Лекция 5. Configuration и profiles
- Практика: перенести Core-приложение на Spring Core
- Мини-проект: service/repository приложение без web-слоя

### Модуль 2. Spring Boot приложение

- Лекция 1. Структура Spring Boot проекта
- Лекция 2. `@SpringBootApplication` и auto-configuration
- Лекция 3. `application.yml`
- Лекция 4. Конфигурация через environment
- Лекция 5. Startup logs и диагностика запуска
- Практика: собрать и запустить Spring Boot приложение
- Мини-проект: Boot-приложение с service layer

### Модуль 3. REST API, JSON и Validation

- Лекция 1. REST controller
- Лекция 2. HTTP methods и status codes в Spring
- Лекция 3. Request/response body
- Лекция 4. DTO и Jackson
- Лекция 5. Validation
- Лекция 6. Global exception handling
- Практика: CRUD REST API
- Мини-проект: TODO/Product REST API

### Модуль 4. Spring Data JPA и Hibernate

- Лекция 1. Entity и table mapping
- Лекция 2. Spring Data repository
- Лекция 3. Query methods
- Лекция 4. Relations basics
- Лекция 5. Lazy loading risks
- Лекция 6. Transactions with `@Transactional`
- Практика: заменить JDBC repository на JPA
- Мини-проект: Order API with PostgreSQL

### Модуль 5. Миграции базы данных

- Лекция 1. Почему ручные изменения БД ломают командную работу
- Лекция 2. Flyway или Liquibase basics
- Лекция 3. Versioned migrations
- Лекция 4. Миграции в test/dev окружении
- Практика: добавить миграции к проекту
- Мини-проект: API с управляемой схемой БД

### Модуль 6. Security Basics

- Лекция 1. Authentication vs authorization
- Лекция 2. Password hashing и bcrypt
- Лекция 3. JWT
- Лекция 4. Spring Security basics
- Лекция 5. Roles и secured endpoints
- Практика: login + protected endpoints
- Мини-проект: API с пользователями и ролями

### Модуль 7. Integration Testing

- Лекция 1. Unit vs integration tests
- Лекция 2. Spring Boot tests
- Лекция 3. MockMvc
- Лекция 4. Testcontainers
- Лекция 5. Testing database and REST flows
- Практика: покрыть API integration-тестами
- Мини-проект: tested REST service

### Модуль 8. Observability

- Лекция 1. Введение в observability
- Лекция 2. Structured logs
- Лекция 3. Correlation id basics
- Лекция 4. Spring Boot Actuator
- Лекция 5. Health checks
- Лекция 6. Metrics и Prometheus basics
- Практика: добавить logs, health и metrics
- Мини-проект: observable REST service

### Модуль 9. Resilience

- Лекция 1. Сетевые сбои в распределенных системах
- Лекция 2. Timeout
- Лекция 3. Retry и backoff
- Лекция 4. Circuit breaker
- Лекция 5. Fallback и idempotency basics
- Практика: HTTP client с retry/circuit breaker
- Мини-проект: устойчивый client-service flow

### Модуль 10. Docker и Docker Compose

- Лекция 1. Введение в контейнеризацию
- Лекция 2. Dockerfile для Spring Boot
- Лекция 3. Multi-stage build
- Лекция 4. Docker Compose: app + PostgreSQL
- Лекция 5. Environment variables
- Практика: контейнеризировать сервис
- Мини-проект: Spring Boot + PostgreSQL в Compose

### Модуль 11. Redis и Cache Basics

- Лекция 1. Зачем нужен cache
- Лекция 2. Redis basics
- Лекция 3. TTL и invalidation
- Лекция 4. Spring Cache
- Лекция 5. Когда cache вреден
- Практика: добавить cache на read endpoint
- Мини-проект: API с Redis cache

### Модуль 12. Advanced Concurrency

- Лекция 1. Повтор Core concurrency
- Лекция 2. `CompletableFuture`
- Лекция 3. Locks и atomics
- Лекция 4. `volatile` и Java Memory Model overview
- Лекция 5. Async external calls
- Практика: параллельные внешние вызовы
- Мини-проект: async aggregation service

### Модуль 13. CI/CD Basics

- Лекция 1. Что такое pipeline
- Лекция 2. Build/test pipeline
- Лекция 3. Docker build in CI
- Лекция 4. Secrets и environment variables
- Лекция 5. Artifacts и quality gates
- Практика: настроить CI для проекта
- Мини-проект: pipeline для backend service

### Модуль 14. Предпроектная работа: Backend Service

- Лекция 1. Проектирование сервиса
- Лекция 2. Границы слоев
- Лекция 3. План тестирования
- Лекция 4. Observability checklist
- Лекция 5. Deployment checklist
- Практика: поэтапная разработка сервиса
- Мини-проект: production-like backend service

## Что не входит в Advanced

Следующие темы лучше оставить за пределами этого курса или дать как optional:

- микросервисная архитектура глубоко;
- Kubernetes глубоко;
- service mesh;
- Kafka/RabbitMQ как полноценный модуль;
- distributed tracing глубоко;
- high-load SQL tuning глубоко;
- domain-driven design глубоко;
- reactive stack;
- cloud provider specifics.

Эти темы требуют уже не просто junior-level Java, а опыта разработки и эксплуатации сервисов.

## Итоговая граница Base -> Core -> Advanced

```text
Java Base
учит писать простые Java-программы
↓
Java Core
учит писать нормальное Java-приложение без фреймворков
↓
Java Advanced
учит делать backend-сервис на Spring Boot с БД, HTTP, security, observability, Docker и production-практиками
```

## Ожидаемый результат после Advanced

Студент после Advanced умеет:

- создать Spring Boot REST API;
- подключить PostgreSQL;
- описать миграции БД;
- реализовать service/repository слои;
- использовать JPA/Hibernate без полной потери понимания SQL;
- добавить validation и error handling;
- реализовать базовую authentication/authorization;
- писать unit и integration tests;
- контейнеризировать сервис;
- читать structured logs;
- добавить health checks и базовые metrics;
- реализовать простой retry/circuit breaker для внешнего HTTP-клиента;
- подготовить проект к ревью и предпроектной работе.

Студент после Advanced еще не обязан быть production engineer. Но он должен понимать, из каких частей состоит современный Java backend-сервис и как эти части связаны между собой.
