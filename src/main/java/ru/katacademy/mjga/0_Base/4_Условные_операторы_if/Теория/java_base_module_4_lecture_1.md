<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<p>&nbsp;</p>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">

<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">Java Base, Модуль 4, Лекция 1<br />Условный оператор if в Java</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть лекции</h3>
<ul>
	<li><strong>if</strong> проверяет условие и выполняет блок кода, если условие равно <code>true</code>.</li>
	<li>В Java условие пишется в круглых скобках: <code>if (condition)</code>.</li>
	<li><strong>else if</strong> добавляет следующую проверку, <strong>else</strong> обрабатывает все остальные случаи.</li>
	<li>Для сложных условий используются операторы <code>&amp;&amp;</code> (И), <code>||</code> (ИЛИ), <code>!</code> (НЕ).</li>
	<li>Фигурные скобки лучше писать всегда, даже если внутри одна строка.</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>
<p>Для лучшего понимания условных операторов в Java прослушайте аудиоподкаст:</p>
<p style="margin: 15px 0;"><a href="https://drive.google.com/file/d/1qETixnQq18nppCnQMTaZV4R3RPirDfsw/view?usp=sharing" style="display: inline-block; background: #1565c0; color: white; padding: 10px 20px; text-decoration: none; border-radius: 5px; font-weight: bold;" target="_blank">🎧 Прослушать об условных операторах</a></p>
<p style="font-size: 14px; color: #666; margin-top: 10px;"><em>Откроется в новой вкладке. Рекомендуется прослушать перед изучением материала для общего понимания или после — для закрепления.</em></p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎯 Чему вы научитесь</h4>
<ul>
	<li>✅ Писать конструкции <code>if</code>, <code>else if</code>, <code>else</code>.</li>
	<li>✅ Использовать операторы сравнения: <code>==</code>, <code>!=</code>, <code>&gt;</code>, <code>&gt;=</code>, <code>&lt;</code>, <code>&lt;=</code>.</li>
	<li>✅ Комбинировать условия через <code>&amp;&amp;</code>, <code>||</code> и <code>!</code>.</li>
	<li>✅ Возвращать разные значения из метода в зависимости от условия.</li>
	<li>✅ Проверять граничные случаи и избегать типичных ошибок.</li>
</ul>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">📚 Предпосылки</h4>
<p>Перед лекцией полезно уверенно знать:</p>
<ul>
	<li>переменные и типы данных <code>int</code>, <code>double</code>, <code>String</code>, <code>boolean</code>;</li>
	<li>методы с параметрами и возвращаемым значением;</li>
	<li>вывод через <code>System.out.println</code>;</li>
	<li>структуру класса <code>Main</code> и метода <code>main</code>.</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Содержание</h2>
<ul>
	<li><a href="#what">Что такое условная конструкция?</a></li>
	<li><a href="#syntax">Базовый if</a></li>
	<li><a href="#compare">Операторы сравнения</a></li>
	<li><a href="#else">if-else</a></li>
	<li><a href="#chain">Цепочка else if</a></li>
	<li><a href="#logic">Логические операторы</a></li>
	<li><a href="#return">Ранний return в методах</a></li>
	<li><a href="#mistakes">Частые ошибки</a></li>
	<li><a href="#practice">Мини-практика</a></li>
	<li><a href="#check">Чек-лист</a></li>
</ul>

<h2 id="what" style="color: #34495e; margin-top: 30px;">1. Что такое условная конструкция?</h2>
<p>Программа часто должна выбирать разные действия в зависимости от данных. Например, приложение банка проверяет, достаточно ли денег на счёте, а сервис доставки решает, какой приоритет дать заказу.</p>
<p>Для таких решений в Java используется оператор <code>if</code>. Он проверяет логическое выражение и выполняет код только тогда, когда результат равен <code>true</code>.</p>

<h2 id="syntax" style="color: #34495e; margin-top: 30px;">2. Базовый if</h2>
<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 15px; margin: 16px 0;">
<h4 style="color: #0c4a6e; margin-top: 0;">🎯 Синтаксис</h4>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>if (условие) {
    // код выполнится, если условие true
}</code></pre>
<p>Условие должно иметь тип <code>boolean</code>. В Java нельзя написать <code>if (1)</code> или <code>if ("yes")</code>: это не логические выражения.</p>
</div>

<h3 style="color: #34495e;">Пример: проверка возраста</h3>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    public static void main(String[] args) {
        int age = 20;

        if (age &gt;= 18) {
            System.out.println("Вы совершеннолетний");
            System.out.println("Можете голосовать на выборах");
        }

        System.out.println("Программа завершена");
    }
}</code></pre>
<div style="background: #f0f0f0; border-left: 3px solid #666; padding: 10px; margin: 10px 0;">
<strong>Ожидаемый вывод:</strong>
<pre style="margin: 5px 0 0 0;">Вы совершеннолетний
Можете голосовать на выборах
Программа завершена</pre>
</div>

<h2 id="compare" style="color: #34495e; margin-top: 30px;">3. Операторы сравнения</h2>
<table style="width: 100%; border-collapse: collapse; background: white;">
	<tbody>
		<tr style="background: #e3f2fd;"><th style="padding: 10px; border: 1px solid #90caf9;">Оператор</th><th style="padding: 10px; border: 1px solid #90caf9;">Смысл</th><th style="padding: 10px; border: 1px solid #90caf9;">Пример</th><th style="padding: 10px; border: 1px solid #90caf9;">Результат</th></tr>
		<tr><td style="padding: 10px; border: 1px solid #90caf9;"><code>==</code></td><td style="padding: 10px; border: 1px solid #90caf9;">равно</td><td style="padding: 10px; border: 1px solid #90caf9;"><code>5 == 5</code></td><td style="padding: 10px; border: 1px solid #90caf9;"><code>true</code></td></tr>
		<tr><td style="padding: 10px; border: 1px solid #90caf9;"><code>!=</code></td><td style="padding: 10px; border: 1px solid #90caf9;">не равно</td><td style="padding: 10px; border: 1px solid #90caf9;"><code>5 != 3</code></td><td style="padding: 10px; border: 1px solid #90caf9;"><code>true</code></td></tr>
		<tr><td style="padding: 10px; border: 1px solid #90caf9;"><code>&lt;</code></td><td style="padding: 10px; border: 1px solid #90caf9;">меньше</td><td style="padding: 10px; border: 1px solid #90caf9;"><code>3 &lt; 5</code></td><td style="padding: 10px; border: 1px solid #90caf9;"><code>true</code></td></tr>
		<tr><td style="padding: 10px; border: 1px solid #90caf9;"><code>&lt;=</code></td><td style="padding: 10px; border: 1px solid #90caf9;">меньше или равно</td><td style="padding: 10px; border: 1px solid #90caf9;"><code>5 &lt;= 5</code></td><td style="padding: 10px; border: 1px solid #90caf9;"><code>true</code></td></tr>
		<tr><td style="padding: 10px; border: 1px solid #90caf9;"><code>&gt;</code></td><td style="padding: 10px; border: 1px solid #90caf9;">больше</td><td style="padding: 10px; border: 1px solid #90caf9;"><code>5 &gt; 3</code></td><td style="padding: 10px; border: 1px solid #90caf9;"><code>true</code></td></tr>
		<tr><td style="padding: 10px; border: 1px solid #90caf9;"><code>&gt;=</code></td><td style="padding: 10px; border: 1px solid #90caf9;">больше или равно</td><td style="padding: 10px; border: 1px solid #90caf9;"><code>5 &gt;= 5</code></td><td style="padding: 10px; border: 1px solid #90caf9;"><code>true</code></td></tr>
	</tbody>
</table>

<div style="background: #fee2e2; padding: 15px; border-radius: 5px; margin-top: 15px;">
<p style="margin: 0;"><strong>❌ Частая ошибка:</strong> путать <code>=</code> и <code>==</code>.</p>
<ul style="margin: 10px 0 0 0;">
	<li><code>x = 5</code> &mdash; присваивание значения.</li>
	<li><code>x == 5</code> &mdash; проверка равенства.</li>
</ul>
</div>

<h2 id="else" style="color: #34495e; margin-top: 30px;">4. if-else: выбор из двух вариантов</h2>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>double balance = 1500.50;
double price = 2000.00;

if (balance &gt;= price) {
    System.out.println("Покупка одобрена");
    System.out.println("Остаток: " + (balance - price) + " руб.");
} else {
    System.out.println("Недостаточно средств");
    System.out.println("Не хватает: " + (price - balance) + " руб.");
}</code></pre>
<p>Для вывода текста и значения в Base достаточно <code>System.out.println</code> и соединения через <code>+</code>.</p>
<p>Блок <code>else</code> выполняется только тогда, когда условие в <code>if</code> ложно.</p>

<h2 id="chain" style="color: #34495e; margin-top: 30px;">5. Цепочка else if</h2>
<p>Когда вариантов больше двух, удобно использовать цепочку проверок.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>int temperature = 25;

if (temperature &lt; 0) {
    System.out.println("freezing");
} else if (temperature &lt;= 17) {
    System.out.println("chilly");
} else if (temperature &lt;= 27) {
    System.out.println("warm");
} else {
    System.out.println("hot");
}</code></pre>
<p>Java проверяет условия сверху вниз и выполняет первый подходящий блок. Остальные блоки цепочки уже не проверяются.</p>

<h2 id="logic" style="color: #34495e; margin-top: 30px;">6. Логические операторы</h2>
<ul>
	<li><code>&amp;&amp;</code> &mdash; И: оба условия должны быть истинными.</li>
	<li><code>||</code> &mdash; ИЛИ: достаточно одного истинного условия.</li>
	<li><code>!</code> &mdash; НЕ: меняет <code>true</code> на <code>false</code> и наоборот.</li>
</ul>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>int age = 20;
boolean hasTicket = true;
boolean vip = false;

if ((age &gt;= 18 &amp;&amp; hasTicket) || vip) {
    System.out.println("allowed");
} else {
    System.out.println("denied");
}</code></pre>

<div style="background: #fff8e1; border-left: 4px solid #ffc107; padding: 15px; margin: 20px 0;">
<h4 style="color: #f57c00; margin-top: 0;">💡 Приоритет операций</h4>
<p>Оператор <code>&amp;&amp;</code> выполняется раньше <code>||</code>. Если условие сложное, используйте скобки: так код читается быстрее и меньше риск ошибиться.</p>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">Почему в задачах запрещают другие операторы выбора</h4>
<p style="margin: 0;">Позже будет отдельная тема про выбор из фиксированных вариантов. В этом модуле цель другая: научиться уверенно писать условия через <code>if</code>, <code>else if</code>, <code>else</code> и логические операторы.</p>
</div>

<h2 id="return" style="color: #34495e; margin-top: 30px;">7. Ранний return в методах</h2>
<p>В задачах модуля часто нужно вернуть строку из метода. Можно использовать цепочку <code>if-else</code>, а можно делать ранний выход через <code>return</code>.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>static String scoreLabel(int score) {
    if (score &lt; 0 || score &gt; 100) {
        return "invalid";
    }

    if (score &gt;= 90) {
        return "excellent";
    }

    if (score &gt;= 70) {
        return "passed";
    }

    return "failed";
}</code></pre>
<p>После выполнения <code>return</code> метод сразу завершается. Код ниже в этом же методе уже не выполняется.</p>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">Коротко про сравнение строк</h4>
<p style="margin: 0;">Числа сравнивают через <code>==</code>, например <code>age == 18</code>. Для строк в Java используют метод <code>equals</code>: <code>text.equals("yes")</code>. Подробная работа со строками будет позже, но это правило полезно знать уже сейчас.</p>
</div>

<h2 id="mistakes" style="color: #34495e; margin-top: 30px;">8. Частые ошибки</h2>
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #ffebee;"><th style="padding: 10px; border: 1px solid #ef9a9a;">Ошибка</th><th style="padding: 10px; border: 1px solid #ef9a9a;">Как исправить</th></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Забыли круглые скобки</td><td style="padding: 10px; border: 1px solid #ef9a9a;">Пишите <code>if (x &gt; 0)</code>.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Поставили <code>=</code> вместо <code>==</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;">Для сравнения используйте <code>==</code>.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Сравнивают строки через <code>==</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;">Для строк используйте <code>text.equals("value")</code>.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Неправильные границы диапазонов</td><td style="padding: 10px; border: 1px solid #ef9a9a;">Проверяйте значения на границах: 0, 18, 70, 90 и т.д.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Глубокая вложенность</td><td style="padding: 10px; border: 1px solid #ef9a9a;">Используйте ранний <code>return</code> или цепочку <code>else if</code>.</td></tr>
	</tbody>
</table>

<h2 id="practice" style="color: #34495e; margin-top: 30px;">9. Мини-практика</h2>
<ul>
	<li>Напишите метод <code>static String describeSign(int n)</code>, который возвращает <code>"positive"</code>, <code>"zero"</code> или <code>"negative"</code>.</li>
	<li>Напишите метод <code>static String ageGroup(int age)</code>, который возвращает <code>"child"</code>, <code>"adult"</code> или <code>"invalid"</code>.</li>
	<li>Проверьте, как меняется результат при граничных значениях: <code>0</code>, <code>1</code>, <code>17</code>, <code>18</code>.</li>
</ul>

<h2 id="check" style="color: #34495e; margin-top: 30px;">✅ Чек-лист самопроверки</h2>
<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 14px; margin: 20px 0;">
<ul style="margin-bottom: 0; list-style: none; padding-left: 0;">
	<li><label><input type="checkbox"> Я понимаю, что условие в <code>if</code> должно быть типа <code>boolean</code>.</label></li>
	<li><label><input type="checkbox"> Я помню про круглые скобки вокруг условия в Java.</label></li>
	<li><label><input type="checkbox"> Я различаю <code>=</code> и <code>==</code>.</label></li>
	<li><label><input type="checkbox"> Я умею строить цепочку <code>if</code> / <code>else if</code> / <code>else</code>.</label></li>
	<li><label><input type="checkbox"> Я могу объединять условия через <code>&amp;&amp;</code> и <code>||</code>.</label></li>
	<li><label><input type="checkbox"> Я проверяю граничные значения, а не только обычные примеры.</label></li>
</ul>
</div>

<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
<p>&nbsp;</p>
