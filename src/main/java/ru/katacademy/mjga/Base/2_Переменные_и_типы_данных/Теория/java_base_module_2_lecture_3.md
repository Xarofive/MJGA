<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<p>&nbsp;</p>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">

<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">Java Base, Модуль 2, Лекция 3<br />Арифметические операции в Java</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть лекции</h3>
<ul>
	<li>Арифметические операции нужны для вычислений в программе.</li>
	<li>Java поддерживает <code>+</code>, <code>-</code>, <code>*</code>, <code>/</code> и <code>%</code>.</li>
	<li>При делении двух <code>int</code> результат тоже будет <code>int</code>.</li>
	<li>Для дробного результата используйте <code>double</code>.</li>
	<li>Операции можно сокращать: <code>+=</code>, <code>-=</code>, <code>*=</code>, <code>/=</code>, <code>%=</code>.</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Содержание</h2>
<ul>
	<li><a href="#intro">Зачем нужны арифметические операции?</a></li>
	<li><a href="#operators">Основные операторы</a></li>
	<li><a href="#examples">Примеры операций</a></li>
	<li><a href="#division">Деление int и double</a></li>
	<li><a href="#remainder">Остаток от деления</a></li>
	<li><a href="#priority">Приоритет операций</a></li>
	<li><a href="#short-ops">Сокращённые операции</a></li>
	<li><a href="#increment">Инкремент и декремент</a></li>
	<li><a href="#common-mistakes">Частые ошибки</a></li>
	<li><a href="#practice">Практические упражнения</a></li>
	<li><a href="#quiz">Проверь себя</a></li>
	<li><a href="#next">Что дальше?</a></li>
</ul>

<h2 id="intro" style="color: #34495e; margin-top: 30px;">Зачем нужны арифметические операции?</h2>
<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p>Арифметика используется почти в любой программе: посчитать стоимость заказа, сумму баллов, возраст пользователя, остаток товара или процент выполнения.</p>
<p>В Java математические действия записываются через операторы, похожие на школьную математику.</p>
</div>

<h2 id="operators" style="color: #34495e; margin-top: 30px;">Основные операторы</h2>
<table style="width: 100%; border-collapse: collapse; margin: 16px 0;">
	<tbody>
		<tr style="background: #e8f5e9;">
			<th style="padding: 10px; border: 1px solid #c8e6c9;">Оператор</th>
			<th style="padding: 10px; border: 1px solid #c8e6c9;">Описание</th>
			<th style="padding: 10px; border: 1px solid #c8e6c9;">Пример</th>
			<th style="padding: 10px; border: 1px solid #c8e6c9;">Результат</th>
		</tr>
		<tr><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>+</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;">Сложение</td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>4 + 2</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>6</code></td></tr>
		<tr><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>-</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;">Вычитание</td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>4 - 2</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>2</code></td></tr>
		<tr><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>*</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;">Умножение</td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>4 * 2</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>8</code></td></tr>
		<tr><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>/</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;">Деление</td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>4 / 2</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>2</code></td></tr>
		<tr><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>%</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;">Остаток от деления</td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>5 % 2</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>1</code></td></tr>
	</tbody>
</table>

<h2 id="examples" style="color: #34495e; margin-top: 30px;">Примеры операций</h2>
<div style="background: #f8f9fa; border: 1px solid #dee2e6; border-radius: 8px; padding: 20px; margin: 20px 0;">
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>int sum = 5 + 3;
System.out.println(sum); // 8

int difference = 10 - 7;
System.out.println(difference); // 3

int product = 4 * 5;
System.out.println(product); // 20</code></pre>
</div>

<h2 id="division" style="color: #34495e; margin-top: 30px;">Деление int и double</h2>
<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #e65100; margin-top: 0;">⚠️ Важное правило</h4>
<p>Если делить два целых числа, Java вернёт целое число и отбросит дробную часть.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>int quotient = 9 / 2;
System.out.println(quotient); // 4</code></pre>
<p>Чтобы получить дробный результат, хотя бы одно число должно быть <code>double</code>.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>double preciseQuotient = 9.0 / 2.0;
System.out.println(preciseQuotient); // 4.5</code></pre>
</div>

<h2 id="remainder" style="color: #34495e; margin-top: 30px;">Остаток от деления</h2>
<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p>Оператор <code>%</code> возвращает остаток от деления.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>int remainder = 9 % 2;
System.out.println(remainder); // 1</code></pre>
<p>Это часто используют для проверки чётности числа:</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>int number = 8;
boolean isEven = number % 2 == 0;
System.out.println(isEven); // true</code></pre>
</div>

<h2 id="priority" style="color: #34495e; margin-top: 30px;">Приоритет операций</h2>
<p>Java выполняет арифметику в привычном порядке:</p>
<ol>
	<li>Скобки <code>()</code></li>
	<li>Умножение <code>*</code>, деление <code>/</code>, остаток <code>%</code></li>
	<li>Сложение <code>+</code> и вычитание <code>-</code></li>
</ol>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>int result = 3 + 5 * 2;
System.out.println(result); // 13

int anotherResult = (3 + 5) * 2;
System.out.println(anotherResult); // 16</code></pre>

<h2 id="short-ops" style="color: #34495e; margin-top: 30px;">Сокращённые операции</h2>
<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p>Если нужно изменить текущее значение переменной, можно использовать сокращённую запись.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>int x = 10;
x += 5; // x = 15
x -= 3; // x = 12
x *= 2; // x = 24
x /= 4; // x = 6
x %= 2; // x = 0</code></pre>
</div>

<h2 id="increment" style="color: #34495e; margin-top: 30px;">Инкремент и декремент</h2>
<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p><code>++</code> увеличивает значение на 1, а <code>--</code> уменьшает значение на 1.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>int count = 0;
count++; // count = 1
count--; // count = 0</code></pre>
</div>

<h2 id="common-mistakes" style="color: #34495e; margin-top: 30px;">Частые ошибки</h2>
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #ffebee;"><th style="padding: 10px; border: 1px solid #ef9a9a;">Ошибка</th><th style="padding: 10px; border: 1px solid #ef9a9a;">Почему так происходит</th></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;"><code>9 / 2</code> ожидают как <code>4.5</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;">Оба числа целые, поэтому Java возвращает целое число <code>4</code>.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;"><code>int result = 9.0 / 2.0;</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;">Результат дробный, его нельзя сохранить в <code>int</code> без явного преобразования.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Используют запятую в дробном числе</td><td style="padding: 10px; border: 1px solid #ef9a9a;">В Java дробная часть пишется через точку: <code>2.5</code>.</td></tr>
	</tbody>
</table>

<h2 id="practice" style="color: #34495e; margin-top: 30px;">Практические упражнения</h2>
<ul>
	<li>Создайте две переменные <code>int a = 10;</code> и <code>int b = 4;</code>, выведите сумму, разность и произведение.</li>
	<li>Проверьте, чему равно <code>10 / 4</code> и <code>10.0 / 4.0</code>.</li>
	<li>Создайте переменную <code>number</code> и проверьте, чётное ли это число через <code>%</code>.</li>
</ul>

<h2 id="quiz" style="color: #34495e; margin-top: 30px;">Проверь себя</h2>
<ul>
	<li>Какие арифметические операторы есть в Java?</li>
	<li>Что делает оператор <code>%</code>?</li>
	<li>Почему <code>9 / 2</code> даёт <code>4</code>?</li>
	<li>Как получить результат <code>4.5</code> при делении <code>9</code> на <code>2</code>?</li>
	<li>Что означает запись <code>x += 5</code>?</li>
	<li>Чем <code>count++</code> отличается от <code>count--</code>?</li>
</ul>

<h2 id="next" style="color: #34495e; margin-top: 30px;">Что дальше?</h2>
<p>Дальше эти операции будут использоваться в практических задачах: сложение, вычитание, деление, расчёт доставки, налогов и преобразование строк в числа.</p>

<div style="background: #d4edda; border-left: 4px solid #28a745; padding: 15px; margin: 20px 0;">
<h3 style="color: #155724; margin-top: 0;">Главное правило</h3>
<p style="margin: 0;">Сначала определите тип данных, а затем выбирайте операцию. Для целых чисел результат деления будет целым, для дробных &mdash; дробным.</p>
</div>

</div>
</div>
<p>&nbsp;</p>
