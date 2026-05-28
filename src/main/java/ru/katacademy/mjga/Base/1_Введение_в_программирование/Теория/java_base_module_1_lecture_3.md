<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title></title>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif;">
<h1 style="text-align: center; color: #2c3e50; border-bottom: 3px solid #3498db; padding-bottom: 15px;">Java Base: Что такое Java и зачем она нужна</h1>

<p><strong>Java Base, Модуль 1, Лекция 3</strong></p>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h3 style="color: #856404; margin-top: 0;">Перед стартом</h3>

<p>В прошлой лекции вы подготовили окружение: установили JDK, настроили IntelliJ IDEA и запустили первую программу.</p>

<p><strong>Сегодня разберём, что такое Java, почему её используют в крупных системах и как выглядит первая полноценная Java-программа.</strong></p>
</div>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #495057; margin-top: 0;">📌 TL;DR — Суть лекции</h4>

<ul>
	<li>Java — один из самых популярных языков программирования в мире.</li>
	<li>Java используется для backend-разработки, банковских систем, Android и enterprise-приложений.</li>
	<li>Главная идея Java: <strong>Write once — run anywhere.</strong></li>
	<li>Java сочетает производительность, надёжность, огромную экосистему и востребованность на рынке.</li>
	<li>Сегодня познакомимся с Java и напишем первую полноценную программу.</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎯 Что вы узнаете</h4>

<ul>
	<li>Что такое Java простыми словами.</li>
	<li>Почему Java стоит изучать начинающему backend-разработчику.</li>
	<li>Где Java используется в реальных проектах.</li>
	<li>Как выглядит программа <code>Hello, world!</code>.</li>
	<li>Что делают <code>class</code>, <code>main()</code> и <code>System.out.println()</code>.</li>
	<li>Почему Java называют платформонезависимым языком.</li>
</ul>
</div>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">Содержание</h4>

<ol>
	<li><a href="#what-is-java">Что такое Java простыми словами</a></li>
	<li><a href="#why-java">Почему стоит изучать Java</a></li>
	<li><a href="#where-java-used">Где используется Java</a></li>
	<li><a href="#first-program">Ваша первая программа на Java</a></li>
	<li><a href="#history">Немного истории</a></li>
	<li><a href="#how-java-works">Как работает Java</a></li>
	<li><a href="#practice">Практика: исследуем мир Java</a></li>
	<li><a href="#self-check">Проверь себя</a></li>
	<li><a href="#whats-next">Что дальше?</a></li>
</ol>
</div>

<h2 id="what-is-java" style="color: #34495e; margin-top: 30px;">Что такое Java простыми словами</h2>

<p><strong>Java</strong> — это язык программирования, созданный для разработки надёжных и долгоживущих приложений.</p>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<h4 style="margin-top: 0; color: #495057;">На Java разрабатывают:</h4>

<ul>
	<li>серверные приложения;</li>
	<li>банковские системы;</li>
	<li>мобильные приложения;</li>
	<li>enterprise-платформы;</li>
	<li>высоконагруженные сервисы.</li>
</ul>
</div>

<p>На Java пишут программы, которые обрабатывают миллионы запросов, работают 24/7 и используются в крупных компаниях по всему миру.</p>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">🤔 Представьте Java как конструктор для больших систем</h4>

<ul>
	<li><strong>Готовые инструменты</strong> — большая стандартная библиотека.</li>
	<li><strong>Подходит для крупных проектов</strong> — Java часто используют в масштабируемых системах.</li>
	<li><strong>Надёжность</strong> — строгая типизация помогает находить ошибки раньше.</li>
	<li><strong>Платформонезависимость</strong> — программы могут работать на разных ОС.</li>
	<li><strong>Экосистема</strong> — вокруг Java есть тысячи библиотек, фреймворков и инструментов.</li>
</ul>
</div>

<h2 id="why-java" style="color: #34495e; margin-top: 30px;">Почему стоит изучать Java</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">👶 Хороший вход в backend</h4>

<p>Java — один из главных языков backend-разработки. На нём удобно изучать архитектуру, базы данных, многопоточность, сети и enterprise-разработку.</p>
</div>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">💼 Много вакансий</h4>

<p>Java используют банки, маркетплейсы, государственные сервисы, IT-компании и enterprise-сектор. Java-разработчики стабильно востребованы на рынке.</p>
</div>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #495057; margin-top: 0;">⚡ Производительность</h4>

<p>Java-приложения работают быстро и способны выдерживать высокие нагрузки. Поэтому Java часто используют в банковских системах, платёжных сервисах и backend крупных платформ.</p>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">🛠 Огромная экосистема</h4>

<p>В Java-экосистеме есть Spring Framework, Hibernate, Kafka, Maven, Gradle и тысячи библиотек. В этом модуле мы не углубляемся в эти инструменты, но важно понимать: вокруг Java уже построен большой промышленный мир.</p>
</div>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">💰 Зарплаты Java-разработчиков в России</h4>

<ul>
	<li><strong>Junior</strong> (начинающий): 80–150 тыс. руб.</li>
	<li><strong>Middle</strong> (опытный): 150–300 тыс. руб.</li>
	<li><strong>Senior</strong> (эксперт): 300–500+ тыс. руб.</li>
</ul>

<p style="font-size: 14px; color: #666;"><em>Данные примерные, зависят от города, компании, навыков и ситуации на рынке.</em></p>
</div>

<h2 id="where-java-used" style="color: #34495e; margin-top: 30px;">Где используется Java</h2>

<p>Java используют тысячи компаний по всему миру.</p>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<h4 style="margin-top: 0; color: #495057;">🌍 Известные компании и продукты на Java</h4>

<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #e3f2fd;">
			<th style="padding: 10px; border: 1px solid #ddd; text-align: left;">Компания / продукт</th>
			<th style="padding: 10px; border: 1px solid #ddd; text-align: left;">Где может использоваться Java</th>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;">Amazon</td>
			<td style="padding: 10px; border: 1px solid #ddd;">backend и внутренние сервисы.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;">Netflix</td>
			<td style="padding: 10px; border: 1px solid #ddd;">backend и распределённые системы.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;">LinkedIn</td>
			<td style="padding: 10px; border: 1px solid #ddd;">высоконагруженные backend-сервисы.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;">Uber</td>
			<td style="padding: 10px; border: 1px solid #ddd;">микросервисная архитектура.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;">Spotify</td>
			<td style="padding: 10px; border: 1px solid #ddd;">backend и обработка данных.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;">Банки</td>
			<td style="padding: 10px; border: 1px solid #ddd;">платёжные и финансовые системы.</td>
		</tr>
	</tbody>
</table>
</div>

<h2 id="first-program" style="color: #34495e; margin-top: 30px;">Ваша первая программа на Java</h2>

<p>В предыдущей лекции вы уже создавали проект и запускали <code>Hello, world!</code>. Сейчас мы вернёмся к этой программе и разберём, какие части в ней обязательны и зачем они нужны.</p>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">👋 Программа Hello, world!</h4>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
public class Main {

    public static void main(String[] args) {
        System.out.println("Hello, world!");
        System.out.println("Я изучаю Java!");
    }
}</pre>
</div>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<h4 style="margin-top: 0; color: #495057;">Что здесь происходит</h4>

<ul>
	<li><code>public class Main</code> — создаём класс, основу Java-программы.</li>
	<li><code>public static void main</code> — главная точка входа в программу. Именно отсюда JVM начинает выполнение.</li>
	<li><code>String[] args</code> — параметры запуска программы. Пока достаточно понимать так: Java оставляет здесь место для данных, которые можно передать программе при запуске из терминала.</li>
	<li><code>System.out.println</code> — вывод текста в консоль.</li>
</ul>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">Про <code>String[] args</code> без перегруза</h4>

<p>Сейчас не нужно глубоко разбирать массивы и параметры командной строки. Важно запомнить: сигнатуру <code>main(String[] args)</code> лучше писать точно так, потому что JVM ищет именно такой метод для старта программы.</p>
</div>

<p>Результат программы:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
Hello, world!
Я изучаю Java!</pre>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">🎯 Попробуйте прямо сейчас</h4>

<ul>
	<li>Измените текст в <code>println</code>.</li>
	<li>Запустите программу снова.</li>
	<li>Добавьте ещё одну строку вывода.</li>
	<li>Попробуйте специально допустить ошибку.</li>
	<li>Прочитайте сообщение об ошибке.</li>
</ul>
</div>

<h2 id="history" style="color: #34495e; margin-top: 30px;">Немного истории</h2>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">📅 Как появилась Java</h4>

<p>Java появилась в компании Sun Microsystems. Создатели хотели сделать язык переносимым, безопасным, надёжным и подходящим для больших систем.</p>
</div>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<h4 style="margin-top: 0; color: #495057;">Основные этапы</h4>

<ul>
	<li><strong>1995</strong> — официальный выпуск Java.</li>
	<li><strong>2000+</strong> — Java становится стандартом enterprise-разработки.</li>
	<li><strong>2010</strong> — Oracle покупает Sun Microsystems.</li>
	<li><strong>Сегодня</strong> — Java используется миллионами разработчиков.</li>
</ul>
</div>

<h2 id="how-java-works" style="color: #34495e; margin-top: 30px;">Как работает Java</h2>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">Процесс запуска Java-программы</h4>

<ol>
	<li>Разработчик пишет код.</li>
	<li><code>javac</code> компилирует код в bytecode.</li>
	<li>JVM запускает bytecode.</li>
	<li>Программа выполняется.</li>
</ol>
</div>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<h4 style="margin-top: 0; color: #495057;">Короткое повторение: почему Java платформонезависима</h4>

<p>Вы уже встречали эту идею раньше. Java-код компилируется не сразу в машинный код. Сначала создаётся bytecode, который запускает JVM на конкретной системе: Windows, Linux или macOS.</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
Java-код (.java)
        ↓ javac
Bytecode (.class)
        ↓ JVM
Работающая программа</pre>
</div>

<h2 id="practice" style="color: #34495e; margin-top: 30px;">Практика: исследуем мир Java</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">🌐 Задание 1 — быстрый обзор проектов</h4>

<p>Откройте 2–3 ссылки и посмотрите, какие задачи решают эти Java-проекты:</p>

<ul>
	<li><a href="https://spring.io/projects/spring-framework" target="_blank">Spring Framework</a> — backend и enterprise-приложения.</li>
	<li><a href="https://www.jetbrains.com/idea/" target="_blank">IntelliJ IDEA</a> — IDE для Java-разработки.</li>
	<li><a href="https://kafka.apache.org/" target="_blank">Apache Kafka</a> — обработка потоков данных.</li>
	<li><a href="https://www.minecraft.net/en-us/download/server" target="_blank">Minecraft Server</a> — серверная часть игры.</li>
</ul>

<p>Не нужно глубоко читать документацию. Достаточно открыть страницу, посмотреть описание и понять, к какой области относится проект.</p>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">🔍 Задание 2 — выберите один проект</h4>

<p>Выберите один проект из списка выше и ответьте на 3 вопроса:</p>

<ul>
	<li>Что делает этот проект?</li>
	<li>Где он может использоваться?</li>
	<li>Почему для такого проекта подходит Java?</li>
</ul>

<p>Ответ может быть коротким: 3–5 предложений.</p>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">💭 Задание 3 — подумать</h4>

<ul>
	<li>Почему Java так долго остаётся популярной?</li>
	<li>Где бы вы хотели использовать Java?</li>
	<li>Какую программу вы хотели бы создать?</li>
</ul>
</div>

<h2 id="self-check" style="color: #34495e; margin-top: 30px;">Проверь себя</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">🧪 Вопросы для самопроверки</h4>

<ol>
	<li>Что такое Java?</li>
	<li>Что делает JVM?</li>
	<li>Что такое bytecode?</li>
	<li>Для чего нужен метод <code>main()</code>?</li>
	<li>Почему Java называют платформонезависимой?</li>
	<li>Назовите 2 компании, использующие Java.</li>
</ol>
</div>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">Подсказки к ответам</h4>

<details>
	<summary>Что такое Java?</summary>
	<p>Java — язык программирования и платформа для создания приложений, которые могут запускаться на разных операционных системах через JVM.</p>
</details>

<details>
	<summary>Что делает JVM?</summary>
	<p>JVM запускает bytecode и выполняет Java-программу на конкретной операционной системе.</p>
</details>

<details>
	<summary>Что такое bytecode?</summary>
	<p>Bytecode — промежуточный код, который создаётся после компиляции Java-программы и запускается JVM.</p>
</details>

<details>
	<summary>Зачем нужен метод main()?</summary>
	<p><code>main()</code> — точка входа в программу. С него JVM начинает выполнение Java-приложения.</p>
</details>

<details>
	<summary>Почему Java называют платформонезависимой?</summary>
	<p>Java-программа компилируется в bytecode. Этот bytecode может запускаться JVM на разных операционных системах.</p>
</details>

<details>
	<summary>Какие компании используют Java?</summary>
	<p>Java используют банки, крупные backend-платформы и enterprise-компании. В качестве примеров можно назвать Amazon, Netflix, LinkedIn, Uber, Spotify и финансовые организации.</p>
</details>
</div>

<div style="background: #d4edda; border: 1px solid #c3e6cb; border-radius: 8px; padding: 15px; margin: 30px 0;">
<h3 style="color: #155724; margin-top: 0;">Чек-лист: что теперь понятно?</h3>

<ul>
	<li><label><input type="checkbox"> Понимаю, что такое Java</label></li>
	<li><label><input type="checkbox"> Могу назвать сферы применения Java</label></li>
	<li><label><input type="checkbox"> Понимаю идею Write once — run anywhere</label></li>
	<li><label><input type="checkbox"> Знаю, зачем нужна JVM</label></li>
	<li><label><input type="checkbox"> Понимаю, что такое bytecode</label></li>
	<li><label><input type="checkbox"> Могу объяснить роль метода main()</label></li>
</ul>
</div>

<h2 id="whats-next" style="color: #34495e; margin-top: 30px;">Что дальше?</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p><strong>В следующей лекции мы разберём структуру Java-программы подробнее.</strong></p>

<p>Вы узнаете:</p>

<ul>
	<li>как программа похожа на рецепт;</li>
	<li>из каких обязательных частей состоит Java-программа;</li>
	<li>почему <code>class</code> — основа Java-программы;</li>
	<li>почему метод <code>main()</code> — точка входа;</li>
	<li>как <code>System.out.println()</code> выводит текст;</li>
	<li>как запускать программу через IntelliJ IDEA и терминал;</li>
	<li>какие частые ошибки возникают у новичков.</li>
</ul>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 30px 0;">
<h3 style="color: #856404; margin-top: 0;">💡 Главное, что нужно запомнить</h3>

<p><strong>Java — это язык для создания надёжных, масштабируемых и долгоживущих систем.</strong></p>
</div>
</div>
