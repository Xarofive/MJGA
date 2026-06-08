<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">📖 Ввод данных в Java: Scanner и BufferedReader</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 14px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 Цель лекции</h3>
<p style="margin: 0;">Научиться читать данные из стандартного ввода и текстового потока, выбирать подходящий инструмент и аккуратно преобразовывать строки в числа.</p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>

<p>Для лучшего понимания ввода данных и обработки исключений в Java прослушайте аудиоподкаст:</p>
<p style="margin: 15px 0;"><a href="https://drive.google.com/file/d/1m38zHBBA8PV-GXi2jLuvfp-o-0OtqmGb/view?usp=sharing" style="display: inline-block; background: #1565c0; color: white; padding: 10px 20px; text-decoration: none; border-radius: 5px; font-weight: bold;" target="_blank">🎧 Прослушать о вводе данных и исключениях</a></p>
<p style="font-size: 14px; color: #666; margin-top: 10px;"><em>Откроется в новой вкладке. Рекомендуется прослушать перед изучением материала для общего понимания или после — для закрепления.</em></p>
</div>

<div style="background: linear-gradient(to right, #ffeaa7, #fdcb6e); border-radius: 8px; padding: 16px; margin: 20px 0;">
<h3 style="color: #2d3436; margin-top: 0;">💼 Контекст и мотивация</h3>
<p style="margin-bottom: 10px;">Большинство программ получают данные не из заранее записанных переменных, а извне: из консоли, файла, сетевого ответа или тестового источника. В Java для первых задач удобно использовать <code>Scanner</code>, а для построчного чтения и больших текстов часто берут <code>BufferedReader</code>.</p>
<p style="margin: 0;">В этом модуле мы рассматриваем ввод как поток строк: читаем текст, очищаем его, преобразуем в нужный тип и отдельно обрабатываем ошибки.</p>
</div>

<h2 style="color: #34495e; margin-top: 28px;">🌊 Поток данных</h2>

<div style="background: #f0f4f8; border-radius: 8px; padding: 16px; margin: 16px 0;">
<p><code>System.in</code> — стандартный поток ввода. Обычно это клавиатура в консоли, но в тестах вместо неё может быть строка или файл.</p>
<p style="margin-bottom: 0;">Важная идея: программе не важно, откуда пришли байты. Она получает поток, читает из него текст и дальше работает с обычными строками.</p>
</div>

<h2 style="color: #34495e; margin-top: 28px;">1. Scanner: быстрый старт</h2>

<p><code>Scanner</code> удобен для учебных задач и небольших консольных программ. Он умеет читать токены, целые строки и сразу преобразовывать числа.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String name = scanner.nextLine();
        int age = scanner.nextInt();

        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
    }
}</code></pre>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 14px; margin: 16px 0;">
<h4 style="color: #e65100; margin-top: 0;">📝 Важная особенность Scanner</h4>
<p><code>nextInt()</code> читает только число и оставляет перевод строки во входе. Если сразу после него вызвать <code>nextLine()</code>, вы можете получить пустую строку.</p>
<p style="margin-bottom: 0;">Надёжный учебный подход: читать строку через <code>nextLine()</code>, затем преобразовывать её через <code>Integer.parseInt(line.trim())</code>.</p>
</div>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">Scanner scanner = new Scanner(System.in);

String line = scanner.nextLine();
int value = Integer.parseInt(line.trim());</code></pre>

<h2 style="color: #34495e; margin-top: 28px;">2. BufferedReader: построчное чтение</h2>

<p><code>BufferedReader</code> читает текст построчно. Он хорошо подходит, когда нужно обработать несколько строк, пропустить пустые строки или протестировать функцию на строковом источнике.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));

        String firstLine = reader.readLine();
        String secondLine = reader.readLine();

        System.out.println(firstLine);
        System.out.println(secondLine);
    }
}</code></pre>

<div style="background: #e3f2fd; border: 1px dashed #64b5f6; border-radius: 6px; padding: 10px; margin: 10px 0;">
<strong>Коротко про <code>throws IOException</code>:</strong> чтение может завершиться ошибкой ввода-вывода. В этой лекции достаточно знать, что <code>throws IOException</code> в заголовке метода передаёт такую ошибку вызывающему коду. Подробно исключения разберём в следующей лекции.
</div>

<h2 style="color: #34495e; margin-top: 28px;">3. Преобразование строк</h2>

<p>Ввод почти всегда приходит как строка. Для целых чисел используйте <code>Integer.parseInt</code>:</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">String raw = " 42 ";
String cleaned = raw.trim();
int number = Integer.parseInt(cleaned);</code></pre>

<p>Если строка не является корректным целым числом, <code>Integer.parseInt</code> выбросит <code>NumberFormatException</code>. Это обычная ситуация для пользовательского ввода, поэтому в реальных программах её нужно обрабатывать.</p>

<h2 style="color: #34495e; margin-top: 28px;">4. Тестируемый ввод</h2>

<p>Функции удобнее тестировать, если они принимают <code>BufferedReader</code>, а не создают его внутри. В тесте можно передать <code>StringReader</code> вместо консоли.</p>
<p><code>StringReader</code> — это источник символов из обычной строки в памяти. Он ведёт себя как маленький текстовый поток: <code>\n</code> внутри строки становится переводом строки, а <code>BufferedReader</code> читает такой текст через привычный <code>readLine()</code>.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">import java.io.BufferedReader;
import java.io.StringReader;

BufferedReader reader = new BufferedReader(new StringReader("10\n20\n"));

String first = reader.readLine();  // "10"
String second = reader.readLine(); // "20"</code></pre>

<div style="background: #ffebee; border: 1px solid #ef5350; border-radius: 8px; padding: 14px; margin: 20px 0;">
<h4 style="color: #c62828; margin-top: 0;">⚠️ Частые ошибки</h4>
<p><strong>Ошибка 1:</strong> смешивать <code>nextInt()</code> и <code>nextLine()</code> без понимания оставшегося перевода строки.</p>
<p><strong>Ошибка 2:</strong> парсить число без <code>trim()</code>, хотя во вводе могут быть пробелы.</p>
<p><strong>Ошибка 3:</strong> считать, что ввод всегда корректный. Любое преобразование строки в число может завершиться ошибкой.</p>
<p style="margin-bottom: 0;"><strong>Ошибка 4:</strong> печатать результат внутри функции, которую нужно только вычислить и вернуть.</p>
</div>

<h2 style="color: #34495e; margin-top: 28px;">📚 Шпаргалка</h2>

<table style="width: 100%; border-collapse: collapse; margin: 16px 0;">
<thead><tr style="background: #e3f2fd;"><th style="padding: 10px; border: 1px solid #90caf9;">Задача</th><th style="padding: 10px; border: 1px solid #90caf9;">Инструмент</th></tr></thead>
<tbody>
<tr><td style="padding: 10px; border: 1px solid #ddd;">Быстро прочитать токен или число</td><td style="padding: 10px; border: 1px solid #ddd;"><code>Scanner</code></td></tr>
<tr><td style="padding: 10px; border: 1px solid #ddd;">Читать текст построчно</td><td style="padding: 10px; border: 1px solid #ddd;"><code>BufferedReader.readLine()</code></td></tr>
<tr><td style="padding: 10px; border: 1px solid #ddd;">Прочитать из консоли через BufferedReader</td><td style="padding: 10px; border: 1px solid #ddd;"><code>new InputStreamReader(System.in)</code></td></tr>
<tr><td style="padding: 10px; border: 1px solid #ddd;">Протестировать чтение на строке</td><td style="padding: 10px; border: 1px solid #ddd;"><code>new StringReader("...")</code></td></tr>
<tr><td style="padding: 10px; border: 1px solid #ddd;">Преобразовать строку в int</td><td style="padding: 10px; border: 1px solid #ddd;"><code>Integer.parseInt(text.trim())</code></td></tr>
</tbody>
</table>

<h2 style="color: #34495e; margin-top: 28px;">🏋️ Практика внутри лекции</h2>

<div style="background: #fffde7; border: 1px solid #fbc02d; border-radius: 8px; padding: 14px; margin: 16px 0;">
<p><strong>Мини-задача:</strong> дан <code>BufferedReader</code>, который содержит две строки с числами. Прочитайте строки, преобразуйте их в <code>int</code> и выведите сумму.</p>
<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">BufferedReader reader = new BufferedReader(new StringReader("7\n5\n"));

int a = Integer.parseInt(reader.readLine().trim());
int b = Integer.parseInt(reader.readLine().trim());

System.out.println(a + b); // 12</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 28px;">✅ Чек-лист самопроверки</h2>

<ul style="margin-bottom: 0;">
	<li><label><input type="checkbox"> Я понимаю, что <code>System.in</code> — стандартный поток ввода</label></li>
	<li><label><input type="checkbox"> Я умею читать строку через <code>Scanner.nextLine()</code></label></li>
	<li><label><input type="checkbox"> Я знаю, почему <code>nextInt()</code> и <code>nextLine()</code> нужно смешивать осторожно</label></li>
	<li><label><input type="checkbox"> Я умею читать строки через <code>BufferedReader.readLine()</code></label></li>
	<li><label><input type="checkbox"> Я преобразую строку в число через <code>Integer.parseInt(text.trim())</code></label></li>
	<li><label><input type="checkbox"> Я понимаю, что некорректный ввод приводит к исключению</label></li>
</ul>
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
