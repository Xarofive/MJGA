<meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1.0">
<title></title>
<div style="max-width:900px;margin:0 auto;padding:20px;background:#f8f9fa;">
<div style="background:#fff;padding:28px;border-radius:12px;box-shadow:0 2px 10px rgba(0,0,0,0.08);overflow-x:auto;"><!-- Заголовок -->
<h1 style="text-align:center;color:#2c3e50;margin-top:0;">Создание и вызов функций в Go</h1>
<!-- TL;DR -->

<div style="background:#e8f5e9;border:2px solid #4caf50;border-radius:10px;padding:14px 16px;margin:16px 0;">
<h3 style="color:#2e7d32;margin:0 0 8px;">📌 TL;DR</h3>

<ul style="margin:0 0 0 18px;">
	<li>Функции &mdash; это переиспользуемые блоки кода</li>
	<li>Объявление: <code>func имя() { ... }</code></li>
	<li>Вызов: <code>имя()</code> (скобки обязательны)</li>
	<li>Можно вызывать много раз подряд</li>
	<li>Параметры и <code>return</code> &mdash; в следующей лекции</li>
</ul>
</div>
<!-- Аудио -->

<div style="background:#e3f2fd;border:1px solid #90caf9;border-radius:10px;padding:14px 16px;margin:16px 0;">
<h4 style="color:#1565c0;margin:0 0 8px;">🎧 Аудиообъяснение</h4>

<p style="margin:0 0 12px;color:#333;">Прослушайте краткое объяснение темы:</p>

<p style="margin:0;"><a href="https://drive.google.com/file/d/1RNDYIJlw6rrXd0OjFqB8YagxBdVp9qo0/view?usp=sharing" style="display:inline-block;background:#1565c0;color:#fff;padding:10px 18px;border-radius:6px;text-decoration:none;font-weight:600;" target="_blank">🎧 Слушать подкаст </a></p>

<p style="font-size:13px;color:#666;margin:8px 0 0;"><em>Откроется в новой вкладке.</em></p>
</div>
<!-- Содержание -->

<div style="background:#f1f5f9;border:1px solid #cbd5e1;border-radius:10px;padding:12px 16px;margin:16px 0;">
<h3 style="color:#0f172a;margin:0 0 8px;">🧭 Содержание</h3>

<ol style="margin:0 0 0 18px;">
	<li><a href="#why" style="color:#0ea5e9;text-decoration:none;">Зачем нужны функции</a></li>
	<li><a href="#syntax" style="color:#0ea5e9;text-decoration:none;">Базовый синтаксис объявления функции</a></li>
	<li><a href="#call" style="color:#0ea5e9;text-decoration:none;">Вызов функции</a></li>
	<li><a href="#order" style="color:#0ea5e9;text-decoration:none;">Порядок объявлений в файле</a></li>
	<li><a href="#naming" style="color:#0ea5e9;text-decoration:none;">Правила именования функций</a></li>
	<li><a href="#pitfalls" style="color:#0ea5e9;text-decoration:none;">Типичные ошибки новичков</a></li>
	<li><a href="#summary" style="color:#0ea5e9;text-decoration:none;">Резюме</a></li>
	<li><a href="#practice" style="color:#0ea5e9;text-decoration:none;">Практические упражнения</a></li>
	<li><a href="#quiz" style="color:#0ea5e9;text-decoration:none;">Проверь себя</a></li>
</ol>
</div>
<!-- Основные разделы -->

<h2 id="why" style="color:#34495e;">1. Зачем нужны функции</h2>

<p style="color:#333;line-height:1.6;">Представьте, что вы готовите борщ. У вас есть рецепт, и каждый раз, когда хочется борща, вы следуете одним и тем же шагам. Функции в программировании &mdash; это как рецепты: один раз написали инструкцию, а потом просто говорите &laquo;сделай борщ&raquo; (вызываете функцию), и она выполняется.</p>

<p style="color:#333;line-height:1.6;">До сих пор весь наш код жил в одной функции <code>main()</code>. Это работает для простых программ, но представьте, если бы весь код большого приложения был в одном месте &mdash; найти нужное было бы невозможно! Функции решают три важные задачи:</p>

<ul style="margin:12px 0;color:#333;line-height:1.6;">
	<li><strong>Разбивка на логические части</strong> &mdash; каждая функция отвечает за одну задачу</li>
	<li><strong>Переиспользование кода</strong> &mdash; не нужно копировать одинаковые куски</li>
	<li><strong>Читабельность</strong> &mdash; имя функции сразу говорит, что она делает</li>
</ul>

<div style="background:#e3f2fd;border:1px solid #90caf9;border-radius:10px;padding:12px 16px;margin:16px 0;">
<h4 style="margin:0 0 6px;color:#1565c0;">💡 Интересный факт</h4>

<p style="margin:0;">В Go функции &mdash; это граждане первого класса. Это значит, что с ними можно делать много интересного (передавать в другие функции, хранить в переменных), но об этом мы поговорим в продвинутых модулях.</p>
</div>

<h2 id="syntax" style="color:#34495e;">2. Базовый синтаксис объявления функции</h2>

<p style="color:#333;line-height:1.6;">Самая простая функция в Go выглядит так:</p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">func имяФункции() {
    // тело функции - код, который выполнится при вызове
}</code></pre>

<p style="color:#333;line-height:1.6;">Разберём по частям:</p>

<ul style="margin:12px 0;color:#333;line-height:1.6;">
	<li><code style="background:#f0f0f0;padding:2px 4px;border-radius:3px;">func</code> &mdash; ключевое слово, говорит компилятору &laquo;эй, тут функция!&raquo;</li>
	<li><code style="background:#f0f0f0;padding:2px 4px;border-radius:3px;">имяФункции</code> &mdash; название, которое мы придумываем</li>
	<li><code style="background:#f0f0f0;padding:2px 4px;border-radius:3px;">()</code> &mdash; пустые скобки означают &laquo;без параметров&raquo; (пока что)</li>
	<li><code style="background:#f0f0f0;padding:2px 4px;border-radius:3px;">{}</code> &mdash; фигурные скобки обрамляют тело функции</li>
</ul>

<p style="color:#333;line-height:1.6;"><strong>Пример 1 &mdash; минимальное объявление и вызов:</strong></p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">package main

import "fmt"

// Объявляем функцию без параметров и без возвращаемых значений
func greet() {
    fmt.Println("Привет от функции greet!")
}

func main() {
    greet() // вызов функции
}</code></pre>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Ожидаемый вывод:</strong>

<pre style="margin:5px 0 0 0;">
Привет от функции greet!</pre>
</div>

<p style="color:#333;line-height:1.6;">Обратите внимание: функцию <code>greet</code> мы объявили на том же уровне, что и <code>main</code> &mdash; в пределах пакета, но не внутри другой функции.</p>

<h2 id="call" style="color:#34495e;">3. Вызов функции</h2>

<p style="color:#333;line-height:1.6;">Чтобы функция заработала, её нужно вызвать. Вызов выглядит просто: пишем имя функции и обязательно добавляем круглые скобки:</p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">имяФункции()  // правильный вызов
имяФункции    // это НЕ вызов; в таком виде в коде будет ошибка компиляции</code></pre>

<div style="background:#ffebee;border:1px solid #ef5350;border-radius:10px;padding:12px 16px;margin:16px 0;">
<h4 style="margin:0 0 6px;color:#c62828;">⚠️ Важно запомнить</h4>

<p style="margin:0;">Без скобок функция не вызовется! Запись <code>greet</code> &mdash; это ссылка на функцию, а <code>greet()</code> &mdash; это команда &laquo;выполни функцию прямо сейчас&raquo;. Если написать <code>greet</code> отдельной строкой в <code>main()</code>, компилятор выдаст ошибку.</p>
</div>

<p style="color:#333;line-height:1.6;"><strong>Пример 2 &mdash; многократные вызовы:</strong></p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">package main

import "fmt"

func sayHello() {
    fmt.Println("Hello!")
}

func main() {
    sayHello()  // первый вызов
    sayHello()  // второй вызов
    sayHello()  // третий вызов
}</code></pre>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Ожидаемый вывод:</strong>

<pre style="margin:5px 0 0 0;">
Hello!
Hello!
Hello!</pre>
</div>

<p style="color:#333;line-height:1.6;">Можно создать несколько функций и вызывать их в разном порядке:</p>

<p style="color:#333;line-height:1.6;"><strong>Пример 3 &mdash; комбинирование нескольких функций:</strong></p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">package main

import "fmt"

func greet() {
    fmt.Println("Привет!")
}

func separator() {
    fmt.Println("---")
}

func main() {
    greet()
    separator()
    greet()
}</code></pre>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Ожидаемый вывод:</strong>

<pre style="margin:5px 0 0 0;">
Привет!
---
Привет!</pre>
</div>

<details style="margin:16px 0;"><summary style="cursor:pointer;color:#0ea5e9;font-weight:bold;">🤔 Мини-задание: что выведет этот код?</summary>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;margin-top:10px;">
<code class="language-go">func star() {
    fmt.Print("*") // Print — как Println, но без перехода на новую строку
}

func main() {
    star()
    star()
    star()
    star()
    star()
    fmt.Println() // переход на новую строку в конце
}</code></pre>

<p style="margin-top:10px;"><strong>Ответ:</strong> <code>*****</code> (пять звёздочек в одной строке, потому что <code>fmt.Print</code> не переводит строку)</p>
</details>

<h2 id="order" style="color:#34495e;">4. Порядок объявлений в файле</h2>

<p style="color:#333;line-height:1.6;">В Go компилятор &laquo;видит&raquo; все функции в пакете сразу, поэтому порядок их объявления не важен. Можно написать функцию до <code>main()</code> или после &mdash; всё будет работать:</p>

<p style="color:#333;line-height:1.6;"><strong>Пример 4 &mdash; функция ниже main():</strong></p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">package main

import "fmt"

func main() {
    printLine() // можно вызывать, даже если определение ниже
    fmt.Println("Середина")
    printLine()
}

func printLine() {
    fmt.Println("----------")
}</code></pre>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Ожидаемый вывод:</strong>

<pre style="margin:5px 0 0 0;">
----------
Середина
----------</pre>
</div>

<div style="background:#fff8e1;border:1px solid #ffe082;border-radius:10px;padding:12px 16px;margin:16px 0;">
<h4 style="margin:0 0 6px;color:#8d6e63;">💡 Замечание</h4>

<p style="margin:0;">В некоторых языках (например, C) порядок важен &mdash; нужно объявить функцию до её использования. В Go это не так, что удобно!</p>
</div>

<p style="color:#333;line-height:1.6;">Но есть одно железное правило:</p>

<div style="background:#ffebee;border:1px solid #ef5350;border-radius:10px;padding:12px 16px;margin:16px 0;">
<h4 style="margin:0 0 6px;color:#c62828;">❌ Нельзя объявлять функцию внутри другой функции</h4>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;margin-top:10px;">
<code class="language-go">func main() {
    func helper() {  // ❌ ОШИБКА! Нельзя так!
        fmt.Println("help")
    }
}</code></pre>
</div>

<h2 id="naming" style="color:#34495e;">5. Правила именования функций</h2>

<p style="color:#333;line-height:1.6;">Имя функции должно быть понятным и отражать её назначение. Технические правила:</p>

<ul style="margin:12px 0;color:#333;line-height:1.6;">
	<li>Начинается с буквы или подчёркивания</li>
	<li>Может содержать буквы, цифры и подчёркивание</li>
	<li>Регистр важен: <code>printMenu</code> и <code>PrintMenu</code> &mdash; разные функции</li>
	<li>В Go-сообществе принято писать имена латиницей в camelCase: <code>printUserInfo</code>, а не <code>print_user_info</code> (это convention, которой стоит придерживаться &mdash; хотя технически Go допускает и Unicode letters)</li>
</ul>

<p style="color:#333;line-height:1.6;"><strong>Пример 5 &mdash; плохо/хорошо про имена:</strong></p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">// ❌ Плохо - непонятно, что делают
func f1() {}
func doIt() {}
func pr() {}

// ✅ Хорошо - сразу ясно назначение
func printMenu() {}
func drawSeparator() {}
func greetUser() {}</code></pre>

<div style="background:#e3f2fd;border:1px solid #90caf9;border-radius:10px;padding:12px 16px;margin:16px 0;">
<h4 style="margin:0 0 6px;color:#1565c0;">🔮 Заглянем в будущее</h4>

<p style="margin:0;">Функции, начинающиеся с заглавной буквы (<code>PrintMenu</code>), экспортируются из пакета &mdash; их можно использовать в других пакетах. Подробно про разделение кода на пакеты &mdash; в продвинутых курсах.</p>
</div>

<p style="color:#333;line-height:1.6;"><strong>Пример 6 &mdash; маленькие &laquo;помощники&raquo; для структуры вывода:</strong></p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">package main

import "fmt"

func header() {
    fmt.Println("=== Моя программа ===")
}

func footer() {
    fmt.Println("=====================")
}

func main() {
    header()
    fmt.Println("Добро пожаловать!")
    footer()
}</code></pre>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Ожидаемый вывод:</strong>

<pre style="margin:5px 0 0 0;">
=== Моя программа ===
Добро пожаловать!
=====================</pre>
</div>

<h2 id="pitfalls" style="color:#34495e;">6. Типичные ошибки новичков</h2>

<h3 style="color:#34495e;font-size:1.2em;margin-top:20px;">Ошибка №1: Забыли скобки при вызове</h3>

<p style="color:#333;line-height:1.6;"><strong>Пример 7 &mdash; забытые скобки:</strong></p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">package main

import "fmt"

func hello() {
    fmt.Println("hi")
}

func main() {
    // hello          // ❌ так не вызовется; без скобок это просто имя
    hello()          // ✅ вызов функции
}</code></pre>

<h3 style="color:#34495e;font-size:1.2em;margin-top:20px;">Ошибка №2: Дублирующие имена функций</h3>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">func greet() {
    fmt.Println("Hello")
}

func greet() {  // ❌ ОШИБКА: greet уже объявлена!
    fmt.Println("Hi")
}</code></pre>

<h3 style="color:#34495e;font-size:1.2em;margin-top:20px;">Ошибка №3: Попытка объявить функцию внутри main</h3>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">func main() {
    // Хочется создать локальную функцию...
    func helper() {  // ❌ ОШИБКА КОМПИЛЯЦИИ!
        fmt.Println("help")
    }
    helper()
}</code></pre>

<h3 style="color:#34495e;font-size:1.2em;margin-top:20px;">Ошибка №4: Неиспользуемый импорт</h3>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">package main

import "fmt"  // импортировали
import "strings"  // импортировали, но не используем - ОШИБКА!

func greet() {
    fmt.Println("Hi")
}

func main() {
    greet()
}</code></pre>

<div style="background:#e8f5e9;border:1px solid #4caf50;border-radius:10px;padding:12px 16px;margin:16px 0;">
<h4 style="margin:0 0 6px;color:#2e7d32;">✅ Совет</h4>

<p style="margin:0;">Используйте IDE с поддержкой Go (VS Code с расширением Go, GoLand) &mdash; они сразу подсвечивают такие ошибки и могут автоматически удалять неиспользуемые импорты.</p>
</div>

<h2 id="summary" style="color:#34495e;">7. Резюме</h2>

<div style="background:#f1f5f9;border:1px solid #cbd5e1;border-radius:10px;padding:14px 16px;margin:16px 0;">
<ul style="margin:0;">
	<li>Функции помогают структурировать код и избежать дублирования</li>
	<li>Объявление: <code>func имя() { тело }</code></li>
	<li>Вызов: <code>имя()</code> &mdash; скобки обязательны!</li>
	<li>Можно вызывать много раз, из циклов и условий</li>
	<li>Порядок объявления в файле не важен</li>
	<li>Имена должны быть понятными: <code>printReport</code>, а не <code>pr</code></li>
</ul>
</div>
<!-- Таблица сравнения -->

<div style="margin:20px 0;">
<h3 style="color:#34495e;">Определение vs Вызов функции</h3>

<table style="width:100%;border-collapse:collapse;margin-top:10px;">
	<thead>
		<tr style="background:#eef2ff;">
			<th style="border:1px solid #c7d2fe;padding:10px;text-align:left;">Действие</th>
			<th style="border:1px solid #c7d2fe;padding:10px;text-align:left;">Синтаксис</th>
			<th style="border:1px solid #c7d2fe;padding:10px;text-align:left;">Где в коде</th>
			<th style="border:1px solid #c7d2fe;padding:10px;text-align:left;">Пример</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="border:1px solid #e5e7eb;padding:10px;">Определение</td>
			<td style="border:1px solid #e5e7eb;padding:10px;font-family:monospace;">func имя() { ... }</td>
			<td style="border:1px solid #e5e7eb;padding:10px;">На уровне пакета</td>
			<td style="border:1px solid #e5e7eb;padding:10px;font-family:monospace;">func greet() { fmt.Println(&quot;Hi&quot;) }</td>
		</tr>
		<tr>
			<td style="border:1px solid #e5e7eb;padding:10px;">Вызов</td>
			<td style="border:1px solid #e5e7eb;padding:10px;font-family:monospace;">имя()</td>
			<td style="border:1px solid #e5e7eb;padding:10px;">Внутри другой функции</td>
			<td style="border:1px solid #e5e7eb;padding:10px;font-family:monospace;">greet()</td>
		</tr>
	</tbody>
</table>
</div>
<!-- Практика -->

<h2 id="practice" style="color:#34495e;">Практические упражнения для самопроверки (необязательные)</h2>

<div style="background:#f8f9fa;border:1px solid #e0e0e0;border-radius:8px;padding:16px;margin:16px 0;">
<h3 style="margin-top:0;color:#2c3e50;">[Базовый] Задача 1: Три приветствия</h3>

<p style="color:#333;">Создайте функцию <code>greet()</code> (без параметров), которая печатает <code>Привет!</code>. В <code>main()</code> вызовите её три раза, по одному вызову в строке.</p>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Ожидаемый вывод:</strong>

<pre style="margin:5px 0 0 0;">
Привет!
Привет!
Привет!</pre>
</div>

<details style="margin:12px 0;"><summary style="cursor:pointer;color:#0ea5e9;font-weight:bold;">Показать решение</summary>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;margin-top:10px;">
<code class="language-go">package main

import "fmt"

func greet() {
    fmt.Println("Привет!")
}

func main() {
    greet()
    greet()
    greet()
}</code></pre>
</details>
</div>

<div style="background:#f8f9fa;border:1px solid #e0e0e0;border-radius:8px;padding:16px;margin:16px 0;">
<h3 style="margin-top:0;color:#2c3e50;">[Средний] Задача 2: Разделители</h3>

<p style="color:#333;">Напишите функцию <code>divider()</code>, печатающую строку из 20 дефисов. В <code>main()</code> выведите:</p>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;">
<pre style="margin:0;">
Start
--------------------
Middle
--------------------
End</pre>
</div>

<p style="color:#666;"><strong>💡 Подсказка:</strong> используйте <code>fmt.Println</code> в <code>divider()</code>.</p>

<details style="margin:12px 0;"><summary style="cursor:pointer;color:#0ea5e9;font-weight:bold;">Показать решение</summary>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;margin-top:10px;">
<code class="language-go">package main

import "fmt"

func divider() {
    fmt.Println("--------------------")
}

func main() {
    fmt.Println("Start")
    divider()
    fmt.Println("Middle")
    divider()
    fmt.Println("End")
}</code></pre>
</details>
</div>

<div style="background:#f8f9fa;border:1px solid #e0e0e0;border-radius:8px;padding:16px;margin:16px 0;">
<h3 style="margin-top:0;color:#2c3e50;">[Со звёздочкой] Задача 3: Мини-меню</h3>

<p style="color:#333;">Реализуйте функцию <code>printMenu()</code>, которая выводит:</p>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;">
<pre style="margin:0;">
1) Добавить
2) Удалить
3) Выйти</pre>
</div>

<p style="color:#333;">В <code>main()</code> выведите заголовок <code>Меню:</code>, затем вызовите <code>printMenu()</code>, затем строку <code>Выберите пункт...</code>.</p>

<p style="color:#666;"><strong>Дополнительно:</strong> вызовите <code>printMenu()</code> дважды &mdash; до и после строки <code>---</code>.</p>

<details style="margin:12px 0;"><summary style="cursor:pointer;color:#0ea5e9;font-weight:bold;">Показать решение</summary>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;margin-top:10px;">
<code class="language-go">package main

import "fmt"

func printMenu() {
    fmt.Println("1) Добавить")
    fmt.Println("2) Удалить")
    fmt.Println("3) Выйти")
}

func main() {
    fmt.Println("Меню:")
    printMenu()
    fmt.Println("---")
    printMenu()
    fmt.Println("Выберите пункт...")
}</code></pre>
</details>
</div>
<!-- Квиз -->

<h2 id="quiz" style="color:#34495e;">Проверь себя</h2>

<ol style="color:#333;line-height:1.8;">
	<li><strong>Как объявить функцию без параметров и возвращаемых значений в Go?</strong>

	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>

	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;"><code>func имяФункции() { /* тело функции */ }</code></p>
	</details>
	</li>
	<li><strong>Где должна располагаться функция относительно main()?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;">Где угодно в том же файле/пакете &mdash; можно выше или ниже <code>main()</code>, порядок не важен.</p>
	</details>
	</li>
	<li><strong>Что произойдёт, если написать hello вместо hello()?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;"><code>hello</code> без скобок не вызывает функцию. Если написать это отдельной строкой в коде, будет ошибка компиляции: значение функции не используется.</p>
	</details>
	</li>
	<li><strong>Можно ли объявить функцию внутри другой функции в Go?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;">Нет, нельзя. Все функции объявляются на уровне пакета, не внутри других функций.</p>
	</details>
	</li>
	<li><strong>Можно ли вызвать одну и ту же функцию несколько раз и зачем это делать?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;">Да, можно вызывать сколько угодно раз. Это нужно для переиспользования кода &mdash; не копировать одинаковую логику, а вызвать готовую функцию.</p>
	</details>
	</li>
	<li><strong>Какие требования к именам функций?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;">Начинаются с буквы, содержат буквы/цифры/подчёркивание. Рекомендуется camelCase и осмысленные имена: <code>calculateSum</code>, а не <code>f1</code>.</p>
	</details>
	</li>
	<li><strong>Что делает func main() и почему через него запускаем программу?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;"><code>func main()</code> &mdash; это точка входа в программу. Go автоматически вызывает эту функцию при запуске программы.</p>
	</details>
	</li>
	<li><strong>Зачем выносить повторяющийся код в функцию?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;">Для удобства поддержки (изменил в одном месте &mdash; работает везде), читаемости (понятное имя вместо кучи строк) и уменьшения размера кода.</p>
	</details>
	</li>
</ol>
<!-- Что дальше --></div>
</div>
