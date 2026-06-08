<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<p>&nbsp;</p>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">

<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">Java Base, Модуль 5, Лекция 1<br />Циклы в Java: for, while и do-while</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть лекции</h3>
<ul>
	<li><strong>Цикл</strong> позволяет выполнить один и тот же блок кода несколько раз.</li>
	<li><code>for</code> удобен, когда известно количество повторений или есть счётчик.</li>
	<li><code>while</code> удобен, когда цикл зависит от условия, а число итераций заранее неизвестно.</li>
	<li><code>do-while</code> выполняет тело хотя бы один раз, а потом проверяет условие.</li>
	<li>В циклах важно обновлять переменные, иначе можно получить бесконечный цикл.</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>
<p>Для лучшего понимания циклов в Java прослушайте аудиоподкаст:</p>
<p style="margin: 15px 0;"><a href="https://drive.google.com/file/d/16srUsd2vS5WlkbCcVfLph2SYJlahYNWm/view?usp=sharing" style="display: inline-block; background: #1565c0; color: white; padding: 10px 20px; text-decoration: none; border-radius: 5px; font-weight: bold;" target="_blank">🎧 Прослушать о циклах</a></p>
<p style="font-size: 14px; color: #666; margin-top: 10px;"><em>Откроется в новой вкладке. Рекомендуется прослушать перед изучением материала для общего понимания или после — для закрепления.</em></p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎯 Чему вы научитесь</h4>
<ul>
	<li>✅ Писать классический цикл <code>for</code>.</li>
	<li>✅ Использовать <code>while</code> для циклов по условию.</li>
	<li>✅ Понимать, когда нужен <code>do-while</code>.</li>
	<li>✅ Накапливать сумму, произведение и другой результат в переменной.</li>
	<li>✅ Избегать бесконечных циклов и ошибок на границах диапазона.</li>
</ul>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">📚 Предпосылки</h4>
<ul>
	<li>переменные и типы <code>int</code>, <code>boolean</code>, <code>String</code>;</li>
	<li>условные операторы <code>if</code>, <code>else</code>;</li>
	<li>операторы сравнения и логические операторы;</li>
	<li>методы с параметрами и <code>return</code>.</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Содержание</h2>
<ul>
	<li><a href="#why">Зачем нужны циклы?</a></li>
	<li><a href="#for">Классический for</a></li>
	<li><a href="#while">Цикл while</a></li>
	<li><a href="#dowhile">Цикл do-while</a></li>
	<li><a href="#accumulator">Паттерн накопления</a></li>
	<li><a href="#digits">Поразрядная обработка числа</a></li>
	<li><a href="#mistakes">Частые ошибки</a></li>
	<li><a href="#practice">Мини-практика</a></li>
	<li><a href="#check">Чек-лист</a></li>
</ul>

<h2 id="why" style="color: #34495e; margin-top: 30px;">1. Зачем нужны циклы?</h2>
<p>Циклы нужны, когда один и тот же код должен выполниться несколько раз. Например: вывести числа от 1 до 10, посчитать сумму значений, обработать каждую цифру числа или удваивать значение до достижения предела.</p>
<p>Без циклов пришлось бы писать много одинаковых строк. С циклом мы описываем правило повторения один раз.</p>

<h2 id="for" style="color: #34495e; margin-top: 30px;">2. Классический for</h2>
<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 16px; margin: 16px 0;">
<h4 style="color: #0c4a6e; margin-top: 0;">🎯 Синтаксис</h4>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>for (инициализация; условие; обновление) {
    // тело цикла
}</code></pre>
<ul>
	<li><strong>Инициализация</strong> выполняется один раз перед циклом.</li>
	<li><strong>Условие</strong> проверяется перед каждой итерацией.</li>
	<li><strong>Обновление</strong> выполняется после каждой итерации.</li>
</ul>
</div>

<h3 style="color: #34495e;">Пример: счётчик от 1 до 5</h3>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    public static void main(String[] args) {
        for (int i = 1; i &lt;= 5; i++) {
            System.out.println(i);
        }

        System.out.println("Цикл завершён");
    }
}</code></pre>
<div style="background: #f0f0f0; border-left: 3px solid #666; padding: 10px; margin: 10px 0;">
<strong>Ожидаемый вывод:</strong>
<pre style="margin: 5px 0 0 0;">1
2
3
4
5
Цикл завершён</pre>
</div>

<h3 style="color: #34495e;">Обратный отсчёт</h3>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>for (int i = 10; i &gt;= 1; i--) {
    System.out.println(i + "...");
}

System.out.println("СТАРТ!");</code></pre>

<h2 id="while" style="color: #34495e; margin-top: 30px;">3. Цикл while</h2>
<p><code>while</code> выполняет тело, пока условие истинно. Такой цикл удобен, когда количество повторений заранее неизвестно или переменная обновляется внутри тела цикла.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>int count = 5;

while (count &gt; 0) {
    System.out.println("Осталось попыток: " + count);
    count--;
}</code></pre>
<div style="background: #fff8e1; border-left: 4px solid #ffc107; padding: 15px; margin: 20px 0;">
<h4 style="color: #f57c00; margin-top: 0;">💡 Важно</h4>
<p style="margin-bottom: 0;">Если забыть <code>count--</code>, условие <code>count &gt; 0</code> всегда останется истинным. Это приведёт к бесконечному циклу.</p>
</div>

<h2 id="dowhile" style="color: #34495e; margin-top: 30px;">4. Цикл do-while</h2>
<p><code>do-while</code> сначала выполняет тело, а потом проверяет условие. Поэтому тело выполняется минимум один раз.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>int value = 1;

do {
    System.out.println(value);
    value *= 2;
} while (value &lt; 100);</code></pre>
<p>В учебных задачах этого модуля чаще всего достаточно <code>for</code> и <code>while</code>, но <code>do-while</code> полезен для меню и повторного запроса ввода.</p>

<h2 id="accumulator" style="color: #34495e; margin-top: 30px;">5. Паттерн накопления</h2>
<p>Многие задачи с циклами строятся вокруг переменной-аккумулятора. Мы создаём переменную до цикла, обновляем её на каждой итерации и возвращаем результат.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>static int sumToN(int n) {
    int sum = 0;

    for (int i = 1; i &lt;= n; i++) {
        sum += i;
    }

    return sum;
}</code></pre>
<p>Тот же паттерн используется для произведения, подсчёта количества, поиска максимума и фильтрации значений по условию.</p>

<h2 id="digits" style="color: #34495e; margin-top: 30px;">6. Поразрядная обработка числа</h2>
<p>Чтобы обработать цифры числа без преобразования в строку, используют деление и остаток от деления на 10.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>int n = 1234;

while (n &gt; 0) {
    int digit = n % 10; // последняя цифра
    n = n / 10;         // отбросили последнюю цифру
}</code></pre>
<p>В Java целочисленное деление отбрасывает дробную часть: <code>1234 / 10</code> даёт <code>123</code>.</p>

<h2 id="mistakes" style="color: #34495e; margin-top: 30px;">7. Частые ошибки</h2>
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #ffebee;"><th style="padding: 10px; border: 1px solid #ef9a9a;">Ошибка</th><th style="padding: 10px; border: 1px solid #ef9a9a;">Как исправить</th></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Цикл не включает последнее число</td><td style="padding: 10px; border: 1px solid #ef9a9a;">Проверьте условие: часто нужно <code>i &lt;= n</code>, а не <code>i &lt; n</code>.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Бесконечный цикл</td><td style="padding: 10px; border: 1px solid #ef9a9a;">Убедитесь, что переменная условия меняется внутри цикла или в обновлении <code>for</code>.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Неверное начальное значение аккумулятора</td><td style="padding: 10px; border: 1px solid #ef9a9a;">Для суммы обычно нужен <code>0</code>, для произведения &mdash; <code>1</code>.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Печать вместо возврата</td><td style="padding: 10px; border: 1px solid #ef9a9a;">В задачах с методами возвращайте результат через <code>return</code>.</td></tr>
	</tbody>
</table>

<h2 id="practice" style="color: #34495e; margin-top: 30px;">8. Мини-практика</h2>
<ul>
	<li>Выведите числа от 1 до 10 через <code>for</code>.</li>
	<li>Посчитайте сумму чисел от 1 до 100.</li>
	<li>Удваивайте число, пока оно меньше 1000.</li>
	<li>Посчитайте сумму цифр числа <code>9876</code>.</li>
</ul>

<h2 id="check" style="color: #34495e; margin-top: 30px;">✅ Чек-лист самопроверки</h2>
<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 14px; margin: 20px 0;">
<ul style="margin-bottom: 0; list-style: none; padding-left: 0;">
	<li><label><input type="checkbox"> Я понимаю, из каких трёх частей состоит классический <code>for</code>.</label></li>
	<li><label><input type="checkbox"> Я умею выбрать между <code>for</code> и <code>while</code>.</label></li>
	<li><label><input type="checkbox"> Я обновляю переменные так, чтобы цикл завершался.</label></li>
	<li><label><input type="checkbox"> Я умею накапливать сумму в переменной.</label></li>
	<li><label><input type="checkbox"> Я проверяю граничные значения: 0, 1, последнее число диапазона.</label></li>
	<li><label><input type="checkbox"> В методах я возвращаю результат через <code>return</code>, а не печатаю его.</label></li>
</ul>
</div>

<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
<p>&nbsp;</p>
