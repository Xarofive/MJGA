# Java Pre-project Curriculum Proposal

Документ описывает курс Java Pre-project как этап после Java Core и перед дополнительным курсом Java Advanced.

## Назначение курса

Pre-project отвечает за переход от учебного Java-приложения без фреймворков к прикладной backend-разработке на Spring.

Главная задача курса - не дать студенту максимальный стек, а довести его до состояния, где он способен:

- уверенно работать с Git в учебном проекте;
- писать CRUD-приложения с БД;
- понимать разницу между JDBC, Hibernate/JPA и Spring Data;
- собирать web-приложение на Spring MVC;
- переносить MVC-приложение в Spring Boot;
- добавлять базовую authentication/authorization через Spring Security;
- делать REST CRUD API;
- использовать простой frontend-слой для асинхронных запросов;
- оформлять личный кабинет и формы через Bootstrap;
- читать чужой код, проходить ревью и исправлять замечания.

Pre-project не должен заменять Java Core и не должен превращаться в инфраструктурный Advanced. Его роль - закрепить Core на реальных web-задачах и подготовить студента к проектной работе.

## Входной профиль студента

Студент перед Pre-project уже должен уметь:

- писать классы, интерфейсы, enum и исключения;
- понимать ООП, инкапсуляцию и границы ответственности классов;
- пользоваться Collections Framework и generics;
- писать JUnit-тесты;
- работать с Maven/Gradle на базовом уровне;
- пользоваться Git на уровне add/commit/branch/merge;
- читать и писать файлы;
- работать с SQL, PostgreSQL и JDBC;
- понимать Repository pattern;
- разделять приложение на `model`, `service`, `repository`, `app`;
- пользоваться логированием на базовом уровне;
- понимать HTTP request/response, status codes, headers/body.

Если Core будет усилен архитектурой, HTTP basics, JDBC и тестами, Pre-project можно разгрузить от объяснения фундамента и сфокусировать на Spring и web-практике.

## Текущее содержание Pre-project

Сейчас Pre-project состоит из следующих блоков:

- основы Git;
- серия задач JDBC и Hibernate;
- Spring MVC + CRUD-приложение;
- Spring Boot + CRUD-приложение;
- Spring Security как доработка предыдущего CRUD-приложения;
- REST CRUD Spring Boot приложение;
- элементы JavaScript для асинхронных запросов;
- frontend-задачи с Bootstrap для оформления личного кабинета.

Frontend появляется только на этапе Spring MVC без Boot, затем усложнение идет через Spring Boot, Security и REST.

## Методическая проблема текущей версии

Текущий Pre-project слишком узко держится на CRUD-прогрессии. Это работает как тренажер Spring, но оставляет слабые места:

- мало явной архитектуры: слои есть, но их ответственность часто не проговаривается;
- мало проектного Git workflow: ветки, review, conflict resolution и README не закреплены как рабочая привычка;
- frontend появляется поздно и воспринимается как оформление, а не как часть web-сценария;
- Security часто воспринимается как набор настроек, а не как модель доступа;
- REST и асинхронные запросы появляются после MVC, но связь между HTML form flow и API flow нужно проговаривать явно;
- мало акцента на тестировании web-слоя и сервисного слоя;
- мало observability даже на базовом уровне: logs, error pages, понятная диагностика запуска.

После усиления Core эти пробелы лучше закрывать именно в Pre-project, но без перегруза Docker, микросервисами и Kubernetes.

## Логичная последовательность модулей

### Модуль 1. Git для проектной работы

**Цель:** перевести Git из набора команд в рабочий процесс.

**Темы:**

- повтор `clone`, `add`, `commit`, `push`, `pull`;
- branch и merge;
- pull request / merge request на уровне процесса;
- conflict resolution;
- `.gitignore`;
- README;
- code review checklist.

**Практика:** вести все последующие задачи через отдельные ветки и ревью-чеклист.

### Модуль 2. JDBC CRUD и Repository

**Цель:** закрепить работу с БД без ORM и Spring Data.

**Темы:**

- JDBC connection;
- DAO/Repository;
- CRUD;
- SQL parameters;
- transactions basics;
- обработка ошибок БД;
- тестирование repository на простой тестовой БД.

**Практика:** консольное или web-ready CRUD-приложение с PostgreSQL.

### Модуль 3. Hibernate и JPA

**Цель:** показать ORM как замену ручного JDBC repository, не теряя понимания SQL.

**Темы:**

- entity;
- mapping таблиц;
- `Session` / `EntityManager` на уровне идеи;
- relationships basics;
- lazy loading risks;
- transactions;
- отличие Hibernate/JPA от Spring Data.

**Практика:** заменить JDBC persistence на Hibernate/JPA.

### Модуль 4. Spring MVC и server-side frontend

**Цель:** собрать первое web-приложение с HTML, формами и серверным рендерингом.

**Темы:**

- MVC model;
- controller;
- templates;
- form submit;
- validation;
- error handling;
- Bootstrap для форм, таблиц и личного кабинета.

**Практика:** CRUD-приложение с web-интерфейсом и Bootstrap-оформлением.

### Модуль 5. Spring Boot CRUD

**Цель:** перенести web-приложение на Spring Boot и понять, что Boot автоматизирует.

**Темы:**

- структура Spring Boot проекта;
- `@SpringBootApplication`;
- auto-configuration на уровне идеи;
- `application.yml`;
- Spring Data repository;
- service layer;
- startup diagnostics.

**Практика:** Spring Boot CRUD-приложение с БД и web-интерфейсом.

### Модуль 6. Spring Security

**Цель:** добавить базовую модель доступа к существующему CRUD-приложению.

**Темы:**

- authentication vs authorization;
- users и roles;
- password hashing;
- login/logout flow;
- protected pages;
- доступ к операциям CRUD по ролям.

**Практика:** доработать Boot CRUD-приложение: пользователи, роли, защищенный личный кабинет.

### Модуль 7. REST CRUD API

**Цель:** показать отличие server-side MVC от API.

**Темы:**

- `@RestController`;
- HTTP methods;
- JSON request/response;
- DTO;
- validation;
- global exception handler;
- status codes.

**Практика:** REST CRUD Spring Boot приложение.

### Модуль 8. JavaScript и асинхронные запросы

**Цель:** связать frontend-слой с REST API.

**Темы:**

- fetch API;
- async request;
- обработка response status;
- обновление таблицы без перезагрузки страницы;
- простая обработка ошибок в UI.

**Практика:** добавить асинхронные CRUD-операции к REST-приложению.

### Модуль 9. Pre-project итоговая сборка

**Цель:** собрать изученные блоки в один понятный проект.

**Проект должен включать:**

- Git workflow;
- README с запуском;
- Spring Boot;
- PostgreSQL;
- Hibernate/JPA или Spring Data JPA;
- service/repository layers;
- server-side pages или REST + JS flow;
- Bootstrap-оформление личного кабинета;
- Spring Security;
- validation и error handling;
- базовые unit/service tests;
- базовые integration/web tests по возможности.

## Что не входит в Pre-project

Следующие темы лучше не включать в обязательный Pre-project:

- Docker и Docker Compose как полноценный модуль;
- микросервисная архитектура;
- Spring Cloud;
- Eureka;
- Config Server;
- API Gateway;
- Kafka/RabbitMQ;
- Zipkin/Sleuth;
- ELK;
- Kubernetes;
- WebFlux/Reactor как отдельный стек;
- продвинутая observability;
- production CI/CD.

Эти темы относятся к дополнительному Java Advanced после Pre-project.

## Итоговая граница Base -> Core -> Pre-project -> Advanced

```text
Java Base
учит писать простые Java-программы
↓
Java Core
учит писать нормальное Java-приложение без фреймворков
↓
Java Pre-project
учит делать Spring CRUD/web/REST-приложение и готовит к проектной работе
↓
Java Advanced
расширяет стек до Docker, микросервисов, Spring Cloud, messaging, reactive и Kubernetes
```

## Ожидаемый результат после Pre-project

Студент после Pre-project умеет:

- вести учебный проект через Git;
- сделать CRUD-приложение с PostgreSQL;
- объяснить разницу JDBC, Hibernate/JPA и Spring Data;
- собрать Spring MVC приложение с server-side frontend;
- перенести приложение на Spring Boot;
- добавить базовую Spring Security модель;
- реализовать REST CRUD API;
- связать REST API с простым JavaScript frontend;
- оформить личный кабинет через Bootstrap;
- объяснить назначение controller/service/repository слоев;
- подготовить проект к ревью.

Студент после Pre-project еще не обязан понимать микросервисы и production-инфраструктуру. Он должен уверенно собрать и объяснить монолитное Spring Boot web/API-приложение.
