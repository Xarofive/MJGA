<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<p>&nbsp;</p>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">

<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">Java Base, Модуль 2, Лекция 2<br />Типы данных в Java</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть лекции</h3>
<ul>
	<li><strong>Тип данных</strong> определяет, какие значения можно хранить в переменной.</li>
	<li>Для старта нужны <code>int</code>, <code>double</code>, <code>String</code> и <code>boolean</code>.</li>
	<li>Java строго проверяет типы: нельзя просто сложить число и текст как два числа.</li>
	<li><code>String</code> пишется с большой буквы, потому что это не примитивный тип, а класс.</li>
	<li>Преобразование типов нужно делать явно, когда Java не может сделать это безопасно сама.</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>
<p><strong>Аудио по типам данных в Java будет добавлено позже.</strong></p>
<p style="margin: 15px 0;"><span style="display: inline-block; background: #1565c0; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold;">🎧 Аудио будет добавлено</span></p>
<p style="font-size: 14px; color: #666; margin-top: 10px;"><em>Пока изучайте материал по тексту и запускайте примеры в IntelliJ IDEA.</em></p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Содержание</h2>
<ul>
	<li><a href="#why-types">Зачем нужны типы данных?</a></li>
	<li><a href="#int-type">Целые числа: int</a></li>
	<li><a href="#double-type">Дробные числа: double</a></li>
	<li><a href="#string-type">Текст: String</a></li>
	<li><a href="#boolean-type">Логический тип: boolean</a></li>
	<li><a href="#conversion">Преобразование типов</a></li>
	<li><a href="#check-type">Как понять тип?</a></li>
	<li><a href="#common-mistakes">Частые ошибки</a></li>
	<li><a href="#practice">Практические упражнения</a></li>
	<li><a href="#quiz">Проверь себя</a></li>
</ul>

<h2 id="why-types" style="color: #34495e; margin-top: 30px;">Зачем нужны типы данных?</h2>
<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p>Типы защищают программу от ошибок. Если переменная объявлена как <code>int</code>, Java не позволит положить туда текст.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>int age = 25;        // правильно
int wrong = "25";    // ошибка: строка не является числом</code></pre>
</div>

<h2 id="int-type" style="color: #34495e; margin-top: 30px;">Целые числа: int</h2>
<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p><code>int</code> хранит целые числа без дробной части.</p>
<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px;"><code>int age = 25;
int count = 100;
int score = -50;</code></pre>
<p>Используйте <code>int</code> для возраста, количества, счётчиков, номеров.</p>
</div>

<h2 id="double-type" style="color: #34495e; margin-top: 30px;">Дробные числа: double</h2>
<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p><code>double</code> хранит числа с дробной частью.</p>
<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px;"><code>double price = 99.99;
double height = 1.75;
double temperature = -5.5;</code></pre>
<p>Дробная часть в Java записывается через точку, не через запятую.</p>
</div>

<h2 id="string-type" style="color: #34495e; margin-top: 30px;">Текст: String</h2>
<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p><code>String</code> хранит текст в двойных кавычках.</p>
<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px;"><code>String name = "Alice";
String city = "Moscow";
String numberAsText = "123";</code></pre>
<p><code>"123"</code> &mdash; это текст. Его нельзя использовать как число без преобразования.</p>
</div>

<h2 id="boolean-type" style="color: #34495e; margin-top: 30px;">Логический тип: boolean</h2>
<div style="background: #fce4ec; border: 1px solid #e91e63; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p><code>boolean</code> хранит только два значения: <code>true</code> или <code>false</code>.</p>
<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px;"><code>boolean isActive = true;
boolean isBlocked = false;

int age = 20;
boolean isAdult = age &gt;= 18;</code></pre>
<p>Позже <code>boolean</code> будет использоваться в условиях <code>if</code>.</p>
</div>

<h2 id="conversion" style="color: #34495e; margin-top: 30px;">Преобразование типов</h2>
<div style="background: #f8f9fa; border: 1px solid #dee2e6; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p>Иногда значение нужно перевести из одного типа в другой.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>int count = 15;
double result = count;       // int безопасно превращается в double

double price = 99.99;
int rounded = (int) price;   // 99, дробная часть отброшена</code></pre>
<p>Преобразование <code>(int) price</code> называется явным приведением типа.</p>
</div>

<h2 id="check-type" style="color: #34495e; margin-top: 30px;">Как понять тип?</h2>
<p>В Java тип обычно видно прямо в объявлении переменной:</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>int n = 25;
double p = 99.99;
String user = "Alice";
boolean ok = true;</code></pre>
<p>При использовании <code>var</code> тип можно увидеть в подсказках IntelliJ IDEA при наведении на переменную.</p>

<h2 id="common-mistakes" style="color: #34495e; margin-top: 30px;">Частые ошибки</h2>
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #ffebee;"><th style="padding: 10px; border: 1px solid #ef9a9a;">Ошибка</th><th style="padding: 10px; border: 1px solid #ef9a9a;">Почему</th></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;"><code>double price = 99,99;</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;">В Java дробная часть пишется через точку.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;"><code>String name = 'Alice';</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;">Строки пишутся в двойных кавычках.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;"><code>boolean ok = 1;</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;">В Java <code>boolean</code> принимает только <code>true</code> или <code>false</code>.</td></tr>
	</tbody>
</table>

<h2 id="practice" style="color: #34495e; margin-top: 30px;">Практические упражнения</h2>
<ul>
	<li>Создайте переменные всех четырёх базовых типов и выведите их.</li>
	<li>Создайте <code>double price</code> и преобразуйте его в <code>int</code>.</li>
	<li>Создайте <code>boolean isAdult</code> через сравнение возраста с 18.</li>
</ul>

<h2 id="quiz" style="color: #34495e; margin-top: 30px;">Проверь себя</h2>
<ul>
	<li>Для чего нужны типы данных?</li>
	<li>Чем <code>int</code> отличается от <code>double</code>?</li>
	<li>Почему <code>String</code> пишется с большой буквы?</li>
	<li>Что хранит <code>boolean</code>?</li>
	<li>Что произойдёт при преобразовании <code>99.99</code> в <code>int</code>?</li>
</ul>

</div>
</div>
<p>&nbsp;</p>
