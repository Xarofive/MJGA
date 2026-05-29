<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">ArrayList в Java: динамический список</h1>

<p style="text-align: center; color: #666; margin-bottom: 30px;">Учимся хранить последовательность элементов, когда размер заранее неизвестен.</p>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">TL;DR</h3>
<ul>
	<li><code>ArrayList</code> — список, который может расти и уменьшаться во время работы программы.</li>
	<li>В отличие от массива <code>int[]</code>, размер <code>ArrayList</code> не нужно знать заранее.</li>
	<li>Элементы идут в понятном порядке: первый добавленный элемент имеет индекс <code>0</code>, второй — <code>1</code>.</li>
	<li>Для строк используйте <code>ArrayList&lt;String&gt;</code>, для целых чисел — <code>ArrayList&lt;Integer&gt;</code>.</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Когда нужен ArrayList</h2>

<p>Массив удобен, когда количество элементов известно заранее. Но во многих задачах данные приходят постепенно: пользователь вводит команды, программа читает строки, фильтрует числа или собирает ключи из <code>HashMap</code> для сортировки. В таких случаях нужен список, который можно пополнять.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">import java.util.ArrayList;

ArrayList&lt;String&gt; names = new ArrayList&lt;&gt;();
names.add("Alice");
names.add("Bob");
names.add("Charlie");

System.out.println(names.get(0)); // Alice
System.out.println(names.size()); // 3</code></pre>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 14px; margin: 16px 0;">
<h4 style="color: #e65100; margin-top: 0;">Что значит &lt;String&gt;</h4>
<p style="margin-bottom: 0;">Запись <code>ArrayList&lt;String&gt;</code> означает: список хранит строки. Коллекции Java работают с объектными типами, поэтому для чисел пишут <code>Integer</code>, а не <code>int</code>: <code>ArrayList&lt;Integer&gt;</code>.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Базовые операции</h2>

<table style="width: 100%; border-collapse: collapse; margin: 16px 0;">
	<thead>
		<tr style="background: #e3f2fd;">
			<th style="border: 1px solid #90caf9; padding: 10px; text-align: left;">Операция</th>
			<th style="border: 1px solid #90caf9; padding: 10px; text-align: left;">Пример</th>
			<th style="border: 1px solid #90caf9; padding: 10px; text-align: left;">Что делает</th>
		</tr>
	</thead>
	<tbody>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Добавить</td><td style="border: 1px solid #ddd; padding: 10px;"><code>list.add("milk")</code></td><td style="border: 1px solid #ddd; padding: 10px;">Добавляет в конец</td></tr>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Получить</td><td style="border: 1px solid #ddd; padding: 10px;"><code>list.get(0)</code></td><td style="border: 1px solid #ddd; padding: 10px;">Возвращает элемент по индексу</td></tr>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Заменить</td><td style="border: 1px solid #ddd; padding: 10px;"><code>list.set(0, "bread")</code></td><td style="border: 1px solid #ddd; padding: 10px;">Меняет элемент на указанном индексе</td></tr>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Удалить</td><td style="border: 1px solid #ddd; padding: 10px;"><code>list.remove(0)</code></td><td style="border: 1px solid #ddd; padding: 10px;">Удаляет элемент по индексу</td></tr>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Размер</td><td style="border: 1px solid #ddd; padding: 10px;"><code>list.size()</code></td><td style="border: 1px solid #ddd; padding: 10px;">Возвращает количество элементов</td></tr>
	</tbody>
</table>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">ArrayList&lt;String&gt; tasks = new ArrayList&lt;&gt;();

tasks.add("read");
tasks.add("practice");

String first = tasks.get(0); // read
tasks.set(1, "solve");
tasks.remove(0);

System.out.println(tasks.size()); // 1</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">Перебор элементов</h2>

<p>Если нужен индекс, используйте обычный цикл:</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">for (int i = 0; i &lt; tasks.size(); i++) {
    System.out.println(i + ": " + tasks.get(i));
}</code></pre>

<p>Если индекс не нужен, используйте <code>for-each</code>:</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">for (String task : tasks) {
    System.out.println(task);
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">ArrayList как пара к HashMap</h2>

<p>В задачах этого модуля <code>ArrayList</code> часто будет работать вместе с <code>HashMap</code>. <code>HashMap</code> быстро отвечает на вопрос «есть ли такой ключ?», а <code>ArrayList</code> сохраняет порядок или помогает отсортировать ключи перед выводом.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">ArrayList&lt;Integer&gt; unique = new ArrayList&lt;&gt;();

unique.add(10);
unique.add(20);
unique.add(30);

for (int value : unique) {
    System.out.println(value);
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">Частые ошибки</h2>

<div style="background: #ffebee; border: 1px solid #ef5350; border-radius: 8px; padding: 14px; margin: 20px 0;">
<ul style="margin-bottom: 0;">
	<li><strong>Индекс за границей:</strong> последний индекс равен <code>list.size() - 1</code>, поэтому <code>list.get(list.size())</code> приведёт к ошибке.</li>
	<li><strong>Неверный тип:</strong> <code>ArrayList&lt;int&gt;</code> писать нельзя, нужен <code>ArrayList&lt;Integer&gt;</code>.</li>
	<li><strong>Удаление в цикле:</strong> если удалять элементы слева направо, легко пропустить следующий элемент после удаления.</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Чек-лист самопроверки</h2>
<ul style="margin-bottom: 0;">
	<li><label><input type="checkbox"> Я могу создать <code>ArrayList&lt;String&gt;</code> и <code>ArrayList&lt;Integer&gt;</code></label></li>
	<li><label><input type="checkbox"> Я понимаю, зачем нужен импорт <code>java.util.ArrayList</code></label></li>
	<li><label><input type="checkbox"> Я использую <code>add</code>, <code>get</code>, <code>set</code>, <code>remove</code> и <code>size</code></label></li>
	<li><label><input type="checkbox"> Я помню, что индексы начинаются с нуля</label></li>
	<li><label><input type="checkbox"> Я понимаю, почему <code>ArrayList</code> помогает сохранить порядок элементов</label></li>
</ul>
</div>
</div>
