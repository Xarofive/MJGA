<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">HashMap: пары ключ-значение</h1>

<p style="text-align: center; color: #666; margin-bottom: 30px;">Быстрый поиск, обновление, удаление и подсчёт по ключу в Java.</p>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">Аудиообъяснение темы</h4>
<p style="margin-bottom: 0;"><strong>Заглушка для аудио:</strong> сюда позже будет добавлена ссылка на подкаст по <code>HashMap</code> в Java.</p>
</div>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">TL;DR</h3>
<ul>
	<li><code>HashMap&lt;K, V&gt;</code> хранит пары: ключ типа <code>K</code> и значение типа <code>V</code>.</li>
	<li>По ключу можно быстро получить значение: обычно это близко к <code>O(1)</code>.</li>
	<li>Создание: <code>HashMap&lt;String, Integer&gt; counts = new HashMap&lt;&gt;();</code></li>
	<li>Операции: <code>put</code>, <code>get</code>, <code>containsKey</code>, <code>remove</code>, <code>size</code>.</li>
	<li>Порядок обхода <code>HashMap</code> не гарантирован.</li>
	<li>Если нужен алфавитный вывод, соберите ключи в <code>ArrayList</code> и отсортируйте через <code>Collections.sort</code>.</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Что такое HashMap</h2>

<p>Представьте телефонную книгу: по имени нужно быстро найти номер. Или счётчик категорий: по названию категории нужно быстро узнать количество. Для таких задач в Java используется <code>HashMap</code>.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">import java.util.HashMap;

HashMap&lt;String, String&gt; phonebook = new HashMap&lt;&gt;();

phonebook.put("Alice", "123456");
phonebook.put("Bob", "789012");

String phone = phonebook.get("Alice"); // 123456</code></pre>

<p><strong>Почему не ArrayList?</strong> В списке для поиска по имени пришлось бы перебирать элементы один за другим. <code>HashMap</code> хранит данные так, чтобы быстро находить значение по ключу.</p>

<h2 style="color: #34495e; margin-top: 30px;">Ключи и значения</h2>

<p>В записи <code>HashMap&lt;String, Integer&gt;</code> первый тип — это тип ключа, второй тип — тип значения.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">HashMap&lt;String, Integer&gt; scores = new HashMap&lt;&gt;();
// ключ: String, значение: Integer

scores.put("Alice", 95);
scores.put("Bob", 87);</code></pre>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 14px; margin: 16px 0;">
<h4 style="color: #e65100; margin-top: 0;">Про ключи в Java</h4>
<p style="margin-bottom: 0;">В этом модуле используем простые ключи: <code>String</code>, <code>Integer</code>, <code>Character</code>. Для собственных классов нужно правильно настраивать <code>equals</code> и <code>hashCode</code>, но классы будут позже, поэтому сейчас не углубляемся.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Создание и инициализация</h2>

<p>Главное правило: перед записью в <code>HashMap</code> объект должен быть создан через <code>new HashMap&lt;&gt;()</code>.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">// Правильно
HashMap&lt;String, Integer&gt; counts = new HashMap&lt;&gt;();
counts.put("apple", 1);

// Неправильно
HashMap&lt;String, Integer&gt; broken = null;
// broken.put("apple", 1); // NullPointerException</code></pre>

<p>Если переменная ссылается на <code>null</code>, а вы пытаетесь вызвать у неё метод, Java выбросит <code>NullPointerException</code>. Поэтому перед работой с коллекцией её нужно создать.</p>

<h2 style="color: #34495e; margin-top: 30px;">Основные операции</h2>

<table style="width: 100%; border-collapse: collapse; margin: 16px 0;">
	<thead>
		<tr style="background: #e3f2fd;">
			<th style="border: 1px solid #90caf9; padding: 10px; text-align: left;">Операция</th>
			<th style="border: 1px solid #90caf9; padding: 10px; text-align: left;">Java</th>
			<th style="border: 1px solid #90caf9; padding: 10px; text-align: left;">Смысл</th>
		</tr>
	</thead>
	<tbody>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Записать</td><td style="border: 1px solid #ddd; padding: 10px;"><code>map.put(key, value)</code></td><td style="border: 1px solid #ddd; padding: 10px;">Добавить или заменить значение</td></tr>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Прочитать</td><td style="border: 1px solid #ddd; padding: 10px;"><code>map.get(key)</code></td><td style="border: 1px solid #ddd; padding: 10px;">Получить значение или <code>null</code></td></tr>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Проверить ключ</td><td style="border: 1px solid #ddd; padding: 10px;"><code>map.containsKey(key)</code></td><td style="border: 1px solid #ddd; padding: 10px;">Понять, есть ли ключ</td></tr>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Удалить</td><td style="border: 1px solid #ddd; padding: 10px;"><code>map.remove(key)</code></td><td style="border: 1px solid #ddd; padding: 10px;">Удалить пару ключ-значение</td></tr>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Размер</td><td style="border: 1px solid #ddd; padding: 10px;"><code>map.size()</code></td><td style="border: 1px solid #ddd; padding: 10px;">Количество пар</td></tr>
	</tbody>
</table>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">HashMap&lt;String, String&gt; phonebook = new HashMap&lt;&gt;();

phonebook.put("Alice", "123456");
phonebook.put("Alice", "999999"); // старое значение заменится

if (phonebook.containsKey("Alice")) {
    System.out.println(phonebook.get("Alice"));
}

phonebook.remove("Alice");
System.out.println(phonebook.size());</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">Проверка наличия ключа</h2>

<p><code>get</code> возвращает <code>null</code>, если ключа нет. Но лучше явно использовать <code>containsKey</code>, когда от наличия ключа зависит логика вывода.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">if (phonebook.containsKey(name)) {
    System.out.println(phonebook.get(name));
} else {
    System.out.println("NOT FOUND");
}</code></pre>

<p>Это особенно важно, если <code>null</code> теоретически может быть допустимым значением. В учебных задачах мы обычно не кладём <code>null</code> в коллекции, но привычка проверять ключ явно полезна.</p>

<h2 style="color: #34495e; margin-top: 30px;">Подсчёт частоты</h2>

<p>Для счётчиков удобно использовать <code>getOrDefault</code>. Метод возвращает значение по ключу, а если ключа нет — указанное значение по умолчанию.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">HashMap&lt;String, Integer&gt; counts = new HashMap&lt;&gt;();

String category = "apple";
int oldCount = counts.getOrDefault(category, 0);
counts.put(category, oldCount + 1);</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">Порядок обхода не гарантирован</h2>

<p><code>HashMap</code> не хранит элементы в порядке добавления и не гарантирует алфавитный порядок. Поэтому нельзя писать решение, которое зависит от порядка обхода <code>keySet()</code>.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">for (String key : counts.keySet()) {
    System.out.println(key + " " + counts.get(key));
}</code></pre>

<p>Такой код подходит только там, где порядок вывода не важен. Если порядок важен, используйте паттерн из следующей лекции: собрать ключи в <code>ArrayList</code>, отсортировать, пройти по отсортированным ключам.</p>

<h2 style="color: #34495e; margin-top: 30px;">Чек-лист самопроверки</h2>
<ul style="margin-bottom: 0;">
	<li><label><input type="checkbox"> Я понимаю запись <code>HashMap&lt;K, V&gt;</code></label></li>
	<li><label><input type="checkbox"> Я могу создать <code>HashMap</code> через <code>new HashMap&lt;&gt;()</code></label></li>
	<li><label><input type="checkbox"> Я использую <code>put</code>, <code>get</code>, <code>containsKey</code>, <code>remove</code> и <code>size</code></label></li>
	<li><label><input type="checkbox"> Я понимаю, почему порядок обхода <code>HashMap</code> нельзя считать стабильным</label></li>
	<li><label><input type="checkbox"> Я могу использовать <code>getOrDefault</code> для счётчиков</label></li>
</ul>
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
