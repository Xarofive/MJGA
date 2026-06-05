<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">switch на практике: команды, символы, статусы и ошибки</h1>

<p style="text-align: center; color: #666; margin-bottom: 30px;">Связываем синтаксис с реальными сценариями: где switch делает код проще, а где лучше не пытаться его применять.</p>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">Практические сценарии</h3>
<ul>
	<li>Маршрутизация команд в консольной программе.</li>
	<li>Классификация символов и простая обработка текста.</li>
	<li>Преобразование кодов ошибок и HTTP-статусов в понятные категории.</li>
	<li>Права доступа по роли пользователя.</li>
	<li>Система меню или обработчик ограниченного набора действий.</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>

<p><strong>Заглушка для аудио.</strong> Здесь позже будет ссылка на подкаст по идиомам switch, fallthrough, ошибкам и управлению потоком.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. Команды из пользовательского ввода</h2>

<p>Команды часто приходят как строки: <code>"add"</code>, <code>"list"</code>, <code>"quit"</code>. Перед <code>switch</code> ввод обычно нормализуют: убирают лишние пробелы и приводят к одному регистру.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">String command = line.trim().toLowerCase();

switch (command) {
    case "add" -> System.out.println("Добавление");
    case "list", "ls" -> System.out.println("Список");
    case "quit", "exit", "q" -> System.out.println("Выход");
    default -> System.out.println("UNKNOWN COMMAND");
}</code></pre>

<p><code>trim()</code> удаляет пробелы по краям строки, <code>toLowerCase()</code> делает команду регистронезависимой. Эти методы уже встречались в модуле строк.</p>

<h2 style="color: #34495e; margin-top: 30px;">2. Символы и Unicode</h2>

<p>Для простых задач можно работать с <code>char</code>. Для полноценной Unicode-обработки в Java лучше использовать code point API из модуля 8. В этом модуле задачи формулируются так, чтобы хватало уже знакомых строковых приёмов.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">public static String classifyAscii(char ch) {
    char lower = Character.toLowerCase(ch);

    return switch (lower) {
        case 'a', 'e', 'i', 'o', 'u' -> "vowel";
        case '0', '1', '2', '3', '4', '5', '6', '7', '8', '9' -> "digit";
        case ' ', '\t', '\n' -> "space";
        default -> "other";
    };
}</code></pre>

<p><code>Character.toLowerCase</code> уже знаком по работе с символами. В задачах ниже он нужен, чтобы <code>'A'</code> и <code>'a'</code> считались одной гласной.</p>

<h2 style="color: #34495e; margin-top: 30px;">3. Диапазоны: сначала категория, потом switch</h2>

<p>В Java <code>case score &gt;= 90 -></code> писать нельзя. <code>case</code> сравнивает значение с конкретными вариантами. Для диапазонов есть два нормальных подхода.</p>

<p><strong>Подход 1: использовать if/else if.</strong> Он честнее, если задача именно про диапазоны:</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">if (score &gt;= 90) {
    return "A";
} else if (score &gt;= 80) {
    return "B";
}</code></pre>

<p><strong>Подход 2: вычислить категорию и переключаться по ней.</strong> Это полезно, когда категория простая и читаемая.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">int bucket = score / 10;

return switch (bucket) {
    case 10, 9 -> "A";
    case 8 -> "B";
    case 7 -> "C";
    case 6 -> "D";
    default -> "F";
};</code></pre>

<p>Перед таким <code>switch</code> нужно отдельно проверить, что <code>score</code> лежит в допустимом диапазоне <code>0..100</code>.</p>

<h2 style="color: #34495e; margin-top: 30px;">4. Статусы и коды ошибок</h2>

<p>Статусы часто приходят как числа. Иногда нас интересует конкретный код, иногда группа кодов.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">public static String httpMessage(int code) {
    return switch (code) {
        case 200 -> "OK";
        case 201 -> "CREATED";
        case 400 -> "BAD REQUEST";
        case 401, 403 -> "FORBIDDEN";
        case 404 -> "NOT FOUND";
        case 500 -> "SERVER ERROR";
        default -> "OTHER";
    };
}</code></pre>

<p>Если нужна не конкретная фраза, а группа, используйте <code>code / 100</code>: <code>2xx</code>, <code>3xx</code>, <code>4xx</code>, <code>5xx</code>.</p>

<h2 style="color: #34495e; margin-top: 30px;">5. Ошибки, которые важно не переносить в практику</h2>

<div style="background: #ffebee; border: 1px solid #ef5350; border-radius: 8px; padding: 14px; margin: 16px 0;">
<ul style="margin-bottom: 0;">
	<li><strong>Не нормализовать команды:</strong> <code>"QUIT"</code> и <code>"quit"</code> внезапно становятся разными командами.</li>
	<li><strong>Забыть default:</strong> неизвестное значение не получает понятного результата.</li>
	<li><strong>Пытаться писать диапазоны в case:</strong> для этого нужен <code>if</code> или предварительная категория.</li>
	<li><strong>Смешивать много логики в ветках:</strong> если ветка разрастается, вынесите действие в отдельный метод.</li>
	<li><strong>Использовать старую форму case: без break:</strong> если нет осознанного fall-through, лучше взять <code>case -></code>.</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">6. Мини-REPL как типичный сценарий</h2>

<p>REPL — это цикл «прочитать команду, выполнить, вывести ответ». В задачах модуля будет мини-версия такого обработчика.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">while ((line = reader.readLine()) != null) {
    String command = line.trim().toLowerCase();

    switch (command) {
        case "ping" -> writer.println("pong");
        case "help" -> writer.println("commands: ping, help, quit");
        case "quit", "exit" -> {
            writer.println("bye");
            return;
        }
        default -> writer.println("UNKNOWN COMMAND");
    }
}</code></pre>

<p><code>BufferedReader</code> и <code>PrintWriter</code> уже были в модуле про ввод. Здесь они нужны для обработки потока команд без лишней привязки к консоли.</p>

<h2 style="color: #34495e; margin-top: 30px;">Чек-лист перед задачами</h2>
<ul style="margin-bottom: 0;">
	<li><label><input type="checkbox"> Я понимаю, зачем нормализовать строковые команды</label></li>
	<li><label><input type="checkbox"> Я умею использовать <code>case "a", "b" -></code> для синонимов команд</label></li>
	<li><label><input type="checkbox"> Я знаю, что диапазоны в Java чаще решаются через <code>if</code> или предварительную категорию</label></li>
	<li><label><input type="checkbox"> Я могу применить <code>switch</code> к ролям, статусам, кодам и командам</label></li>
	<li><label><input type="checkbox"> Я понимаю, что большие ветки лучше выносить в отдельные методы</label></li>
</ul>
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
