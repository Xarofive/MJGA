<p>&nbsp;</p>

<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50;">break, continue и метки: тонкости и паттерны управления циклами</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть за 30 секунд</h3>

<ul>
	<li><code>break</code> немедленно выходит из текущего цикла (но не из функции)</li>
	<li><code>continue</code> пропускает остаток итерации, но пост-выражение всё равно выполняется</li>
	<li>В while-стиле <code>for</code> опасность зацикливания при неправильном <code>continue</code></li>
	<li>Метки позволяют управлять внешними циклами из вложенных</li>
	<li><code>break label</code> выходит ровно из отмеченного цикла, <code>break</code> &mdash; только из ближайшего</li>
	<li>Early-continue паттерн делает код плоским и читаемым</li>
	<li>Всегда используйте <code>fmt.Println</code> или <code>fmt.Printf</code> вместо встроенных <code>print</code>/<code>println</code></li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>

<p><strong>Для лучшего понимания управления циклами</strong> прослушайте тематический подкаст:</p>

<p style="margin: 15px 0;"><a href="https://drive.google.com/file/d/1k3psWdOfPaK6oQX-NMES1W-M4NpMGBvb/view?usp=sharing" style="display: inline-block; background: #1565c0; color: white; padding: 10px 20px; text-decoration: none; border-radius: 5px; font-weight: bold;" target="_blank">🎧 Прослушать о break и continue</a></p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎯 Чему вы научитесь</h4>

<ul>
	<li>✅ Правильно применять <code>break</code> для раннего выхода из циклов</li>
	<li>✅ Использовать <code>continue</code> без создания бесконечных циклов</li>
	<li>✅ Понимать, когда выполняется пост-выражение при <code>continue</code></li>
	<li>✅ Безопасно работать с <code>continue</code> в while-стиле циклов</li>
	<li>✅ Использовать метки для управления вложенными циклами</li>
	<li>✅ Применять паттерны early-continue и break-guard</li>
	<li>✅ Отличать <code>break</code> от <code>return</code></li>
</ul>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">📚 Предпосылки</h4>

<p>Для изучения этой темы вы должны знать:</p>

<ul>
	<li>Переменные и их объявление (<code>var</code>, <code>:=</code>)</li>
	<li>Условные операторы (<code>if</code>, <code>else</code>)</li>
	<li>Логические операторы (<code>&amp;&amp;</code>, <code>||</code>, <code>!</code>)</li>
	<li>Три формы цикла <code>for</code> (классическая, while-стиль, бесконечная)</li>
</ul>
</div>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 15px; margin: 20px 0;">
<p style="margin: 0;"><strong>⚠️ Напоминание из прошлого модуля:</strong> В классической форме <code>for init; cond; post {}</code> пост-выражение (например <code>i++</code>) выполняется даже при <code>continue</code>! Это важно для понимания материала ниже.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. break &mdash; немедленный выход из текущего цикла</h2>

<p>Оператор <code>break</code> немедленно прерывает выполнение текущего цикла и передаёт управление первой инструкции после цикла. Важно понимать отличие от <code>return</code>.</p>

<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #0c4a6e; margin-top: 0;">📊 Сравнение break vs return</h4>

<table style="width: 100%; border-collapse: collapse; margin-top: 15px;">
	<tbody>
		<tr style="background: #f8f9fa;">
			<th style="padding: 10px; border: 1px solid #dee2e6;">Оператор</th>
			<th style="padding: 10px; border: 1px solid #dee2e6;">Действие</th>
			<th style="padding: 10px; border: 1px solid #dee2e6;">Код после цикла</th>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #dee2e6;"><code>break</code></td>
			<td style="padding: 10px; border: 1px solid #dee2e6;">Выходит из цикла</td>
			<td style="padding: 10px; border: 1px solid #dee2e6;">Выполняется</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #dee2e6;"><code>return</code></td>
			<td style="padding: 10px; border: 1px solid #dee2e6;">Выходит из функции</td>
			<td style="padding: 10px; border: 1px solid #dee2e6;">НЕ выполняется</td>
		</tr>
	</tbody>
</table>
</div>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    sum := 0
    limit := 50

    fmt.Println("Суммируем числа до превышения лимита")

    for i := 1; i &lt;= 100; i++ {
        sum += i
        fmt.Printf("Добавили %d, сумма = %d\n", i, sum)

        if sum &gt; limit {
            fmt.Printf("Превысили лимит %d! Выходим из цикла\n", limit)
            break  // Выход из цикла, НО НЕ из функции
        }
    }

    // Этот код ВЫПОЛНИТСЯ после break
    fmt.Printf("Итоговая сумма: %d\n", sum)
    fmt.Println("Программа продолжается после цикла")
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #0c4a6e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Суммируем числа до превышения лимита
Добавили 1, сумма = 1
Добавили 2, сумма = 3
Добавили 3, сумма = 6
Добавили 4, сумма = 10
Добавили 5, сумма = 15
Добавили 6, сумма = 21
Добавили 7, сумма = 28
Добавили 8, сумма = 36
Добавили 9, сумма = 45
Добавили 10, сумма = 55
Превысили лимит 50! Выходим из цикла
Итоговая сумма: 55
Программа продолжается после цикла</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">2. continue &mdash; пропуск остатка тела цикла</h2>

<p>Оператор <code>continue</code> прерывает текущую итерацию цикла &mdash; весь код ниже <code>continue</code> до закрывающей скобки <code>}</code> не выполняется, и цикл сразу переходит к следующей итерации. В классической форме <code>for</code> пост-выражение всё равно выполняется!</p>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 15px; margin: 20px 0;">
<p style="margin: 0;"><strong>⚠️ ЯРКОЕ ПРЕДУПРЕЖДЕНИЕ:</strong> В классической форме <code>for i := 0; i &lt; 10; i++</code> часть <code>i++</code> выполняется ДАЖЕ при <code>continue</code>. Это не баг, а фича!</p>
</div>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    fmt.Println("Печать только нечётных чисел от 1 до 10:")

    // Классическая форма - безопасно с continue
    for i := 1; i &lt;= 10; i++ {
        if i%2 == 0 {
            // Пропускаем чётные числа
            continue  // ВАЖНО: i++ всё равно выполнится!
        }
        fmt.Printf("%d ", i)
    }
    fmt.Println("\nГотово!")
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #ef4444; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Печать только нечётных чисел от 1 до 10:
1 3 5 7 9
Готово!</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">3. While-стиль for и ловушки с continue</h2>

<p>В while-стиле цикла <code>for condition {}</code> нет автоматического пост-выражения. Если не быть осторожным с <code>continue</code>, легко создать бесконечный цикл!</p>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #991b1b; margin-top: 0;">❌ ОПАСНЫЙ ПРИМЕР (закомментирован)</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    // НЕПРАВИЛЬНО - создаст бесконечный цикл!
    /*
    i := 0
    for i &lt; 10 {
        if i == 5 {
            continue  // i не увеличится, застрянем на 5 НАВСЕГДА!
        }
        fmt.Println(i)
        i++  // Этот код не выполнится при i == 5
    }
    */

    // ПРАВИЛЬНАЯ ВЕРСИЯ - инкремент ДО continue
    fmt.Println("Правильный while-стиль с continue:")
    i := 0
    for i &lt; 10 {
        if i == 5 {
            i++  // Увеличиваем ПЕРЕД continue
            continue
        }
        fmt.Println(i)
        i++
    }
}</code></pre>
</div>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #991b1b; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Правильный while-стиль с continue:
0
1
2
3
4
6
7
8
9</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">4. Метки: синтаксис, именование и применение</h2>

<p>Метки позволяют управлять внешними циклами из вложенных. Это особенно полезно, когда нужно выйти сразу из нескольких уровней вложенности.</p>

<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #0c4a6e; margin-top: 0;">🎯 Синтаксис меток</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0;">
<code class="language-go">labelName:  // Метка перед внешним циклом
for condition1 {
    for condition2 {
        if something {
            break labelName     // Выход из обоих циклов
            // или
            continue labelName  // Следующая итерация внешнего цикла
        }
    }
}</code></pre>

<h4 style="color: #0c4a6e; margin-top: 15px;">📝 Гайд по именованию меток</h4>

<table style="width: 100%; border-collapse: collapse; margin-top: 10px;">
	<tbody>
		<tr style="background: #f8f9fa;">
			<th style="padding: 10px; border: 1px solid #dee2e6;">✅ Хорошо</th>
			<th style="padding: 10px; border: 1px solid #dee2e6;">❌ Плохо</th>
			<th style="padding: 10px; border: 1px solid #dee2e6;">Почему</th>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #dee2e6;"><code>outer</code></td>
			<td style="padding: 10px; border: 1px solid #dee2e6;"><code>label1</code></td>
			<td style="padding: 10px; border: 1px solid #dee2e6;">Описывает позицию</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #dee2e6;"><code>rows</code></td>
			<td style="padding: 10px; border: 1px solid #dee2e6;"><code>loop</code></td>
			<td style="padding: 10px; border: 1px solid #dee2e6;">Описывает смысл</td>
		</tr>
		<tr>
			<td style="padding: 10px; border: 1px solid #dee2e6;"><code>search</code></td>
			<td style="padding: 10px; border: 1px solid #dee2e6;"><code>l</code></td>
			<td style="padding: 10px; border: 1px solid #dee2e6;">Описывает действие</td>
		</tr>
	</tbody>
</table>

<p style="margin-top: 15px;"><strong>⚠️ Важно:</strong> В Go объявление метки без её использования &mdash; ошибка компиляции (<code>label X defined and not used</code>). Метки имеют смысл только для управления вложенными циклами; не оставляйте &laquo;осиротевшие&raquo; метки в коде.</p>
</div>

<p>Пример с <code>break</code> и меткой:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    fmt.Println("Ищем пару чисел с произведением &gt; 50:")

outer:  // Метка для внешнего цикла
    for i := 1; i &lt;= 10; i++ {
        for j := 1; j &lt;= 10; j++ {
            product := i * j
            if product &gt; 50 {
                fmt.Printf("Нашли! %d × %d = %d\n", i, j, product)
                break outer  // Выход из ОБОИХ циклов
            }
        }
    }

    fmt.Println("Поиск завершён")
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #0c4a6e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Ищем пару чисел с произведением &gt; 50:
Нашли! 6 × 9 = 54
Поиск завершён</code></pre>
</div>

<p>Пример с <code>continue</code> и меткой:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    fmt.Println("Пропускаем строку 2:")

rows:
    for i := 1; i &lt;= 3; i++ {
        for j := 1; j &lt;= 3; j++ {
            if i == 2 {
                continue rows  // Переход к следующей строке
            }
            fmt.Printf("(%d,%d) ", i, j)
        }
        fmt.Println()
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #0c4a6e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Пропускаем строку 2:
(1,1) (1,2) (1,3)
(3,1) (3,2) (3,3)</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">5. Паттерны: эффективное использование break и continue</h2>

<h3 style="color: #34495e;">Early-continue (Guard Clauses)</h3>

<p>Паттерн early-continue позволяет избежать глубокой вложенности и делает код более плоским и читаемым. Вместо больших блоков <code>if-else</code>, мы проверяем условия и пропускаем ненужные случаи.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    // FizzBuzz с early-continue для плоского кода
    fmt.Println("FizzBuzz от 1 до 20:")

    for i := 1; i &lt;= 20; i++ {
        // Guard clauses с continue
        if i%15 == 0 {
            fmt.Printf("%d: FizzBuzz\n", i)
            continue
        }
        if i%3 == 0 {
            fmt.Printf("%d: Fizz\n", i)
            continue
        }
        if i%5 == 0 {
            fmt.Printf("%d: Buzz\n", i)
            continue
        }
        // Основной случай без вложенности
        fmt.Printf("%d: %d\n", i, i)
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #34495e; margin-top: 0;">📋 Ожидаемый вывод (фрагмент):</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>FizzBuzz от 1 до 20:
1: 1
2: 2
3: Fizz
4: 4
5: Buzz
6: Fizz
...
15: FizzBuzz
...</code></pre>
</div>

<h3 style="color: #34495e;">Break-guard вместо флагов</h3>

<p>Вместо использования флагов для отслеживания состояния, используйте <code>break</code> для раннего выхода:</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    number := 91
    fmt.Printf("Ищем первый делитель числа %d (кроме 1 и самого числа):\n", number)

    // Паттерн break-guard вместо флага found := false
    for divisor := 2; divisor &lt; number; divisor++ {
        if number%divisor == 0 {
            fmt.Printf("Нашли! %d делится на %d\n", number, divisor)
            fmt.Printf("%d не является простым числом\n", number)
            break  // Ранний выход вместо флага
        }
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #34495e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Ищем первый делитель числа 91 (кроме 1 и самого числа):
Нашли! 91 делится на 7
91 не является простым числом</code></pre>
</div>

<h3 style="color: #34495e;">Поиск первого подходящего во вложенных циклах</h3>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    targetSum := 15
    fmt.Printf("Ищем пару чисел с суммой %d:\n", targetSum)

search:  // Метка для паттерна поиска
    for i := 1; i &lt;= 10; i++ {
        for j := 1; j &lt;= 10; j++ {
            sum := i + j
            if sum == targetSum {
                fmt.Printf("Нашли первую пару: %d + %d = %d\n", i, j, targetSum)
                break search  // Выход при первом совпадении
            }
        }
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #34495e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Ищем пару чисел с суммой 15:
Нашли первую пару: 5 + 10 = 15</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">6. Антипаттерны и стиль кода</h2>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #991b1b; margin-top: 0;">❌ Антипаттерн: изменение переменной цикла в теле</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0;">
<code class="language-go">// НЕПРАВИЛЬНО (пример для разбора — не компилируем, оставляем закомментированным)
/*
for i := 0; i &lt; 10; i++ {
    fmt.Println(i)
    if i == 5 {
        i += 3  // Неожиданное изменение счётчика
    }
}
*/

// ПРАВИЛЬНО — явный пропуск через continue
package main

import "fmt"

func shouldSkip(i int) bool {
    return i == 6 || i == 7
}

func main() {
    for i := 0; i &lt; 10; i++ {
        if shouldSkip(i) {
            continue
        }
        fmt.Println(i)
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #34495e; margin-top: 0;">📋 Ожидаемый вывод (правильный вариант):</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>0
1
2
3
4
5
8
9</code></pre>
</div>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #991b1b; margin-top: 0;">📋 Что бы вывел антипаттерн (если раскомментировать):</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>0
1
2
3
4
5
9</code></pre>

<p style="margin: 10px 0 0 0; font-size: 0.9em;">Пропущены 6, 7, 8 &mdash; <code>i += 3</code> сместил счётчик ещё ДО выполнения пост-выражения <code>i++</code>, поэтому следующая итерация началась с <code>i == 9</code>, а не с <code>i == 6</code>.</p>
</div>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">📝 Памятка по стилю кода</h4>

<ul>
	<li>Всегда используйте <code>fmt.Println/Printf</code>, НЕ встроенную <code>println</code></li>
	<li>Давайте меткам понятные имена (<code>outer</code>, <code>search</code>), не <code>label1</code></li>
	<li>Выносите магические числа в переменные с понятными именами</li>
	<li>Избегайте глубокой вложенности через early-continue</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Шпаргалка по синтаксису</h2>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-go">// Классический for
for i := 0; i &lt; 10; i++ {
    // пост-выражение i++ выполнится даже при continue
}

// While-стиль
count := 10
for count &gt; 0 {
count--  // Не забудьте изменять переменную!
}

// Бесконечный
for {
if exitCondition {
break
}
}

// break - выход из текущего цикла
for i := 0; i &lt; 10; i++ {
if i == 5 {
break  // Выход при i == 5
}
fmt.Println(i)  // Напечатает 0,1,2,3,4 — каждое значение в отдельной строке (Println)
}

// continue - пропуск итерации
for i := 0; i &lt; 5; i++ {
if i == 2 {
continue  // Пропустит i == 2
}
fmt.Println(i)  // Напечатает 0,1,3,4 — каждое значение в отдельной строке (Println)
}

// Метки для вложенных циклов
outer:
for i := 0; i &lt; 3; i++ {
for j := 0; j &lt; 3; j++ {
if i*j &gt; 2 {
break outer  // Выход из обоих циклов
}
fmt.Printf("(%d,%d) ", i, j)
}
}</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Практика внутри лекции</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">📝 Упражнение 1: Нечётные числа с continue</h4>

<p><strong>Задача:</strong> Выведите все нечётные числа от 1 до 20 используя классическую форму <code>for</code> и оператор <code>continue</code>.</p>

<details><summary style="cursor: pointer; color: #1565c0; font-weight: bold;">Показать решение</summary>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin-top: 10px; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    fmt.Println("Нечётные числа от 1 до 20:")

    for i := 1; i &lt;= 20; i++ {
        if i%2 == 0 {
            continue  // Пропускаем чётные
        }
        fmt.Printf("%d ", i)
    }
    fmt.Println()
}</code></pre>

<p><strong>Ожидаемый вывод:</strong></p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code>Нечётные числа от 1 до 20:
1 3 5 7 9 11 13 15 17 19</code></pre>
</details>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">📝 Упражнение 2: Сумма с ранним выходом</h4>

<p><strong>Задача:</strong> Суммируйте натуральные числа 1, 2, 3... пока сумма не превысит 100. Выведите последнее добавленное число и итоговую сумму. Используйте <code>break</code>.</p>

<details><summary style="cursor: pointer; color: #2e7d32; font-weight: bold;">Показать решение</summary>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin-top: 10px; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    sum := 0
    lastAdded := 0
    threshold := 100

    for i := 1; ; i++ {  // Бесконечный со счётчиком
        sum += i
        lastAdded = i

        if sum &gt; threshold {
            break  // Ранний выход
        }
    }

    fmt.Printf("Последнее добавленное число: %d\n", lastAdded)
    fmt.Printf("Итоговая сумма: %d\n", sum)
}</code></pre>

<p><strong>Ожидаемый вывод:</strong></p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code>Последнее добавленное число: 14
Итоговая сумма: 105</code></pre>
</details>
</div>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #e65100; margin-top: 0;">📝 Упражнение 3: Вложенные циклы с меткой</h4>

<p><strong>Задача:</strong> Найдите первую пару чисел (i, j) где оба от 1 до 10, такую что i*j &gt; 40. Выйдите из обоих циклов используя метку.</p>

<details><summary style="cursor: pointer; color: #e65100; font-weight: bold;">Показать решение</summary>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin-top: 10px; overflow-x: auto;">
<code class="language-go">package main

import "fmt"

func main() {
    fmt.Println("Ищем первую пару с произведением &gt; 40:")

search:
    for i := 1; i &lt;= 10; i++ {
        for j := 1; j &lt;= 10; j++ {
            product := i * j
            if product &gt; 40 {
                fmt.Printf("Нашли: %d × %d = %d\n", i, j, product)
                break search  // Выход по метке
            }
        }
    }

    fmt.Println("Поиск завершён")
}</code></pre>

<p><strong>Ожидаемый вывод:</strong></p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code>Ищем первую пару с произведением &gt; 40:
Нашли: 5 × 9 = 45
Поиск завершён</code></pre>
</details>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Проверочные мини-кейсы (квиз)</h2>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">🧩 Вопрос 1: Что выведет код?</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code class="language-go">for i := 0; i &lt; 3; i++ {
    if i == 1 {
        continue
    }
    fmt.Print(i)
}</code></pre>

<details><summary style="cursor: pointer; color: #6a1b9a; font-weight: bold;">Показать ответ</summary>

<p><strong>Ответ:</strong> 02</p>

<p><strong>Разбор:</strong> При i == 1 выполняется continue, который пропускает fmt.Print(i), но пост-выражение i++ всё равно выполняется. Поэтому печатаются только 0 и 2.</p>
</details>
</div>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">🧩 Вопрос 2: Опасность в while-стиле?</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code class="language-go">i := 0
for i &lt; 3 {
    if i == 1 {
        continue
    }
    fmt.Print(i)
    i++
}</code></pre>

<details><summary style="cursor: pointer; color: #6a1b9a; font-weight: bold;">Показать ответ</summary>

<p><strong>Ответ:</strong> Программа напечатает <code>0</code>, затем зависнет в бесконечном цикле.</p>

<p><strong>Разбор:</strong> На итерации i=0 печатается <code>0</code>, затем <code>i++</code> делает i=1. На i=1 срабатывает <code>continue</code>, который пропускает <code>i++</code>. Переменная остаётся равной 1, и цикл <code>for i &lt; 3</code> продолжается бесконечно &mdash; без новых выводов после первого <code>0</code>.</p>
</details>
</div>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">🧩 Вопрос 3: break vs return</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code class="language-go">func main() {
    for i := 0; i &lt; 3; i++ {
        if i == 1 {
            break
        }
        fmt.Print(i)
    }
    fmt.Print("END")
}</code></pre>

<details><summary style="cursor: pointer; color: #6a1b9a; font-weight: bold;">Показать ответ</summary>

<p><strong>Ответ:</strong> 0END</p>

<p><strong>Разбор:</strong> break выходит только из цикла, не из функции. Поэтому &quot;END&quot; печатается.</p>
</details>
</div>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">🧩 Вопрос 4: Метки и break</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code class="language-go">outer:
for i := 0; i &lt; 2; i++ {
    for j := 0; j &lt; 2; j++ {
        if i+j == 1 {
            break outer
        }
        fmt.Printf("(%d,%d)", i, j)
    }
}</code></pre>

<details><summary style="cursor: pointer; color: #6a1b9a; font-weight: bold;">Показать ответ</summary>

<p><strong>Ответ:</strong> (0,0)</p>

<p><strong>Разбор:</strong> При i=0, j=1 сумма равна 1, срабатывает break outer, который выходит из обоих циклов.</p>
</details>
</div>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">🧩 Вопрос 5: Порядок во вложенных циклах</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code class="language-go">for i := 1; i &lt;= 2; i++ {
    for j := 1; j &lt;= 2; j++ {
        fmt.Printf("%d%d ", i, j)
    }
}</code></pre>

<details><summary style="cursor: pointer; color: #6a1b9a; font-weight: bold;">Показать ответ</summary>

<p><strong>Ответ:</strong> 11 12 21 22</p>

<p><strong>Разбор:</strong> Внешний цикл фиксирует i, внутренний перебирает все j, затем i увеличивается.</p>
</details>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Итоги</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p>Вы освоили продвинутые техники управления циклами в Go. Теперь вы умеете:</p>

<ul>
	<li>✅ Использовать <code>break</code> для раннего выхода из циклов</li>
	<li>✅ Применять <code>continue</code> для пропуска итераций без зацикливания</li>
	<li>✅ Понимать, что пост-выражение выполняется даже при <code>continue</code></li>
	<li>✅ Безопасно работать с <code>continue</code> в while-стиле циклов</li>
	<li>✅ Использовать метки для управления вложенными циклами</li>
	<li>✅ Применять паттерны early-continue и break-guard</li>
	<li>✅ Избегать антипаттернов и писать чистый код</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Что дальше</h2>

<p>После освоения управления циклами, следующий логический шаг &mdash; изучение коллекций данных. В следующем модуле вы изучите массивы и срезы &mdash; основные структуры для хранения последовательностей данных в Go. Вы также познакомитесь с оператором <code>range</code>, который делает перебор коллекций элегантным и идиоматичным для Go. Эти знания откроют путь к работе с реальными данными и алгоритмами.</p>

<h2 style="color: #34495e; margin-top: 30px;">✅ Чек-лист самопроверки</h2>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<ul style="list-style: none; padding-left: 0;">
	<li>☑️ Понимаю, когда выполняется пост-выражение (например, <code>i++</code>) в классическом <code>for</code></li>
	<li>☑️ Умею безопасно писать while-стиль без зацикливания</li>
	<li>☑️ Отличаю <code>break</code> от <code>return</code></li>
	<li>☑️ Могу использовать метки для выхода/продолжения внешнего цикла</li>
	<li>☑️ Использую guard-clauses для &laquo;плоского&raquo; кода</li>
	<li>☑️ Не меняю переменную цикла внутри тела без необходимости</li>
	<li>☑️ Всегда использую fmt.* вместо println</li>
</ul>
</div>
</div>
</div>
