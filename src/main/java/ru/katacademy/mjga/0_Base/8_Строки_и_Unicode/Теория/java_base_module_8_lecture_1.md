<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50;">Строки и текст в Java: UTF-16, байты и Unicode</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть за 30 секунд</h3>
<ul>
	<li><code>String</code> в Java неизменяемая: любое изменение создаёт новую строку</li>
	<li><code>length()</code> возвращает количество UTF-16 code units, а не всегда количество видимых символов</li>
	<li>Для размера в байтах используйте <code>s.getBytes(StandardCharsets.UTF_8).length</code></li>
	<li>Для Unicode code points используйте <code>codePointCount</code>, <code>codePoints()</code>, <code>offsetByCodePoints</code></li>
	<li>Не режьте строки с эмодзи обычными индексами, если вам нужны именно символы</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>
<p><strong>Заглушка для аудио.</strong> Здесь позже будет ссылка на подкаст по строкам, UTF-8/UTF-16 и Unicode в Java.</p>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">📚 Предпосылки</h4>
<p>Нужно понимать переменные, методы, циклы, массивы и базовые типы. В этой теме важно аккуратно различать байты, индексы строки и Unicode code points.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. String: неизменяемость и базовые операции</h2>
<p>Строка в Java &mdash; объект типа <code>String</code>. После создания содержимое строки нельзя изменить. Методы вроде <code>toUpperCase()</code>, <code>trim()</code> и конкатенация возвращают новую строку.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    public static void main(String[] args) {
        String text = "Java";
        String changed = text + "!";

        System.out.println(text);
        System.out.println(changed);
        System.out.println(text == changed);
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">2. Байты vs символы</h2>
<p>Java хранит строки как последовательность UTF-16 code units. Метод <code>length()</code> показывает именно их количество. Размер строки в UTF-8 байтах нужно считать явно.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.nio.charset.StandardCharsets;

public class Main {
    public static void main(String[] args) {
        String ascii = "Hello";
        String cyrillic = "Привет";
        String emoji = "Java🚀";

        System.out.println(ascii.length());
        System.out.println(ascii.getBytes(StandardCharsets.UTF_8).length);

        System.out.println(cyrillic.length());
        System.out.println(cyrillic.getBytes(StandardCharsets.UTF_8).length);

        System.out.println(emoji.length());
        System.out.println(emoji.codePointCount(0, emoji.length()));
        System.out.println(emoji.getBytes(StandardCharsets.UTF_8).length);
    }
}</code></pre>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🔎 Почему у эмодзи длина 4?</h4>
<p style="margin-bottom: 0;">Строка <code>"Java🚀"</code> содержит 5 Unicode code points: <code>J</code>, <code>a</code>, <code>v</code>, <code>a</code>, <code>🚀</code>. Но <code>🚀</code> занимает две UTF-16 ячейки, поэтому <code>length()</code> вернёт <code>6</code>. Для количества Unicode code points используйте <code>codePointCount</code>.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">3. Code point: безопасная единица Unicode</h2>
<p>Если нужно пройти по строке с учётом эмодзи и символов вне базовой плоскости Unicode, используйте <code>codePoints()</code> или методы <code>codePointAt</code> и <code>offsetByCodePoints</code>.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    public static void main(String[] args) {
        String text = "Hi🚀";

        int[] points = text.codePoints().toArray();
        for (int point : points) {
            System.out.println(new String(Character.toChars(point)) + " U+" + Integer.toHexString(point).toUpperCase());
        }
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">4. Безопасная подстрока по code points</h2>
<p>Обычный <code>substring</code> принимает индексы UTF-16. Если параметры заданы в символах/code points, сначала переведите их в индексы UTF-16 через <code>offsetByCodePoints</code>.</p>
<p><code>Math.min(start + length, total)</code> выбирает меньшее из двух чисел. Здесь это защита от выхода за конец строки: если запрошенная длина слишком большая, метод остановится на последнем доступном символе.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    static String substringByCodePoints(String s, int start, int length) {
        int total = s.codePointCount(0, s.length());
        int endPoint = Math.min(start + length, total);

        int beginIndex = s.offsetByCodePoints(0, start);
        int endIndex = s.offsetByCodePoints(0, endPoint);
        return s.substring(beginIndex, endIndex);
    }

    public static void main(String[] args) {
        System.out.println(substringByCodePoints("Hello😊世界", 5, 3));
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">Типичные ошибки</h2>
<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p><strong>Ошибка 1:</strong> считать <code>length()</code> количеством всех видимых символов. Для эмодзи это может быть неверно.</p>
<p><strong>Ошибка 2:</strong> брать <code>substring</code> по произвольным индексам внутри surrogate pair.</p>
<p style="margin-bottom: 0;"><strong>Ошибка 3:</strong> считать размер строки в байтах через <code>length()</code>. Для байтов нужен <code>getBytes(StandardCharsets.UTF_8)</code>.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">✅ Чек-лист самопроверки</h2>
<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<ul style="list-style: none; padding-left: 0;">
	<li><label><input type="checkbox"> Я понимаю, что <code>String</code> неизменяемый</label></li>
	<li><label><input type="checkbox"> Я отличаю <code>length()</code> от размера в UTF-8 байтах</label></li>
	<li><label><input type="checkbox"> Я умею получить количество code points</label></li>
	<li><label><input type="checkbox"> Я не режу Unicode-текст произвольными индексами</label></li>
</ul>
</div>
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
