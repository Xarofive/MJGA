<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">⚡ Исключения в Java: try, catch, throw</h1>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 14px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">🎧 Аудиоподкаст</h4>
<p style="margin: 0;">Заглушка для аудио: сюда позже будет добавлена ссылка на дополнительное объяснение темы про исключения в Java.</p>
</div>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 14px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 Цель лекции</h3>
<p style="margin: 0;">Понять, как Java сообщает об ошибках через исключения, как их перехватывать, когда выбрасывать свои ошибки и чем отличаются проверяемые и непроверяемые исключения.</p>
</div>

<div style="background: linear-gradient(to right, #ffeaa7, #fdcb6e); border-radius: 8px; padding: 16px; margin: 20px 0;">
<h3 style="color: #2d3436; margin-top: 0;">💼 Контекст и мотивация</h3>
<p style="margin-bottom: 10px;">Ввод пользователя, чтение файлов и преобразование строк в числа часто завершаются неудачей. Вместо специальных кодов возврата Java использует исключения: объект ошибки прерывает обычный ход выполнения и передаётся в ближайший подходящий <code>catch</code>.</p>
<p style="margin: 0;">Хороший код не скрывает ошибку, а сообщает о ней понятно: что пошло не так, на каком значении и что должен сделать вызывающий код.</p>
</div>

<h2 style="color: #34495e; margin-top: 28px;">1. Исключение — сигнал о проблеме</h2>

<p>Если <code>Integer.parseInt</code> не может преобразовать строку в число, он выбрасывает <code>NumberFormatException</code>:</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">int value = Integer.parseInt("abc"); // NumberFormatException</code></pre>

<p>Чтобы программа не завершилась аварийно, опасный участок можно обернуть в <code>try/catch</code>.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">try {
    int value = Integer.parseInt("abc");
    System.out.println(value);
} catch (NumberFormatException e) {
    System.out.println("Некорректное число");
}</code></pre>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 14px; margin: 16px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎯 Базовое правило</h4>
<p style="margin-bottom: 0;">Перехватывайте исключение только там, где вы реально можете принять решение: показать сообщение, заменить значение, повторить ввод или вернуть более понятную ошибку выше.</p>
</div>

<h2 style="color: #34495e; margin-top: 28px;">2. throw: выбросить свою ошибку</h2>

<p>Если функция получила некорректный аргумент, она может выбросить <code>IllegalArgumentException</code>.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">static int parsePositive(String text) {
    int value = Integer.parseInt(text.trim());

    if (value <= 0) {
        throw new IllegalArgumentException("value must be positive: " + value);
    }

    return value;
}</code></pre>

<p><code>throw</code> создаёт исключительную ситуацию. После него обычное выполнение метода прекращается.</p>

<h2 style="color: #34495e; margin-top: 28px;">3. Непроверяемые исключения</h2>

<p>Исключения вроде <code>IllegalArgumentException</code>, <code>NumberFormatException</code>, <code>ArithmeticException</code> и <code>NullPointerException</code> относятся к непроверяемым. Компилятор не требует писать <code>throws</code> или <code>try/catch</code>, но ошибка всё равно может произойти во время выполнения.</p>

<table style="width: 100%; border-collapse: collapse; margin: 16px 0;">
<thead><tr style="background: #e3f2fd;"><th style="padding: 10px; border: 1px solid #90caf9;">Исключение</th><th style="padding: 10px; border: 1px solid #90caf9;">Когда возникает</th></tr></thead>
<tbody>
<tr><td style="padding: 10px; border: 1px solid #ddd;"><code>NumberFormatException</code></td><td style="padding: 10px; border: 1px solid #ddd;">Строка не является числом</td></tr>
<tr><td style="padding: 10px; border: 1px solid #ddd;"><code>IllegalArgumentException</code></td><td style="padding: 10px; border: 1px solid #ddd;">Методу передали недопустимый аргумент</td></tr>
<tr><td style="padding: 10px; border: 1px solid #ddd;"><code>ArithmeticException</code></td><td style="padding: 10px; border: 1px solid #ddd;">Например, целочисленное деление на ноль</td></tr>
<tr><td style="padding: 10px; border: 1px solid #ddd;"><code>NullPointerException</code></td><td style="padding: 10px; border: 1px solid #ddd;">Обращение к методу или полю через <code>null</code></td></tr>
</tbody>
</table>

<h2 style="color: #34495e; margin-top: 28px;">4. Проверяемые исключения</h2>

<p><code>IOException</code> — проверяемое исключение. Компилятор требует явно показать, что метод может столкнуться с ошибкой ввода-вывода.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">import java.io.BufferedReader;
import java.io.IOException;

static String readRequiredLine(BufferedReader reader) throws IOException {
    String line = reader.readLine();

    if (line == null) {
        throw new IllegalArgumentException("line is required");
    }

    return line;
}</code></pre>

<p><code>throws IOException</code> в сигнатуре означает: метод сам не обрабатывает ошибку чтения, а передаёт её вызывающему коду.</p>

<h2 style="color: #34495e; margin-top: 28px;">5. try-with-resources</h2>

<p>Если объект нужно закрывать после работы, используйте <code>try-with-resources</code>. Он автоматически вызовет <code>close()</code>.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">try (Scanner scanner = new Scanner(System.in)) {
    String line = scanner.nextLine();
    System.out.println(line);
}</code></pre>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 14px; margin: 16px 0;">
<h4 style="color: #e65100; margin-top: 0;">📝 В учебных задачах</h4>
<p style="margin-bottom: 0;">Если метод получает <code>BufferedReader</code> параметром, не закрывайте его внутри метода. Ресурс закрывает тот код, который его создал.</p>
</div>

<h2 style="color: #34495e; margin-top: 28px;">📚 Шпаргалка</h2>

<ul>
	<li><code>try</code> — участок кода, где может возникнуть исключение</li>
	<li><code>catch</code> — обработчик конкретного типа исключения</li>
	<li><code>throw</code> — выбросить исключение вручную</li>
	<li><code>throws</code> — указать, что метод может передать исключение наружу</li>
	<li><code>IllegalArgumentException</code> — некорректный аргумент метода</li>
	<li><code>IOException</code> — ошибка ввода-вывода, которую компилятор требует учитывать</li>
</ul>

<h2 style="color: #34495e; margin-top: 28px;">🏋️ Практика внутри лекции</h2>

<div style="background: #fffde7; border: 1px solid #fbc02d; border-radius: 8px; padding: 14px; margin: 16px 0;">
<p><strong>Мини-задача:</strong> напишите метод, который принимает строку и возвращает число. Если строка пустая после <code>trim()</code>, выбросьте <code>IllegalArgumentException</code> с текстом <code>"empty input"</code>.</p>
<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">static int parseRequiredInt(String text) {
    String cleaned = text.trim();

    if (cleaned.isEmpty()) {
        throw new IllegalArgumentException("empty input");
    }

    return Integer.parseInt(cleaned);
}</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 28px;">🎲 Квиз: Проверьте понимание</h2>

<div style="background: #f0f4f8; border-radius: 8px; padding: 16px; margin: 16px 0;">
<p><strong>Что произойдёт?</strong></p>
<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">try {
    int x = 10 / 0;
    System.out.println("ok");
} catch (ArithmeticException e) {
    System.out.println("division error");
}</code></pre>
<p style="margin-bottom: 0;">Ответ: будет напечатано <code>division error</code>. Строка <code>System.out.println("ok")</code> не выполнится.</p>
</div>

<h2 style="color: #34495e; margin-top: 28px;">✅ Чек-лист самопроверки</h2>

<ul style="margin-bottom: 0;">
	<li><label><input type="checkbox"> Я понимаю, что исключение прерывает обычный ход метода</label></li>
	<li><label><input type="checkbox"> Я умею оборачивать опасный код в <code>try/catch</code></label></li>
	<li><label><input type="checkbox"> Я знаю, когда использовать <code>throw new IllegalArgumentException(...)</code></label></li>
	<li><label><input type="checkbox"> Я отличаю <code>throw</code> от <code>throws</code></label></li>
	<li><label><input type="checkbox"> Я понимаю, почему <code>IOException</code> нужно указать или обработать</label></li>
	<li><label><input type="checkbox"> Я не скрываю ошибку пустым <code>catch</code></label></li>
</ul>
</div>
</div>
