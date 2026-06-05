<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50;">Практические приёмы работы со строками в Java</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть за 30 секунд</h3>
<ul>
	<li><code>trim()</code> убирает пробелы по краям, <code>split("\\s+")</code> разбивает по группам whitespace</li>
	<li><code>equalsIgnoreCase</code> сравнивает строки без учёта регистра</li>
	<li><code>toLowerCase()</code> + <code>contains()</code> дают простой поиск без учёта регистра</li>
	<li><code>StringBuilder</code> нужен для эффективной сборки строки в цикле</li>
	<li><code>Integer.toString</code> и <code>Integer.parseInt</code> преобразуют числа и строки</li>
	<li><code>Character.isLetter</code>, <code>isDigit</code>, <code>isWhitespace</code> классифицируют символы</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. Нормализация пробелов</h2>
<p>Чтобы заменить любые группы пробельных символов одним пробелом, можно обрезать края, разбить строку регулярным выражением и собрать обратно.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    static String normalizeSpaces(String s) {
        String trimmed = s.trim();
        if (trimmed.isEmpty()) {
            return "";
        }
        String[] words = trimmed.split("\\s+");
        return String.join(" ", words);
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">2. Сравнение и поиск без учёта регистра</h2>
<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    static boolean containsIgnoreCase(String text, String part) {
        return text.toLowerCase().contains(part.toLowerCase());
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">3. Эффективная конкатенация: StringBuilder</h2>
<p>Строки неизменяемы, поэтому конкатенация через <code>+=</code> в большом цикле создаёт много промежуточных объектов. Для сборки результата используйте <code>StringBuilder</code>.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    static String joinNumbers(int[] nums) {
        StringBuilder builder = new StringBuilder();
        for (int i = 0; i &lt; nums.length; i++) {
            if (i &gt; 0) {
                builder.append(",");
            }
            builder.append(nums[i]);
        }
        return builder.toString();
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">4. Преобразование чисел</h2>
<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    public static void main(String[] args) {
        String text = Integer.toString(42);
        int value = Integer.parseInt("42");

        System.out.println(text);
        System.out.println(value);
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">5. Классификация символов</h2>
<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    public static void main(String[] args) {
        String text = "A1 Привет!";

        for (int cp : text.codePoints().toArray()) {
            System.out.println(Character.isLetter(cp) + " " + Character.isDigit(cp) + " " + Character.isWhitespace(cp));
        }
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">Важные предостережения</h2>
<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p><strong>Ошибка 1:</strong> использовать <code>+=</code> в большом цикле вместо <code>StringBuilder</code>.</p>
<p><strong>Ошибка 2:</strong> забывать обработать пустую строку при нормализации пробелов.</p>
<p style="margin-bottom: 0;"><strong>Ошибка 3:</strong> использовать <code>contains</code> без нормализации регистра, если поиск должен быть регистронезависимым.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">✅ Чек-лист самопроверки</h2>
<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<ul style="list-style: none; padding-left: 0;">
	<li><label><input type="checkbox"> Я умею нормализовать пробелы через <code>trim</code>, <code>split</code>, <code>String.join</code></label></li>
	<li><label><input type="checkbox"> Я использую <code>StringBuilder</code> для сборки строки в цикле</label></li>
	<li><label><input type="checkbox"> Я умею искать подстроку без учёта регистра</label></li>
	<li><label><input type="checkbox"> Я знаю базовые методы класса <code>Character</code></label></li>
</ul>
</div>
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
