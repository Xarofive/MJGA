<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<p>&nbsp;</p>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">

<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">Java Base, Модуль 2, Лекция 1<br />Переменные в Java</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть лекции</h3>
<ul>
	<li><strong>Переменная</strong> &mdash; это именованное место для хранения значения.</li>
	<li>В Java у каждой переменной есть <strong>тип</strong>, <strong>имя</strong> и <strong>значение</strong>.</li>
	<li>Переменную можно объявить с явным типом: <code>int age = 25;</code>.</li>
	<li>В Base пишем типы явно: <code>int age = 25;</code>, <code>String name = "Alice";</code>.</li>
	<li><strong>Константы</strong> создаются через <code>final</code> и не меняются после присваивания.</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>
<p>Для лучшего понимания переменных и типов данных в Java прослушайте аудиоподкаст:</p>
<p style="margin: 15px 0;"><a href="https://drive.google.com/file/d/1EehJt-Jtyozj1QOVIKsoZL5gF-iy-Ihm/view?usp=sharing" style="display: inline-block; background: #1565c0; color: white; padding: 10px 20px; text-decoration: none; border-radius: 5px; font-weight: bold;" target="_blank">🎧 Прослушать о переменных и типах данных</a></p>
<p style="font-size: 14px; color: #666; margin-top: 10px;"><em>Откроется в новой вкладке. Рекомендуется прослушать перед изучением материала для общего понимания или после — для закрепления.</em></p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Содержание</h2>
<ul>
	<li><a href="#what-are-variables">Что такое переменные?</a></li>
	<li><a href="#declaration">Объявление переменных</a></li>
	<li><a href="#data-types">Основные типы данных</a></li>
	<li><a href="#multiple-variables">Несколько переменных</a></li>
	<li><a href="#naming-rules">Правила именования</a></li>
	<li><a href="#constants">Константы final</a></li>
	<li><a href="#common-mistakes">Частые ошибки</a></li>
	<li><a href="#practice">Практические упражнения</a></li>
	<li><a href="#quiz">Проверь себя</a></li>
	<li><a href="#next">Что дальше?</a></li>
</ul>

<h2 id="what-are-variables" style="color: #34495e; margin-top: 30px;">Что такое переменные?</h2>
<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 15px; margin: 16px 0;">
<h4 style="color: #0c4a6e; margin-top: 0;">📦 Переменные &mdash; это коробочки для данных</h4>
<p>Переменная хранит одно значение, к которому можно обратиться по имени.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>int age = 25;
String name = "Alice";
boolean isStudent = true;</code></pre>
<p><strong>Зачем нужны переменные:</strong></p>
<ul>
	<li>сохранять данные: имя, возраст, цену, результат вычисления;</li>
	<li>использовать значение несколько раз;</li>
	<li>менять значение во время работы программы.</li>
</ul>
</div>

<h2 id="declaration" style="color: #34495e; margin-top: 30px;">Объявление переменных</h2>
<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">📝 Полная форма</h4>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>тип имяПеременной = значение;</code></pre>
<p><strong>Примеры:</strong></p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>int age = 25;             // целое число
String name = "Alice";    // текст
double height = 1.75;     // дробное число
boolean isStudent = true; // да/нет</code></pre>
<p>Точка с запятой <code>;</code> завершает инструкцию в Java.</p>
</div>


<h2 id="data-types" style="color: #34495e; margin-top: 30px;">Основные типы данных</h2>
<div style="background: #f8f9fa; border: 1px solid #dee2e6; border-radius: 8px; padding: 20px; margin: 20px 0;">
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #e8f5e9;"><th style="padding: 10px; border: 1px solid #c8e6c9;">Тип</th><th style="padding: 10px; border: 1px solid #c8e6c9;">Что хранит</th><th style="padding: 10px; border: 1px solid #c8e6c9;">Пример</th></tr>
		<tr><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>int</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;">целые числа</td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>int count = 10;</code></td></tr>
		<tr><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>double</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;">дробные числа</td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>double price = 99.99;</code></td></tr>
		<tr><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>String</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;">текст</td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>String city = "Moscow";</code></td></tr>
		<tr><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>boolean</code></td><td style="padding: 10px; border: 1px solid #c8e6c9;">true или false</td><td style="padding: 10px; border: 1px solid #c8e6c9;"><code>boolean ok = true;</code></td></tr>
	</tbody>
</table>
</div>

<h2 id="multiple-variables" style="color: #34495e; margin-top: 30px;">Несколько переменных</h2>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>int a = 10;
int b = 20;
int sum = a + b;</code></pre>
<p>В Java можно объявить несколько переменных одного типа в одной строке, но новичкам лучше писать по одной переменной на строку.</p>

<h2 id="naming-rules" style="color: #34495e; margin-top: 30px;">Правила именования</h2>
<ul>
	<li>Имена переменных пишут в стиле <code>camelCase</code>: <code>userName</code>, <code>totalPrice</code>.</li>
	<li>Имя должно объяснять смысл значения.</li>
	<li>Нельзя начинать имя с цифры.</li>
	<li>Не используйте ключевые слова Java: <code>class</code>, <code>public</code>, <code>int</code>.</li>
</ul>

<h2 id="constants" style="color: #34495e; margin-top: 30px;">Константы final</h2>
<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p>Если значение не должно меняться, используйте <code>final</code>.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>final int TAX_PERCENT = 13;
final String CURRENCY = "RUB";</code></pre>
<p>Константы часто пишут заглавными буквами через подчёркивание.</p>
</div>

<h2 id="common-mistakes" style="color: #34495e; margin-top: 30px;">Частые ошибки</h2>
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #ffebee;"><th style="padding: 10px; border: 1px solid #ef9a9a;">Ошибка</th><th style="padding: 10px; border: 1px solid #ef9a9a;">Как исправить</th></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;"><code>int age = "25";</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;">Для числа используйте <code>25</code>, без кавычек.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;"><code>String name = Alice;</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;">Текст пишется в кавычках: <code>"Alice"</code>.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;"><code>boolean ok = "true";</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;"><code>true</code> и <code>false</code> пишутся без кавычек.</td></tr>
	</tbody>
</table>

<h2 id="practice" style="color: #34495e; margin-top: 30px;">Практические упражнения</h2>
<ul>
	<li>Создайте переменные <code>age</code>, <code>name</code>, <code>height</code>, <code>isActive</code> и выведите их.</li>
	<li>Поменяйте значение переменной <code>age</code> и запустите программу снова.</li>
	<li>Создайте константу <code>COURSE_NAME</code> и попробуйте изменить её значение.</li>
</ul>

<h2 id="quiz" style="color: #34495e; margin-top: 30px;">Проверь себя</h2>
<ul>
	<li>Что такое переменная?</li>
	<li>Из каких частей состоит объявление переменной?</li>
	<li>Чем <code>int</code> отличается от <code>String</code>?</li>
	<li>Зачем нужен <code>final</code>?</li>
	<li>Почему <code>"25"</code> и <code>25</code> &mdash; разные значения?</li>
</ul>

<h2 id="next" style="color: #34495e; margin-top: 30px;">Что дальше?</h2>
<p>Дальше разберём типы данных подробнее: целые числа, дробные числа, строки, логические значения и преобразование типов.</p>

<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
<p>&nbsp;</p>
