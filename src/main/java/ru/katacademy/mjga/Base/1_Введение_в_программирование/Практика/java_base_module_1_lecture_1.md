<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title></title>
<div style="max-width: 900px; margin: 0 auto; padding: 20px;">
<h1 style="text-align: center; color: #2c3e50; border-bottom: 3px solid #3498db; padding-bottom: 15px;">Java Base: Введение в программирование на Java</h1>

<p><strong>Java Base, Модуль 1, Лекция 1</strong></p>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h3 style="color: #856404; margin-top: 0;">Добро пожаловать в Java Base!</h3>

<p>Сегодня вы сделаете первый шаг в программировании на Java: разберётесь, что такое программа, как Java-код превращается в исполняемую программу и какие инструменты нужны разработчику.</p>

<p><strong>Эта лекция — входная точка в курс. Здесь мы не углубляемся в сложный синтаксис, а собираем базовую картину: зачем нужна Java, как она работает и что будет дальше.</strong></p>
</div>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #495057; margin-top: 0;">📌 TL;DR — Суть лекции</h4>

<ul>
	<li>Программирование — это создание точных инструкций для компьютера.</li>
	<li>Java — один из самых популярных языков для backend и enterprise-разработки.</li>
	<li>Java-программа сначала компилируется в <code>bytecode</code>, затем запускается внутри JVM.</li>
	<li>Для разработки нужен JDK и среда разработки IntelliJ IDEA.</li>
	<li>Сегодня вы подготовитесь к созданию и запуску первой Java-программы.</li>
</ul>
</div>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h3 style="color: #6a1b9a; margin-top: 0;">🎧 Аудиообъяснение темы</h3>

<p>Для лучшего понимания основ программирования и Java прослушайте аудиоподкаст:</p>

<p style="margin: 20px 0;"><a href="#" style="display: inline-block; background: #6a1b9a; color: white; padding: 12px 24px; text-decoration: none; border-radius: 5px; font-weight: bold;" target="_blank">🎧 Прослушать введение в Java и программирование</a></p>

<p style="font-size: 14px; color: #666;"><em>Откроется в новой вкладке. Рекомендуется прослушать перед изучением материала для общего понимания или после — для закрепления.</em></p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎯 Что вы узнаете</h4>

<ul>
	<li>Что такое программирование</li>
	<li>Как работает Java-программа</li>
	<li>Что такое JVM, JDK и bytecode</li>
	<li>Почему Java используют в backend и enterprise-разработке</li>
	<li>Как начать мыслить алгоритмами</li>
</ul>

<p><strong>К концу лекции вы будете понимать, как Java-код проходит путь от текста в редакторе до работающей программы.</strong></p>
</div>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">Содержание</h4>

<ol>
	<li><a href="#lesson-goals">Цели урока</a></li>
	<li><a href="#what-is-programming">Что такое программирование?</a></li>
	<li><a href="#how-java-works">Как работает Java</a></li>
	<li><a href="#jvm-jdk-bytecode">Что такое JVM, JDK и bytecode</a></li>
	<li><a href="#practice-instructions">Мини-практика: создаём инструкции</a></li>
	<li><a href="#programming-principles">Основные принципы программирования</a></li>
	<li><a href="#practice-algorithmic-thinking">Практика: алгоритмическое мышление</a></li>
	<li><a href="#why-java">Почему будем изучать Java</a></li>
	<li><a href="#practice-java-projects">Практика: исследуем проекты на Java</a></li>
	<li><a href="#glossary">Мини-словарь</a></li>
	<li><a href="#self-check">Проверь себя</a></li>
	<li><a href="#whats-next">Что дальше?</a></li>
</ol>
</div>

<h2 id="lesson-goals" style="color: #34495e; margin-top: 30px;">Цели урока</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<ul>
	<li>Понять, что такое программирование.</li>
	<li>Узнать, как работает Java-программа.</li>
	<li>Познакомиться с платформой Java.</li>
	<li>Подготовить окружение для разработки.</li>
	<li>Создать первую Java-программу.</li>
</ul>
</div>

<h2 id="what-is-programming" style="color: #34495e; margin-top: 30px;">Что такое программирование?</h2>

<p><strong>Программирование</strong> — это процесс создания компьютерных программ, которые решают конкретные задачи.</p>

<p><strong>Программа</strong> — это набор инструкций, которые компьютер выполняет шаг за шагом.</p>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">Аналогия: приготовление чая 🍵</h4>

<p>Если вы объясняете человеку, как приготовить чай, вы даёте последовательность действий:</p>

<ol>
	<li>Налить воду.</li>
	<li>Вскипятить чайник.</li>
	<li>Положить чай в кружку.</li>
	<li>Залить кипятком.</li>
</ol>

<p>Компьютер работает похожим образом — только инструкции записываются на языке программирования.</p>
</div>

<h2 id="how-java-works" style="color: #34495e; margin-top: 30px;">Как работает Java</h2>

<p>Java-программа проходит несколько этапов перед запуском:</p>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<h4 style="margin-top: 0; color: #495057;">Java в 4 шагах:</h4>

<ol>
	<li>Разработчик пишет код на Java.</li>
	<li>Java-компилятор <code>javac</code> переводит код в <code>bytecode</code>.</li>
	<li>JVM загружает <code>bytecode</code>.</li>
	<li>Программа выполняется на компьютере.</li>
</ol>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
Java-код (.java)
        ↓ javac
Bytecode (.class)
        ↓ JVM
Работающая программа</pre>
</div>

<h2 id="jvm-jdk-bytecode" style="color: #34495e; margin-top: 30px;">Что такое JVM, JDK и bytecode</h2>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">JVM — Java Virtual Machine</h4>

<p><strong>JVM</strong> — это специальная виртуальная машина, которая запускает Java-программы.</p>

<p>Главная идея Java:</p>

<p style="background: #f8f9fa; border-left: 4px solid #00695c; padding: 15px; margin: 15px 0;"><strong>Write once — run anywhere.</strong></p>

<p>Java-код может запускаться на Windows, Linux и macOS без переписывания программы.</p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">JDK — Java Development Kit</h4>

<p><strong>JDK</strong> — это набор инструментов для Java-разработки.</p>

<p>В него входят:</p>

<ul>
	<li>компилятор <code>javac</code>;</li>
	<li>JVM;</li>
	<li>стандартные библиотеки Java;</li>
	<li>инструменты для разработки.</li>
</ul>
</div>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #495057; margin-top: 0;">Bytecode</h4>

<p><strong>Bytecode</strong> — это промежуточный код, который создаётся после компиляции Java-программы.</p>

<p>Именно bytecode запускается внутри JVM.</p>
</div>

<h2 id="practice-instructions" style="color: #34495e; margin-top: 30px;">Мини-практика: создаём инструкции</h2>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">P.S.</h4>

<p>Вся практика в этой лекции выполняется самостоятельно для самопроверки. Ментором не проверяется.</p>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">🧪 Практика #1</h4>

<p><strong>Базовый уровень</strong></p>
<p>Запишите пошаговые инструкции:</p>

<ul>
	<li>как приготовить кофе;</li>
	<li>как включить компьютер;</li>
	<li>как отправить сообщение в Telegram.</li>
</ul>

<p><strong>Средний уровень</strong></p>
<p>Напишите алгоритм вычисления среднего значения трёх чисел.</p>

<p><strong>Продвинутый уровень</strong></p>
<p>Придумайте алгоритм поиска максимального числа среди трёх значений.</p>

<p>Проверьте:</p>

<ul>
	<li>достаточно ли точные шаги;</li>
	<li>сможет ли другой человек выполнить инструкции без дополнительных вопросов.</li>
</ul>
</div>

<h2 id="programming-principles" style="color: #34495e; margin-top: 30px;">Основные принципы программирования</h2>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<ul>
	<li><strong>Алгоритмическое мышление</strong> — разбивайте сложное на простые шаги.</li>
	<li><strong>Точность</strong> — компьютер выполняет буквально то, что написано.</li>
	<li><strong>Логика</strong> — условия, ветвления и повторения управляют программой.</li>
	<li><strong>Повторное использование</strong> — хороший код удобно применять повторно.</li>
</ul>
</div>

<h2 id="practice-algorithmic-thinking" style="color: #34495e; margin-top: 30px;">Практика: алгоритмическое мышление</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">🧪 Практика #2</h4>

<p><strong>Задание:</strong> разбейте задачу «Собрать компьютер для работы» на шаги.</p>

<p>Пример:</p>

<ol>
	<li>Подготовить комплектующие.</li>
	<li>Установить процессор.</li>
	<li>Установить оперативную память.</li>
	<li>Подключить накопитель.</li>
	<li>Установить операционную систему.</li>
</ol>

<p>После этого:</p>

<ul>
	<li>разбейте каждый пункт на подшаги;</li>
	<li>проверьте точность инструкций.</li>
</ul>
</div>

<h2 id="why-java" style="color: #34495e; margin-top: 30px;">Почему будем изучать Java</h2>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">🔗 Java в реальной разработке</h4>

<ul>
	<li>Java используется в enterprise-разработке.</li>
	<li>Подходит для backend и высоконагруженных систем.</li>
	<li>Имеет огромную экосистему библиотек и инструментов.</li>
	<li>Используется в банках, маркетплейсах и крупных IT-компаниях.</li>
	<li>Java-разработчики востребованы на рынке.</li>
</ul>
</div>

<h2 id="practice-java-projects" style="color: #34495e; margin-top: 30px;">Практика: исследуем проекты на Java</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">🧪 Практика #3</h4>

<p>Посмотрите известные проекты и платформы на Java:</p>

<ul>
	<li>Spring Framework</li>
	<li>IntelliJ IDEA</li>
	<li>Elasticsearch</li>
	<li>Jenkins</li>
	<li>Apache Kafka</li>
	<li>Minecraft Server</li>
	<li>Hibernate</li>
</ul>

<p><strong>Задание:</strong> выберите 1–2 проекта и кратко опишите:</p>

<ul>
	<li>зачем там используется Java;</li>
	<li>какие задачи решает этот проект.</li>
</ul>
</div>

<h2 id="glossary" style="color: #34495e; margin-top: 30px;">Мини-словарь</h2>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #e3f2fd;">
			<th style="padding: 10px; border: 1px solid #ddd; text-align: left;">Термин</th>
			<th style="padding: 10px; border: 1px solid #ddd; text-align: left;">Описание</th>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><strong>Алгоритм</strong></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Последовательность шагов для решения задачи.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><strong>Программа</strong></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Алгоритм, записанный на языке программирования.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><strong>Компилятор</strong></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Переводит код в bytecode.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><strong>JVM</strong></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Виртуальная машина для запуска Java.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><strong>Переменная</strong></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Место хранения данных.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><strong>Отладка</strong></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Поиск и исправление ошибок.</td>
		</tr>
	</tbody>
</table>
</div>

<h2 id="self-check" style="color: #34495e; margin-top: 30px;">Проверь себя</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">🧪 Вопросы для самопроверки</h4>

<ol>
	<li>Что такое программа?</li>
	<li>Что делает JVM?</li>
	<li>Для чего нужен JDK?</li>
	<li>Что такое bytecode?</li>
	<li>Почему Java называют платформонезависимым языком?</li>
	<li>Назовите 2 известных проекта на Java.</li>
</ol>
</div>

<div style="background: #d4edda; border: 1px solid #c3e6cb; border-radius: 8px; padding: 15px; margin: 30px 0;">
<h3 style="color: #155724; margin-top: 0;">Чек-лист: Что вы теперь понимаете? 🚀</h3>

<ul>
	<li>☐ Понимаю, что такое программирование</li>
	<li>☐ Могу объяснить, что такое программа</li>
	<li>☐ Понимаю разницу между Java-кодом и bytecode</li>
	<li>☐ Знаю, зачем нужна JVM</li>
	<li>☐ Знаю, зачем нужен JDK</li>
	<li>☐ Могу привести примеры проектов, где используется Java</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 id="whats-next" style="color: #1565c0; margin-top: 0;">Что дальше? 🚀</h4>

<p><strong>В следующем уроке мы подготовим рабочее окружение и запустим первую Java-программу.</strong></p>

<p>Вы узнаете:</p>

<ul>
	<li>✅ как установить JDK 21;</li>
	<li>✅ как настроить Java в системе;</li>
	<li>✅ как установить IntelliJ IDEA;</li>
	<li>✅ как создать первый Java-проект;</li>
	<li>✅ как запустить программу <code>Hello, world!</code>.</li>
</ul>

<p style="background: #f8f9fa; border-left: 4px solid #1565c0; padding: 15px; margin: 15px 0;"><strong>🎯 К концу следующей лекции:</strong> у вас будет установлен JDK 21, настроена IntelliJ IDEA и запущена первая Java-программа.</p>
</div>
</div>
