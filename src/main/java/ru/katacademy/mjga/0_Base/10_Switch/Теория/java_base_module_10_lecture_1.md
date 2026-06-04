<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">switch в Java: базовая модель и классический синтаксис</h1>

<p style="text-align: center; color: #666; margin-bottom: 30px;">Разбираем, когда ветвление по набору конкретных значений читается лучше, чем длинная цепочка <code>if/else if</code>.</p>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">TL;DR</h3>
<ul>
	<li><code>switch</code> выбирает ветку по значению одного выражения.</li>
	<li>Он хорошо подходит для команд, кодов, ролей, статусов, месяцев, пунктов меню.</li>
	<li>Классическая форма использует <code>case:</code>, <code>break</code> и <code>default</code>.</li>
	<li>Если забыть <code>break</code>, выполнение провалится в следующую ветку. Это называется fall-through.</li>
	<li>Для диапазонов и сложных условий обычно лучше подходит <code>if/else if</code>.</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. Зачем нужен switch</h2>

<p>Представьте, что программа получила код команды: <code>"start"</code>, <code>"stop"</code>, <code>"help"</code> или <code>"quit"</code>. Нужно выбрать действие по одному конкретному значению. Можно написать цепочку <code>if</code>, но при большом количестве вариантов код быстро становится шумным.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">if (command.equals("start")) {
    System.out.println("Запуск");
} else if (command.equals("stop")) {
    System.out.println("Остановка");
} else if (command.equals("help")) {
    System.out.println("Справка");
} else {
    System.out.println("Неизвестная команда");
}</code></pre>

<p>Тот же выбор через <code>switch</code> показывает намерение яснее: мы маршрутизируем одно значение по набору допустимых вариантов.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">switch (command) {
    case "start":
        System.out.println("Запуск");
        break;
    case "stop":
        System.out.println("Остановка");
        break;
    case "help":
        System.out.println("Справка");
        break;
    default:
        System.out.println("Неизвестная команда");
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">2. Из чего состоит классический switch</h2>

<ul>
	<li><code>switch (value)</code> — значение, по которому выбирается ветка.</li>
	<li><code>case ...:</code> — один из вариантов значения.</li>
	<li><code>break</code> — остановить выполнение текущего <code>switch</code>.</li>
	<li><code>default</code> — ветка для всех значений, которые не подошли ни под один <code>case</code>.</li>
</ul>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">public static String monthName(int month) {
    switch (month) {
        case 1:
            return "январь";
        case 2:
            return "февраль";
        case 3:
            return "март";
        default:
            return "unknown";
    }
}</code></pre>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 14px; margin: 16px 0;">
<h4 style="color: #1565c0; margin-top: 0;">Почему здесь нет break</h4>
<p style="margin-bottom: 0;">Если ветка сразу делает <code>return</code>, метод завершается. До следующего <code>case</code> выполнение уже не дойдёт, поэтому <code>break</code> не нужен.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">3. Fall-through: что происходит без break</h2>

<p>В классической форме <code>case:</code> Java не останавливается автоматически после найденной ветки. Если нет <code>break</code>, <code>return</code> или другого выхода, выполнение перейдёт ниже.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">switch (command) {
    case "start":
        System.out.println("Запуск");
    case "stop":
        System.out.println("Остановка");
    default:
        System.out.println("Готово");
}</code></pre>

<p>Если <code>command</code> равен <code>"start"</code>, программа выведет сразу три строки. Для новичков это почти всегда ошибка.</p>

<div style="background: #ffebee; border: 1px solid #ef5350; border-radius: 8px; padding: 14px; margin: 16px 0;">
<h4 style="color: #c62828; margin-top: 0;">Частая ошибка</h4>
<p style="margin-bottom: 0;">Забыть <code>break</code> в классическом <code>switch</code>. Если ветка не делает <code>return</code>, обычно после неё нужен <code>break</code>.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">4. Несколько case для одного результата</h2>

<p>Иногда несколько значений должны вести к одному действию. В классическом синтаксисе можно поставить несколько <code>case</code> подряд.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">public static String season(int month) {
    switch (month) {
        case 12:
        case 1:
        case 2:
            return "winter";
        case 3:
        case 4:
        case 5:
            return "spring";
        case 6:
        case 7:
        case 8:
            return "summer";
        case 9:
        case 10:
        case 11:
            return "autumn";
        default:
            return "unknown";
    }
}</code></pre>

<p>Здесь fall-through используется осознанно: пустые ветки <code>case 12</code> и <code>case 1</code> проваливаются к общему коду для зимы. В современной форме Java это можно записать компактнее — это будет в следующей лекции.</p>

<h2 style="color: #34495e; margin-top: 30px;">5. С какими типами работает switch</h2>

<p>В этом курсе достаточно знать такие типы:</p>

<ul>
	<li><code>int</code> — числовые коды, номера месяцев, пункты меню;</li>
	<li><code>char</code> — один символ;</li>
	<li><code>String</code> — команды, роли, текстовые статусы.</li>
</ul>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">switch (role) {
    case "admin":
        return "all";
    case "editor":
        return "write";
    case "viewer":
        return "read";
    default:
        return "none";
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">6. switch или if</h2>

<table style="width: 100%; border-collapse: collapse; margin: 16px 0;">
	<thead>
		<tr style="background: #e3f2fd;">
			<th style="border: 1px solid #90caf9; padding: 10px; text-align: left;">Ситуация</th>
			<th style="border: 1px solid #90caf9; padding: 10px; text-align: left;">Что выбрать</th>
		</tr>
	</thead>
	<tbody>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Одна переменная сравнивается с конкретными значениями</td><td style="border: 1px solid #ddd; padding: 10px;"><code>switch</code></td></tr>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Нужны диапазоны: <code>score &gt;= 90</code></td><td style="border: 1px solid #ddd; padding: 10px;"><code>if/else if</code> или предварительная категория</td></tr>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Нужно проверить несколько разных переменных</td><td style="border: 1px solid #ddd; padding: 10px;"><code>if/else if</code></td></tr>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">Есть неизвестные значения из пользовательского ввода</td><td style="border: 1px solid #ddd; padding: 10px;"><code>default</code> обязателен</td></tr>
	</tbody>
</table>

<h2 style="color: #34495e; margin-top: 30px;">Чек-лист самопроверки</h2>
<ul style="margin-bottom: 0;">
	<li><label><input type="checkbox"> Я понимаю, что <code>switch</code> выбирает ветку по одному значению</label></li>
	<li><label><input type="checkbox"> Я знаю роли <code>case</code>, <code>break</code> и <code>default</code></label></li>
	<li><label><input type="checkbox"> Я понимаю, что такое fall-through</label></li>
	<li><label><input type="checkbox"> Я умею группировать несколько <code>case</code> для одного результата</label></li>
	<li><label><input type="checkbox"> Я не использую <code>switch</code> вместо <code>if</code> для сложных условий</label></li>
</ul>
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
