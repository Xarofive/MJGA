<div style="max-width: 900px; margin: 0 auto; padding: 20px;">
<h1 style="text-align: center; color: rgb(173, 191, 210); border-bottom: 3px solid rgb(63, 150, 207); padding-bottom: 15px;">🔧 Основы Git для разработчика Go</h1>

<h2 style="color: rgb(173, 191, 210); margin-top: 30px;">📋 Содержание</h2>

<ul style="background: rgb(31, 31, 31); padding: 20px; border-radius: 5px;">
	<li><a href="#goals">Цели урока</a></li>
	<li><a href="#intro">Введение: что такое Git и зачем он нужен</a></li>
	<li><a href="#install">Установка и настройка Git</a></li>
	<li><a href="#concepts">Основные концепции Git</a></li>
	<li><a href="#commands">Базовые команды Git</a></li>
	<li><a href="#workflow">Рабочий процесс для выполнения заданий</a></li>
	<li><a href="#status">Проверка статуса заданий</a></li>
	<li><a href="#problems">Решение типичных проблем</a></li>
	<li><a href="#additional">Дополнительные команды</a></li>
	<li><a href="#resources">Дополнительные ресурсы</a></li>
</ul>

<div style="background: rgb(41, 41, 41); border: 2px solid rgb(76, 174, 79); border-radius: 8px; padding: 15px; margin: 20px 0px;">
<h3 style="color: rgb(162, 221, 165); margin-top: 0px;">Откуда мы пришли и куда идём</h3>

<p>Ты уже пишешь Go-код &mdash; теперь научимся сохранять его в Git и сдавать задания. Git нужен для каждой задачи курса.</p>
</div>

<h2 id="goals" style="color: rgb(173, 191, 210); margin-top: 30px;">🎯 Цели урока</h2>

<div style="background: rgb(41, 41, 41); border-left: 4px solid rgb(63, 150, 207); padding: 20px; margin: 20px 0px; border-radius: 5px;">
<p>После изучения этой лекции ты сможешь:</p>

<ul>
	<li>Понимать основные концепции системы контроля версий Git</li>
	<li>Настраивать Git для работы с нашей учебной платформой</li>
	<li>Выполнять базовые операции с репозиториями и ветками</li>
	<li>Следовать рабочему процессу для выполнения и сдачи заданий курса</li>
	<li>Решать типичные проблемы при работе с Git</li>
</ul>
</div>

<h2 id="intro" style="color: rgb(173, 191, 210); margin-top: 30px;">📝 Введение: что такое Git и зачем он нужен</h2>

<p>Git &mdash; это распределённая система контроля версий, которая помогает отслеживать изменения в коде, работать в команде и управлять разными версиями проекта. Git позволяет:</p>

<ul>
	<li>Хранить историю изменений кода</li>
	<li>Создавать параллельные версии проекта (ветки)</li>
	<li>Легко возвращаться к предыдущим версиям</li>
	<li>Синхронизировать код между разработчиками</li>
</ul>

<div style="background: rgb(33, 79, 44); border: 1px solid rgb(41, 97, 54); border-radius: 8px; padding: 20px; margin: 20px 0px;">
<h3 style="color: rgb(153, 229, 171); margin-top: 0px;">🎮 Интерактивное обучение Git</h3>

<p>Настоятельно рекомендуем пройти интерактивную игру-обучение Git, которая поможет визуально понять основные концепции:</p>

<p style="text-align: center; font-size: 18px;"><a href="https://learngitbranching.js.org/?locale=ru_RU" style="background: rgb(63, 150, 207); color: rgb(255, 255, 255); padding: 10px 20px; text-decoration: none; border-radius: 5px; display: inline-block;">🎮 Начать интерактивное обучение Git</a></p>

<p style="margin-top: 15px;">Эта игра покажет визуально как работают команды Git, что происходит с репозиторием при выполнении различных операций. Прохождение займет около 30-60 минут и значительно упростит понимание материала!</p>
</div>

<p>В нашем курсе Git используется для выполнения заданий, их автоматической проверки и получения обратной связи от менторов.</p>

<h2 id="install" style="color: rgb(173, 191, 210); margin-top: 30px;">🔧 Установка и настройка Git</h2>

<h3 style="color: rgb(153, 199, 229);">Установка Git</h3>

<div style="background: rgb(31, 31, 31); border: 1px solid rgb(43, 43, 43); border-radius: 8px; padding: 20px; margin: 15px 0px;">
<table style="width: 100%; border-collapse: collapse;">
	<thead>
		<tr style="background: rgb(43, 43, 43);">
			<th style="text-align: left; padding: 10px; border: 1px solid rgb(54, 54, 54);">Операционная система</th>
			<th style="text-align: left; padding: 10px; border: 1px solid rgb(54, 54, 54);">Инструкции</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);">Windows</td>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);">Скачайте и установите с <a href="https://git-scm.com/download/win">git-scm.com/download/win</a></td>
		</tr>
		<tr style="background: rgb(31, 31, 31);">
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);">macOS</td>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);">Используйте Homebrew: <code>brew install git</code> или скачайте с <a href="https://git-scm.com/download/mac">git-scm.com/download/mac</a></td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);">Linux (Ubuntu/Debian)</td>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);"><code>sudo apt-get update &amp;&amp; sudo apt-get install git</code></td>
		</tr>
		<tr style="background: rgb(31, 31, 31);">
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);">Linux (Fedora)</td>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);"><code>sudo dnf install git</code></td>
		</tr>
	</tbody>
</table>
</div>

<p>Проверьте установку, запустив команду:</p>

<div style="background: rgb(33, 33, 33); border: 1px solid rgb(77, 77, 77); border-radius: 4px; padding: 15px; margin: 15px 0px;">
<pre style="margin: 0; font-family: monospace;">
git --version</pre>
</div>

<h3 style="color: rgb(153, 199, 229);">Базовая настройка Git</h3>

<div style="background: rgb(102, 75, 0); border: 1px solid rgb(102, 75, 0); border-radius: 8px; padding: 20px; margin: 20px 0px;">
<h4 style="color: rgb(229, 210, 153); margin-top: 0px;">⚠️ ВАЖНО</h4>

<p style="margin-bottom: 0;">Email должен совпадать с тем, который вы указали на учебной платформе!</p>
</div>

<div style="background: rgb(33, 33, 33); border: 1px solid rgb(77, 77, 77); border-radius: 4px; padding: 15px; margin: 15px 0px;">
<pre style="margin: 0; font-family: monospace;">
# Установка вашего имени
git config --global user.name &quot;Ваше Имя&quot;

# Установка вашего email
git config --global user.email &quot;ваш.email@example.com&quot;

# Проверка настроек
git config --list</pre>
</div>

<h2 id="concepts" style="color: rgb(173, 191, 210); margin-top: 30px;">💡 Основные концепции Git</h2>

<div style="background: rgb(31, 31, 31); border: 1px solid rgb(43, 43, 43); border-radius: 8px; padding: 20px; margin: 15px 0px;">
<table style="width: 100%; border-collapse: collapse;">
	<thead>
		<tr style="background: rgb(43, 43, 43);">
			<th style="text-align: left; padding: 10px; border: 1px solid rgb(54, 54, 54);">Термин</th>
			<th style="text-align: left; padding: 10px; border: 1px solid rgb(54, 54, 54);">Описание</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);"><strong>Репозиторий</strong></td>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);">Место хранения кода и истории изменений</td>
		</tr>
		<tr style="background: rgb(31, 31, 31);">
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);"><strong>Коммит</strong></td>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);">Зафиксированное состояние кода с комментарием</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);"><strong>Ветка</strong></td>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);">Параллельная линия разработки</td>
		</tr>
		<tr style="background: rgb(31, 31, 31);">
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);"><strong>Рабочая директория</strong></td>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);">Место, где вы редактируете файлы</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);"><strong>Индекс (staging)</strong></td>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);">Промежуточная область между рабочей директорией и репозиторием</td>
		</tr>
		<tr style="background: rgb(31, 31, 31);">
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);"><strong>Удалённый репозиторий</strong></td>
			<td style="padding: 10px; border: 1px solid rgb(54, 54, 54);">Копия репозитория на сервере (например, в GitLab)</td>
		</tr>
	</tbody>
</table>
</div>

<div style="background: rgb(41, 41, 41); border-left: 4px solid rgb(63, 150, 207); padding: 20px; margin: 20px 0px; border-radius: 5px;">
<h4 style="color: rgb(153, 199, 229); margin-top: 0px;">📊 Рабочий процесс Git</h4>

<pre style="margin: 0; font-family: monospace; text-align: center;">
Рабочая директория &rarr; Индекс (staging) &rarr; Локальный репозиторий &rarr; Удаленный репозиторий
      (git add)         (git commit)           (git push)
</pre>
</div>

<h2 id="commands" style="color: rgb(173, 191, 210); margin-top: 30px;">⚡ Базовые команды Git</h2>

<div style="background: rgb(36, 36, 36); border: 1px solid rgb(135, 34, 34); border-radius: 8px; padding: 20px; margin: 20px 0px;">
<h3 style="color: rgb(229, 153, 153); margin-top: 0px;">🚨 Критически важно: Создание форка репозитория</h3>

<p><strong>Перед клонированием репозитория, необходимо создать его форк (копию) в вашем аккаунте:</strong></p>

<ol>
	<li>Перейдите по ссылке <a href="https://studentgit.kata.academy/kata-go/kata-go">https://studentgit.kata.academy/kata-go/kata-go</a></li>
	<li>Нажмите кнопку <strong>&quot;Fork&quot;</strong> в правом верхнем углу страницы</li>
	<li>Дождитесь создания форка репозитория в вашем аккаунте</li>
</ol>

<p style="margin-bottom: 0;"><strong>Без этого шага не удастся подключиться к репозиторию через консоль!</strong></p>
</div>

<h3 style="color: rgb(153, 199, 229);">Клонирование репозитория</h3>

<p>После создания форка вы можете клонировать репозиторий:</p>

<div style="background: rgb(33, 33, 33); border: 1px solid rgb(77, 77, 77); border-radius: 4px; padding: 15px; margin: 15px 0px;">
<pre style="margin: 0; font-family: monospace;">
# Клонирование репозитория
git clone https://studentgit.kata.academy/ваш_логин/kata-go.git

# Переход в директорию проекта
cd kata-go</pre>
</div>

<div style="background: rgb(41, 41, 41); border: 1px solid rgb(34, 89, 135); border-radius: 8px; padding: 15px; margin: 15px 0px;">
<p style="margin: 0;"><strong>HTTPS vs SSH:</strong> в GitLab есть два способа подключения. <strong>HTTPS</strong> (как в примере выше) проще настроить &mdash; Git будет запрашивать логин и пароль. <strong>SSH</strong> требует настройки ключей, но не запрашивает пароль при каждом push. Мы рекомендуем HTTPS для начала. Если хотите использовать SSH, следуйте <a href="https://docs.gitlab.com/ee/user/ssh.html">инструкции GitLab по настройке SSH-ключей</a>.</p>
</div>

<h3 style="color: rgb(153, 199, 229);">Файл .gitignore</h3>

<p>Файл <code>.gitignore</code> указывает Git, какие файлы и директории <strong>не нужно</strong> отслеживать. Без него в репозиторий могут попасть бинарники, файлы IDE и другие артефакты.</p>

<div style="background: rgb(33, 33, 33); border: 1px solid rgb(77, 77, 77); border-radius: 4px; padding: 15px; margin: 15px 0px;">
<pre style="margin: 0; font-family: monospace;">
# Бинарники Go
*.exe
*.out
/bin/

# IDE
.idea/
.vscode/

# Временные файлы
*.tmp
*.log</pre>
</div>

<p>Создайте <code>.gitignore</code> в корне репозитория до первого коммита. Это предотвратит случайное добавление ненужных файлов командой <code>git add .</code></p>

<h3 style="color: rgb(153, 199, 229);">Работа с ветками</h3>

<div style="background: rgb(102, 75, 0); border: 1px solid rgb(102, 75, 0); border-radius: 8px; padding: 15px; margin: 15px 0px;">
<p style="margin: 0;">Для каждого задания в нашем курсе нужно создать отдельную ветку с определенным именем!</p>
</div>

<div style="background: rgb(33, 33, 33); border: 1px solid rgb(77, 77, 77); border-radius: 4px; padding: 15px; margin: 15px 0px;">
<pre style="margin: 0; font-family: monospace;">
# Просмотр текущей ветки
git branch

# Создание новой ветки и переключение на неё
git switch -c task/имя-задачи

# Например, для задачи &quot;JSON Stats&quot;
git switch -c task/json-stats-lite

# Альтернативный вариант (старый синтаксис, работает так же):
# git checkout -b task/json-stats-lite</pre>
</div>

<p><strong>Флаг <code>-c</code></strong> означает &laquo;create&raquo; &mdash; создать новую ветку и сразу переключиться на неё. Без <code>-c</code> команда <code>git switch</code> переключается на уже существующую ветку.</p>

<h3 style="color: rgb(153, 199, 229);">Фиксация изменений</h3>

<div style="background: rgb(33, 33, 33); border: 1px solid rgb(77, 77, 77); border-radius: 4px; padding: 15px; margin: 15px 0px;">
<pre style="margin: 0; font-family: monospace;">
# Просмотр измененных файлов
git status

# Добавление файлов в индекс
git add .               # Добавить все изменения
git add путь/к/файлу    # Добавить конкретный файл

# Создание коммита
git commit -m &quot;feat: краткое описание изменений&quot;</pre>
</div>

<h3 style="color: rgb(153, 199, 229);">Отправка изменений на сервер</h3>

<div style="background: rgb(33, 33, 33); border: 1px solid rgb(77, 77, 77); border-radius: 4px; padding: 15px; margin: 15px 0px;">
<pre style="margin: 0; font-family: monospace;">
# Первая отправка новой ветки
git push -u origin task/имя-задачи

# Последующие отправки (после -u можно использовать просто)
git push</pre>
</div>

<h2 id="workflow" style="color: rgb(173, 191, 210); margin-top: 30px;">📋 Рабочий процесс для выполнения заданий</h2>

<div style="background: rgb(41, 41, 41); border-left: 4px solid rgb(63, 150, 207); padding: 20px; margin: 20px 0px; border-radius: 5px;">
<p>В нашем курсе используется следующий рабочий процесс:</p>

<ol>
	<li><strong>Создание форка</strong> основного репозитория (выполняется один раз в начале курса)</li>
	<li><strong>Клонирование репозитория</strong> (выполняется один раз в начале курса)</li>
	<li><strong>Создание ветки</strong> для конкретной задачи в формате <code>task/имя-задачи</code></li>
	<li><strong>Реализация решения</strong> в соответствии с требованиями задачи</li>
	<li><strong>Проверка</strong> работы решения локально</li>
	<li><strong>Коммит и пуш</strong> изменений в вашу ветку</li>
	<li><strong>Отправка ссылки</strong> на ветку для заданий с меткой &quot;mentor review&quot;</li>
</ol>
</div>

<h3 style="color: rgb(153, 199, 229);">Пример выполнения задания</h3>

<div style="background: rgb(31, 31, 31); border: 1px solid rgb(43, 43, 43); border-radius: 8px; padding: 20px; margin: 15px 0px;">
<h4 style="margin-top: 0px; color: rgb(186, 191, 197);">📋 Пошаговый пример для задания &quot;hello-world&quot;:</h4>

<pre style="margin: 0; font-family: monospace;">
# 1. Создаем ветку для задания &quot;hello-world&quot;
git switch -c task/hello-world

# 2. Создаем директорию и файлы, пишем код...

# 3. Проверяем локально
go run .
go test ./...

# 4. Фиксируем изменения
git add .
git commit -m &quot;feat: реализация задачи hello-world&quot;

# 5. Отправляем на сервер
git push -u origin task/hello-world

# 6. Для заданий с меткой &quot;mentor review&quot; - отправляем ссылку:
# https://studentgit.kata.academy/ваш_логин/kata-go/-/tree/task/hello-world
</pre>
</div>

<div style="background: rgb(33, 79, 44); border: 2px solid rgb(42, 167, 71); border-radius: 8px; padding: 20px; margin: 30px 0px; text-align: center;">
<h3 style="color: rgb(153, 229, 171); margin: 0px;">Минимум для сдачи первого задания &mdash; выше</h3>

<p style="margin: 10px 0px 0px; color: rgb(153, 229, 171);">Разделы ниже &mdash; расширенный материал. К ним можно вернуться позже, когда возникнет необходимость.</p>
</div>

<h2 id="status" style="color: rgb(173, 191, 210); margin-top: 30px;">✅ Проверка статуса заданий</h2>

<p><strong>CI/CD</strong> (Continuous Integration / Continuous Delivery) &mdash; автоматический запуск проверок (сборка, тесты) при каждом push в репозиторий. В нашем курсе CI запускает автотесты для вашего решения.</p>

<p>После отправки ветки, система автоматически запускает проверку вашего решения. Вы можете следить за ее статусом в разделе <strong>CI/CD &rarr; Pipelines</strong> на странице вашего проекта в GitLab.</p>

<div style="background: rgb(31, 31, 31); border: 1px solid rgb(43, 43, 43); border-radius: 8px; padding: 20px; margin: 15px 0px;">
<h3 style="color: rgb(186, 191, 197); margin-top: 0px;">📊 Индикаторы статуса проверки:</h3>

<ul style="list-style: none; padding-left: 0;">
	<li style="margin: 10px 0;"><strong style="color: rgb(153, 229, 171);">✅ Зеленая галочка (passed)</strong>: ваше решение успешно прошло все тесты</li>
	<li style="margin: 10px 0;"><strong style="color: rgb(229, 153, 161);">❌ Красный крестик (failed)</strong>: в решении есть ошибки, требуется исправление</li>
	<li style="margin: 10px 0;"><strong style="color: rgb(153, 190, 229);">🔄 Синий индикатор (running)</strong>: проверка в процессе</li>
</ul>
</div>

<div style="background: rgb(102, 75, 0); border: 1px solid rgb(102, 75, 0); border-radius: 8px; padding: 20px; margin: 20px 0px;">
<h4 style="color: rgb(229, 210, 153); margin-top: 0px;">Если проверка не прошла:</h4>

<ol>
	<li>Изучите журнал ошибок на странице Pipeline</li>
	<li>Внесите исправления в код</li>
	<li>Снова выполните коммит и отправьте изменения</li>
</ol>
</div>

<div style="background: rgb(36, 36, 36); border: 1px solid rgb(135, 34, 34); border-radius: 8px; padding: 20px; margin: 20px 0px;">
<h3 style="color: rgb(229, 153, 153); margin-top: 0px;">🚨 Важные файлы репозитория</h3>

<p><strong>ВАЖНО!</strong> В репозитории есть системные файлы, которые необходимы для корректной работы автоматической проверки заданий:</p>

<ul>
	<li><strong>.gitlab-ci.yml</strong> - файл конфигурации CI/CD, необходимый для запуска автоматических тестов. <strong>Не удаляйте этот файл</strong> даже если он кажется &quot;лишним&quot;!</li>
</ul>

<p style="margin-bottom: 0;">Удаление этих файлов приведет к тому, что система автоматической проверки не сможет запустить тесты для вашего решения.</p>
</div>

<h2 id="problems" style="color: rgb(173, 191, 210); margin-top: 30px;">🔧 Решение типичных проблем с Git</h2>

<div style="margin: 20px 0;">
<h3 style="color: rgb(187, 195, 195);">💭 Решения для распространенных проблем</h3>

<details style="background: rgb(36, 36, 36); border: 1px solid rgb(54, 66, 78); border-radius: 6px; margin: 10px 0px; padding: 10px;"><summary style="cursor: pointer; font-weight: 500; color: rgb(153, 189, 229);">⚠️ Конфликты при слиянии</summary>

<div style="margin: 10px 0px 0px; color: rgb(184, 191, 198);">
<p>Если Git сообщает о конфликтах, это означает, что одни и те же строки были изменены в разных версиях файла:</p>

<pre style="background: rgb(33, 33, 33); padding: 10px; border-radius: 4px;">
# 1. Откройте конфликтующие файлы, найдите места с маркерами:
&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD
Ваш локальный код
=======
Код из удаленного репозитория
&gt;&gt;&gt;&gt;&gt;&gt;&gt; branch-name

# 2. Отредактируйте файл, оставив нужный код и удалив маркеры
# 3. Добавьте файлы в индекс и создайте коммит
git add .
git commit -m &quot;fix: разрешение конфликтов&quot;
</pre>
</div>
</details>

<details style="background: rgb(36, 36, 36); border: 1px solid rgb(54, 66, 78); border-radius: 6px; margin: 10px 0px; padding: 10px;"><summary style="cursor: pointer; font-weight: 500; color: rgb(153, 189, 229);">↩️ Отмена изменений</summary>

<div style="margin: 10px 0px 0px; color: rgb(184, 191, 198);">
<pre style="background: rgb(33, 33, 33); padding: 10px; border-radius: 4px;">
# Отмена изменений в одном файле
git restore путь/к/файлу

# Отмена всех незакоммиченных изменений
git restore .

# Отмена последнего коммита (с сохранением изменений)
git reset --soft HEAD~1
</pre>
</div>
</details>

<details style="background: rgb(36, 36, 36); border: 1px solid rgb(54, 66, 78); border-radius: 6px; margin: 10px 0px; padding: 10px;"><summary style="cursor: pointer; font-weight: 500; color: rgb(153, 189, 229);">🚫 Ошибка при push: отклонено из-за расхождения историй</summary>

<div style="margin: 10px 0px 0px; color: rgb(184, 191, 198);">
<pre style="background: rgb(33, 33, 33); padding: 10px; border-radius: 4px;">
# Получите изменения с сервера и объедините их с вашими
git pull origin ваша_ветка

# Разрешите конфликты, если они есть, затем отправьте изменения
git push
</pre>
</div>
</details>
</div>

<h2 id="additional" style="color: rgb(173, 191, 210); margin-top: 30px;">💡 Дополнительные полезные команды</h2>

<div style="background: rgb(31, 31, 31); border: 1px solid rgb(43, 43, 43); border-radius: 8px; padding: 20px; margin: 15px 0px;">
<h4 style="margin-top: 0px; color: rgb(186, 191, 197);">📋 Полезные команды для ежедневной работы:</h4>

<pre style="margin: 0; font-family: monospace;">
# Просмотр истории коммитов
git log

# Компактный просмотр истории
git log --oneline

# Просмотр различий между текущим состоянием и последним коммитом
git diff

# Просмотр всех веток (локальных и удаленных)
git branch -a

# Удаление локальной ветки
git branch -d имя-ветки

# Переключение на существующую ветку
git switch имя-ветки

# Скачивание изменений без слияния
git fetch

# Просмотр удаленных репозиториев
git remote -v
</pre>
</div>

<div style="background: rgb(33, 79, 44); border: 1px solid rgb(41, 97, 54); border-radius: 8px; padding: 20px; margin: 30px 0px;">
<h3 style="color: rgb(153, 229, 171); margin-top: 0px;">✅ Выводы по теме лекции</h3>

<ul>
	<li>Git - это мощный инструмент для контроля версий, необходимый каждому разработчику</li>
	<li>Правильный рабочий процесс с Git повышает эффективность разработки и упрощает проверку кода</li>
	<li>Для успешного выполнения заданий в нашем курсе:
	<ul>
		<li>Сначала создайте форк репозитория, затем клонируйте его</li>
		<li>Создавайте ветки командой <code>git switch -c task/имя-задачи</code></li>
		<li>Используйте тот же email в Git, что и на учебной платформе</li>
		<li>Следите за статусом автоматической проверки в GitLab</li>
		<li>Для заданий с меткой &quot;mentor review&quot; отправляйте ссылку на вашу ветку</li>
	</ul>
	</li>
</ul>
</div>

<h2 id="resources" style="color: rgb(173, 191, 210); margin-top: 30px;">📚 Дополнительные ресурсы</h2>

<div style="background: rgb(31, 31, 31); border: 1px solid rgb(43, 43, 43); border-radius: 8px; padding: 20px; margin: 15px 0px;">
<ul>
	<li><a href="https://git-scm.com/book/ru/v2">Официальная книга Pro Git на русском</a> - полное руководство по Git</li>
	<li><a href="https://learngitbranching.js.org/?locale=ru_RU">Интерактивное обучение Git</a> - визуальная игра для изучения Git (рекомендуем пройти!)</li>
	<li><a href="https://training.github.com/downloads/ru/github-git-cheat-sheet/">Шпаргалка по Git</a> - краткая справка по командам</li>
</ul>
</div>

<div style="text-align: center; color: rgb(191, 191, 191); margin-top: 40px;">
<p><em>Удачи в освоении Git! 🚀</em></p>
</div>
</div>
<style id="night-eye-overrides" type="text/css">@media screen {body{background-color:rgb(28,28,33);color:rgb(191,191,191);}blockquote{border-bottom:0px solid rgb(77,77,77);border-top:0px solid rgb(77,77,77);border-right:0px solid rgb(77,77,77);border-left:0px solid rgb(77,77,77);border-color:rgb(77,77,77);}a{color:rgb(153,204,229);}hr{border-top:1px solid rgb(77,77,77);border-color:rgb(77,77,77) currentcolor currentcolor;}img.right{border:1px solid rgb(77,77,77);}img.left{border:1px solid rgb(77,77,77);}.marker{background-color:hsla(44,100%,20%,1);}figure{background:rgba(0,0,0,0.05);outline:rgb(204,204,204) solid 1px;}a > img{outline:rgb(153,204,229) solid 1px;}.code-featured{border:5px solid hsla(0,60%,50%,1);}.math-featured{box-shadow:rgb(159,40,40) 0px 0px 2px;background-color:rgba(204,51,51,0.05);}.image-grayscale{background-color:hsla(240,8%,12%,1);color:rgb(191,191,191);}.cke_table-faked-selection{background:hsla(0,0%,44%,1) !important;color:hsla(0,0%,75%,1);}.cke_table-faked-selection a{color:hsla(0,0%,75%,1);}.cke_editable:focus .cke_table-faked-selection{background:rgb(41,112,163) !important;color:hsla(0,0%,100%,1);}.cke_editable:focus .cke_table-faked-selection a{color:hsla(0,0%,100%,1);}.hljs{background:rgb(31,31,31);color:rgb(191,191,191);}.hljs-comment, .hljs-quote{color:rgb(191,191,191);}.hljs-doctag, .hljs-keyword, .hljs-formula{color:rgb(229,153,228);}.hljs-section, .hljs-name, .hljs-selector-tag, .hljs-deletion, .hljs-subst{color:rgb(229,159,153);}.hljs-literal{color:rgb(153,207,229);}.hljs-string, .hljs-regexp, .hljs-addition, .hljs-attribute, .hljs-meta-string{color:rgb(170,213,170);}.hljs-built_in, .hljs-class .hljs-title{color:rgb(229,205,153);}.hljs-attr, .hljs-variable, .hljs-template-variable, .hljs-type, .hljs-selector-class, .hljs-selector-attr, .hljs-selector-pseudo, .hljs-number{color:rgb(229,205,153);}.hljs-symbol, .hljs-bullet, .hljs-link, .hljs-meta, .hljs-selector-id, .hljs-title{color:rgb(153,177,229);}img.cke_flash{border:1px solid rgb(112,112,112);}.cke_editable form{border:1px dotted rgb(204,51,51);}img.cke_hidden{border:1px solid rgb(112,112,112);}img.cke_iframe{border:1px solid rgb(112,112,112);}.cke_contents_ltr a.cke_anchor, .cke_contents_ltr a.cke_anchor_empty, .cke_editable.cke_contents_ltr a[name], .cke_editable.cke_contents_ltr a[data-cke-saved-name]{border:1px dotted rgb(51,51,204);}.cke_contents_ltr img.cke_anchor{border:1px dotted rgb(51,51,204);}.cke_contents_rtl a.cke_anchor, .cke_contents_rtl a.cke_anchor_empty, .cke_editable.cke_contents_rtl a[name], .cke_editable.cke_contents_rtl a[data-cke-saved-name]{border:1px dotted rgb(51,51,204);}.cke_contents_rtl img.cke_anchor{border:1px dotted rgb(51,51,204);}div.cke_pagebreak{border-bottom:1px dotted rgb(153,153,153) !important;border-top:1px dotted rgb(153,153,153) !important;}.cke_show_blocks h6:not([contenteditable="false"]):not(.cke_show_blocks_off), .cke_show_blocks h5:not([contenteditable="false"]):not(.cke_show_blocks_off), .cke_show_blocks h4:not([contenteditable="false"]):not(.cke_show_blocks_off), .cke_show_blocks h3:not([contenteditable="false"]):not(.cke_show_blocks_off), .cke_show_blocks h2:not([contenteditable="false"]):not(.cke_show_blocks_off), .cke_show_blocks h1:not([contenteditable="false"]):not(.cke_show_blocks_off), .cke_show_blocks blockquote:not([contenteditable="false"]):not(.cke_show_blocks_off), .cke_show_blocks address:not([contenteditable="false"]):not(.cke_show_blocks_off), .cke_show_blocks pre:not([contenteditable="false"]):not(.cke_show_blocks_off), .cke_show_blocks div:not([contenteditable="false"]):not(.cke_show_blocks_off), .cke_show_blocks p:not([contenteditable="false"]):not(.cke_show_blocks_off){border:1px dotted hsla(0,0%,50%,1);}.cke_show_borders table.cke_show_border, .cke_show_borders table.cke_show_border > tr > td, .cke_show_borders table.cke_show_border > tr > th, .cke_show_borders table.cke_show_border > tbody > tr > td, .cke_show_borders table.cke_show_border > tbody > tr > th, .cke_show_borders table.cke_show_border > thead > tr > td, .cke_show_borders table.cke_show_border > thead > tr > th, .cke_show_borders table.cke_show_border > tfoot > tr > td, .cke_show_borders table.cke_show_border > tfoot > tr > th{border:1px dotted rgb(69,69,69);}.cke_widget_wrapper:hover > .cke_widget_element{outline:rgb(229,208,153) solid 2px;}.cke_widget_wrapper:hover .cke_widget_editable{outline:rgb(229,208,153) solid 2px;}.cke_widget_wrapper.cke_widget_focused > .cke_widget_element, .cke_widget_wrapper .cke_widget_editable.cke_widget_editable_focused{outline:rgb(153,194,229) solid 2px;}}
</style>
