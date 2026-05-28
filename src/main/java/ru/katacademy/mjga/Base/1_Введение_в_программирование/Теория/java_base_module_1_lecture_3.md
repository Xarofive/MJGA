<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title></title>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif;">
<h1 style="text-align: center; color: #2c3e50; border-bottom: 3px solid #3498db; padding-bottom: 15px;">Java Base: Что такое Java и зачем она нужна</h1>

<p><strong>Java Base, Модуль 1, Лекция 3</strong></p>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #495057; margin-top: 0;">📌 TL;DR — Суть лекции</h4>

<ul>
	<li>Java — один из самых популярных языков программирования в мире.</li>
	<li>Java часто используют для backend-разработки, банковских систем, Android и enterprise-приложений.</li>
	<li>Главная идея Java: <strong>Write once — run anywhere</strong>.</li>
	<li>Java сочетает надёжность, производительность, строгую типизацию и большую экосистему.</li>
	<li>Сегодня разберём, зачем нужна Java и почему её продолжают использовать в крупных проектах.</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">Цели урока</h4>

<ul>
	<li>Понять, что такое Java.</li>
	<li>Узнать краткую историю Java.</li>
	<li>Разобрать ключевые особенности языка.</li>
	<li>Понять, где Java используется в реальной разработке.</li>
	<li>Познакомиться с экосистемой Java.</li>
</ul>
</div>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">Содержание</h4>

<ol>
	<li><a href="#what-is-java">Что такое Java</a></li>
	<li><a href="#history">История создания Java</a></li>
	<li><a href="#features">Ключевые особенности Java</a></li>
	<li><a href="#usage">Области применения Java</a></li>
	<li><a href="#ecosystem">Экосистема Java</a></li>
	<li><a href="#salary">Зарплаты Java-разработчиков</a></li>
	<li><a href="#philosophy">Философия Java</a></li>
	<li><a href="#self-check">Проверь себя</a></li>
	<li><a href="#whats-next">Что дальше?</a></li>
</ol>
</div>

<h2 id="what-is-java" style="color: #34495e; margin-top: 30px;">Что такое Java</h2>

<p><strong>Java</strong> — это язык программирования и платформа для создания приложений, которые могут работать на разных операционных системах.</p>

<p>На Java пишут программы, которые должны быть надёжными, понятными для команды и способными работать годами: backend-сервисы, банковские системы, enterprise-платформы, Android-приложения и высоконагруженные сервисы.</p>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">Простыми словами</h4>

<p>Java хорошо подходит для больших систем, где важны стабильность, строгие правила, поддержка команды и предсказуемое поведение программы.</p>
</div>

<h2 id="history" style="color: #34495e; margin-top: 30px;">История создания Java</h2>

<p>Java появилась в компании Sun Microsystems. Создатели хотели сделать язык переносимым, безопасным, надёжным и подходящим для больших систем.</p>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<ul>
	<li><strong>1995</strong> — официальный выпуск Java.</li>
	<li><strong>2000+</strong> — Java становится стандартом enterprise-разработки.</li>
	<li><strong>2010</strong> — Oracle покупает Sun Microsystems.</li>
	<li><strong>Сегодня</strong> — Java используется миллионами разработчиков и большим количеством компаний.</li>
</ul>
</div>

<h2 id="features" style="color: #34495e; margin-top: 30px;">Ключевые особенности Java</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">1. Платформонезависимость</h4>

<p>Java-код компилируется в bytecode, который запускается JVM. Поэтому одну и ту же программу можно запускать на Windows, Linux и macOS, если там установлена подходящая JVM.</p>
</div>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">2. Статическая типизация</h4>

<p>Java проверяет типы данных ещё до запуска программы. Это помогает находить часть ошибок заранее, на этапе компиляции.</p>
</div>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #495057; margin-top: 0;">3. Автоматическое управление памятью</h4>

<p>Java сама освобождает память, которая больше не нужна программе. За это отвечает сборщик мусора. Новичку пока достаточно знать: большую часть ручной работы с памятью Java берёт на себя.</p>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">4. Большая стандартная библиотека</h4>

<p>Стандартная библиотека — это набор готовых возможностей языка: работа со строками, коллекциями, файлами, датами, сетью и другими задачами.</p>
</div>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">5. Объектно-ориентированный подход</h4>

<p>В Java код часто организуют вокруг объектов и классов. Подробно это будет позже; сейчас достаточно понимать, что <code>class</code> — один из базовых строительных блоков Java-программы.</p>
</div>

<h2 id="usage" style="color: #34495e; margin-top: 30px;">Области применения Java</h2>

<p>Java широко используется для разработки:</p>

<ul>
	<li>backend-сервисов и API;</li>
	<li>банковских и платёжных систем;</li>
	<li>enterprise-приложений;</li>
	<li>Android-приложений;</li>
	<li>высоконагруженных сервисов;</li>
	<li>систем обработки данных;</li>
	<li>desktop-приложений.</li>
</ul>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<h4 style="margin-top: 0; color: #495057;">Примеры компаний и продуктов</h4>

<ul>
	<li>Amazon — backend и внутренние сервисы.</li>
	<li>Netflix — backend и распределённые системы.</li>
	<li>LinkedIn — высоконагруженные backend-сервисы.</li>
	<li>Банки — платёжные и финансовые системы.</li>
	<li>Minecraft Server — серверная часть игры.</li>
</ul>
</div>

<h2 id="ecosystem" style="color: #34495e; margin-top: 30px;">Экосистема Java</h2>

<p><strong>Экосистема</strong> — это всё, что окружает язык: библиотеки, фреймворки, инструменты, документация и сообщество.</p>

<ul>
	<li><strong>Spring Framework</strong> — популярный фреймворк для backend и enterprise-разработки.</li>
	<li><strong>Hibernate</strong> — инструмент для работы с базами данных.</li>
	<li><strong>Apache Kafka</strong> — платформа для потоковой обработки данных.</li>
	<li><strong>Maven и Gradle</strong> — системы сборки проектов. В этом модуле мы их не используем, они появятся позже.</li>
	<li><strong>IntelliJ IDEA</strong> — IDE, в которой удобно писать Java-код.</li>
</ul>

<h2 id="salary" style="color: #34495e; margin-top: 30px;">Зарплаты Java-разработчиков</h2>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">💰 Примерные зарплаты в России</h4>

<ul>
	<li><strong>Junior</strong> (начинающий): 80–150 тыс. руб.</li>
	<li><strong>Middle</strong> (опытный): 150–300 тыс. руб.</li>
	<li><strong>Senior</strong> (эксперт): 300–500+ тыс. руб.</li>
</ul>

<p style="font-size: 14px; color: #666;"><em>Данные примерные, зависят от города, компании, навыков и ситуации на рынке.</em></p>
</div>

<h2 id="philosophy" style="color: #34495e; margin-top: 30px;">Философия Java</h2>

<p>Java создавалась как практичный язык для больших и долгоживущих программ.</p>

<ol>
	<li><strong>Надёжность</strong> — лучше найти ошибку раньше, чем в работающей системе.</li>
	<li><strong>Переносимость</strong> — один и тот же код должен работать на разных платформах.</li>
	<li><strong>Читаемость</strong> — код должен быть понятен не только автору, но и команде.</li>
	<li><strong>Практичность</strong> — язык используется для реальных задач бизнеса.</li>
</ol>

<h2 id="self-check" style="color: #34495e; margin-top: 30px;">Проверь себя</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<ol>
	<li>Что такое Java?</li>
	<li>Почему Java называют платформонезависимой?</li>
	<li>Что такое JVM?</li>
	<li>Что такое стандартная библиотека?</li>
	<li>Где используется Java?</li>
	<li>Назовите 2 инструмента или фреймворка из Java-экосистемы.</li>
</ol>
</div>

<h2 id="whats-next" style="color: #34495e; margin-top: 30px;">Что дальше?</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p><strong>На следующем уроке мы разберём базовую структуру Java-программы.</strong></p>

<p>Вы увидите, зачем нужны <code>class</code>, <code>main()</code> и <code>System.out.println()</code>, а затем сможете писать первые простые программы самостоятельно.</p>
</div>
</div>
