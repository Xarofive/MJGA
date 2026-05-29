<meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1.0">
<title></title>
<div style="max-width:900px;margin:0 auto;padding:20px;background:#f8f9fa;">
<div style="background:#fff;padding:28px;border-radius:12px;box-shadow:0 2px 10px rgba(0,0,0,0.08);overflow-x:auto;"><!-- Заголовок -->
<h1 style="text-align:center;color:#2c3e50;margin-top:0;">Возвращаемые значения функций в Go</h1>
<!-- TL;DR -->

<div style="background:#e8f5e9;border:2px solid #4caf50;border-radius:10px;padding:14px 16px;margin:16px 0;">
<h3 style="color:#2e7d32;margin:0 0 8px;">📌 TL;DR</h3>

<ul style="margin:0 0 0 18px;">
	<li>Функции могут возвращать значения для дальнейшего использования</li>
	<li>Тип возвращаемого значения указывается после параметров</li>
	<li>Для возврата используется ключевое слово <code>return</code></li>
	<li>Возвращаемое значение можно сохранить в переменную или использовать сразу</li>
	<li>Функция может возвращать несколько значений: <code>func f() (int, int)</code></li>
	<li>Функции-вычисления делают код модульным и переиспользуемым</li>
</ul>
</div>
<!-- Содержание -->

<div style="background:#f1f5f9;border:1px solid #cbd5e1;border-radius:10px;padding:12px 16px;margin:16px 0;">
<h3 style="color:#0f172a;margin:0 0 8px;">🧭 Содержание</h3>

<ol style="margin:0 0 0 18px;">
	<li><a href="#why" style="color:#0ea5e9;text-decoration:none;">Зачем возвращаемые значения</a></li>
	<li><a href="#single" style="color:#0ea5e9;text-decoration:none;">Синтаксис возвращаемого значения</a></li>
	<li><a href="#usage" style="color:#0ea5e9;text-decoration:none;">Использование возвращаемых значений</a></li>
	<li><a href="#examples" style="color:#0ea5e9;text-decoration:none;">Примеры функций с возвратом</a></li>
	<li><a href="#pitfalls" style="color:#0ea5e9;text-decoration:none;">Типичные ошибки</a></li>
	<li><a href="#summary" style="color:#0ea5e9;text-decoration:none;">Резюме</a></li>
	<li><a href="#practice" style="color:#0ea5e9;text-decoration:none;">Практические упражнения</a></li>
	<li><a href="#quiz" style="color:#0ea5e9;text-decoration:none;">Проверь себя</a></li>
</ol>
</div>
<!-- Основные разделы -->

<h2 id="why" style="color:#34495e;">1. Зачем возвращаемые значения</h2>

<p style="color:#333;line-height:1.6;">Функция &mdash; это не только &laquo;исполнитель&raquo;, но и &laquo;вычислитель&raquo;. Представьте калькулятор: вы вводите числа (параметры), нажимаете кнопку операции (вызываете функцию), и калькулятор показывает результат (возвращаемое значение).</p>

<p style="color:#333;line-height:1.6;">До сих пор наши функции что-то делали (печатали текст), но ничего не возвращали. Теперь они смогут вычислять значения и передавать их дальше &mdash; как кирпичики, из которых строится программа.</p>

<div style="background:#e3f2fd;border:1px solid #90caf9;border-radius:10px;padding:12px 16px;margin:16px 0;">
<h4 style="margin:0 0 6px;color:#1565c0;">💡 Функции-действия vs Функции-вычисления</h4>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:12px;overflow-x:auto;margin:8px 0 0;">
<code class="language-go">// Функция-действие (ничего не возвращает)
func printGreeting(name string) {
    fmt.Println("Привет,", name)
}

// Функция-вычисление (возвращает результат)
func makeGreeting(name string) string {
    return "Привет, " + name
}</code></pre>
</div>

<h2 id="single" style="color:#34495e;">2. Синтаксис возвращаемого значения</h2>

<p style="color:#333;line-height:1.6;">Чтобы функция возвращала значение, нужно:</p>

<ol style="margin:12px 0;color:#333;line-height:1.6;">
	<li>Указать тип возвращаемого значения после параметров</li>
	<li>Использовать ключевое слово <code>return</code> для возврата значения</li>
</ol>

<p style="color:#333;line-height:1.6;">Общий синтаксис:</p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">func имяФункции(параметры) ТипВозврата {
    // вычисления
    return значение
}</code></pre>

<p style="color:#333;line-height:1.6;">Тип возвращаемого значения указывается <strong>после</strong> списка параметров (или после пустых скобок, если параметров нет), <strong>перед</strong> открывающей фигурной скобкой.</p>

<p style="color:#333;line-height:1.6;"><strong>Пример 1 &mdash; функция возвращает квадрат числа:</strong></p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">package main

import "fmt"

// Функция square возвращает квадрат числа n
func square(n int) int {  // int после параметров - тип возврата
    return n * n
}

func main() {
    result := square(5)  // сохраняем результат в переменную
    fmt.Println("Квадрат числа 5 равен:", result)

    // Можно использовать сразу в выражении
    fmt.Println("Квадрат числа 7:", square(7))
}</code></pre>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Ожидаемый вывод:</strong>

<pre style="margin:5px 0 0 0;">
Квадрат числа 5 равен: 25
Квадрат числа 7: 49</pre>
</div>

<h2 id="usage" style="color:#34495e;">3. Использование возвращаемых значений</h2>

<p style="color:#333;line-height:1.6;">Когда функция возвращает значение, вы можете:</p>

<ul style="margin:12px 0;color:#333;line-height:1.6;">
	<li><strong>Сохранить в переменную:</strong> <code>result := myFunc()</code></li>
	<li><strong>Использовать в выражении:</strong> <code>fmt.Println(myFunc())</code></li>
	<li><strong>Передать другой функции:</strong> <code>otherFunc(myFunc())</code></li>
	<li><strong>Использовать в вычислениях:</strong> <code>total := myFunc() + 10</code></li>
</ul>

<p style="color:#333;line-height:1.6;"><strong>Пример 2 &mdash; разные способы использования возвращаемых значений:</strong></p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">package main

import "fmt"

func double(x int) int {
    return x * 2
}

func addTen(x int) int {
    return x + 10
}

func main() {
    // Сохранение в переменную
    doubled := double(3)
    fmt.Println("Удвоенное:", doubled)

    // Использование в выражении
    fmt.Println("Прямо в print:", double(4))

    // Передача другой функции
    result := addTen(double(5))  // сначала double(5) = 10, потом addTen(10) = 20
    fmt.Println("Композиция функций:", result)

    // В вычислениях
    total := double(6) + double(7)  // 12 + 14
    fmt.Println("Сумма удвоенных:", total)
}</code></pre>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Ожидаемый вывод:</strong>

<pre style="margin:5px 0 0 0;">
Удвоенное: 6
Прямо в print: 8
Композиция функций: 20
Сумма удвоенных: 26</pre>
</div>

<h2 id="examples" style="color:#34495e;">4. Примеры функций с возвратом</h2>

<p style="color:#333;line-height:1.6;">Рассмотрим несколько полезных примеров функций с возвращаемыми значениями:</p>

<p style="color:#333;line-height:1.6;"><strong>Пример 3 &mdash; функции для работы со строками:</strong></p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">package main

import "fmt"

// Добавляет восклицательный знак к строке
func exclaim(text string) string {
    return text + "!"
}

// Создает приветствие
func greet(name string) string {
    return "Здравствуйте, " + name
}

// Форматирует цену
func formatPrice(price float64) string {
    return fmt.Sprintf("%.2f руб.", price)
}

func main() {
    // Работа со строками
    excited := exclaim("Ура")
    fmt.Println(excited)

    greeting := greet("Александр")
    fmt.Println(greeting)

    // Композиция строковых функций
    excitedGreeting := exclaim(greet("Мария"))
    fmt.Println(excitedGreeting)

    // Форматирование
    priceTag := formatPrice(99.90)
    fmt.Println("Цена:", priceTag)
}</code></pre>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Ожидаемый вывод:</strong>

<pre style="margin:5px 0 0 0;">
Ура!
Здравствуйте, Александр
Здравствуйте, Мария!
Цена: 99.90 руб.</pre>
</div>

<p style="color:#333;line-height:1.6;"><strong>Пример 4 &mdash; математические функции:</strong></p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">package main

import "fmt"

// Возвращает куб числа
func cube(n int) int {
    return n * n * n
}

// Возвращает среднее арифметическое двух чисел
func average(a, b float64) float64 {
    return (a + b) / 2.0
}

// Проверяет, четное ли число
// n%2 — остаток от деления на 2 (0 для чётных, 1 для нечётных)
func isEven(n int) bool {
    return n%2 == 0
}

func main() {
    // Куб числа
    fmt.Println("Куб 3:", cube(3))

    // Среднее значение
    avg := average(10.5, 20.5)
    fmt.Println("Среднее:", avg)

    // Логические функции
    fmt.Println("10 четное?", isEven(10))
    fmt.Println("7 четное?", isEven(7))
}</code></pre>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Ожидаемый вывод:</strong>

<pre style="margin:5px 0 0 0;">
Куб 3: 27
Среднее: 15.5
10 четное? true
7 четное? false</pre>
</div>

<details style="margin:16px 0;"><summary style="cursor:pointer;color:#0ea5e9;font-weight:bold;">🤔 Мини-задание: что вернёт функция?</summary>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;margin-top:10px;">
<code class="language-go">func mystery(x int) int {
    x = x * 2
    x = x + 1
    return x
}

// Что вернёт mystery(3)?</code></pre>

<p style="margin-top:10px;"><strong>Ответ:</strong> 7 (сначала 3*2=6, потом 6+1=7)</p>
</details>

<h2 id="pitfalls" style="color:#34495e;">5. Типичные ошибки</h2>

<h3 style="color:#34495e;font-size:1.2em;margin-top:20px;">Ошибка №1: Забыли return</h3>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">// ❌ Ошибка компиляции: missing return
func bad(x int) int {
    result := x * 2
    // забыли return result
}

// ✅ Правильно
func good(x int) int {
    result := x * 2
    return result
}</code></pre>

<h3 style="color:#34495e;font-size:1.2em;margin-top:20px;">Ошибка №2: Неправильный тип возвращаемого значения</h3>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">// ❌ Ошибка: возвращаем string вместо int
func wrongType() int {
    return "hello"  // cannot use "hello" (type string) as type int
}

// ✅ Правильно
func correctType() string {
    return "hello"
}</code></pre>

<h3 style="color:#34495e;font-size:1.2em;margin-top:20px;">Ошибка №3: Игнорирование возвращаемого значения</h3>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">func calculate(x int) int {
    return x * 10
}

func main() {
    // ⚠️ Вызываем функцию, но не используем результат
    calculate(5)  // результат потерян

    // ✅ Правильно - сохраняем или используем результат
    result := calculate(5)
    fmt.Println(result)

    // ✅ Или используем сразу
    fmt.Println(calculate(5))
}</code></pre>

<h3 style="color:#34495e;font-size:1.2em;margin-top:20px;">Ошибка №4: Попытка изменить параметр и вернуть его</h3>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;">
<code class="language-go">// Работает, но может запутать
func increment(n int) int {
    n = n + 1  // меняем локальную копию
    return n   // возвращаем измененную копию
}

// Более ясный вариант
func incrementClear(n int) int {
    return n + 1  // сразу возвращаем результат
}</code></pre>

<div style="background:#ffebee;border:1px solid #ef5350;border-radius:10px;padding:12px 16px;margin:16px 0;">
<h4 style="margin:0 0 6px;color:#c62828;">⚠️ Важно запомнить</h4>

<ul style="margin:8px 0 0 18px;">
	<li>Если функция объявлена с типом возврата, она <strong>обязана</strong> вернуть значение</li>
	<li>Тип возвращаемого значения должен точно соответствовать объявленному</li>
	<li>Возвращаемое значение нужно использовать, иначе теряется смысл функции</li>
</ul>
</div>

<h2 id="summary" style="color:#34495e;">6. Резюме</h2>

<div style="background:#f1f5f9;border:1px solid #cbd5e1;border-radius:10px;padding:14px 16px;margin:16px 0;">
<ul style="margin:0;">
	<li>Функции могут возвращать значения &mdash; это делает их вычислителями</li>
	<li>Тип возврата указывается после параметров: <code>func f(x int) string</code></li>
	<li>Для возврата используется ключевое слово <code>return</code></li>
	<li>Возвращаемое значение можно сохранить, использовать в выражениях или передать другой функции</li>
	<li>Функция с объявленным типом возврата обязана вернуть значение этого типа</li>
	<li>Функция может вернуть несколько значений через скобки в типе: <code>func f() (int, int)</code></li>
</ul>
</div>
<!-- Таблица сравнения -->

<div style="margin:20px 0;">
<h3 style="color:#34495e;">Функции с возвратом и без</h3>

<table style="width:100%;border-collapse:collapse;margin-top:10px;">
	<thead>
		<tr style="background:#eef2ff;">
			<th style="border:1px solid #c7d2fe;padding:10px;text-align:left;">Тип функции</th>
			<th style="border:1px solid #c7d2fe;padding:10px;text-align:left;">Сигнатура</th>
			<th style="border:1px solid #c7d2fe;padding:10px;text-align:left;">Пример</th>
			<th style="border:1px solid #c7d2fe;padding:10px;text-align:left;">Использование</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="border:1px solid #e5e7eb;padding:10px;">Без возврата</td>
			<td style="border:1px solid #e5e7eb;padding:10px;font-family:monospace;">func f()</td>
			<td style="border:1px solid #e5e7eb;padding:10px;font-family:monospace;">func print() { fmt.Println(&quot;Hi&quot;) }</td>
			<td style="border:1px solid #e5e7eb;padding:10px;">Просто вызов: <code>print()</code></td>
		</tr>
		<tr>
			<td style="border:1px solid #e5e7eb;padding:10px;">С возвратом</td>
			<td style="border:1px solid #e5e7eb;padding:10px;font-family:monospace;">func f() тип</td>
			<td style="border:1px solid #e5e7eb;padding:10px;font-family:monospace;">func get() int { return 42 }</td>
			<td style="border:1px solid #e5e7eb;padding:10px;">Сохранение: <code>x := get()</code></td>
		</tr>
	</tbody>
</table>
</div>
<!-- Практика -->

<h2 id="practice" style="color:#34495e;">7. Практические упражнения для самопроверки</h2>

<div style="background:#f8f9fa;border:1px solid #e0e0e0;border-radius:8px;padding:16px;margin:16px 0;">
<h3 style="margin-top:0;color:#2c3e50;">[Базовый] Задача 1: Утроение числа</h3>

<p style="color:#333;">Напишите функцию <code>triple(n int) int</code>, которая возвращает утроенное значение числа.</p>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Ожидаемый вывод для triple(4):</strong>

<pre style="margin:5px 0 0 0;">
12</pre>
</div>

<details style="margin:12px 0;"><summary style="cursor:pointer;color:#0ea5e9;font-weight:bold;">Показать решение</summary>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;margin-top:10px;">
<code class="language-go">package main

import "fmt"

func triple(n int) int {
    return n * 3
}

func main() {
    fmt.Println(triple(4))  // 12
    fmt.Println(triple(7))  // 21
}</code></pre>
</details>
</div>

<div style="background:#f8f9fa;border:1px solid #e0e0e0;border-radius:8px;padding:16px;margin:16px 0;">
<h3 style="margin-top:0;color:#2c3e50;">[Средний] Задача 2: Конвертер температуры</h3>

<p style="color:#333;">Реализуйте функцию <code>celsiusToFahrenheit(c float64) float64</code>, которая конвертирует градусы Цельсия в Фаренгейты по формуле: F = C &times; 1.8 + 32</p>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Проверка:</strong> 0&deg;C = 32&deg;F, 100&deg;C = 212&deg;F</div>

<details style="margin:12px 0;"><summary style="cursor:pointer;color:#0ea5e9;font-weight:bold;">Показать решение</summary>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;margin-top:10px;">
<code class="language-go">package main

import "fmt"

func celsiusToFahrenheit(c float64) float64 {
    return c*1.8 + 32
}

func main() {
    fmt.Printf("0°C = %.1f°F\n", celsiusToFahrenheit(0))      // 32.0
    fmt.Printf("100°C = %.1f°F\n", celsiusToFahrenheit(100))  // 212.0
    fmt.Printf("37°C = %.1f°F\n", celsiusToFahrenheit(37))    // 98.6
}</code></pre>
</details>
</div>

<div style="background:#f8f9fa;border:1px solid #e0e0e0;border-radius:8px;padding:16px;margin:16px 0;">
<h3 style="margin-top:0;color:#2c3e50;">[Со звёздочкой] Задача 3: Форматирование времени</h3>

<p style="color:#333;">Напишите функцию <code>formatTime(hours, minutes int) string</code>, которая принимает часы и минуты и возвращает строку в формате &quot;HH:MM&quot;.</p>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Требования:</strong>

<ul style="margin:5px 0 0 20px;">
	<li>Часы и минуты должны быть двузначными (с ведущим нулем)</li>
	<li>Используйте fmt.Sprintf для форматирования</li>
</ul>
</div>

<details style="margin:12px 0;"><summary style="cursor:pointer;color:#0ea5e9;font-weight:bold;">Показать решение</summary>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;margin-top:10px;">
<code class="language-go">package main

import "fmt"

func formatTime(hours, minutes int) string {
    // %02d — вывести число минимум из 2 цифр, дополняя нулём слева
    return fmt.Sprintf("%02d:%02d", hours, minutes)
}

func main() {
    fmt.Println(formatTime(9, 5))    // 09:05
    fmt.Println(formatTime(14, 30))  // 14:30
    fmt.Println(formatTime(0, 0))    // 00:00
}</code></pre>
</details>
</div>
<!-- Квиз -->

<h2 id="quiz" style="color:#34495e;">8. Проверь себя</h2>

<ol style="color:#333;line-height:1.8;">
	<li><strong>Где в сигнатуре функции указывается тип возвращаемого значения?</strong>

	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>

	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;">После списка параметров (или пустых скобок), перед открывающей фигурной скобкой: <code>func имя(параметры) ТипВозврата {</code></p>
	</details>
	</li>
	<li><strong>Какое ключевое слово используется для возврата значения?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;">Ключевое слово <code>return</code></p>
	</details>
	</li>
	<li><strong>Можно ли не использовать возвращаемое значение функции?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;">Технически можно (просто вызвать функцию), но это нелогично &mdash; теряется результат вычислений. Обычно это признак ошибки в коде.</p>
	</details>
	</li>
	<li><strong>Что произойдет, если забыть return в функции с объявленным типом возврата?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;">Ошибка компиляции: &quot;missing return at end of function&quot;</p>
	</details>
	</li>
	<li><strong>Может ли функция без параметров возвращать значение?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;">Да, например: <code>func getMaxScore() int { return 100 }</code></p>
	</details>
	</li>
	<li><strong>Как использовать возвращаемое значение одной функции в другой?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;">Передать вызов первой функции как аргумент второй: <code>result := funcB(funcA())</code></p>
	</details>
	</li>
	<li><strong>Может ли return находиться в середине функции?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;">Да, return может быть в любом месте функции (например, внутри <code>if</code>). Код после return не выполняется.</p>
	</details>
	</li>
	<li><strong>Что вернет функция: <code>func test() int { x := 10; return x+5 }</code>?</strong>
	<details style="margin:8px 0;"><summary style="cursor:pointer;color:#0ea5e9;">Показать ответ</summary>
	<p style="margin:8px 0;padding:10px;background:#f0f0f0;border-radius:5px;">15 (создается переменная x со значением 10, затем возвращается x+5 = 15)</p>
	</details>
	</li>
</ol>
<!-- Что дальше -->

<div style="background:#fff3e0;border:1px solid #ffb74d;border-radius:10px;padding:14px 16px;margin:20px 0;">
<h3 style="color:#e65100;margin:0 0 8px;">🔢 Множественный возврат</h3>

<p style="color:#333;line-height:1.6;">Go &mdash; один из немногих языков, где функция может возвращать <strong>несколько значений</strong> одновременно. Это одна из ключевых особенностей языка. Типы перечисляются в скобках после параметров:</p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;margin:8px 0;">
<code class="language-go">package main

import "fmt"

// Возвращает частное и остаток от деления
func divmod(a, b int) (int, int) {
    return a / b, a % b
}

func main() {
    q, r := divmod(10, 3)
    fmt.Println("частное:", q, "остаток:", r)
}</code></pre>

<div style="background:#f0f0f0;border-left:3px solid #666;padding:10px;margin:10px 0;"><strong>Ожидаемый вывод:</strong>

<pre style="margin:5px 0 0 0;">
частное: 3 остаток: 1</pre>
</div>

<p style="color:#333;line-height:1.6;">При вызове несколько результатов принимаются через запятую: <code>q, r := divmod(...)</code>. Если какой-то из результатов вам не нужен, замените имя на <code>_</code> (blank identifier): <code>q, _ := divmod(10, 3)</code>.</p>

<p style="color:#333;line-height:1.6;">Ещё один пример &mdash; функция-обмен, возвращающая значения в обратном порядке:</p>

<pre style="background:#f8f9fa;border:1px solid #e9ecef;border-radius:8px;padding:14px;overflow-x:auto;margin:8px 0;">
<code class="language-go">func swap(a, b int) (int, int) {
    return b, a
}</code></pre>

<p style="color:#333;line-height:1.6;margin:0;">Множественный возврат особенно удобен для пары &laquo;результат + признак ошибки&raquo;. С обработкой ошибок мы познакомимся подробно в следующих курсах.</p>
</div>

<div style="background:#e3f2fd;border:1px solid #90caf9;border-radius:10px;padding:14px 16px;margin:20px 0;">
<h3 style="color:#1565c0;margin:0 0 8px;">🚀 Что дальше?</h3>

<p style="margin:0;">Теперь вы умеете создавать функции, которые не только выполняют действия, но и возвращают результаты. Следующий шаг &mdash; условные конструкции <code>if/else</code>: с ними вы сможете выбирать разные ветки логики и возвращать разные значения в зависимости от входных данных. Дальше &mdash; циклы, коллекции и другие инструменты Go.</p>
</div>
</div>
</div>
