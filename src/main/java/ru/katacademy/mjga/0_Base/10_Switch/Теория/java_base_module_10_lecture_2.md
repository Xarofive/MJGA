<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">Современный switch: case ->, switch expression и yield</h1>

<p style="text-align: center; color: #666; margin-bottom: 30px;">В Java 21 можно писать switch компактнее и безопаснее: без случайного fall-through и лишних временных переменных.</p>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">TL;DR</h3>
<ul>
	<li><code>case value -></code> выполняет только свою ветку и не требует <code>break</code>.</li>
	<li>Несколько значений можно перечислить через запятую: <code>case 1, 2, 3 -></code>.</li>
	<li><code>switch</code> может быть выражением и сразу возвращать значение.</li>
	<li>Если ветка switch expression многострочная, значение возвращается через <code>yield</code>.</li>
	<li>В switch expression должен быть результат для всех возможных значений, обычно через <code>default</code>.</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. Стрелочная форма case -></h2>

<p>Классический <code>case:</code> требует помнить про <code>break</code>. Стрелочная форма делает одну ветку изолированной: выполнилась ветка — <code>switch</code> закончился.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">switch (command) {
    case "start" -> System.out.println("Запуск");
    case "stop" -> System.out.println("Остановка");
    case "help" -> System.out.println("Справка");
    default -> System.out.println("Неизвестная команда");
}</code></pre>

<p>Для учебных задач в Java 21 это часто лучшая форма: меньше служебного кода и меньше риска забыть <code>break</code>.</p>

<h2 style="color: #34495e; margin-top: 30px;">2. Несколько значений в одном case</h2>

<p>В современной форме не нужно писать несколько пустых <code>case</code> подряд. Значения можно перечислить через запятую.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">public static String season(int month) {
    return switch (month) {
        case 12, 1, 2 -> "winter";
        case 3, 4, 5 -> "spring";
        case 6, 7, 8 -> "summer";
        case 9, 10, 11 -> "autumn";
        default -> "unknown";
    };
}</code></pre>

<p>Такая запись явно говорит: эти значения равноправны и дают один результат.</p>

<h2 style="color: #34495e; margin-top: 30px;">3. switch как statement и как expression</h2>

<p><strong>Statement</strong> — это инструкция, которая что-то делает. Например, печатает текст:</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">switch (status) {
    case 200 -> System.out.println("OK");
    case 404 -> System.out.println("Not Found");
    default -> System.out.println("Other");
}</code></pre>

<p><strong>Expression</strong> — это выражение, которое даёт значение. Его можно присвоить переменной или сразу вернуть из метода:</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">String message = switch (status) {
    case 200 -> "OK";
    case 404 -> "Not Found";
    case 500 -> "Server Error";
    default -> "Other";
};</code></pre>

<p>Обратите внимание на точку с запятой после закрывающей фигурной скобки. Она нужна, потому что весь <code>switch</code> является частью присваивания.</p>

<h2 style="color: #34495e; margin-top: 30px;">4. Что такое yield</h2>

<p><code>yield</code> — это специальное слово для <code>switch expression</code>. Оно означает: &laquo;отдать значение из этой ветки наружу, чтобы весь <code>switch</code> стал этим значением&raquo;.</p>

<p>В короткой стрелочной ветке значение стоит сразу после <code>-></code>, поэтому <code>yield</code> не нужен:</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">String label = switch (status) {
    case 1 -> "new";
    case 2 -> "done";
    default -> "unknown";
};</code></pre>

<p>Но если ветка стала блоком <code>{ ... }</code>, Java уже не видит одно готовое значение после стрелки. Внутри блока можно объявить переменные, сделать проверки, подготовить результат. В конце нужно явно сказать, какое значение отдаёт эта ветка. Для этого и нужен <code>yield</code>.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">String result = switch (operation) {
    case "trim" -> text.trim();
    case "upper" -> text.toUpperCase();
    case "wrap" -> {
        String trimmed = text.trim();
        yield "[" + trimmed + "]";
    }
    default -> text;
};</code></pre>

<p>В примере ветка <code>"wrap"</code> сначала очищает строку, потом возвращает наружу строку в квадратных скобках. Наружу — это не из метода, а именно из текущей ветки <code>switch</code>.</p>

<h3 style="color: #34495e; margin-top: 24px;">yield, return и break: в чём разница</h3>

<table style="width: 100%; border-collapse: collapse; margin: 16px 0;">
	<thead>
		<tr style="background: #e3f2fd;">
			<th style="border: 1px solid #90caf9; padding: 10px; text-align: left;">Ключевое слово</th>
			<th style="border: 1px solid #90caf9; padding: 10px; text-align: left;">Что завершает</th>
			<th style="border: 1px solid #90caf9; padding: 10px; text-align: left;">Когда использовать</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="border: 1px solid #ddd; padding: 10px;"><code>yield</code></td>
			<td style="border: 1px solid #ddd; padding: 10px;">Только ветку <code>switch expression</code></td>
			<td style="border: 1px solid #ddd; padding: 10px;">Когда многострочная ветка должна отдать значение всему <code>switch</code></td>
		</tr>
		<tr>
			<td style="border: 1px solid #ddd; padding: 10px;"><code>return</code></td>
			<td style="border: 1px solid #ddd; padding: 10px;">Весь метод</td>
			<td style="border: 1px solid #ddd; padding: 10px;">Когда метод должен немедленно вернуть результат</td>
		</tr>
		<tr>
			<td style="border: 1px solid #ddd; padding: 10px;"><code>break</code></td>
			<td style="border: 1px solid #ddd; padding: 10px;">Классический <code>switch</code> или цикл</td>
			<td style="border: 1px solid #ddd; padding: 10px;">Когда нужно выйти из конструкции без возврата значения</td>
		</tr>
	</tbody>
</table>

<p><code>yield</code> не заменяет <code>return</code>. Если вы пишете <code>return</code> внутри ветки, вы завершаете весь метод. Если пишете <code>yield</code>, вы завершаете только ветку и отдаёте значение в выражение <code>switch</code>.</p>

<h3 style="color: #34495e; margin-top: 24px;">Почему нельзя просто написать значение в блоке</h3>

<p>Такой код не скомпилируется: блок ветки не знает, какое значение нужно вернуть наружу.</p>

<pre style="background: #ffebee; border: 1px solid #ef5350; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">String result = switch (operation) {
    case "wrap" -> {
        String trimmed = text.trim();
        "[" + trimmed + "]"; // ошибка: значение не отдано наружу
    }
    default -> text;
};</code></pre>

<p>Правильно — явно использовать <code>yield</code>:</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">String result = switch (operation) {
    case "wrap" -> {
        String trimmed = text.trim();
        yield "[" + trimmed + "]";
    }
    default -> text;
};</code></pre>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 14px; margin: 16px 0;">
<h4 style="color: #e65100; margin-top: 0;">Короткое правило</h4>
<p style="margin-bottom: 0;">Если <code>switch</code> стоит справа от <code>=</code> или после <code>return</code>, он должен дать значение. Короткая ветка даёт значение сразу после <code>-></code>. Многострочная ветка даёт значение через <code>yield</code>.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">5. default в switch expression</h2>

<p>Когда <code>switch</code> должен вернуть значение, Java должна понимать, что значение будет получено при любом входе. Если вход приходит от пользователя или из внешней системы, добавляйте <code>default</code>.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">public static String accessLevel(String role) {
    return switch (role.toLowerCase()) {
        case "admin" -> "all";
        case "editor" -> "write";
        case "viewer" -> "read";
        default -> "none";
    };
}</code></pre>

<p>Без <code>default</code> неизвестная роль осталась бы без результата. Для данных из пользовательского ввода это почти всегда ошибка проектирования.</p>

<h2 style="color: #34495e; margin-top: 30px;">6. Что выбрать: case: или case -></h2>

<table style="width: 100%; border-collapse: collapse; margin: 16px 0;">
	<thead>
		<tr style="background: #e3f2fd;">
			<th style="border: 1px solid #90caf9; padding: 10px; text-align: left;">Форма</th>
			<th style="border: 1px solid #90caf9; padding: 10px; text-align: left;">Когда использовать</th>
		</tr>
	</thead>
	<tbody>
		<tr><td style="border: 1px solid #ddd; padding: 10px;"><code>case:</code></td><td style="border: 1px solid #ddd; padding: 10px;">Когда нужно понять старый код или осознанно использовать fall-through.</td></tr>
		<tr><td style="border: 1px solid #ddd; padding: 10px;"><code>case -></code></td><td style="border: 1px solid #ddd; padding: 10px;">Для нового кода, где каждая ветка независима.</td></tr>
		<tr><td style="border: 1px solid #ddd; padding: 10px;">switch expression</td><td style="border: 1px solid #ddd; padding: 10px;">Когда нужно получить значение: строку, код, категорию, результат операции.</td></tr>
	</tbody>
</table>

<h2 style="color: #34495e; margin-top: 30px;">7. Мини-практика</h2>

<p>Определите оценку по баллу от <code>0</code> до <code>100</code>. Сначала проверьте, что балл лежит в допустимом диапазоне, затем вычислите десяток и используйте <code>switch expression</code>:</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">public static String grade(int score) {
    if (score &lt; 0 || score &gt; 100) {
        return "invalid";
    }

    int bucket = score / 10;

    return switch (bucket) {
        case 10, 9 -> "A";
        case 8 -> "B";
        case 7 -> "C";
        case 6 -> "D";
        default -> "F";
    };
}</code></pre>

<p>Здесь <code>switch</code> работает не по диапазону напрямую, а по заранее вычисленной категории <code>bucket</code>. Это важный Java-паттерн для задач с числовыми интервалами.</p>

<h2 style="color: #34495e; margin-top: 30px;">Чек-лист самопроверки</h2>
<ul style="margin-bottom: 0;">
	<li><label><input type="checkbox"> Я понимаю разницу между <code>case:</code> и <code>case -></code></label></li>
	<li><label><input type="checkbox"> Я умею перечислять несколько значений через запятую</label></li>
	<li><label><input type="checkbox"> Я могу вернуть значение через switch expression</label></li>
	<li><label><input type="checkbox"> Я понимаю, когда нужен <code>yield</code></label></li>
	<li><label><input type="checkbox"> Я добавляю <code>default</code> для внешних и пользовательских значений</label></li>
</ul>
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
