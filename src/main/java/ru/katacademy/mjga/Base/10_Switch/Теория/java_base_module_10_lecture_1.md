<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">🎛️ switch в Java: базовая модель и синтаксис</h1>

<div style="background: linear-gradient(to right, #e3f2fd, #bbdefb); border-radius: 8px; padding: 16px; margin: 20px 0;">
<h3 style="color: #1565c0; margin-top: 0;">📝 TL;DR</h3>
<p><code>switch</code> выбирает одну ветку по значению выражения. Он удобен, когда одна переменная сравнивается с набором конкретных значений: числами, символами, строками или enum-значениями.</p>
<p style="margin-bottom: 0;">В классическом Java <code>switch</code> после каждой ветки обычно нужен <code>break</code>. Без него выполнение перейдёт в следующую ветку — это называется fall-through.</p>
</div>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 14px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">🎯 Чему вы научитесь</h3>
<ul>
	<li>Писать классический <code>switch</code> с <code>case</code>, <code>default</code> и <code>break</code></li>
	<li>Группировать несколько <code>case</code> для одного результата</li>
	<li>Понимать, когда <code>switch</code> читается лучше цепочки <code>if/else if</code></li>
	<li>Использовать <code>switch</code> со строками, символами и числами</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 28px;">1. Базовая форма</h2>

<p>Классический <code>switch</code> сравнивает значение выражения с каждым <code>case</code>. Если совпадение найдено, выполняется код этой ветки.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">static String dayName(int day) {
    switch (day) {
        case 1:
            return "понедельник";
        case 2:
            return "вторник";
        case 3:
            return "среда";
        default:
            return "неизвестно";
    }
}</code></pre>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 14px; margin: 16px 0;">
<h4 style="color: #e65100; margin-top: 0;">📝 Почему здесь нет break</h4>
<p style="margin-bottom: 0;">Если ветка сразу делает <code>return</code>, метод завершается, поэтому <code>break</code> уже не нужен. Если ветка присваивает значение переменной и выполнение должно продолжиться после <code>switch</code>, используйте <code>break</code>.</p>
</div>

<h2 style="color: #34495e; margin-top: 28px;">2. break и fall-through</h2>

<p>Если в ветке нет <code>break</code> или <code>return</code>, Java продолжит выполнять следующую ветку. Чаще всего это ошибка.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">static String commandType(String command) {
    String result;

    switch (command) {
        case "start":
            result = "run";
            break;
        case "stop":
            result = "halt";
            break;
        default:
            result = "unknown";
            break;
    }

    return result;
}</code></pre>

<h2 style="color: #34495e; margin-top: 28px;">3. Несколько case для одного результата</h2>

<p>Если несколько значений должны дать один результат, можно поставить несколько <code>case</code> подряд.</p>

<pre style="background: #263238; color: #aed581; padding: 12px; border-radius: 4px; margin: 10px 0;"><code class="language-java">static String season(int month) {
    switch (month) {
        case 12:
        case 1:
        case 2:
            return "зима";
        case 3:
        case 4:
        case 5:
            return "весна";
        default:
            return "неизвестно";
    }
}</code></pre>

<p>Здесь fall-through используется осознанно: пустые ветки <code>case 12</code> и <code>case 1</code> ведут к общему коду для зимы.</p>

<h2 style="color: #34495e; margin-top: 28px;">4. switch и if/else</h2>

<table style="width: 100%; border-collapse: collapse; margin: 16px 0;">
<thead><tr style="background: #e3f2fd;"><th style="padding: 10px; border: 1px solid #90caf9;">Ситуация</th><th style="padding: 10px; border: 1px solid #90caf9;">Что выбрать</th></tr></thead>
<tbody>
<tr><td style="padding: 10px; border: 1px solid #ddd;">Одна переменная сравнивается с конкретными значениями</td><td style="padding: 10px; border: 1px solid #ddd;"><code>switch</code></td></tr>
<tr><td style="padding: 10px; border: 1px solid #ddd;">Нужны диапазоны: <code>score &gt;= 90</code></td><td style="padding: 10px; border: 1px solid #ddd;"><code>if/else if</code></td></tr>
<tr><td style="padding: 10px; border: 1px solid #ddd;">Условия зависят от разных переменных</td><td style="padding: 10px; border: 1px solid #ddd;"><code>if/else if</code></td></tr>
<tr><td style="padding: 10px; border: 1px solid #ddd;">Нужно явно обработать неизвестное значение</td><td style="padding: 10px; border: 1px solid #ddd;"><code>default</code></td></tr>
</tbody>
</table>

<h2 style="color: #34495e; margin-top: 28px;">✅ Чек-лист самопроверки</h2>

<ul style="margin-bottom: 0;">
	<li><label><input type="checkbox"> Я понимаю, что <code>switch</code> выбирает ветку по значению</label></li>
	<li><label><input type="checkbox"> Я использую <code>default</code> для неизвестных значений</label></li>
	<li><label><input type="checkbox"> Я ставлю <code>break</code>, если ветка не завершается через <code>return</code></label></li>
	<li><label><input type="checkbox"> Я умею группировать несколько <code>case</code> для одного результата</label></li>
	<li><label><input type="checkbox"> Я не использую <code>switch</code> для сложных диапазонов, где лучше подходит <code>if</code></label></li>
</ul>
</div>
</div>
