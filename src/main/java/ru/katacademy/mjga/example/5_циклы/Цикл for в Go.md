<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title></title>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50;">Цикл for в Go: единственный, но универсальный</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть за 30 секунд</h3>

<ul>
	<li>В Go есть только один цикл &mdash; <code>for</code>, но он заменяет все остальные</li>
	<li>Классическая форма: <code>for init; condition; post {}</code></li>
	<li>Сокращённая форма (как while): <code>for condition {}</code></li>
	<li>Бесконечный цикл: <code>for {}</code></li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>

<p><strong>Для лучшего понимания циклов</strong> прослушайте тематический подкаст:</p>

<p style="margin: 15px 0;"><a href="https://drive.google.com/file/d/1q_VlYQHtcgsDyBF5qV_JulmJMMdUy7Ul/view?usp=sharing" style="display: inline-block; background: #1565c0; color: white; padding: 10px 20px; text-decoration: none; border-radius: 5px; font-weight: bold;" target="_blank">🎧 Прослушать о циклах</a></p>

<p style="font-size: 14px; color: #666; margin-top: 10px;"><em>Откроется в новой вкладке. Слушайте и экспериментируйте с кодом.</em></p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎯 Чему вы научитесь</h4>

<ul>
	<li>✅ Писать все базовые формы цикла <code>for</code></li>
	<li>✅ Избегать типичных ошибок с циклами</li>
	<li>✅ Писать читаемые и эффективные циклы</li>
</ul>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">📚 Предпосылки</h4>

<p>Для изучения этой темы вы должны знать:</p>

<ul>
	<li>Переменные и их объявление (<code>var</code>, <code>:=</code>)</li>
	<li>Базовые типы данных (<code>int</code>, <code>bool</code>)</li>
	<li>Условные операторы (<code>if</code>, <code>else</code>)</li>
	<li>Операторы сравнения и логические операторы</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. Философия циклов в Go</h2>

<p>В отличие от большинства языков программирования, где есть <code>while</code>, <code>do-while</code>, <code>for</code> и <code>foreach</code>, в Go есть только один цикл &mdash; <code>for</code>. Это может показаться ограничением, но на самом деле это преимущество. Один универсальный инструмент, который покрывает все случаи использования, делает язык проще и понятнее.</p>

<p>Цикл <code>for</code> в Go имеет несколько форм, каждая из которых оптимизирована под конкретную задачу. Давайте изучим их последовательно, от самой полной к самой простой.</p>

<h2 style="color: #34495e; margin-top: 30px;">2. Классическая форма for</h2>

<p>Классическая форма цикла <code>for</code> состоит из трёх частей, разделённых точкой с запятой:</p>

<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #0c4a6e; margin-top: 0;">🎯 Синтаксис классического for</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">for инициализация; условие; пост-выражение {
    // тело цикла
}</code></pre>

<p>Разберём каждую часть:</p>

<ul>
	<li><strong>Инициализация</strong> &mdash; выполняется один раз перед началом цикла. Обычно здесь объявляется счётчик</li>
	<li><strong>Условие</strong> &mdash; проверяется перед каждой итерацией. Если истинно, тело цикла выполняется. Должно быть типа <code>bool</code></li>
	<li><strong>Пост-выражение</strong> &mdash; простой оператор, выполняемый после каждой итерации тела цикла. Чаще всего это <code>i++</code> или <code>i--</code>, но допустимы и другие операции: <code>i += 2</code>, <code>value *= 2</code>, вызов функции и т.п. (см. Пример 2 с <code>i--</code> и Пример 4 с <code>value *= 2</code>)</li>
</ul>

<div style="background: #fff3cd; padding: 15px; border-radius: 5px; margin-top: 15px;">
<p style="margin: 0;"><strong>⚠️ Важные правила:</strong></p>

<ul style="margin: 10px 0 0 0;">
	<li>Фигурные скобки <code>{}</code> обязательны всегда, даже для одной строки</li>
	<li>Круглые скобки вокруг заголовка цикла не нужны (в отличие от C/Java)</li>
	<li>Любую из трёх частей можно опустить</li>
</ul>
</div>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">💻 Пример 1: Классический счётчик от 1 до 5</h4>

<p>Самый распространённый случай использования &mdash; перебор чисел в диапазоне:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    // i объявляется и инициализируется значением 1
    // Цикл продолжается пока i &lt;= 5
    // После каждой итерации i увеличивается на 1
    for i := 1; i &lt;= 5; i++ {
        fmt.Println(i)
    }

    // Переменная i здесь уже не существует
    fmt.Println("Цикл завершён")
}</code></pre>

<p>Давайте проследим выполнение цикла пошагово:</p>

<ol>
	<li>Инициализация: <code>i := 1</code> &mdash; создаётся переменная i со значением 1</li>
	<li>Проверка условия: <code>1 &lt;= 5</code> &mdash; истина, выполняем тело</li>
	<li>Вывод: 1</li>
	<li>Пост-выражение: <code>i++</code> &mdash; теперь i равно 2</li>
	<li>Проверка условия: <code>2 &lt;= 5</code> &mdash; истина, выполняем тело</li>
	<li>И так далее...</li>
	<li>Когда i станет 6, условие <code>6 &lt;= 5</code> будет ложным, цикл завершится</li>
</ol>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #2e7d32; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0; overflow-x: auto;">
<code>1
2
3
4
5
Цикл завершён</code></pre>
</div>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">💻 Пример 2: Обратный отсчёт</h4>

<p>Цикл может считать и в обратном направлении:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    fmt.Println("Запуск через:")

    // Считаем от 10 до 1
    for i := 10; i &gt;= 1; i-- {
        fmt.Printf("%d...\n", i)
    }

    fmt.Println("СТАРТ! 🚀")
}</code></pre>

<p>Здесь мы используем <code>i--</code> для уменьшения счётчика и условие <code>i &gt;= 1</code> для продолжения цикла.</p>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #1565c0; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0; overflow-x: auto;">
<code>Запуск через:
10...
9...
8...
7...
6...
5...
4...
3...
2...
1...
СТАРТ! 🚀</code></pre>
</div>
</div>

<h2 style="color: #34495e; margin-top: 30px;">3. Цикл for как while</h2>

<p>Если опустить инициализацию и пост-выражение, получится аналог цикла <code>while</code> из других языков. Это удобно, когда счётчик уже существует или когда условие не связано со счётчиком.</p>

<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #0c4a6e; margin-top: 0;">🎯 Синтаксис for как while</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">for условие {
    // тело цикла
}</code></pre>

<p>Цикл выполняется, пока условие истинно. Важно не забывать изменять переменные внутри цикла, чтобы условие в какой-то момент стало ложным!</p>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">💻 Пример 3: Цикл с внешним счётчиком</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    count := 5

    // Цикл продолжается, пока count &gt; 0
    for count &gt; 0 {
        fmt.Printf("Осталось попыток: %d\n", count)
        count-- // ВАЖНО: не забыть уменьшить счётчик!
    }

    fmt.Println("Попытки закончились")
}</code></pre>

<p>Обратите внимание: мы должны сами позаботиться об изменении переменной <code>count</code> внутри цикла. Если забыть <code>count--</code>, получится бесконечный цикл!</p>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #2e7d32; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0; overflow-x: auto;">
<code>Осталось попыток: 5
Осталось попыток: 4
Осталось попыток: 3
Осталось попыток: 2
Осталось попыток: 1
Попытки закончились</code></pre>
</div>
</div>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #e65100; margin-top: 0;">💻 Пример 4: Удвоение числа до предела</h4>

<p>Вот пример, где условие не связано напрямую со счётчиком итераций:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    value := 1
    limit := 100

    fmt.Println("Удваиваем число до достижения предела:")

    for value &lt; limit {
        fmt.Printf("Текущее значение: %d\n", value)
        value *= 2  // Удваиваем значение
    }

    fmt.Printf("Финальное значение: %d (превысило предел %d)\n", value, limit)
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #e65100; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0; overflow-x: auto;">
<code>Удваиваем число до достижения предела:
Текущее значение: 1
Текущее значение: 2
Текущее значение: 4
Текущее значение: 8
Текущее значение: 16
Текущее значение: 32
Текущее значение: 64
Финальное значение: 128 (превысило предел 100)</code></pre>
</div>
</div>

<h2 style="color: #34495e; margin-top: 30px;">4. Бесконечный цикл</h2>

<p>Если опустить все три части (или просто условие), получится бесконечный цикл. Это полезно для серверов, игровых циклов или когда условие выхода проверяется внутри цикла.</p>

<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #0c4a6e; margin-top: 0;">🎯 Синтаксис бесконечного цикла</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">for {
    // тело цикла
    // выход через return
}</code></pre>

<p>Без явного выхода такой цикл будет выполняться вечно. Пока мы знаем один способ выйти из него &mdash; <code>return</code>, который завершает функцию. Другие способы управления циклом (<code>break</code>, <code>continue</code>) мы изучим в следующем модуле.</p>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">💻 Пример 5: Бесконечный цикл с return</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    sum := 0
    count := 0

    fmt.Println("Суммируем числа 1, 2, 3... пока сумма не превысит 20")

    for {
        count++
        sum += count
        fmt.Printf("Добавили %d, сумма = %d\n", count, sum)

        if sum &gt; 20 {
            fmt.Printf("Сумма превысила 20! Просуммировали числа от 1 до %d\n", count)
            return  // Выходим из функции main
        }
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #2e7d32; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0; overflow-x: auto;">
<code>Суммируем числа 1, 2, 3... пока сумма не превысит 20
Добавили 1, сумма = 1
Добавили 2, сумма = 3
Добавили 3, сумма = 6
Добавили 4, сумма = 10
Добавили 5, сумма = 15
Добавили 6, сумма = 21
Сумма превысила 20! Просуммировали числа от 1 до 6</code></pre>
</div>
</div>

<h2 style="color: #34495e; margin-top: 30px;">5. Типичные ошибки и как их избежать</h2>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #991b1b; margin-top: 0;">❌ Ошибка 1: Бесконечный цикл из-за забытого инкремента</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">// НЕПРАВИЛЬНО
package main

import "fmt"

func main() {
    i := 0
    for i &lt; 10 {
        fmt.Println(i)
        // Забыли i++ - цикл будет бесконечным!
    }
}

// ПРАВИЛЬНО
package main

import "fmt"

func main() {
    i := 0
    for i &lt; 10 {
        fmt.Println(i)
        i++ // Не забываем увеличить счётчик
    }
}</code></pre>
</div>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #991b1b; margin-top: 0;">❌ Ошибка 2: Неправильное условие (off-by-one)</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">// Хотим вывести числа от 1 до 10

// НЕПРАВИЛЬНО - выведет от 1 до 9
package main

import "fmt"

func main() {
    for i := 1; i &lt; 10; i++ {
        fmt.Println(i)
    }
}

// ПРАВИЛЬНО - выведет от 1 до 10
package main

import "fmt"

func main() {
    for i := 1; i &lt;= 10; i++ {
        fmt.Println(i)
    }
}</code></pre>

<p>Ошибка &quot;на единицу&quot; (off-by-one) &mdash; одна из самых частых. Всегда проверяйте граничные значения!</p>
</div>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #991b1b; margin-top: 0;">❌ Ошибка 3: Изменение переменной цикла внутри тела</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">// ЗАПУТАННО И ОПАСНО
package main

import "fmt"

func main() {
    for i := 0; i &lt; 10; i++ {
        fmt.Println(i)
        if i == 5 {
            i += 2 // Изменяем i внутри цикла - плохая практика
        }
    }
}

// ЛУЧШЕ - явно задать нужный диапазон или использовать if
package main

import "fmt"

func main() {
    for i := 0; i &lt; 10; i++ {
        if i != 6 &amp;&amp; i != 7 {
            fmt.Println(i)
        }
    }
}</code></pre>

<p>Изменение переменной цикла внутри тела делает код трудночитаемым и подверженным ошибкам.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">6. Вложенные циклы</h2>

<p>Внутри тела <code>for</code> можно поставить ещё один <code>for</code>. Внешний цикл обычно задаёт &laquo;строки&raquo;, внутренний &mdash; &laquo;столбцы&raquo;. На каждой итерации внешнего цикла внутренний цикл проходит весь свой диапазон от начала до конца.</p>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">💻 Пример 6: Таблица умножения 3&times;3</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    for i := 1; i &lt;= 3; i++ {
        for j := 1; j &lt;= 3; j++ {
            fmt.Printf("%d×%d=%d ", i, j, i*j)
        }
        fmt.Println()
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #2e7d32; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0; overflow-x: auto;">
<code>1×1=1 1×2=2 1×3=3
2×1=2 2×2=4 2×3=6
3×1=3 3×2=6 3×3=9</code></pre>
</div>
</div>

<div style="background: #fff3cd; padding: 15px; border-radius: 5px; margin-top: 15px;">
<p style="margin: 0;"><strong>📌 Важно:</strong></p>

<ul style="margin: 10px 0 0 0;">
	<li>Имя счётчика внутреннего цикла должно отличаться от внешнего: <code>i</code> снаружи, <code>j</code> внутри</li>
	<li>Не путайте порядок индексов: внешний задаёт строку, внутренний &mdash; столбец</li>
	<li>Вложенные циклы выполняют тело внутреннего цикла <em>N&times;M</em> раз &mdash; будьте осторожны при больших диапазонах</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Шпаргалка по синтаксису</h2>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">// Классический for с тремя частями
for i := 0; i &lt; 10; i++ {
    // код
}

// for как while (только условие)
for условие {
// код
}

// Бесконечный цикл (выход через return)
for {
// код
if условие {
return
}
}

// Вложенные циклы
for i := 1; i &lt;= 3; i++ {
for j := 1; j &lt;= 3; j++ {
fmt.Printf("%d×%d=%d ", i, j, i*j)
}
fmt.Println()
}</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Как проверить код локально</h2>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p>Чтобы проверить свой код перед отправкой, создайте файл <code>main.go</code> и запустите его:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

// Вставьте сюда свою функцию
func sumToN(n int) int {
    // ваш код
    return 0
}

func main() {
    // Проверяем на нескольких значениях
    fmt.Println(sumToN(5))   // ожидаем 15
    fmt.Println(sumToN(10))  // ожидаем 55
    fmt.Println(sumToN(0))   // ожидаем 0
}</code></pre>

<p>Запустите в терминале:</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;">
<code>go run main.go</code></pre>

<p style="margin-bottom: 0;">Сравните вывод с ожидаемыми значениями. Если результаты совпадают &mdash; решение готово к отправке.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Практика: упражнения для закрепления</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">📝 Упражнение 1: Таблица умножения</h4>

<p><strong>Задача:</strong> Выведите таблицу умножения для числа 7 (от 7&times;1 до 7&times;10).</p>

<details><summary style="cursor: pointer; color: #1565c0; font-weight: bold;">Показать решение</summary>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin-top: 10px; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    number := 7
    fmt.Printf("Таблица умножения для %d:\n", number)

    for i := 1; i &lt;= 10; i++ {
        result := number * i
        fmt.Printf("%d × %d = %d\n", number, i, result)
    }
}</code></pre>

<p><strong>Ожидаемый вывод:</strong></p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code>Таблица умножения для 7:
7 × 1 = 7
7 × 2 = 14
7 × 3 = 21
7 × 4 = 28
7 × 5 = 35
7 × 6 = 42
7 × 7 = 49
7 × 8 = 56
7 × 9 = 63
7 × 10 = 70</code></pre>
</details>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">📝 Упражнение 2: Факториал числа</h4>

<p><strong>Задача:</strong> Вычислите факториал числа 6 (6! = 1 &times; 2 &times; 3 &times; 4 &times; 5 &times; 6).</p>

<details><summary style="cursor: pointer; color: #2e7d32; font-weight: bold;">Показать решение</summary>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin-top: 10px; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    n := 6
    result := 1

    for i := 1; i &lt;= n; i++ {
        result *= i
        fmt.Printf("%d! = %d\n", i, result)
    }

    fmt.Printf("\nФакториал %d равен %d\n", n, result)
}</code></pre>

<p><strong>Ожидаемый вывод:</strong></p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code>1! = 1
2! = 2
3! = 6
4! = 24
5! = 120
6! = 720

Факториал 6 равен 720</code></pre>
</details>
</div>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #e65100; margin-top: 0;">📝 Упражнение 3: Поиск первого числа</h4>

<p><strong>Задача:</strong> Найдите первое число, которое при возведении в квадрат даёт результат больше 50.</p>

<details><summary style="cursor: pointer; color: #e65100; font-weight: bold;">Показать решение</summary>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin-top: 10px; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    fmt.Println("Ищем первое число, квадрат которого больше 50:")

    i := 1
    for i*i &lt;= 50 {
        fmt.Printf("%d² = %d\n", i, i*i)
        i++
    }

    fmt.Printf("\nНашли! %d² = %d &gt; 50\n", i, i*i)
}</code></pre>

<p><strong>Ожидаемый вывод:</strong></p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code>Ищем первое число, квадрат которого больше 50:
1² = 1
2² = 4
3² = 9
4² = 16
5² = 25
6² = 36
7² = 49

Нашли! 8² = 64 &gt; 50</code></pre>
</details>
</div>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">📝 Упражнение 4: Треугольник из звёздочек</h4>

<p><strong>Задача:</strong> Выведите треугольник из звёздочек высотой 5 строк.</p>

<details><summary style="cursor: pointer; color: #6a1b9a; font-weight: bold;">Показать решение</summary>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin-top: 10px; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    height := 5
    fmt.Printf("Треугольник высотой %d:\n", height)

    for i := 1; i &lt;= height; i++ {
        // Внутренний цикл для печати звёздочек
        for j := 1; j &lt;= i; j++ {
            fmt.Print("*")
        }
        fmt.Println()  // Переход на новую строку
    }
}</code></pre>

<p><strong>Ожидаемый вывод:</strong></p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code>Треугольник высотой 5:
*
**
***
****
*****</code></pre>
</details>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Итоги</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p>Вы изучили цикл <code>for</code> &mdash; единственный, но универсальный цикл в Go. Теперь вы умеете:</p>

<ul>
	<li><strong>Использовать классическую форму</strong> с инициализацией, условием и пост-выражением</li>
	<li><strong>Применять сокращённую форму</strong> для создания аналога while</li>
	<li><strong>Создавать бесконечные циклы</strong> с выходом по условию</li>
	<li><strong>Избегать типичных ошибок</strong> с циклами</li>
</ul>

<div style="background: white; padding: 15px; border-radius: 5px; margin-top: 15px;">
<h4 style="color: #1565c0; margin-top: 0;">🚀 Что изучать дальше</h4>

<p>После освоения базовых форм цикла, рекомендуем изучить:</p>

<ul>
	<li><strong>break и continue</strong> &mdash; управление выполнением цикла (пропуск итераций, досрочный выход)</li>
	<li><strong>Массивы и срезы</strong> &mdash; коллекции данных в Go</li>
	<li><strong>Оператор range</strong> &mdash; удобный способ перебора коллекций</li>
</ul>
</div>
</div>

<h2 style="color: #34495e; margin-top: 30px;">✅ Чек-лист самопроверки</h2>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<ul style="list-style: none; padding-left: 0;">
	<li>☑️ Я понимаю структуру классического цикла <code>for</code></li>
	<li>☑️ Я могу написать цикл в стиле while</li>
	<li>☑️ Я знаю, как создать и остановить бесконечный цикл</li>
	<li>☑️ Я не забываю обновлять счётчики в циклах while-стиля</li>
	<li>☑️ Я проверяю граничные условия (off-by-one)</li>
	<li>☑️ Я не изменяю переменную цикла внутри тела без необходимости</li>
	<li>☑️ Я всегда использую <code>fmt.Println</code> вместо встроенной <code>println</code></li>
</ul>
</div>
</div>
</div>
