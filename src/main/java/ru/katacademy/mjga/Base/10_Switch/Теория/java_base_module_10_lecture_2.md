<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">⚙️ switch на практике: строки, символы и команды</h1>

<div style="background: linear-gradient(to right, #e3f2fd, #bbdefb); border-radius: 8px; padding: 16px; margin: 20px 0;">
<h3 style="color: #1565c0; margin-top: 0;">📝 TL;DR</h3>
<p><code>switch</code> хорошо подходит для маршрутизации команд, классификации символов, выбора сообщения по коду и обработки ограниченного набора ролей или статусов.</p>
<p style="margin-bottom: 0;">В Java <code>switch</code> можно применять к <code>int</code>, <code>char</code>, <code>String</code> и некоторым другим типам. Для диапазонов остаётся <code>if/else if</code>.</p>
</div>

<h2 style="color: #34495e; margin-top: 28px;">1. switch по строке</h2>

<p>Перед сравнением команд обычно нормализуют строку: убирают пробелы и приводят к одному регистру.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">static String handleCommand(String input) {
    if (input == null) {
        return "ERR";
    }

    String command = input.trim().toLowerCase();

    switch (command) {
        case "start":
            return "RUN";
        case "stop":
            return "STOP";
        case "quit":
            return "QUIT";
        default:
            return "UNKNOWN";
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 28px;">2. switch по символу</h2>

<p><code>char</code> удобен для классификации ASCII-символов: гласных, операторов, коротких команд.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">static boolean isEnglishVowel(char ch) {
    switch (Character.toLowerCase(ch)) {
        case 'a':
        case 'e':
        case 'i':
        case 'o':
        case 'u':
            return true;
        default:
            return false;
    }
}</code></pre>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 14px; margin: 16px 0;">
<h4 style="color: #e65100; margin-top: 0;">📝 Unicode и char</h4>
<p style="margin-bottom: 0;">Для простых учебных задач с буквами подходит <code>char</code>. Для полноценной обработки всех Unicode-символов в Java используют code point API из модуля 8. В этом модуле задачи остаются в рамках уже знакомых строковых приёмов.</p>
</div>

<h2 style="color: #34495e; margin-top: 28px;">3. Команды из потока</h2>

<p>После модуля 9 можно читать строки через <code>BufferedReader</code>, разбирать команду и передавать её в <code>switch</code>.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">String line = reader.readLine();
String command = line.trim().toLowerCase();

switch (command) {
    case "help":
        System.out.println("HELP");
        break;
    case "quit":
        return;
    default:
        System.out.println("ERR unknown command");
        break;
}</code></pre>

<h2 style="color: #34495e; margin-top: 28px;">4. Типичные ошибки</h2>

<div style="background: #ffebee; border: 1px solid #ef5350; border-radius: 8px; padding: 14px; margin: 20px 0;">
<p><strong>Ошибка 1:</strong> забыть <code>break</code> в ветке, которая не делает <code>return</code>.</p>
<p><strong>Ошибка 2:</strong> сравнивать команды без <code>trim()</code> и <code>toLowerCase()</code>.</p>
<p><strong>Ошибка 3:</strong> использовать <code>switch</code> там, где нужны диапазоны и сложные условия.</p>
<p style="margin-bottom: 0;"><strong>Ошибка 4:</strong> не добавлять <code>default</code> для неизвестных значений.</p>
</div>

<h2 style="color: #34495e; margin-top: 28px;">🏋️ Мини-практика</h2>

<div style="background: #fffde7; border: 1px solid #fbc02d; border-radius: 8px; padding: 14px; margin: 16px 0;">
<p><strong>Задача:</strong> напишите метод <code>operatorName(char op)</code>, который возвращает <code>"plus"</code>, <code>"minus"</code>, <code>"multiply"</code>, <code>"divide"</code> или <code>"unknown"</code>.</p>
<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">static String operatorName(char op) {
    switch (op) {
        case '+':
            return "plus";
        case '-':
            return "minus";
        case '*':
            return "multiply";
        case '/':
            return "divide";
        default:
            return "unknown";
    }
}</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 28px;">✅ Чек-лист самопроверки</h2>
<ul style="margin-bottom: 0;">
	<li><label><input type="checkbox"> Я нормализую строковые команды перед <code>switch</code></label></li>
	<li><label><input type="checkbox"> Я умею использовать <code>switch</code> по <code>char</code></label></li>
	<li><label><input type="checkbox"> Я понимаю, когда нужен <code>break</code>, а когда достаточно <code>return</code></label></li>
	<li><label><input type="checkbox"> Я использую <code>default</code> для неизвестных команд и кодов</label></li>
</ul>
</div>
</div>
