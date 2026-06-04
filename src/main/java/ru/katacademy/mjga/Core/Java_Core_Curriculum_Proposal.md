# Java Core Curriculum Proposal

Документ проектирует курс Java Core как прямое продолжение Java Base на основе файла `java_base_student_portrait.md`.

Источник ограничений:

- студент знает базовый синтаксис, `main`, методы, условия, циклы, массивы, строки, базовый ввод, базовые исключения, `ArrayList`, `HashMap`, простые классы, объекты, ссылки, `null`, Debugger и stack trace;
- студент полноценно изучил только 4 примитивных типа: `int`, `double`, `boolean`, `char`; `String` изучался как основной ссылочный тип;
- студент не изучал `byte`, `short`, `long`, `float`, диапазоны примитивов, преобразования числовых типов, Git, Maven/Gradle, JUnit, инкапсуляцию, конструкторы, наследование, интерфейсы, `enum`, полноценный Collections Framework, generics как тему, Files API, Stream API, lambdas, SQL/JDBC и многопоточность;
- Base уже дал прикладные `ArrayList`/`HashMap`, но не дал `List`/`Map`/`Set` как интерфейсы;
- Base уже дал простые классы и объекты, но не дал коммерчески нормальную объектную модель с `private`, конструкторами, инвариантами, `equals/hashCode` и пакетами.

Главный принцип Core: не начинать с фреймворков и "магии". Сначала закрываются пробелы Base, затем нормализуется ООП, затем появляются тесты, сборка, Collections Framework, generics, файлы, streams, SQL/JDBC и базовая многопоточность.

## 1. Логичная последовательность модулей Core

### Модуль 1. Переход в Core: типы, пакеты, Git и рабочий процесс

**Цель модуля:** выровнять старт Core: закрыть пробел по примитивам, ввести пакеты и базовый Git, закрепить рабочий цикл в IDE.

**Из Base используется:** `main`, методы, `int`, `double`, `boolean`, `char`, `String`, условия, циклы, массивы, строки, базовый Debugger, терминал `java -version`/`javac -version`.

**Новые знания:** `byte`, `short`, `long`, `float`, диапазоны, переполнение, numeric promotion, cast, суффиксы `L`/`f`, `package`, структура исходников, Git `init/add/commit/status/log/diff`, `.gitignore`.

**Почему здесь:** отчет явно фиксирует, что полная система примитивов и Git не изучены. Без них нельзя честно начинать Core: `long` нужен для идентификаторов и времени, `float/double` надо различать, Git нужен для коммерческого workflow.

### Модуль 2. Классы по-взрослому: инкапсуляция, конструкторы, состояние

**Цель модуля:** перевести базовое ООП Base из "поля открыты, объект создается пустым" в нормальную модель: данные защищены, объект создается валидным, поведение живет рядом с состоянием.

**Из Base используется:** простые классы, поля, объектные методы, `new`, `null`, ссылки, `==` для ссылок, методы с `return`, условия.

**Новые знания:** `private`, `public`, package-private, getters/setters, constructors, `this`, перегрузка конструкторов, инварианты, `static`, `final`, константы, композиция объектов.

**Почему здесь:** Base уже дал классы и состояние, но отчет прямо запрещает молча использовать `private`, constructors, getters/setters. Эти темы нужны до наследования, коллекций объектов и тестирования доменной логики.

### Модуль 3. Объектные контракты: `Object`, `toString`, `equals/hashCode`, `enum`

**Цель модуля:** научить студента делать объекты, которые корректно сравниваются, читаемо выводятся и безопасно используются в коллекциях.

**Из Base используется:** классы, ссылки, `==`, `HashMap`, `String.equals`, простые методы, `switch`.

**Новые знания:** базовая роль `Object`, `toString`, `equals`, `hashCode`, контракт равенства, сравнение ссылок vs сравнение состояния, `enum`, `switch` по `enum`.

**Почему здесь:** отчет отмечает `equals/hashCode` как упомянутую, но не изученную тему. Ее надо дать до `HashSet`, `Map` с ключами-объектами и полноценного Collections Framework. `enum` логично появляется после классов и перед статусами в проектах.

### Модуль 4. Сборка, зависимости и тестирование: Maven, Gradle, JUnit

**Цель модуля:** перевести студента от одиночных `.java` и проверяющей обвязки к реальному проекту с тестами и зависимостями.

**Из Base используется:** IntelliJ IDEA, запуск проекта, Debugger, stack trace, методы и классы.

**Новые знания:** стандартная структура проекта, Maven как основной инструмент, Gradle как инструмент, который студент должен узнавать и запускать, зависимости, lifecycle/tasks, JUnit 5, assertions, parameterized tests, тестовый Debugger.

**Почему здесь:** тестирование нельзя вводить до осмысленных классов и инкапсуляции. Но слишком поздно вводить JUnit вредно: следующие модули должны проверяться тестами, а не только ручным запуском.

### Модуль 5. Collections Framework и Generics

**Цель модуля:** расширить прикладные `ArrayList`/`HashMap` из Base до коммерчески нормального владения коллекциями и типобезопасностью.

**Из Base используется:** массивы, циклы, `ArrayList`, `HashMap`, сортировка ключей через `Collections.sort`, классы, `equals/hashCode`.

**Новые знания:** `List`, `Set`, `Map` как стандартные интерфейсы коллекций; `ArrayList`, `LinkedList`, `HashSet`, `LinkedHashSet`, `TreeSet`, `HashMap`, `LinkedHashMap`, `TreeMap`; `Iterator`; `Comparable`, `Comparator`; generics, generic methods/classes, wrapper types, autoboxing/unboxing.

**Почему здесь:** отчет говорит, что `ArrayList`/`HashMap` изучены прикладно, но `List`/`Map`/`Set` и generics не изучены. После `equals/hashCode` студент готов понять, почему Set и Map ведут себя именно так.

### Модуль 6. Исключения глубже и Files API

**Цель модуля:** превратить базовый `try/catch/throw/throws` из Base в практическую обработку ошибок и работу с файлами.

**Из Base используется:** базовые исключения, `BufferedReader`, `PrintWriter`, `String`, массивы, коллекции, JUnit.

**Новые знания:** иерархия исключений, checked vs unchecked повторно и глубже, выбор стандартного исключения, контекст ошибки, try-with-resources на практике, `Path`, `Files`, чтение/запись текстовых файлов, CSV/простые текстовые форматы, кодировки.

**Почему здесь:** Files API нельзя вводить до try-with-resources и нормальной обработки ошибок. Коллекции уже есть, значит можно читать файл в список объектов и тестировать результат.

### Модуль 7. Наследование, полиморфизм и интерфейсы

**Цель модуля:** дать студенту объектное расширение поведения без преждевременной абстракции.

**Из Base и Core используется:** классы, инкапсуляция, конструкторы, `equals/hashCode`, коллекции объектов, JUnit.

**Новые знания:** `extends`, `super`, overriding, `@Override`, abstract classes, polymorphism, interfaces, default/static interface methods на базовом уровне, custom exceptions как прикладной пример наследования, dependency inversion на простых примерах.

**Почему здесь:** отчет предлагает цепочку "инкапсуляция -> конструкторы -> наследование -> полиморфизм -> интерфейсы". Студент должен сначала уметь создавать корректные объекты и тестировать их, иначе наследование станет синтаксической магией.

### Модуль 8. Lambda и Stream API

**Цель модуля:** научить студента читать и писать современную обработку коллекций без потери понимания циклов.

**Из Base и Core используется:** циклы, коллекции, generics, интерфейсы, `Comparator`, `Files.readAllLines`, JUnit.

**Новые знания:** functional interfaces, lambda expressions, method references, `Predicate`, `Function`, `Consumer`, `Supplier`, Stream pipeline, `filter`, `map`, `sorted`, `distinct`, `limit`, `collect`, `Collectors`, `Optional` на базовом уровне.

**Почему здесь:** Base косвенно видел `codePoints().toArray()`, но Stream API не изучался. Lambdas требуют интерфейсов и generics; Stream API требует коллекций. Поэтому модуль не может стоять раньше.

### Модуль 9. SQL и JDBC

**Цель модуля:** дать минимальную, но реальную работу с реляционными данными без ORM и фреймворков.

**Из Base и Core используется:** классы, коллекции, exceptions, Files/ресурсы, Maven/Gradle, JUnit.

**Новые знания:** таблицы, строки, первичный ключ, `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `WHERE`, `ORDER BY`, простые `JOIN`, JDBC, `Connection`, `PreparedStatement`, `ResultSet`, DAO/repository, SQL injection, transactions на базовом уровне.

**Почему здесь:** SQL не изучался в Base. JDBC нельзя давать до исключений, try-with-resources, классов и коллекций. ORM переносится в Advanced, чтобы не скрывать JDBC-основу.

### Модуль 10. Базовая многопоточность

**Цель модуля:** дать junior-уровень понимания потоков: что может выполняться параллельно, где появляются гонки и как безопасно запускать задачи.

**Из Base и Core используется:** методы, классы, исключения, коллекции, интерфейсы, lambdas.

**Новые знания:** `Thread`, `Runnable`, `Callable`, `ExecutorService`, `Future`, race condition, `synchronized`, immutability как прием безопасности, concurrent collections обзорно.

**Почему здесь:** многопоточность перегружает новичка, если дать ее раньше ООП, interfaces и lambdas. В Core нужна базовая грамотность, но глубокая concurrency-модель уходит в Advanced.

### Модуль 11. Итоговый проект: консольное Java-приложение уровня Junior

**Цель модуля:** собрать все Core-навыки в одно приложение с Git, сборкой, тестами, файлами или JDBC, слоями и понятной доменной моделью.

**Из Base и Core используется:** все предыдущие темы.

**Новые знания:** проектная декомпозиция, простая слоистая архитектура, service/repository, DTO на базовом уровне, code review checklist, README, запуск приложения из CLI.

**Почему здесь:** проект завершает курс и проверяет не знание отдельных конструкций, а способность собрать поддерживаемое приложение.

## 2. Лекции и практики по модулям

### Модуль 1. Переход в Core: типы, пакеты, Git и рабочий процесс

| Лекция | Чему учит | Обязательные темы до лекции | Практические задачи |
|---|---|---|---|
| 1. Повтор Base без повторения Base | Диагностика: методы, условия, циклы, массивы, строки, `ArrayList`/`HashMap`, Debugger | Весь Base | Найти и исправить 5 ошибок в методах с массивами, строками и `HashMap`; пройти одну задачу через Debug |
| 2. Полная карта примитивов Java | `byte`, `short`, `int`, `long`, `float`, `double`, `char`, `boolean`, диапазоны и смысл выбора | Base-типы `int/double/boolean/char` | Подобрать типы для доменных полей: id, age, price, rating, flag; написать отчет о выборе |
| 3. Числовые преобразования и переполнение | cast, numeric promotion, суффиксы `L`/`f`, деление int/double, переполнение | Арифметика, методы | Реализовать калькулятор скидок/налогов с `long` и `double`; найти баг переполнения |
| 4. Пакеты и структура исходников | `package`, `import`, размещение классов, имя пакета, разделение кода по смыслу | `public class`, `import` из Base | Разнести 5 классов по пакетам `model`, `service`, `util` |
| 5. Git для учебного и рабочего процесса | `git init/status/add/commit/log/diff`, `.gitignore`, смысл маленьких коммитов | Терминал из Base | Создать репозиторий, сделать 3 осмысленных коммита, показать diff до коммита |

**Практика модуля:** консольная утилита расчета доставки: примитивы, методы, пакеты, Git-коммиты.

**Мини-проект:** `core-start-calculator` с пакетами `app`, `model`, `service`, README и историей Git из 5 коммитов.

### Модуль 2. Классы по-взрослому: инкапсуляция, конструкторы, состояние

| Лекция | Чему учит | Обязательные темы до лекции | Практические задачи |
|---|---|---|---|
| 1. Зачем скрывать поля | `private`, публичные методы как управляемый доступ, инвариант объекта | Простые классы Base, поля и методы | Переделать `BankAccount` с открытых полей на `private` |
| 2. Getters/setters без автоматизма | Когда getter уместен, когда setter вреден, валидация в setter | `private`, условия | `Product` с проверкой цены и количества |
| 3. Конструкторы | Создание валидного объекта, параметры конструктора, конструктор по умолчанию | `new`, поля, методы | `Student(name, age, averageGrade)` с проверками |
| 4. `this` и перегрузка конструкторов | Разрешение конфликта имен, `this(...)`, несколько способов создать объект | Конструкторы | `User` с несколькими конструкторами |
| 5. `static`, `final`, константы | Статическое состояние vs состояние объекта, константы, utility-класс | Base `static` методы, объекты | Вынести лимиты в constants; исправить неверный `static balance` |
| 6. Композиция объектов | Один объект содержит другой, связь `Order` -> `Customer` -> `Address` | Конструкторы, ссылки | Модель заказа с адресом доставки |

**Практика модуля:** переписать задачи Base по классам в инкапсулированный стиль.

**Мини-проект:** доменная модель интернет-заказа: `Customer`, `Address`, `Product`, `Order`, `OrderService`.

### Модуль 3. Объектные контракты: `Object`, `toString`, `equals/hashCode`, `enum`

| Лекция | Чему учит | Обязательные темы до лекции | Практические задачи |
|---|---|---|---|
| 1. Все классы как объекты | Базовая роль `Object`, почему есть `toString`, `equals`, `hashCode` | Классы, ссылки | Прочитать вывод объекта до/после `toString` |
| 2. `toString` для диагностики | Читаемое представление объекта, не путать с бизнес-форматом | Инкапсуляция | Реализовать `toString` для `Product` и `Order` |
| 3. `equals`: сравнение состояния | `==` vs `equals`, null-safe сравнение, какие поля входят в идентичность | Ссылки, `String.equals` | `ProductId`, `UserEmail`, сравнение клиентов |
| 4. `hashCode` и контракт с `equals` | Почему равные объекты должны иметь одинаковый hash, связь с `HashMap` | `HashMap` Base, `equals` | Использовать объект как ключ `HashMap` |
| 5. `enum` для статусов и ролей | Объявление enum, поля/методы enum базово, `switch` по enum | `switch`, классы | `OrderStatus`, `UserRole`, переходы статусов |
| 6. Объект как ключ и значение | Почему контракт важен для коллекций, типовые ошибки | `equals/hashCode`, `HashMap` | Найти баг в `HashMap<OrderId, Order>` |

**Практика модуля:** реализовать `OrderId`, `OrderStatus`, `Order`, сравнение заказов по id.

**Мини-проект:** каталог заказов в памяти с поиском по id и статусу.

### Модуль 4. Сборка, зависимости и тестирование: Maven, Gradle, JUnit

| Лекция | Чему учит | Обязательные темы до лекции | Практические задачи |
|---|---|---|---|
| 1. Зачем нужен build tool | Структура проекта, `src/main/java`, `src/test/java`, зависимости | Пакеты, классы | Перенести мини-проект в Maven layout |
| 2. Maven как основной путь | `pom.xml`, lifecycle, `compile`, `test`, `package`, dependencies | Терминал, пакеты | Собрать jar, добавить зависимость |
| 3. Gradle как второй стандарт | `build.gradle`, tasks, wrapper, отличие подхода от Maven | Maven-концепции | Запустить `./gradlew test`, прочитать build file |
| 4. JUnit 5: первый тест | `@Test`, assertions, expected/actual, тестовые имена | Методы, классы | Написать тесты для `OrderService` |
| 5. Тестирование ошибок | `assertThrows`, проверка сообщений, negative cases | Исключения Base/Core | Тесты на невалидный заказ |
| 6. Parameterized tests и test data | Повторяемые проверки без копипаста | JUnit basics | Тесты на расчет доставки для разных данных |
| 7. Debugging тестов | Breakpoint в тесте, stack trace тестового падения | Debugger Base, JUnit | Найти ошибку через падающий тест |

**Практика модуля:** покрыть тестами мини-проект модуля 3.

**Мини-проект:** `order-core-tested`: Maven/Gradle версия проекта с JUnit 5, README и Git history.

### Модуль 5. Collections Framework и Generics

| Лекция | Чему учит | Обязательные темы до лекции | Практические задачи |
|---|---|---|---|
| 1. От `ArrayList` к `List` | Стандартный интерфейс коллекции vs реализация; пока без создания собственных интерфейсов | `ArrayList` Base, классы | Заменить `ArrayList` в сигнатурах на `List` |
| 2. `Set`: уникальность | `HashSet`, `LinkedHashSet`, `TreeSet`, роль `equals/hashCode` | `equals/hashCode` | Уникальные email пользователей |
| 3. `Map` как интерфейс | `HashMap`, `LinkedHashMap`, `TreeMap`, порядок и сортировка ключей | `HashMap` Base | Индекс заказов по id/status |
| 4. Iterator и безопасное удаление | `Iterator`, `remove`, ошибка изменения коллекции при обходе | Циклы, коллекции | Удалить отмененные заказы без ошибки |
| 5. Generics: зачем нужны `<T>` | Типобезопасность, generic class, generic method | Обертки `Integer`, `String`, коллекции | `Box<T>`, `Repository<T>` |
| 6. Ограничения generics | Wrapper types, autoboxing, нельзя `List<int>`, type inference | Base ошибка `ArrayList<int>` | Исправить сырой `List` и unchecked warnings |
| 7. `Comparable` и `Comparator` | Natural order, внешняя сортировка, composition comparators | `Collections.sort`, classes | Сортировать товары по цене/названию |

**Практика модуля:** in-memory repository для заказов: `List`, `Set`, `Map`, сортировка, фильтрация.

**Мини-проект:** `inventory-repository`: склад с уникальными товарами, индексами и тестами.

### Модуль 6. Исключения глубже и Files API

| Лекция | Чему учит | Обязательные темы до лекции | Практические задачи |
|---|---|---|---|
| 1. Иерархия исключений | `Exception`, `RuntimeException`, checked/unchecked глубже | Base exceptions | Классифицировать ошибки приложения |
| 2. Выбор стандартного исключения | Когда `IllegalArgumentException`, когда `IllegalStateException`, когда пробрасывать checked exception | Base exceptions, classes | Заменить неинформативные ошибки на стандартные исключения с контекстом |
| 3. try-with-resources на практике | Автоматическое закрытие ресурсов, кто владеет ресурсом | Base `BufferedReader`, exceptions | Прочитать файл безопасно |
| 4. `Path` и `Files` | `Path.of`, `Files.readString`, `readAllLines`, `writeString`, `exists` | Строки, коллекции | Загрузить список товаров из файла |
| 5. Текстовые форматы и CSV без магии | Разделители, экранирование на базовом уровне, ошибки формата | Strings, exceptions | CSV parser для товаров |
| 6. Кодировки | UTF-8, связь с Base Unicode, `StandardCharsets.UTF_8` | Base Unicode | Прочитать файл с кириллицей и эмодзи |

**Практика модуля:** импорт/экспорт товаров из CSV с тестами ошибок.

**Мини-проект:** `file-backed-inventory`: репозиторий, который сохраняет и загружает данные из файла.

### Модуль 7. Наследование, полиморфизм и интерфейсы

| Лекция | Чему учит | Обязательные темы до лекции | Практические задачи |
|---|---|---|---|
| 1. Наследование без злоупотребления | `extends`, reuse vs modeling, `is-a` | Инкапсуляция, конструкторы | `DiscountPolicy` пока без интерфейса: базовый и наследник |
| 2. `super` и конструкторы наследников | Вызов конструктора родителя, protected осторожно | Constructors | Иерархия платежей |
| 3. Overriding и `@Override` | Переопределение поведения, dynamic dispatch | Inheritance | Разные способы расчета комиссии |
| 4. Абстрактные классы | Общий код плюс обязательные методы | Overriding | `BaseReportExporter` |
| 5. Интерфейсы | Контракт без состояния реализации, `implements` | Polymorphism | `Repository`, `Notifier`, `PriceCalculator` |
| 6. Custom exceptions как прикладное наследование | `extends RuntimeException`/`Exception`, когда свой тип ошибки оправдан | Exceptions, inheritance, constructors | `InvalidOrderException`, `StorageException` |
| 7. Полиморфизм в коллекциях | `List<Interface>`, вызов общего метода | Interfaces, collections, generics | Список разных валидаторов |
| 8. Композиция против наследования | Когда лучше вложить объект, чем наследоваться | All OOP | Перепроектировать плохую иерархию |

**Практика модуля:** платежи и скидки через интерфейсы и полиморфизм.

**Мини-проект:** модуль расчета заказа с несколькими стратегиями скидок и доставки.

### Модуль 8. Lambda и Stream API

| Лекция | Чему учит | Обязательные темы до лекции | Практические задачи |
|---|---|---|---|
| 1. Functional interfaces | Один абстрактный метод, `Predicate`, `Function`, `Consumer`, `Supplier` | Interfaces, generics | Написать фильтр заказов через `Predicate` |
| 2. Lambda syntax | Параметры, тело, return, effectively final | Functional interfaces | Заменить анонимные фильтры на lambda |
| 3. Method references | `Class::method`, `object::method`, constructor reference | Lambdas, methods | Сортировка и mapping через references |
| 4. Stream pipeline | Source, intermediate, terminal operations | Collections | `filter`, `map`, `sorted`, `count`, `toList` |
| 5. Collectors | `toList`, `toSet`, `groupingBy`, `joining`, `toMap` осторожно | Streams, Map/Set | Отчет по заказам по статусам |
| 6. Optional базово | Отсутствие значения без `null` в API поиска | Exceptions, collections | `findById` возвращает `Optional<Order>` |
| 7. Цикл или stream | Читаемость, отладка, когда stream вреден | Base loops, streams | Переписать stream в цикл и наоборот |

**Практика модуля:** аналитика заказов через streams с тестами.

**Мини-проект:** `order-analytics`: отчеты по файлу заказов.

### Модуль 9. SQL и JDBC

| Лекция | Чему учит | Обязательные темы до лекции | Практические задачи |
|---|---|---|---|
| 1. Реляционная модель | Таблица, строка, колонка, primary key, foreign key на простом уровне | Классы, id, коллекции | Спроектировать таблицы `products`, `orders` |
| 2. SQL SELECT | `SELECT`, `WHERE`, `ORDER BY`, `LIMIT` | Collections filtering/sorting analogies | Запросы к учебной БД |
| 3. INSERT/UPDATE/DELETE | Изменение данных, ограничения | Exceptions | CRUD товаров |
| 4. JOIN | Связь таблиц, получение данных заказа с товарами | SQL basics | Заказы с позициями |
| 5. JDBC подключение | `Connection`, URL, driver, try-with-resources | Maven/Gradle, exceptions, files resources | Подключиться к локальной/embedded БД |
| 6. `PreparedStatement` | Параметры, SQL injection, безопасные запросы | JDBC basics | Поиск по email/status |
| 7. `ResultSet` -> object mapping | Преобразование строки БД в объект | Classes, constructors | `ProductMapper` |
| 8. DAO/Repository | Разделение SQL и бизнес-логики | Interfaces, exceptions | `ProductRepositoryJdbc` |
| 9. Transactions базово | Несколько операций как одно действие | JDBC, exceptions | Создать заказ и позиции атомарно |

**Практика модуля:** JDBC repository для товаров и заказов.

**Мини-проект:** `jdbc-order-storage` с тестами repository-слоя.

### Модуль 10. Базовая многопоточность

| Лекция | Чему учит | Обязательные темы до лекции | Практические задачи |
|---|---|---|---|
| 1. Зачем нужны потоки | Последовательное vs параллельное выполнение, проблема общей памяти | Methods, classes | Запустить две независимые задачи |
| 2. `Thread` и `Runnable` | Создание потока, start vs run | Interfaces | Простая фоновая обработка |
| 3. `ExecutorService` | Пул потоков, submit, shutdown | Interfaces, lambdas | Обработать список файлов параллельно |
| 4. `Callable` и `Future` | Задача с результатом, checked exceptions | Generics, exceptions | Параллельный расчет отчетов |
| 5. Race condition | Общая изменяемая переменная, непредсказуемый результат | References, state | Сломанный счетчик и воспроизведение гонки |
| 6. `synchronized` и immutability | Минимальная синхронизация, почему immutable проще | Encapsulation, final | Потокобезопасный счетчик |
| 7. Concurrent collections обзорно | Когда обычная коллекция опасна, `ConcurrentHashMap` на уровне применения | Collections, Map | Параллельный подсчет слов |

**Практика модуля:** параллельная обработка набора файлов с подсчетом статистики.

**Мини-проект:** `parallel-log-counter` с ограниченным, понятным применением потоков.

### Модуль 11. Итоговый проект уровня Java Core

| Лекция | Чему учит | Обязательные темы до лекции | Практические задачи |
|---|---|---|---|
| 1. От задачи к структуре приложения | Слои `model`, `repository`, `service`, `app`, границы ответственности | Все Core-модули | Разбить ТЗ на классы и пакеты |
| 2. CLI без хаоса | Команды, парсинг, валидация, сообщения об ошибках | Base input, exceptions, enum | Командный интерфейс для заказов |
| 3. Repository choice | In-memory, file-backed, JDBC-backed tradeoffs | Collections, Files, JDBC | Выбрать и обосновать хранилище |
| 4. Тестовая стратегия | Unit tests для service, integration tests для repository | JUnit, Maven/Gradle | План тестов итогового проекта |
| 5. Git workflow | Ветки, маленькие коммиты, pull request mindset | Git basics | Разработка фичи в отдельной ветке |
| 6. Code review checklist | Читаемость, ошибки, тесты, исключения, инкапсуляция | All Core | Провести ревью чужого решения |

**Практика модуля:** поэтапная разработка итогового приложения.

**Мини-проект:** `order-management-core`: консольное приложение с доменной моделью, тестами, сборкой, Git history и одним видом хранения: file или JDBC.

## 3. Проверка педагогической последовательности

| Тема | Можно использовать без объяснения? | Нужно повторение? | Что предварительно изучить |
|---|---|---|---|
| `int`, `double`, `boolean`, `char`, `String` | Да | Короткая диагностика | Base |
| `byte`, `short`, `long`, `float` | Нет | Да, как новая тема | Base arithmetic |
| Numeric cast/promotion/overflow | Нет | Да | Все примитивы |
| Git basics | Нет | Нет, новая тема | Терминал Base |
| `package` | Нет | Нет, новая тема | `import`, class |
| `private` | Нет | Нет, новая тема | Base classes |
| Constructors | Нет | Нет, новая тема | `new`, fields |
| Getters/setters | Нет | Нет, новая тема | `private`, constructors |
| `static/final` в объектной модели | Частично `static` да, `final` нет | Да | Classes, fields |
| `equals/hashCode` | Нет | Нет, новая тема | References, `==`, `String.equals` |
| `enum` | Нет | Нет, новая тема | Classes, `switch` |
| Maven/Gradle | Нет | Нет, новая тема | Packages, classes, Git useful |
| JUnit | Нет | Нет, новая тема | Methods, classes, build tool |
| `List`/`Map`/`Set` | Нет | Да для `ArrayList`/`HashMap` | Collections Base, interfaces later partly |
| Generics | Нет | Да для `ArrayList<String>` notation | Collections, wrappers |
| Files API | Нет | Да for Base input/exceptions | Exceptions, collections |
| Inheritance | Нет | Нет, новая тема | Encapsulation, constructors |
| Interfaces | Нет | Нет, новая тема | Inheritance/polymorphism basics |
| Lambda | Нет | Нет, новая тема | Interfaces, generics |
| Stream API | Нет | Да for loops/collections contrast | Lambda, collections |
| SQL | Нет | Нет, новая тема | Classes, collections, repositories concept |
| JDBC | Нет | Нет, новая тема | SQL, exceptions, try-with-resources, build tool |
| Multithreading | Нет | Нет, новая тема | Interfaces, lambdas, mutable state |
| Debugging | Да, базово | Да, через практику | Base Debugger |

## 4. Карта зависимостей между темами

### Типы и базовый язык

```text
Base: int/double/boolean/char/String
↓
byte/short/long/float
↓
Диапазоны и переполнение
↓
Numeric promotion и cast
↓
Корректный выбор типов в доменной модели
```

### Объектная модель

```text
Base: простые классы, поля, методы, new, null, ссылки
↓
private и контролируемый доступ
↓
Конструкторы и this
↓
Инварианты объекта
↓
Композиция
↓
toString / equals / hashCode
↓
enum для ограниченных состояний
↓
Наследование
↓
Полиморфизм
↓
Интерфейсы
↓
Стратегии, repository/service-контракты
```

### Коллекции и generics

```text
Base: массивы
↓
Base: ArrayList и HashMap прикладно
↓
equals/hashCode
↓
List / Set / Map как интерфейсы
↓
Реализации коллекций и порядок обхода
↓
Iterator и безопасное изменение
↓
Generics
↓
Comparable / Comparator
↓
Коллекции доменных объектов
```

### Ошибки, файлы и внешние данные

```text
Base: try/catch, throw, throws, BufferedReader
↓
Иерархия исключений
↓
try-with-resources
↓
Path / Files
↓
Парсинг текстовых форматов
↓
Repository на файлах
↓
JDBC repository
```

```text
Base: exceptions
↓
Иерархия исключений
↓
Наследование
↓
Custom exceptions
↓
Ошибки доменного и repository-слоя
```

### Тестирование и сборка

```text
Base: IntelliJ запуск и Debugger
↓
Пакеты и структура проекта
↓
Maven / Gradle
↓
JUnit basics
↓
assertThrows и parameterized tests
↓
Debugging тестов
↓
Тестовая стратегия итогового проекта
```

### Functional Java

```text
Interfaces
↓
Generics
↓
Functional interfaces
↓
Lambda
↓
Method references
↓
Stream API
↓
Collectors
↓
Optional
```

### SQL/JDBC

```text
Классы и доменная модель
↓
Collections и repositories
↓
Exceptions и try-with-resources
↓
SQL basics
↓
JDBC Connection / PreparedStatement / ResultSet
↓
Object mapping
↓
DAO / Repository
↓
Transactions базово
```

### Многопоточность

```text
Mutable state и references
↓
Interfaces
↓
Lambdas
↓
Thread / Runnable
↓
ExecutorService
↓
Callable / Future
↓
Race condition
↓
synchronized
↓
Concurrent collections обзорно
```

## 5. Оценка обязательных тем

| Тема | Должна быть в Core? | Где появляется | Что требуется до изучения |
|---|---|---|---|
| Git | Да | Модуль 1 | Терминал Base, понимание файлов проекта |
| Maven | Да | Модуль 4 | Packages, classes, Git желательно |
| Gradle | Да, но легче Maven | Модуль 4 | Понимание build tool через Maven |
| JUnit | Да | Модуль 4 | Методы, классы, Maven/Gradle |
| Debugging | Да, как повтор и практика | Модули 1, 4, 11 | Base Debugger |
| Collections Framework | Да | Модуль 5 | Base `ArrayList`/`HashMap`, `equals/hashCode` |
| Generics | Да | Модуль 5 | Collections, wrappers, классы |
| equals/hashCode | Да | Модуль 3 | Ссылки, `==`, `String.equals`, классы |
| enum | Да | Модуль 3 | Classes, `switch` |
| Files API | Да | Модуль 6 | Exceptions, try-with-resources, collections |
| Stream API | Да | Модуль 8 | Collections, generics, lambda |
| Lambda | Да | Модуль 8 | Interfaces, generics |
| SQL | Да | Модуль 9 | Classes, collections, basic repositories |
| JDBC | Да | Модуль 9 | SQL, exceptions, try-with-resources, Maven/Gradle |
| Многопоточность | Да, базово | Модуль 10 | Interfaces, lambdas, mutable state, collections |

## 6. Итоговая программа курса

### Модуль 1. Переход в Core

- Лекция 1. Повтор Base без повторения Base
- Лекция 2. Полная карта примитивов Java
- Лекция 3. Числовые преобразования и переполнение
- Лекция 4. Пакеты и структура исходников
- Лекция 5. Git для учебного и рабочего процесса
- Практика: расчет доставки с корректным выбором типов
- Мини-проект: `core-start-calculator`

### Модуль 2. Инкапсуляция и конструкторы

- Лекция 1. Зачем скрывать поля
- Лекция 2. Getters/setters без автоматизма
- Лекция 3. Конструкторы
- Лекция 4. `this` и перегрузка конструкторов
- Лекция 5. `static`, `final`, константы
- Лекция 6. Композиция объектов
- Практика: переписывание Base-классов в инкапсулированный стиль
- Мини-проект: доменная модель интернет-заказа

### Модуль 3. Объектные контракты и enum

- Лекция 1. Все классы как объекты
- Лекция 2. `toString` для диагностики
- Лекция 3. `equals`: сравнение состояния
- Лекция 4. `hashCode` и контракт с `equals`
- Лекция 5. `enum` для статусов и ролей
- Лекция 6. Объект как ключ и значение
- Практика: `OrderId`, `OrderStatus`, `Order`
- Мини-проект: каталог заказов в памяти

### Модуль 4. Сборка и тестирование

- Лекция 1. Зачем нужен build tool
- Лекция 2. Maven как основной путь
- Лекция 3. Gradle как второй стандарт
- Лекция 4. JUnit 5: первый тест
- Лекция 5. Тестирование ошибок
- Лекция 6. Parameterized tests и test data
- Лекция 7. Debugging тестов
- Практика: покрытие тестами каталога заказов
- Мини-проект: `order-core-tested`

### Модуль 5. Collections Framework и Generics

- Лекция 1. От `ArrayList` к `List`
- Лекция 2. `Set`: уникальность
- Лекция 3. `Map` как интерфейс
- Лекция 4. Iterator и безопасное удаление
- Лекция 5. Generics: зачем нужны `<T>`
- Лекция 6. Ограничения generics
- Лекция 7. `Comparable` и `Comparator`
- Практика: in-memory repository
- Мини-проект: `inventory-repository`

### Модуль 6. Исключения и Files API

- Лекция 1. Иерархия исключений
- Лекция 2. Выбор стандартного исключения
- Лекция 3. try-with-resources на практике
- Лекция 4. `Path` и `Files`
- Лекция 5. Текстовые форматы и CSV без магии
- Лекция 6. Кодировки
- Практика: импорт/экспорт товаров из CSV
- Мини-проект: `file-backed-inventory`

### Модуль 7. Наследование, полиморфизм и интерфейсы

- Лекция 1. Наследование без злоупотребления
- Лекция 2. `super` и конструкторы наследников
- Лекция 3. Overriding и `@Override`
- Лекция 4. Абстрактные классы
- Лекция 5. Интерфейсы
- Лекция 6. Custom exceptions как прикладное наследование
- Лекция 7. Полиморфизм в коллекциях
- Лекция 8. Композиция против наследования
- Практика: платежи и скидки через полиморфизм
- Мини-проект: стратегии скидок и доставки

### Модуль 8. Lambda и Stream API

- Лекция 1. Functional interfaces
- Лекция 2. Lambda syntax
- Лекция 3. Method references
- Лекция 4. Stream pipeline
- Лекция 5. Collectors
- Лекция 6. Optional базово
- Лекция 7. Цикл или stream
- Практика: аналитика заказов
- Мини-проект: `order-analytics`

### Модуль 9. SQL и JDBC

- Лекция 1. Реляционная модель
- Лекция 2. SQL SELECT
- Лекция 3. INSERT/UPDATE/DELETE
- Лекция 4. JOIN
- Лекция 5. JDBC подключение
- Лекция 6. `PreparedStatement`
- Лекция 7. `ResultSet` -> object mapping
- Лекция 8. DAO/Repository
- Лекция 9. Transactions базово
- Практика: JDBC repository
- Мини-проект: `jdbc-order-storage`

### Модуль 10. Базовая многопоточность

- Лекция 1. Зачем нужны потоки
- Лекция 2. `Thread` и `Runnable`
- Лекция 3. `ExecutorService`
- Лекция 4. `Callable` и `Future`
- Лекция 5. Race condition
- Лекция 6. `synchronized` и immutability
- Лекция 7. Concurrent collections обзорно
- Практика: параллельная обработка файлов
- Мини-проект: `parallel-log-counter`

### Модуль 11. Итоговый проект Java Core

- Лекция 1. От задачи к структуре приложения
- Лекция 2. CLI без хаоса
- Лекция 3. Repository choice
- Лекция 4. Тестовая стратегия
- Лекция 5. Git workflow
- Лекция 6. Code review checklist
- Практика: поэтапная разработка итогового приложения
- Мини-проект: `order-management-core`

## 7. Критический анализ программы

### Каких тем не хватает для Junior Java Developer

Для уровня Junior Java Developer после Core еще будут нужны темы, которые лучше вынести в следующий курс или отдельный блок:

- HTTP, REST, JSON как формат обмена;
- Spring Core / Spring Boot;
- ORM/JPA/Hibernate;
- Docker basics;
- логирование через SLF4J/Logback;
- основы Linux CLI шире, чем запуск Java;
- базовая безопасность web/API;
- работа с внешними API;
- миграции БД;
- интеграционное тестирование web-приложений.

Эти темы не стоит насильно добавлять в Core: отчет показывает, что студент только выходит из Base, и Core уже содержит большой переход к коммерческой Java.

### Какие темы перегружают Core и могут быть перенесены в Advanced

- Глубокая многопоточность: memory model, volatile, locks, atomics, completable futures глубоко.
- Глубокие generics: recursive bounds, wildcard capture, type erasure в деталях.
- Продвинутые Stream API collectors и parallel streams.
- NIO глубоко: channels, buffers, async IO.
- Gradle глубоко: custom tasks/plugins.
- SQL глубоко: индексы, планы запросов, нормализация подробно, транзакционные уровни изоляции.
- Архитектурные паттерны за пределами service/repository.

### Какие темы лучше убрать из Core

Не убрать полностью, а ограничить:

- Многопоточность оставить базовой, без глубоких concurrency-механизмов.
- Gradle дать как практическую ориентацию, не как второй полноценный build tool наравне с Maven.
- Wildcards (`? extends`, `? super`) лучше перенести в Advanced или дать как optional после наследования и generics; в основном Core-потоке они не нужны для первых коммерческих задач.
- `Optional` дать как API-результат поиска, не как повсеместную замену `null`.

### Какие темы стоит добавить

На основе пробелов отчета полезно добавить:

- packages и структура проекта, потому что Base этого не закрепил;
- code style и readable code checklist;
- README и запуск проекта по инструкции;
- простое логирование можно дать ближе к итоговому проекту, но без обязательного глубокого модуля;
- регулярные выражения как короткий optional-блок после строк или файлов, если задачи Core используют parsing сложнее CSV.

## 8. Дорожная карта Base -> Core -> Advanced

```text
Java Base
↓
Java Core
↓
Java Advanced
```

### Java Base: граница ответственности

Base отвечает за вход в программирование и базовый Java-синтаксис:

- `main`, вывод, переменные;
- 4 примитива `int`, `double`, `boolean`, `char` и `String`;
- методы, условия, циклы;
- массивы и строки;
- базовый ввод и базовые исключения;
- прикладные `ArrayList` и `HashMap`;
- простые классы, объекты, поля, методы, ссылки и `null`;
- базовый Debugger и stack trace.

Base не обязан готовить к коммерческому проекту. Он готовит студента к тому, чтобы Core мог вводить проектную Java без провала в синтаксисе.

### Java Core: граница ответственности

Core отвечает за превращение студента Base в кандидата на Junior Java Developer без фреймворков:

- полная система примитивов и преобразования типов;
- Git basics;
- packages и структура проекта;
- инкапсуляция, конструкторы, объектные инварианты;
- `equals/hashCode`, `toString`, `enum`;
- Maven/Gradle basics и JUnit;
- Collections Framework и generics;
- Files API и практическая обработка исключений;
- наследование, полиморфизм, интерфейсы;
- lambda и Stream API;
- SQL и JDBC;
- базовая многопоточность;
- итоговое консольное приложение с тестами, сборкой, Git и хранением данных.

Core не должен скрывать фундамент за Spring или ORM. Его задача - сделать Java понятной и применимой.

### Java Advanced: граница ответственности

Advanced отвечает за промышленную backend-разработку:

- Spring Core, Spring Boot, Spring MVC;
- REST API, JSON, validation;
- JPA/Hibernate, transactions deeper;
- security basics;
- Docker и окружение;
- logging/monitoring basics;
- integration tests;
- advanced concurrency;
- advanced SQL/performance;
- CI/CD basics;
- проектная архитектура и командная разработка.

Advanced должен начинаться только после того, как студент умеет писать и тестировать обычное Java-приложение без фреймворков.
