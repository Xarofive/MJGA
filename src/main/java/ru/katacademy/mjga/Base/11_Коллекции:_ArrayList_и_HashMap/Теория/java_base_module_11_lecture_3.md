<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">Практические паттерны HashMap и ArrayList</h1>

<p style="text-align: center; color: #666; margin-bottom: 30px;">Собираем приёмы, которые нужны в задачах модуля: множество, частотный анализ, сортировка ключей и вложенные карты.</p>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">Что будет использоваться в практике</h3>
<ul style="margin-bottom: 0;">
	<li><code>HashMap&lt;Integer, Boolean&gt;</code> как множество: быстро проверить, встречалось ли число.</li>
	<li><code>HashMap&lt;String, Integer&gt;</code> как счётчик частот.</li>
	<li><code>ArrayList&lt;String&gt;</code> для сохранения порядка или сортировки ключей.</li>
	<li><code>HashMap&lt;String, HashMap&lt;String, Integer&gt;&gt;</code> для группировки товаров по категориям.</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. HashMap как множество</h2>

<p>В этом модуле множество можно представить как <code>HashMap&lt;Integer, Boolean&gt;</code>. Ключ — сам элемент, значение — отметка <code>true</code>. Нам важно быстро проверить, встречался ли элемент раньше.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">HashMap&lt;Integer, Boolean&gt; seen = new HashMap&lt;&gt;();
ArrayList&lt;Integer&gt; unique = new ArrayList&lt;&gt;();

for (int value : values) {
    if (!seen.containsKey(value)) {
        seen.put(value, true);
        unique.add(value);
    }
}</code></pre>

<p>Такой паттерн решает задачу удаления дубликатов с сохранением порядка: <code>HashMap</code> быстро проверяет повтор, <code>ArrayList</code> хранит результат в порядке первого появления.</p>

<h2 style="color: #34495e; margin-top: 30px;">2. Частотный анализ</h2>

<p>Если нужно посчитать, сколько раз встретилась каждая строка, используйте <code>HashMap&lt;String, Integer&gt;</code>.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">HashMap&lt;String, Integer&gt; counts = new HashMap&lt;&gt;();

for (String category : categories) {
    int oldCount = counts.getOrDefault(category, 0);
    counts.put(category, oldCount + 1);
}</code></pre>

<p><code>getOrDefault(category, 0)</code> означает: если ключ есть, возьми его значение; если ключа нет, используй <code>0</code>.</p>

<h2 style="color: #34495e; margin-top: 30px;">3. Сортированный вывод HashMap</h2>

<p>У <code>HashMap</code> нет гарантированного порядка обхода. Для предсказуемого вывода соберите ключи в <code>ArrayList</code> и отсортируйте их.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">import java.util.ArrayList;
import java.util.Collections;
import java.util.HashMap;

ArrayList&lt;String&gt; keys = new ArrayList&lt;&gt;(counts.keySet());
Collections.sort(keys);

for (String key : keys) {
    System.out.println(key + " " + counts.get(key));
}</code></pre>

<p><code>keySet()</code> возвращает набор ключей. Конструктор <code>new ArrayList&lt;&gt;(counts.keySet())</code> копирует эти ключи в список, а <code>Collections.sort(keys)</code> сортирует список на месте.</p>

<h2 style="color: #34495e; margin-top: 30px;">4. Вложенный HashMap</h2>

<p>Для данных с двумя уровнями удобно использовать <code>HashMap</code> внутри <code>HashMap</code>. Например: категория → товар → стоимость.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">HashMap&lt;String, HashMap&lt;String, Integer&gt;&gt; inventory = new HashMap&lt;&gt;();

String category = "groceries";
String item = "milk";
int totalCost = 100;

if (!inventory.containsKey(category)) {
    inventory.put(category, new HashMap&lt;&gt;());
}

HashMap&lt;String, Integer&gt; items = inventory.get(category);
int oldCost = items.getOrDefault(item, 0);
items.put(item, oldCost + totalCost);</code></pre>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 14px; margin: 16px 0;">
<h4 style="color: #e65100; margin-top: 0;">Важная деталь</h4>
<p style="margin-bottom: 0;">Перед записью во внутренний <code>HashMap</code> его нужно создать. Если категории ещё нет и вы сразу напишете <code>inventory.get(category).put(item, cost)</code>, программа упадёт с <code>NullPointerException</code>.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">5. Командный ввод</h2>

<p>В задачах с командами удобно читать строку целиком через <code>BufferedReader</code>, разбивать её на части и обрабатывать первую часть как команду.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">String line = reader.readLine();
String[] parts = line.split("\\s+");

String command = parts[0];

switch (command) {
    case "PUT":
        String name = parts[1];
        String phone = parts[2];
        phonebook.put(name, phone);
        break;
    case "COUNT":
        writer.println(phonebook.size());
        break;
}</code></pre>

<p><code>split("\\s+")</code> разбивает строку по одному или нескольким пробельным символам. <code>BufferedReader</code> и <code>PrintWriter</code> уже встречались в модуле про ввод; здесь они нужны для быстрой обработки большого количества команд.</p>

<h2 style="color: #34495e; margin-top: 30px;">Чек-лист перед практикой</h2>
<ul style="margin-bottom: 0;">
	<li><label><input type="checkbox"> Я понимаю, как использовать <code>HashMap&lt;Integer, Boolean&gt;</code> для проверки повторов</label></li>
	<li><label><input type="checkbox"> Я могу увеличить счётчик через <code>getOrDefault</code></label></li>
	<li><label><input type="checkbox"> Я знаю, что <code>HashMap</code> не гарантирует порядок обхода</label></li>
	<li><label><input type="checkbox"> Я могу отсортировать ключи через <code>ArrayList</code> и <code>Collections.sort</code></label></li>
	<li><label><input type="checkbox"> Я понимаю, зачем создавать внутренний <code>HashMap</code> перед записью</label></li>
</ul>
</div>
</div>
