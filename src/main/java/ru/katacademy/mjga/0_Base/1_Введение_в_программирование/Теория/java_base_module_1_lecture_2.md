<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title></title>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif;">
<h1 style="text-align: center; color: #2c3e50; border-bottom: 3px solid #3498db; padding-bottom: 15px;">Java Base: Установка Java и настройка окружения</h1>

<p><strong>Java Base, Модуль 1, Лекция 2</strong></p>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h3 style="color: #856404; margin-top: 0;">Перед стартом</h3>

<p>Сегодня вы подготовите рабочее окружение для Java-разработки: установите JDK 21, настроите IntelliJ IDEA Community и запустите первую программу.</p>

<p><strong>Эта лекция — пошаговая инструкция. Не нужно запоминать всё сразу: просто выполняйте шаги для вашей операционной системы.</strong></p>

<p><strong>Важно:</strong> в этой лекции не используем Maven и Gradle. Сначала разберёмся с Java, файлами <code>.java</code>, методом <code>main</code> и запуском программы.</p>
</div>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #495057; margin-top: 0;">📌 TL;DR — что сделаем</h4>

<ul>
	<li>Установим JDK 21 LTS.</li>
	<li>Настроим Java в системе.</li>
	<li>Установим IntelliJ IDEA Community.</li>
	<li>Проверим Java через терминал.</li>
	<li>Создадим первый Java-проект.</li>
	<li>Запустим программу <code>Hello, world!</code>.</li>
</ul>

<p><strong>Цель лекции:</strong> за 20–30 минут получить рабочий результат: Java установлена, код написан, программа запускается.</p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎯 Что вы узнаете</h4>

<ul>
	<li>Зачем нужен JDK и чем он отличается от JVM.</li>
	<li>Как проверить Java через терминал.</li>
	<li>Что такое IntelliJ IDEA и зачем нужна IDE.</li>
	<li>Как создать первый Java-проект без Maven и Gradle.</li>
	<li>Как запустить программу <code>Hello, world!</code>.</li>
	<li>Какие ошибки чаще всего возникают у новичков.</li>
</ul>

<p><strong>К концу лекции у вас будет готовое окружение для дальнейшего изучения Java.</strong></p>
</div>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">Содержание</h4>

<ol>
	<li><a href="#lesson-goals">Цели урока</a></li>
	<li><a href="#why-environment">Зачем нужно окружение разработчика</a></li>
	<li><a href="#jdk-jvm">Что такое JDK и JVM</a></li>
	<li><a href="#windows-install">Установка JDK 21 на Windows</a></li>
	<li><a href="#linux-install">Установка JDK 21 на Linux (Ubuntu)</a></li>
	<li><a href="#macos-install">Установка JDK 21 на macOS</a></li>
	<li><a href="#check-java">Проверка установки Java</a></li>
	<li><a href="#idea">Что такое IntelliJ IDEA</a></li>
	<li><a href="#idea-install">Установка IntelliJ IDEA Community</a></li>
	<li><a href="#first-project">Создание первого Java-проекта</a></li>
	<li><a href="#hello-world">Первая программа на Java</a></li>
	<li><a href="#mini-practice">Mini Practice</a></li>
	<li><a href="#production-task">Production-Style Task</a></li>
	<li><a href="#faq">FAQ и типичные ошибки</a></li>
	<li><a href="#links">Полезные ссылки</a></li>
	<li><a href="#results">Итоги</a></li>
	<li><a href="#self-check">Проверь себя</a></li>
	<li><a href="#whats-next">Что дальше?</a></li>
</ol>
</div>

<h2 id="lesson-goals" style="color: #34495e; margin-top: 30px;">Цели урока</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<ul>
	<li>Установить JDK 21 LTS.</li>
	<li>Понять разницу между JDK, JVM и <code>javac</code>.</li>
	<li>Проверить Java через терминал.</li>
	<li>Установить IntelliJ IDEA Community.</li>
	<li>Создать и запустить первый Java-проект.</li>
</ul>
</div>

<h2 id="why-environment" style="color: #34495e; margin-top: 30px;">Зачем нужно окружение разработчика</h2>

<p>Перед тем как писать код, нужно подготовить инструменты. Java-разработка обычно включает JDK, IDE, терминал и системные переменные.</p>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<h4 style="margin-top: 0; color: #495057;">Без окружения Java-программы не смогут:</h4>

<ul>
	<li>компилироваться;</li>
	<li>запускаться;</li>
	<li>корректно открываться в IDE;</li>
	<li>использовать нужную версию Java.</li>
</ul>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">Важно для новичков</h4>

<p>В этой лекции не будет Maven, Gradle, зависимостей, plugins, repositories и lifecycle. Эти инструменты появятся позже, когда вы уже будете понимать, что такое файл, класс, компиляция и запуск программы.</p>
</div>

<h2 id="jdk-jvm" style="color: #34495e; margin-top: 30px;">Что такое JDK и JVM</h2>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">JVM — Java Virtual Machine</h4>

<p><strong>JVM</strong> — это виртуальная машина, которая запускает Java-программы.</p>

<p>Именно JVM помогает Java-коду работать на разных операционных системах: Windows, Linux и macOS.</p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">JDK — Java Development Kit</h4>

<p><strong>JDK</strong> — это набор инструментов для разработки на Java.</p>

<p>В него входят:</p>

<ul>
	<li>JVM;</li>
	<li>компилятор <code>javac</code>;</li>
	<li>стандартные библиотеки Java;</li>
	<li>инструменты разработки.</li>
</ul>
</div>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #495057; margin-top: 0;">Коротко</h4>

<p><strong>JVM</strong> запускает Java-программы. <strong>JDK</strong> нужен разработчику, чтобы писать, компилировать и запускать Java-код.</p>
</div>

<h2 id="windows-install" style="color: #34495e; margin-top: 30px;">1) Установка JDK 21 на Windows</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">Шаги</h4>

<ol>
	<li>Скачайте <a href="https://download.oracle.com/java/21/latest/jdk-21_windows-x64_bin.exe" target="_blank">JDK 21 LTS для Windows: x64 Installer</a>.</li>
	<li>Запустите установщик.</li>
	<li>Оставьте настройки по умолчанию.</li>
	<li>Дождитесь завершения установки.</li>
	<li>Откройте PowerShell или CMD.</li>
</ol>

<p>Если после установки команды не работают, проверьте системные переменные:</p>

<ul>
	<li><code>JAVA_HOME</code> должен указывать на папку JDK, например <code>C:\Program Files\Java\jdk-21</code>;</li>
	<li>в <code>PATH</code> должен быть путь <code>%JAVA_HOME%\bin</code> или полный путь до папки <code>bin</code> внутри JDK.</li>
</ul>

<p>Проверьте установку:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
java -version
javac -version</pre>

<p>Ожидаемый результат:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
java version "21"
javac 21</pre>
</div>

<h2 id="linux-install" style="color: #34495e; margin-top: 30px;">2) Установка JDK 21 на Linux (Ubuntu)</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">Установка через apt</h4>

<p>Для Ubuntu сначала попробуйте установить JDK из стандартных пакетов:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
sudo apt update
sudo apt install openjdk-21-jdk -y</pre>

<p>Если пакет <code>openjdk-21-jdk</code> недоступен в вашей версии Ubuntu, используйте <a href="https://adoptium.net/temurin/releases/?version=21" target="_blank">Eclipse Temurin JDK 21</a> или обновите список доступных пакетов для вашей системы.</p>

<p>Проверка установки:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
java -version
javac -version</pre>
</div>

<h2 id="macos-install" style="color: #34495e; margin-top: 30px;">3) Установка JDK 21 на macOS</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">Установка через Homebrew</h4>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
brew install openjdk@21</pre>

<p>После установки Homebrew может показать команды для добавления Java в <code>PATH</code>. Выполните их, если <code>java -version</code> не видит JDK 21.</p>

<p>Частый вариант для macOS:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
echo 'export PATH="/opt/homebrew/opt/openjdk@21/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc</pre>

<p>Проверка установки:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
java -version
javac -version</pre>
</div>

<h2 id="check-java" style="color: #34495e; margin-top: 30px;">Проверка установки Java</h2>

<p>После установки важно проверить не только <code>java</code>, но и <code>javac</code>. Если <code>java</code> есть, а <code>javac</code> нет, часто это означает, что установлен не JDK или система не видит путь к нему.</p>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<h4 style="margin-top: 0; color: #495057;">Проверка переменной JAVA_HOME</h4>

<p>Linux и macOS:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
echo $JAVA_HOME</pre>

<p>Windows:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
echo %JAVA_HOME%</pre>

<p>Если команда ничего не выводит, это не всегда критично для IntelliJ IDEA, но для терминала и будущих инструментов лучше настроить <code>JAVA_HOME</code> сразу.</p>
</div>

<h2 id="idea" style="color: #34495e; margin-top: 30px;">Что такое IntelliJ IDEA</h2>

<p><strong>IntelliJ IDEA</strong> — одна из самых популярных IDE для Java-разработки.</p>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">IDE помогает:</h4>

<ul>
	<li>писать код быстрее;</li>
	<li>запускать программы;</li>
	<li>видеть ошибки до запуска;</li>
	<li>работать с проектами;</li>
	<li>читать структуру кода.</li>
</ul>

<p><strong>В курсе используем IntelliJ IDEA Community Edition.</strong></p>
</div>

<h2 id="idea-install" style="color: #34495e; margin-top: 30px;">4) Установка IntelliJ IDEA Community</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">Шаги</h4>

<ol>
	<li>Скачайте <a href="https://www.jetbrains.com/idea/download/" target="_blank">IntelliJ IDEA Community Edition</a>.</li>
	<li>Запустите установщик.</li>
	<li>Оставьте настройки по умолчанию.</li>
	<li>Разрешите создание ярлыков, если это удобно.</li>
	<li>Разрешите ассоциацию <code>.java</code> файлов, если установщик предлагает этот пункт.</li>
</ol>
</div>

<h2 id="first-project" style="color: #34495e; margin-top: 30px;">5) Создание первого Java-проекта</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">Создание проекта</h4>

<ol>
	<li>Откройте IntelliJ IDEA.</li>
	<li>Нажмите <strong>New Project</strong>.</li>
	<li>Выберите <strong>Java</strong>.</li>
	<li>Укажите <strong>JDK 21</strong>.</li>
	<li>Создайте проект без Maven и Gradle.</li>
	<li>Назовите проект, например <code>hello-java</code>.</li>
	<li>Создайте файл <code>Main.java</code> в папке <code>src</code>, если IntelliJ IDEA не создала его автоматически.</li>
</ol>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">Почему без Maven и Gradle?</h4>

<p><strong>Maven</strong> и <strong>Gradle</strong> — это системы сборки. Они помогают управлять зависимостями, запуском тестов, сборкой проекта и подключением внешних библиотек.</p>

<p>На первом шаге важно понять базовый путь: файл <code>.java</code> → компиляция → запуск. Системы сборки появятся позже, когда они будут решать понятную проблему: вручную управлять проектом и библиотеками станет неудобно.</p>
</div>

<h2 id="hello-world" style="color: #34495e; margin-top: 30px;">6) Первая программа на Java</h2>

<p>Создайте файл <code>Main.java</code> и добавьте код:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
public class Main {

    public static void main(String[] args) {
        System.out.println("Hello, world!");
    }
}</pre>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<h4 style="margin-top: 0; color: #495057;">Запуск программы</h4>

<ul>
	<li>Нажмите зелёную кнопку <strong>Run</strong>.</li>
	<li>Или используйте <strong>Shift + F10</strong>.</li>
	<li>Посмотрите результат в консоли.</li>
</ul>
</div>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">Что происходит при запуске</h4>

<ol>
	<li>Код компилируется в bytecode.</li>
	<li>JVM загружает программу.</li>
	<li>Программа выполняется.</li>
	<li>Результат выводится в консоль.</li>
</ol>
</div>

<h2 id="mini-practice" style="color: #34495e; margin-top: 30px;">Mini Practice</h2>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">P.S.</h4>

<p>Практика выполняется самостоятельно для самопроверки. Ментором не проверяется.</p>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">🧪 Проверяем окружение</h4>

<ul>
	<li>Измените текст внутри <code>println</code>.</li>
	<li>Запустите программу повторно.</li>
	<li>Специально допустите ошибку в коде.</li>
	<li>Прочитайте сообщение об ошибке.</li>
	<li>Верните код в рабочее состояние.</li>
</ul>
</div>

<h2 id="production-task" style="color: #34495e; margin-top: 30px;">Production-Style Task</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">Настройка окружения разработчика</h4>

<p>Представьте, что вы пришли в backend-команду. Ваша задача — подготовить рабочее место так, чтобы можно было сразу запускать Java-код.</p>

<p><strong>Сделайте:</strong></p>

<ul>
	<li>установите Java 21;</li>
	<li>настройте IntelliJ IDEA;</li>
	<li>создайте проект;</li>
	<li>убедитесь, что программа запускается без ошибок.</li>
</ul>

<p><strong>Дополнительно:</strong></p>

<ul>
	<li>проверьте версию Java через терминал;</li>
	<li>объясните разницу между JDK и JVM;</li>
	<li>научитесь читать ошибки запуска.</li>
</ul>
</div>

<h2 id="faq" style="color: #34495e; margin-top: 30px;">FAQ и типичные ошибки</h2>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 15px 0;">
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #e3f2fd;">
			<th style="padding: 10px; border: 1px solid #ddd; text-align: left;">Проблема</th>
			<th style="padding: 10px; border: 1px solid #ddd; text-align: left;">Что проверить</th>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><code>java is not recognized</code></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Java не добавлена в <code>PATH</code>. Проверьте путь к папке <code>bin</code> внутри JDK.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><code>javac not found</code></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Установлен не JDK или путь к JDK не настроен.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;">Проект не запускается</td>
			<td style="padding: 10px; border: 1px solid #ddd;">Проверьте выбранный SDK в IntelliJ IDEA.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><code>main method not found</code></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Проверьте сигнатуру <code>public static void main(String[] args)</code>.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><code>class not found</code></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Проверьте имя класса, имя файла и выбранную конфигурацию запуска.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;">Имя файла подчёркнуто красным</td>
			<td style="padding: 10px; border: 1px solid #ddd;">Если класс называется <code>public class Main</code>, файл должен называться <code>Main.java</code>.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><code>invalid source release: 21</code></td>
			<td style="padding: 10px; border: 1px solid #ddd;">В проекте выбрана старая версия SDK. Укажите JDK 21 в настройках проекта.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;">В терминале другая версия Java</td>
			<td style="padding: 10px; border: 1px solid #ddd;">В системе установлено несколько JDK. Проверьте <code>PATH</code> и <code>JAVA_HOME</code>.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;">IDEA не видит Java</td>
			<td style="padding: 10px; border: 1px solid #ddd;">Укажите путь до JDK вручную в настройках Project SDK.</td>
		</tr>
	</tbody>
</table>
</div>

<h2 id="links" style="color: #34495e; margin-top: 30px;">Полезные ссылки</h2>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #e3f2fd;">
			<th style="padding: 10px; border: 1px solid #ddd; text-align: left;">Ссылка</th>
			<th style="padding: 10px; border: 1px solid #ddd; text-align: left;">Зачем нужна</th>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><a href="https://adoptium.net/temurin/releases/?version=21" target="_blank">Eclipse Temurin JDK 21</a></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Удобный бесплатный JDK-дистрибутив. Хороший вариант для установки на учебный компьютер.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><a href="https://www.oracle.com/java/technologies/downloads/" target="_blank">Oracle JDK</a></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Официальные сборки JDK от Oracle. Можно использовать для курса, если выбрали Oracle JDK 21.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><a href="https://openjdk.org/projects/jdk/21/" target="_blank">OpenJDK 21</a></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Страница проекта OpenJDK 21. Это больше справочная страница о релизе, а не самый удобный установщик для новичка.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><a href="https://www.jetbrains.com/idea/download/" target="_blank">IntelliJ IDEA</a></td>
			<td style="padding: 10px; border: 1px solid #ddd;">IDE для Java-разработки. В курсе используем бесплатную Community Edition или доступную бесплатную сборку IntelliJ IDEA.</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #ddd;"><a href="https://docs.oracle.com/en/java/" target="_blank">Документация Java</a></td>
			<td style="padding: 10px; border: 1px solid #ddd;">Официальная документация. Пригодится позже, когда начнёте читать API и справочные материалы.</td>
		</tr>
	</tbody>
</table>

<p style="background: #f8f9fa; border-left: 4px solid #00695c; padding: 15px; margin: 15px 0;"><strong>Для курса достаточно одного JDK.</strong> Не устанавливайте сразу несколько разных сборок, если в этом нет необходимости: новичку сложнее понять, какую версию видит терминал и какую использует IntelliJ IDEA.</p>
</div>

<h2 id="results" style="color: #34495e; margin-top: 30px;">Итоги</h2>

<div style="background: #d4edda; border: 1px solid #c3e6cb; border-radius: 8px; padding: 15px; margin: 30px 0;">
<h3 style="color: #155724; margin-top: 0;">Чек-лист: окружение готово?</h3>

<ul>
	<li><label><input type="checkbox"> Установлен JDK 21</label></li>
	<li><label><input type="checkbox"> Команда <code>java -version</code> работает</label></li>
	<li><label><input type="checkbox"> Команда <code>javac -version</code> работает</label></li>
	<li><label><input type="checkbox"> Проверена переменная <code>JAVA_HOME</code></label></li>
	<li><label><input type="checkbox"> Установлена IntelliJ IDEA Community</label></li>
	<li><label><input type="checkbox"> Создан первый Java-проект</label></li>
	<li><label><input type="checkbox"> Запущена программа <code>Hello, world!</code></label></li>
	<li><label><input type="checkbox"> Понятна разница между JDK и JVM</label></li>
</ul>
</div>

<h2 id="self-check" style="color: #34495e; margin-top: 30px;">Проверь себя</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">🧪 Вопросы для самопроверки</h4>

<ol>
	<li>Что такое JVM?</li>
	<li>Для чего нужен JDK?</li>
	<li>Чем JDK отличается от JRE?</li>
	<li>Что делает <code>javac</code>?</li>
	<li>Что такое IntelliJ IDEA?</li>
	<li>Что происходит при запуске Java-программы?</li>
	<li>Почему в этой лекции не используем Maven и Gradle?</li>
</ol>
</div>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">Подсказки к ответам</h4>

<details>
	<summary>Что такое JVM?</summary>
	<p>JVM — виртуальная машина, которая запускает Java bytecode на конкретной операционной системе.</p>
</details>

<details>
	<summary>Для чего нужен JDK?</summary>
	<p>JDK нужен разработчику: в нём есть JVM, компилятор <code>javac</code>, стандартные библиотеки и инструменты разработки.</p>
</details>

<details>
	<summary>Что делает javac?</summary>
	<p><code>javac</code> компилирует Java-код из файла <code>.java</code> в bytecode, который затем запускает JVM.</p>
</details>

<details>
	<summary>Почему пока без Maven и Gradle?</summary>
	<p>Потому что сначала важно понять базу: файл, класс, метод <code>main</code>, компиляцию и запуск программы.</p>
</details>
</div>

<h2 id="whats-next" style="color: #34495e; margin-top: 30px;">Что дальше?</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p><strong>В следующем уроке мы разберём, из каких частей состоит Java-программа и как она запускается.</strong></p>

<p>Вы узнаете:</p>

<ul>
	<li>почему Java остаётся одним из самых популярных языков программирования;</li>
	<li>где Java используется: backend, банки, Android и enterprise-приложения;</li>
	<li>почему <code>class</code> — основа Java-программы;</li>
	<li>почему метод <code>main()</code> — точка входа в программу;</li>
	<li>как <code>System.out.println()</code> выводит текст в консоль;</li>
	<li>как запускать программу через IntelliJ IDEA и терминал;</li>
	<li>какие ошибки чаще всего возникают в первой Java-программе.</li>
</ul>

<p><strong>Главная идея следующей лекции:</strong> Java-программа похожа на рецепт: у неё есть структура, порядок выполнения и точка, с которой всё начинается.</p>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 30px 0;">
<h3 style="color: #856404; margin-top: 0;">💡 Запомните</h3>

<p><strong>Настроенное окружение — фундамент всей дальнейшей разработки. Если Java запускается и IntelliJ IDEA видит JDK 21, вы готовы писать код.</strong></p>
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
