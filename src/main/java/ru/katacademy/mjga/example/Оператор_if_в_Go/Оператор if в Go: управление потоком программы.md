<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title></title>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">Оператор if в Go: управление потоком программы</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть за 30 секунд</h3>

<ul>
	<li><strong>if</strong> проверяет условие и выполняет код только если оно истинно (<code>true</code>)</li>
	<li><strong>Фигурные скобки {}</strong> обязательны, круглые скобки вокруг условия &mdash; не нужны</li>
	<li><strong>else if</strong> создаёт цепочки проверок, <strong>else</strong> &mdash; альтернативу для всех остальных случаев</li>
	<li><strong>Короткая форма</strong> <code>if x := 10; x &gt; 5 {...}</code> позволяет объявить переменную прямо в условии</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>

<p><strong>Для лучшего понимания условных конструкций</strong> прослушайте тематический подкаст:</p>

<p style="margin: 15px 0;"><a href="https://drive.google.com/file/d/1fWQCfNvUewtscfotj0qdQWrqD4AFI3G_/view?usp=sharing" style="display: inline-block; background: #1565c0; color: white; padding: 10px 20px; text-decoration: none; border-radius: 5px; font-weight: bold;" target="_blank">🎧 Прослушать об условных операторах</a></p>

<p style="font-size: 14px; color: #666; margin-top: 10px;"><em>Откроется в новой вкладке. Слушайте и экспериментируйте с кодом.</em></p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎯 Чему вы научитесь</h4>

<ul>
	<li>✅ Писать условные конструкции с <code>if</code>, <code>else if</code> и <code>else</code></li>
	<li>✅ Использовать операторы сравнения и логические операторы</li>
	<li>✅ Применять короткую форму инициализации в <code>if</code></li>
	<li>✅ Понимать область видимости переменных в условиях</li>
	<li>✅ Форматировать код согласно стандартам Go</li>
	<li>✅ Избегать типичных ошибок с условиями</li>
</ul>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">📚 Предпосылки</h4>

<p>Для изучения этой темы вы должны знать:</p>

<ul>
	<li>Переменные и их объявление (<code>var</code>, <code>:=</code>)</li>
	<li>Базовые типы данных (<code>int</code>, <code>float64</code>, <code>string</code>, <code>bool</code>)</li>
	<li>Функции с параметрами и <code>return</code> (базовый уровень из модуля 03)</li>
	<li>Операторы сравнения (<code>==</code>, <code>!=</code>, <code>&gt;</code>, <code>&gt;=</code>, <code>&lt;</code>, <code>&lt;=</code>)</li>
	<li>Вывод данных (<code>fmt.Println</code>, <code>fmt.Printf</code>)</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. Что такое условная конструкция?</h2>

<p>В программировании часто нужно выполнять разные действия в зависимости от условий. Представьте, что вы пишете программу для банкомата. Она должна проверить баланс карты перед выдачей денег. Или приложение для интернет-магазина, которое применяет скидку только если сумма покупки больше определённой суммы. Для таких задач и существуют условные конструкции.</p>

<p>В Go основной условный оператор &mdash; это <code>if</code>. Он проверяет условие и выполняет код только если условие истинно. Давайте разберём, как это работает.</p>

<h2 style="color: #34495e; margin-top: 30px;">2. Базовый if: первое знакомство</h2>

<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #0c4a6e; margin-top: 0;">🎯 Синтаксис и правила</h4>

<p>Конструкция <code>if</code> в Go имеет простой и понятный синтаксис. Вот его базовая форма:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">if условие {
    // код выполнится только если условие == true
}</code></pre>

<p>Важно понимать, что <strong>условие</strong> &mdash; это выражение, которое возвращает булево значение (<code>bool</code>), то есть либо <code>true</code> (истина), либо <code>false</code> (ложь). Если условие истинно, код внутри фигурных скобок выполнится. Если ложно &mdash; программа пропустит этот блок и продолжит выполнение дальше.</p>

<div style="background: #fff3cd; padding: 15px; border-radius: 5px; margin-top: 15px;">
<p style="margin: 0;"><strong>⚠️ Важные правила Go:</strong></p>

<ul style="margin: 10px 0 0 0;">
	<li>Условие должно быть типа <code>bool</code> (true или false)</li>
	<li>Фигурные скобки <code>{}</code> <strong>обязательны</strong> даже для одной строки кода (в отличие от C или Java)</li>
	<li>Круглые скобки <code>()</code> вокруг условия <strong>не нужны</strong> и не рекомендуются (в отличие от многих других языков)</li>
	<li>Открывающая скобка <code>{</code> должна быть на той же строке, что и <code>if</code></li>
</ul>
</div>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">💻 Пример 1: Простая проверка возраста</h4>

<p>Давайте напишем программу, которая проверяет, является ли человек совершеннолетним:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    age := 20

    // Проверяем, что возраст больше или равен 18
    if age &gt;= 18 {
        fmt.Println("Вы совершеннолетний")
        fmt.Println("Можете голосовать на выборах")
    }

    // Эта строка выполнится в любом случае
    fmt.Println("Программа завершена")
}</code></pre>

<p>В этом примере выражение <code>age &gt;= 18</code> возвращает <code>true</code>, потому что 20 действительно больше или равно 18. Поэтому код внутри блока <code>if</code> выполнится.</p>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #2e7d32; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0; overflow-x: auto;">
<code>Вы совершеннолетний
Можете голосовать на выборах
Программа завершена</code></pre>
</div>

<p>Обратите внимание: последняя строка &quot;Программа завершена&quot; выводится независимо от условия, потому что она находится вне блока <code>if</code>.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">3. Операторы сравнения</h2>

<p>Прежде чем двигаться дальше, давайте разберём операторы сравнения, которые часто используются в условиях. Эти операторы сравнивают два значения и возвращают булев результат.</p>

<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #0c4a6e; margin-top: 0;">📊 Таблица операторов сравнения</h4>

<table style="width: 100%; border-collapse: collapse; background: white;">
	<tbody>
		<tr style="background: #e3f2fd;">
			<th style="padding: 10px; border: 1px solid #90caf9;">Оператор</th>
			<th style="padding: 10px; border: 1px solid #90caf9;">Название</th>
			<th style="padding: 10px; border: 1px solid #90caf9;">Пример</th>
			<th style="padding: 10px; border: 1px solid #90caf9;">Результат</th>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>==</code></td>
			<td style="padding: 10px; border: 1px solid #90caf9;">Равно</td>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>5 == 5</code></td>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>true</code></td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>!=</code></td>
			<td style="padding: 10px; border: 1px solid #90caf9;">Не равно</td>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>5 != 3</code></td>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>true</code></td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>&lt;</code></td>
			<td style="padding: 10px; border: 1px solid #90caf9;">Меньше</td>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>3 &lt; 5</code></td>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>true</code></td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>&lt;=</code></td>
			<td style="padding: 10px; border: 1px solid #90caf9;">Меньше или равно</td>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>5 &lt;= 5</code></td>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>true</code></td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>&gt;</code></td>
			<td style="padding: 10px; border: 1px solid #90caf9;">Больше</td>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>5 &gt; 3</code></td>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>true</code></td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>&gt;=</code></td>
			<td style="padding: 10px; border: 1px solid #90caf9;">Больше или равно</td>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>5 &gt;= 5</code></td>
			<td style="padding: 10px; border: 1px solid #90caf9;"><code>true</code></td>
		</tr>
	</tbody>
</table>

<div style="background: #fee2e2; padding: 15px; border-radius: 5px; margin-top: 15px;">
<p style="margin: 0;"><strong>❌ Частая ошибка новичков:</strong></p>

<p style="margin: 10px 0 0 0;">Путать <code>=</code> (присваивание) и <code>==</code> (сравнение). Запомните:</p>

<ul style="margin: 5px 0 0 0;">
	<li><code>x = 5</code> &mdash; присваивает переменной x значение 5</li>
	<li><code>x == 5</code> &mdash; проверяет, равна ли переменная x числу 5</li>
</ul>
</div>
</div>

<h2 style="color: #34495e; margin-top: 30px;">4. if-else: выбор из двух вариантов</h2>

<p>Часто нужно выполнить одно действие, если условие истинно, и другое &mdash; если ложно. Для этого используется конструкция <code>if-else</code>. Блок <code>else</code> выполняется только когда условие в <code>if</code> ложно.</p>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">💻 Пример 2: Проверка баланса при покупке</h4>

<p>Представим систему оплаты в интернет-магазине. Нужно проверить, достаточно ли денег на счету для покупки:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    balance := 1500.50  // Баланс на счету
    price := 2000.00    // Цена товара

    if balance &gt;= price {
        // Этот блок выполнится, если денег достаточно
        fmt.Println("Покупка одобрена")
        fmt.Printf("Остаток: %.2f руб.\n", balance-price)
    } else {
        // Этот блок выполнится, если денег недостаточно
        fmt.Println("Недостаточно средств")
        fmt.Printf("Не хватает: %.2f руб.\n", price-balance)
    }
}</code></pre>

<p>В этом примере условие <code>balance &gt;= price</code> проверяет, достаточно ли денег. Поскольку 1500.50 меньше 2000.00, условие ложно, и выполнится блок <code>else</code>.</p>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #1565c0; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0; overflow-x: auto;">
<code>Недостаточно средств
Не хватает: 499.50 руб.</code></pre>
</div>

<div style="background: #fee2e2; padding: 15px; border-radius: 5px; margin-top: 15px;">
<p style="margin: 0;"><strong>❌ Важное правило Go:</strong></p>

<p style="margin: 10px 0 0 0;"><code>else</code> должен быть на той же строке, что и закрывающая скобка <code>}</code> от <code>if</code>. Это связано с автоматической подстановкой точки с запятой в Go.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code class="language-go">// ✅ Правильно
if condition {
    // код
} else {
    // код
}

// ❌ Неправильно - вызовет ошибку компиляции
if condition {
    // код
}
else {  // Ошибка: unexpected else
    // код
}</code></pre>
</div>
</div>

<h2 style="color: #34495e; margin-top: 30px;">5. else if: цепочки условий</h2>

<p>Когда нужно проверить несколько условий последовательно, используются цепочки <code>else if</code>. Это позволяет создавать многоуровневые проверки, где выполнится только первый блок с истинным условием.</p>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #e65100; margin-top: 0;">💻 Пример 3: Система оценок</h4>

<p>Создадим систему, которая преобразует числовую оценку в буквенную и даёт обратную связь студенту:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    score := 85

    // Проверяем условия по порядку сверху вниз
    if score &gt;= 90 {
        fmt.Println("Оценка: Отлично (A)")
        fmt.Println("Вы показали выдающийся результат!")
    } else if score &gt;= 75 {
        fmt.Println("Оценка: Хорошо (B)")
        fmt.Println("Хороший результат, продолжайте в том же духе")
    } else if score &gt;= 60 {
        fmt.Println("Оценка: Удовлетворительно (C)")
        fmt.Println("Есть над чем поработать")
    } else {
        fmt.Println("Оценка: Неудовлетворительно (D)")
        fmt.Println("Требуется пересдача")
    }
}</code></pre>

<p>Важно понимать логику выполнения: Go проверяет условия последовательно сверху вниз. Как только находится первое истинное условие, выполняется соответствующий блок кода, а остальные проверки пропускаются.</p>

<p>В нашем примере score = 85:</p>

<ol>
	<li>Проверяется <code>score &gt;= 90</code> (85 &gt;= 90) &mdash; ложь, идём дальше</li>
	<li>Проверяется <code>score &gt;= 75</code> (85 &gt;= 75) &mdash; истина! Выполняется этот блок</li>
	<li>Остальные условия не проверяются</li>
</ol>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #e65100; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0; overflow-x: auto;">
<code>Оценка: Хорошо (B)
Хороший результат, продолжайте в том же духе</code></pre>
</div>

<div style="background: #fef3c7; padding: 10px; border-radius: 5px; margin-top: 15px;">
<p style="margin: 0;"><strong>⚠️ Важно:</strong> <code>else if</code> пишется как два отдельных слова (не <code>elseif</code> или <code>elif</code> как в некоторых других языках)</p>
</div>
</div>

<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #0c4a6e; margin-top: 0;">🔄 Вложенные if vs else if</h4>

<p>Важно понимать разницу между вложенными <code>if</code> и цепочкой <code>else if</code>:</p>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
<div style="background: white; padding: 15px; border-radius: 5px;">
<h5 style="color: #0c4a6e; margin-top: 0;">Вложенные if</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code class="language-go">if age &gt;= 18 {
    if hasLicense {
        fmt.Println("Можете водить")
    }
}</code></pre>

<p>Используйте когда:</p>

<ul>
	<li>Второе условие имеет смысл только при истинности первого</li>
	<li>Условия логически зависимы</li>
</ul>
</div>

<div style="background: white; padding: 15px; border-radius: 5px;">
<h5 style="color: #0c4a6e; margin-top: 0;">Цепочка else if</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code class="language-go">if score &gt;= 90 {
    fmt.Println("Отлично")
} else if score &gt;= 75 {
    fmt.Println("Хорошо")
}</code></pre>

<p>Используйте когда:</p>

<ul>
	<li>Проверяются взаимоисключающие варианты</li>
	<li>Нужна последовательная проверка диапазонов</li>
</ul>
</div>
</div>
</div>

<h2 style="color: #34495e; margin-top: 30px;">6. Логические операторы в условиях</h2>

<p>Часто одного условия недостаточно. Например, для получения студенческой скидки нужно быть и студентом, и иметь возраст от 18 до 25 лет. Для таких сложных проверок используются логические операторы.</p>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">🔧 Операторы &amp;&amp; (И), || (ИЛИ), ! (НЕ)</h4>

<div style="background: white; padding: 15px; border-radius: 5px; margin-bottom: 15px;">
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #e8f5e9;">
			<th style="padding: 10px; border: 1px solid #c8e6c9;">Оператор</th>
			<th style="padding: 10px; border: 1px solid #c8e6c9;">Название</th>
			<th style="padding: 10px; border: 1px solid #c8e6c9;">Описание</th>
			<th style="padding: 10px; border: 1px solid #c8e6c9;">Пример</th>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #c8e6c9;"><code>&amp;&amp;</code></td>
			<td style="padding: 10px; border: 1px solid #c8e6c9;">И (AND)</td>
			<td style="padding: 10px; border: 1px solid #c8e6c9;">Оба условия должны быть истинны</td>
			<td style="padding: 10px; border: 1px solid #c8e6c9;"><code>x &gt; 0 &amp;&amp; x &lt; 10</code></td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #c8e6c9;"><code>||</code></td>
			<td style="padding: 10px; border: 1px solid #c8e6c9;">ИЛИ (OR)</td>
			<td style="padding: 10px; border: 1px solid #c8e6c9;">Хотя бы одно условие должно быть истинно</td>
			<td style="padding: 10px; border: 1px solid #c8e6c9;"><code>day == &quot;Сб&quot; || day == &quot;Вс&quot;</code></td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #c8e6c9;"><code>!</code></td>
			<td style="padding: 10px; border: 1px solid #c8e6c9;">НЕ (NOT)</td>
			<td style="padding: 10px; border: 1px solid #c8e6c9;">Инвертирует условие</td>
			<td style="padding: 10px; border: 1px solid #c8e6c9;"><code>!isWeekend</code></td>
		</tr>
	</tbody>
</table>
</div>

<h4 style="color: #2e7d32; margin-top: 20px;">💻 Пример 4: Комбинирование логических операторов</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    age := 19
    hasPermission := true
    isWeekend := false

    // Оператор &amp;&amp; (И) - оба условия должны быть истинны
    if age &gt;= 18 &amp;&amp; hasPermission {
        fmt.Println("Доступ разрешён (совершеннолетний И есть разрешение)")
    }

    // Оператор || (ИЛИ) - хотя бы одно условие должно быть истинно
    if age &lt; 14 || age &gt; 65 {
        fmt.Println("Льготный билет (ребёнок ИЛИ пенсионер)")
    } else {
        fmt.Println("Полная стоимость билета")
    }

    // Оператор ! (НЕ) - инвертирует условие
    if !isWeekend {
        fmt.Println("Сегодня рабочий день")
    }

    // Комбинация операторов с группировкой скобками для читабельности
    if (age &gt;= 18 &amp;&amp; age &lt;= 25) &amp;&amp; (hasPermission || isWeekend) {
        fmt.Println("Студенческая скидка доступна")
    }
}</code></pre>

<p>Обратите внимание на последнее условие: мы используем скобки для группировки. Хотя они не обязательны с точки зрения синтаксиса, они улучшают читабельность сложных условий.</p>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #2e7d32; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0; overflow-x: auto;">
<code>Доступ разрешён (совершеннолетний И есть разрешение)
Полная стоимость билета
Сегодня рабочий день
Студенческая скидка доступна</code></pre>
</div>
</div>

<div style="background: #e3f2fd; padding: 15px; border-radius: 5px; margin: 15px 0;">
<h5 style="color: #1565c0; margin-top: 0;">⚡ Важная концепция: короткое замыкание (short-circuit)</h5>

<p>Go использует &quot;ленивые&quot; вычисления для логических операторов. Это означает, что если результат уже очевиден, дальнейшие проверки не выполняются:</p>

<ul>
	<li>Для <code>&amp;&amp;</code>: если первое условие ложно, второе не проверяется (результат всё равно будет false)</li>
	<li>Для <code>||</code>: если первое условие истинно, второе не проверяется (результат всё равно будет true)</li>
</ul>

<p>Это важно для производительности и безопасности. Например:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    num := 10
    den := 0  // делитель равен нулю

    // Благодаря короткому замыканию, деление не выполнится
    // и программа не упадёт с паникой
    if den != 0 &amp;&amp; num/den &gt; 1 {
        fmt.Println("Результат больше 1")
    } else {
        fmt.Println("Деление на ноль предотвращено!")
    }

    // Если бы мы написали наоборот, была бы паника:
    // if num/den &gt; 1 &amp;&amp; den != 0 {  // Паника!
}</code></pre>

<p>В этом примере условие <code>den != 0</code> проверяется первым. Так как оно ложно (den равен 0), второе условие <code>num/den &gt; 1</code> не вычисляется, и мы избегаем деления на ноль.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">7. Короткая форма с инициализацией</h2>

<p>Go позволяет объявить переменную прямо в условии <code>if</code>. Это удобно, когда переменная нужна только для проверки и внутри блоков <code>if</code>/<code>else</code>. Такая форма делает код более компактным и ограничивает область видимости переменной.</p>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">🎯 Синтаксис короткой формы</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">if переменная := выражение; условие {
    // переменная доступна здесь
} else {
    // переменная доступна и здесь
}
// переменная НЕ доступна здесь</code></pre>

<p>Сначала выполняется инициализация переменной, затем проверяется условие. Переменная существует только внутри всей конструкции <code>if-else</code>.</p>

<h4 style="color: #6a1b9a; margin-top: 20px;">💻 Пример 5: Область видимости в короткой форме</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    fmt.Println("=== Проверка температуры ===")

    // Короткая форма: объявляем temp прямо в if
    // temp существует только внутри конструкции if-else if-else
    if temp := -5; temp &lt; 0 {
        fmt.Printf("При %d°C вода замерзает\n", temp)
        fmt.Println("Состояние: лёд")
    } else if temp &lt; 100 {
        fmt.Printf("При %d°C вода в жидком состоянии\n", temp)
        fmt.Println("Состояние: жидкость")
    } else {
        fmt.Printf("При %d°C вода кипит\n", temp)
        fmt.Println("Состояние: пар")
    }

    // fmt.Println(temp)  // Ошибка компиляции! temp не существует вне if

    fmt.Println("\n=== Проверка делимости ===")

    // Оператор % — остаток от деления (17 % 5 = 2, потому что 17 = 5*3 + 2)
    if remainder := 17 % 5; remainder == 0 {
        fmt.Println("17 делится на 5 без остатка")
    } else {
        fmt.Printf("17 делится на 5 с остатком %d\n", remainder)
    }
    // remainder тоже недоступен здесь
}</code></pre>

<p>Короткая форма особенно полезна, когда нужно вычислить значение и сразу его проверить, при этом не засоряя внешнюю область видимости временными переменными.</p>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #6a1b9a; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0; overflow-x: auto;">
<code>=== Проверка температуры ===
При -5°C вода замерзает
Состояние: лёд

=== Проверка делимости ===
17 делится на 5 с остатком 2</code></pre>
</div>

<div style="background: #fff3cd; padding: 15px; border-radius: 5px; margin-top: 15px;">
<h4 style="color: #856404; margin-top: 0;">⚠️ Осторожно: одинаковые имена переменных</h4>

<p>Если переменная в короткой форме <code>if</code> называется так же, как уже существующая &mdash; внутри <code>if</code> будет использоваться <strong>новая</strong>, а снаружи останется <strong>старая</strong>:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">x := 10
if x := 5; x &gt; 0 {
    fmt.Println("внутри:", x)   // выведет: 5 (новая переменная)
}
fmt.Println("снаружи:", x)      // выведет: 10 (старая переменная)</code></pre>

<p><strong>Совет:</strong> Чтобы не запутаться, давайте разные имена &mdash; например, <code>n</code> вместо повторного <code>x</code>.</p>
</div>
</div>

<h2 style="color: #34495e; margin-top: 30px;">8. Стиль и форматирование</h2>

<p>В Go есть официальный инструмент форматирования кода &mdash; <code>go fmt</code>. Он автоматически приводит ваш код к стандартному стилю. Это важно для читабельности и совместной работы.</p>

<div style="background: #f8f9fa; border: 1px solid #dee2e6; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #495057; margin-top: 0;">📐 Правила хорошего стиля в Go</h4>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
<div style="background: #d4edda; padding: 15px; border-radius: 5px;">
<h5 style="color: #155724; margin-top: 0;">✅ Хороший стиль</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">// Без лишних скобок
if x &gt; 0 {
    fmt.Println("Положительное")
}

// Компактная проверка
if score &gt;= 60 {
    fmt.Println("Зачёт")
}</code></pre>
</div>

<div style="background: #fee2e2; padding: 15px; border-radius: 5px;">
<h5 style="color: #991b1b; margin-top: 0;">❌ Плохой стиль</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">// Лишние скобки (не нужны)
if (x &gt; 0) {
    fmt.Println("Положительное")
}

// Слишком сложно
if ((score &gt;= 60)) {
    fmt.Println("Зачёт")
}</code></pre>
</div>
</div>

<div style="background: #e3f2fd; padding: 15px; border-radius: 5px; margin-top: 15px;">
<h4 style="color: #1565c0; margin-top: 0;">🛠️ Использование go fmt</h4>

<p>Чтобы отформатировать ваш код, просто выполните в терминале:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code class="language-bash"># Форматировать текущий файл
go fmt main.go

# Форматировать все файлы в текущей директории и поддиректориях
go fmt ./...</code></pre>

<p><strong>Совет:</strong> Запускайте <code>go fmt</code> перед каждым коммитом или настройте автоформатирование в вашем редакторе кода.</p>
</div>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Шпаргалка по синтаксису</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">// Базовый if
if условие {
    // код
}

// if-else
if условие {
// код если true
} else {
// код если false
}

// Цепочка else if (два слова!)
if условие1 {
// код
} else if условие2 {
// код
} else if условие3 {
// код
} else {
// код по умолчанию
}

// Короткая форма с инициализацией
if x := выражение; условие {
// x доступен здесь
} else {
// x доступен и здесь
}
// x НЕ доступен здесь

// Логические операторы
if условие1 &amp;&amp; условие2 {  // И
// выполнится если оба истинны
}

if условие1 || условие2 {  // ИЛИ
// выполнится если хотя бы одно истинно
}

if !условие {  // НЕ
// выполнится если условие ложно
}</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Частые ошибки и как их исправлять</h2>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #fee2e2;">
			<th style="padding: 10px; border: 1px solid #fca5a5;">Симптом</th>
			<th style="padding: 10px; border: 1px solid #fca5a5;">Причина</th>
			<th style="padding: 10px; border: 1px solid #fca5a5;">Как исправить</th>
		</tr>
		<tr style="background: white;">
			<td style="padding: 10px; border: 1px solid #fca5a5;"><code>non-bool condition</code></td>
			<td style="padding: 10px; border: 1px solid #fca5a5;">Использование не-bool в условии</td>
			<td style="padding: 10px; border: 1px solid #fca5a5;">Убедитесь что условие возвращает <code>bool</code></td>
		</tr>
		<tr style="background: white;">
			<td style="padding: 10px; border: 1px solid #fca5a5;"><code>syntax error: unexpected else</code></td>
			<td style="padding: 10px; border: 1px solid #fca5a5;"><code>else</code> на новой строке</td>
			<td style="padding: 10px; border: 1px solid #fca5a5;">Поместите <code>else</code> на ту же строку что и <code>}</code></td>
		</tr>
		<tr style="background: white;">
			<td style="padding: 10px; border: 1px solid #fca5a5;"><code>undefined: variable</code></td>
			<td style="padding: 10px; border: 1px solid #fca5a5;">Переменная из короткой формы вне области видимости</td>
			<td style="padding: 10px; border: 1px solid #fca5a5;">Объявите переменную до <code>if</code> если нужна после</td>
		</tr>
		<tr style="background: white;">
			<td style="padding: 10px; border: 1px solid #fca5a5;">Путаница с <code>=</code> и <code>==</code></td>
			<td style="padding: 10px; border: 1px solid #fca5a5;"><code>=</code> присваивание, <code>==</code> сравнение</td>
			<td style="padding: 10px; border: 1px solid #fca5a5;">Используйте <code>==</code> для сравнения в условиях</td>
		</tr>
		<tr style="background: white;">
			<td style="padding: 10px; border: 1px solid #fca5a5;">Пишут <code>elseif</code> или <code>elif</code></td>
			<td style="padding: 10px; border: 1px solid #fca5a5;">В Go только <code>else if</code> (два слова)</td>
			<td style="padding: 10px; border: 1px solid #fca5a5;">Всегда пишите как два отдельных слова</td>
		</tr>
		<tr style="background: white;">
			<td style="padding: 10px; border: 1px solid #fca5a5;">Теневание переменных</td>
			<td style="padding: 10px; border: 1px solid #fca5a5;">Переменная с <code>:=</code> внутри if затеняет внешнюю</td>
			<td style="padding: 10px; border: 1px solid #fca5a5;">Используйте разные имена для ясности</td>
		</tr>
		<tr style="background: white;">
			<td style="padding: 10px; border: 1px solid #fca5a5;">Использование <code>println</code> вместо пакета fmt</td>
			<td style="padding: 10px; border: 1px solid #fca5a5;">Встроенная функция vs пакет fmt</td>
			<td style="padding: 10px; border: 1px solid #fca5a5;">Всегда используйте <code>fmt.Println</code></td>
		</tr>
	</tbody>
</table>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Практика: упражнения для закрепления</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">📝 Упражнение 1: Переписать вложенные if в цепочку else if</h4>

<p><strong>Задача:</strong> Определите уровень игрока по количеству очков, используя цепочку <code>else if</code>.</p>

<details><summary style="cursor: pointer; color: #2e7d32; font-weight: bold;">Показать решение</summary>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin-top: 10px; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    points := 250

    if points &gt;= 300 {
        fmt.Println("Уровень: Мастер")
    } else if points &gt;= 200 {
        fmt.Println("Уровень: Эксперт")
    } else if points &gt;= 100 {
        fmt.Println("Уровень: Продвинутый")
    } else {
        fmt.Println("Уровень: Новичок")
    }
}</code></pre>

<p><strong>Ожидаемый вывод:</strong> <code>Уровень: Эксперт</code></p>
</details>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">📝 Упражнение 2: Короткая инициализация и область видимости</h4>

<p><strong>Задача:</strong> Используйте короткую форму <code>if</code> для проверки чётности числа.</p>

<details><summary style="cursor: pointer; color: #1565c0; font-weight: bold;">Показать решение</summary>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin-top: 10px; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    number := 17

    if remainder := number % 2; remainder == 0 {
        fmt.Printf("%d - чётное число\n", number)
        fmt.Printf("Остаток от деления на 2: %d\n", remainder)
    } else {
        fmt.Printf("%d - нечётное число\n", number)
        fmt.Printf("Остаток от деления на 2: %d\n", remainder)
    }

    fmt.Println("Проверка завершена")
}</code></pre>

<p><strong>Ожидаемый вывод:</strong></p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code>17 - нечётное число
Остаток от деления на 2: 1
Проверка завершена</code></pre>
</details>
</div>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #e65100; margin-top: 0;">📝 Упражнение 3: Логические операторы</h4>

<p><strong>Задача:</strong> Реализуйте систему контроля доступа с использованием логических операторов.</p>

<details><summary style="cursor: pointer; color: #e65100; font-weight: bold;">Показать решение</summary>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin-top: 10px; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    hasCard := true
    pinCorrect := false
    isEmergency := true

    // Доступ разрешён если (карта И правильный PIN) ИЛИ экстренная ситуация
    if (hasCard &amp;&amp; pinCorrect) || isEmergency {
        fmt.Println("Доступ разрешён")
        if isEmergency &amp;&amp; !pinCorrect {
            fmt.Println("Внимание: экстренный доступ без PIN")
        }
    } else {
        fmt.Println("Доступ запрещён")
        if hasCard &amp;&amp; !pinCorrect {
            fmt.Println("Причина: неверный PIN")
        } else if !hasCard {
            fmt.Println("Причина: нет карты")
        }
    }
}</code></pre>

<p><strong>Ожидаемый вывод:</strong></p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code>Доступ разрешён
Внимание: экстренный доступ без PIN</code></pre>
</details>
</div>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">📝 Упражнение 4: Проверка високосного года</h4>

<p><strong>Задача:</strong> Определите, является ли год високосным. Год високосный, если он делится на 400, ИЛИ делится на 4 И не делится на 100.</p>

<details><summary style="cursor: pointer; color: #6a1b9a; font-weight: bold;">Показать решение</summary>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin-top: 10px; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    year := 2024

    // Високосный если: делится на 400 ИЛИ (делится на 4 И не делится на 100)
    if (year%400 == 0) || (year%4 == 0 &amp;&amp; year%100 != 0) {
        fmt.Printf("%d - високосный год\n", year)
        fmt.Println("В феврале 29 дней")
    } else {
        fmt.Printf("%d - обычный год\n", year)
        fmt.Println("В феврале 28 дней")
    }

    // Проверим другие годы
    fmt.Println("\nПроверка других лет:")

    year = 1900
    if (year%400 == 0) || (year%4 == 0 &amp;&amp; year%100 != 0) {
        fmt.Printf("%d - високосный\n", year)
    } else {
        fmt.Printf("%d - обычный\n", year)
    }

    year = 2000
    if (year%400 == 0) || (year%4 == 0 &amp;&amp; year%100 != 0) {
        fmt.Printf("%d - високосный\n", year)
    } else {
        fmt.Printf("%d - обычный\n", year)
    }

    year = 2023
    if (year%400 == 0) || (year%4 == 0 &amp;&amp; year%100 != 0) {
        fmt.Printf("%d - високосный\n", year)
    } else {
        fmt.Printf("%d - обычный\n", year)
    }
}</code></pre>

<p><strong>Ожидаемый вывод:</strong></p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code>2024 - високосный год
В феврале 29 дней

Проверка других лет:
1900 - обычный
2000 - високосный
2023 - обычный</code></pre>
</details>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">📝 Упражнение 5: Проверка доставки</h4>

<p><strong>Задача:</strong> Определите возможность доставки товара. Доставка доступна если вес не больше 10 кг И город - Москва или Санкт-Петербург.</p>

<details><summary style="cursor: pointer; color: #2e7d32; font-weight: bold;">Показать решение</summary>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin-top: 10px; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    weightKg := 7
    city := "Москва"

    if weightKg &lt;= 10 &amp;&amp; (city == "Москва" || city == "Санкт-Петербург") {
        fmt.Println("✅ Доставка доступна")
        fmt.Printf("Вес: %d кг, Город: %s\n", weightKg, city)

        // Дополнительная логика для разных городов
        if city == "Москва" {
            fmt.Println("Срок доставки: 1-2 дня")
        } else {
            fmt.Println("Срок доставки: 2-3 дня")
        }
    } else {
        fmt.Println("❌ Доставка недоступна")

        // Объясняем причину
        if weightKg &gt; 10 {
            fmt.Printf("Причина: вес %d кг превышает лимит 10 кг\n", weightKg)
        } else {
            fmt.Printf("Причина: доставка в город %s не осуществляется\n", city)
        }
    }
}</code></pre>

<p><strong>Ожидаемый вывод:</strong></p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code>✅ Доставка доступна
Вес: 7 кг, Город: Москва
Срок доставки: 1-2 дня</code></pre>
</details>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Итоги</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p>Вы изучили оператор <code>if</code> &mdash; фундаментальный инструмент управления потоком выполнения программы в Go. Теперь вы умеете:</p>

<ul>
	<li><strong>Использовать базовый if</strong> для выполнения кода при истинном условии</li>
	<li><strong>Применять else</strong> для альтернативного пути выполнения</li>
	<li><strong>Создавать цепочки else if</strong> для множественных проверок (помните &mdash; два слова!)</li>
	<li><strong>Использовать операторы сравнения</strong> (<code>==</code>, <code>!=</code>, <code>&lt;</code>, <code>&gt;</code>, <code>&lt;=</code>, <code>&gt;=</code>)</li>
	<li><strong>Комбинировать условия</strong> с логическими операторами (<code>&amp;&amp;</code>, <code>||</code>, <code>!</code>)</li>
	<li><strong>Применять короткую форму</strong> для объявления переменных с ограниченной областью видимости</li>
	<li><strong>Понимать короткое замыкание</strong> для безопасных и эффективных проверок</li>
	<li><strong>Форматировать код</strong> с помощью <code>go fmt</code></li>
</ul>

<div style="background: white; padding: 15px; border-radius: 5px; margin-top: 15px;">
<h4 style="color: #1565c0; margin-top: 0;">🚀 Что изучать дальше</h4>

<p>После освоения условных конструкций, рекомендуем изучить:</p>

<ul>
	<li><strong>Циклы for</strong> &mdash; единственный тип цикла в Go, но очень гибкий</li>
	<li><strong>break и continue</strong> &mdash; управление выполнением цикла</li>
	<li><strong>Массивы и срезы</strong> &mdash; коллекции данных в Go</li>
	<li><strong>Строки и Unicode</strong> &mdash; работа с текстом в Go</li>
</ul>
</div>
</div>

<h2 style="color: #34495e; margin-top: 30px;">✅ Чек-лист самопроверки</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<ul style="list-style: none; padding-left: 0;">
	<li>☑️ Я понимаю, что условие в <code>if</code> должно быть типа <code>bool</code></li>
	<li>☑️ Я знаю, что фигурные скобки <code>{}</code> обязательны даже для одной строки</li>
	<li>☑️ Я помню, что круглые скобки <code>()</code> вокруг условия не нужны</li>
	<li>☑️ Я умею использовать <code>else</code> и <code>else if</code> (два слова!)</li>
	<li>☑️ Я знаю все операторы сравнения и их отличия</li>
	<li>☑️ Я понимаю разницу между <code>=</code> (присваивание) и <code>==</code> (сравнение)</li>
	<li>☑️ Я знаю логические операторы <code>&amp;&amp;</code>, <code>||</code>, <code>!</code></li>
	<li>☑️ Я понимаю концепцию короткого замыкания</li>
	<li>☑️ Я могу использовать короткую форму с инициализацией</li>
	<li>☑️ Я понимаю область видимости переменных в короткой форме</li>
	<li>☑️ Я знаю, что одинаковые имена в короткой форме if создают новые переменные</li>
	<li>☑️ Я умею использовать <code>go fmt</code> для форматирования кода</li>
	<li>☑️ Я всегда использую <code>fmt.Println</code> вместо встроенной <code>println</code></li>
</ul>
</div>
</div>
</div>
