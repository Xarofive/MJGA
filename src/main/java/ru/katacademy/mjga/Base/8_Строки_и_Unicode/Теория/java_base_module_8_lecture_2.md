<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50;">Итерация по строкам в Java: char и code point</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть за 30 секунд</h3>
<ul>
	<li>Цикл по <code>charAt(i)</code> идёт по UTF-16 code units</li>
	<li>Цикл по <code>codePoints()</code> идёт по Unicode code points</li>
	<li>Эмодзи может занимать два <code>char</code>, но один code point</li>
	<li>Для позиции в code points используйте отдельный счётчик</li>
	<li>Для поиска и обрезки Unicode-текста чаще безопаснее работать с code points</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>
<p><strong>Заглушка для аудио.</strong> Здесь позже будет ссылка на подкаст по итерации строк в Java.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. Итерация через charAt</h2>
<p><code>charAt</code> полезен для ASCII и простого текста, но он не всегда равен одному Unicode-символу.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    public static void main(String[] args) {
        String text = "Hi🚀!";

        for (int i = 0; i &lt; text.length(); i++) {
            System.out.println("char index=" + i + ", value=" + text.charAt(i));
        }
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">2. Итерация через codePoints</h2>
<p><code>codePoints()</code> возвращает поток целых чисел, где каждое число &mdash; Unicode code point. Чтобы вывести его как строку, используйте <code>Character.toChars</code>.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    public static void main(String[] args) {
        String text = "Hi🚀!";
        int symbolIndex = 0;

        for (int codePoint : text.codePoints().toArray()) {
            String symbol = new String(Character.toChars(codePoint));
            System.out.println("symbol index=" + symbolIndex + ", value=" + symbol);
            symbolIndex++;
        }
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">3. Поиск позиции символа</h2>
<p>Если нужна позиция именно в Unicode code points, считайте её отдельно. Индекс в <code>String</code> и номер символа могут отличаться.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    static int findCodePointPosition(String s, int target) {
        int position = 0;
        for (int i = 0; i &lt; s.length(); ) {
            int current = s.codePointAt(i);
            if (current == target) {
                return position;
            }
            i += Character.charCount(current);
            position++;
        }
        return -1;
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">4. Последние N символов</h2>
<p>Для обрезки с конца по code points удобно сначала посчитать общее количество code points, затем перевести позицию в индекс UTF-16.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    static String lastCodePoints(String s, int n) {
        if (n &lt;= 0) {
            return "";
        }

        int total = s.codePointCount(0, s.length());
        if (n &gt;= total) {
            return s;
        }

        int begin = s.offsetByCodePoints(0, total - n);
        return s.substring(begin);
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">Важные предостережения</h2>
<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p><strong>Ошибка 1:</strong> считать индекс <code>charAt</code> номером Unicode-символа.</p>
<p><strong>Ошибка 2:</strong> увеличивать индекс всегда на 1 при ручном проходе по code points. Нужно прибавлять <code>Character.charCount(codePoint)</code>.</p>
<p style="margin-bottom: 0;"><strong>Ошибка 3:</strong> забывать, что <code>substring</code> принимает UTF-16 индексы.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">✅ Чек-лист самопроверки</h2>
<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<ul style="list-style: none; padding-left: 0;">
	<li><label><input type="checkbox"> Я понимаю разницу между <code>char</code> и code point</label></li>
	<li><label><input type="checkbox"> Я умею пройти строку через <code>codePoints()</code></label></li>
	<li><label><input type="checkbox"> Я использую <code>Character.charCount</code> при ручном проходе</label></li>
	<li><label><input type="checkbox"> Я умею получить последние N code points строки</label></li>
</ul>
</div>
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
