<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<p>&nbsp;</p>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">

<h1 style="text-align: center; color: #2c3e50;">Java Base, Модуль 6, Лекция 1<br />break, continue и метки в Java</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть лекции</h3>
<ul>
	<li><code>break</code> немедленно выходит из ближайшего цикла.</li>
	<li><code>continue</code> пропускает остаток текущей итерации и переходит к следующей.</li>
	<li>В классическом <code>for</code> шаг цикла выполняется даже после <code>continue</code>.</li>
	<li>В <code>while</code> нужно вручную обновлять счётчик перед <code>continue</code>, иначе возможен бесконечный цикл.</li>
	<li>Метки в Java позволяют выйти из внешнего цикла: <code>break outer;</code>.</li>
	<li>Паттерн guard clauses с <code>continue</code> помогает писать плоский код без глубокой вложенности.</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>
<p><strong>Аудио по break и continue в Java будет добавлено позже.</strong></p>
<p style="margin: 15px 0;"><span style="display: inline-block; background: #1565c0; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold;">🎧 Аудио будет добавлено</span></p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎯 Чему вы научитесь</h4>
<ul>
	<li>✅ Правильно применять <code>break</code> для раннего выхода из циклов.</li>
	<li>✅ Использовать <code>continue</code> без создания бесконечных циклов.</li>
	<li>✅ Отличать <code>break</code> от <code>return</code>.</li>
	<li>✅ Управлять вложенными циклами через метки.</li>
	<li>✅ Применять guard clauses в циклах.</li>
</ul>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">📚 Предпосылки</h4>
<ul>
	<li>циклы <code>for</code> и <code>while</code>;</li>
	<li>условные операторы <code>if</code>, <code>else</code>;</li>
	<li>операторы <code>&amp;&amp;</code>, <code>||</code>, <code>!</code>;</li>
	<li>вывод через <code>System.out.println</code> и <code>System.out.printf</code>.</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. break &mdash; выход из цикла</h2>
<p><code>break</code> прерывает ближайший цикл и передаёт управление первой инструкции после него. Это не то же самое, что <code>return</code>: <code>return</code> завершает весь метод.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>int sum = 0;

for (int i = 1; i &lt;= 100; i++) {
    sum += i;

    if (sum &gt; 50) {
        break;
    }
}

System.out.println(sum);</code></pre>

<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #0c4a6e; margin-top: 0;">📊 break vs return</h4>
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #e3f2fd;"><th style="padding: 10px; border: 1px solid #90caf9;">Оператор</th><th style="padding: 10px; border: 1px solid #90caf9;">Что завершает</th><th style="padding: 10px; border: 1px solid #90caf9;">Код после цикла</th></tr>
		<tr><td style="padding: 10px; border: 1px solid #90caf9;"><code>break</code></td><td style="padding: 10px; border: 1px solid #90caf9;">цикл</td><td style="padding: 10px; border: 1px solid #90caf9;">выполняется</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #90caf9;"><code>return</code></td><td style="padding: 10px; border: 1px solid #90caf9;">метод</td><td style="padding: 10px; border: 1px solid #90caf9;">не выполняется</td></tr>
	</tbody>
</table>
</div>

<h2 style="color: #34495e; margin-top: 30px;">2. continue &mdash; пропуск итерации</h2>
<p><code>continue</code> пропускает оставшийся код текущей итерации. В классическом <code>for</code> после этого всё равно выполняется шаг цикла, например <code>i++</code>.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>for (int i = 1; i &lt;= 10; i++) {
    if (i % 2 == 0) {
        continue;
    }

    System.out.println(i);
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">3. continue в while</h2>
<p>В <code>while</code> нет автоматического шага. Если перед <code>continue</code> не изменить переменную условия, цикл может зависнуть.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>int i = 0;

while (i &lt; 10) {
    if (i == 5) {
        i++;
        continue;
    }

    System.out.println(i);
    i++;
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">4. Метки во вложенных циклах</h2>
<p>Обычный <code>break</code> выходит только из ближайшего цикла. Чтобы выйти сразу из нескольких вложенных циклов, в Java можно использовать метку.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>outer:
for (int i = 1; i &lt;= 9; i++) {
    for (int j = 1; j &lt;= 9; j++) {
        if (i * j == 45) {
            System.out.println(i + " " + j);
            break outer;
        }
    }
}</code></pre>
<p>Метки используйте точечно. Если можно решить задачу без метки и код остаётся простым, лучше не усложнять.</p>

<h2 style="color: #34495e; margin-top: 30px;">5. Guard clauses с continue</h2>
<p>Guard clauses &mdash; это ранние проверки, которые сразу пропускают неподходящий случай. Такой подход уменьшает вложенность.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>for (int i = 1; i &lt;= 30; i++) {
    if (i % 15 == 0) {
        System.out.println("FizzBuzz");
        continue;
    }

    if (i % 3 == 0) {
        System.out.println("Fizz");
        continue;
    }

    if (i % 5 == 0) {
        System.out.println("Buzz");
        continue;
    }

    System.out.println(i);
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">✅ Чек-лист самопроверки</h2>
<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 14px; margin: 20px 0;">
<ul style="margin-bottom: 0; list-style: none; padding-left: 0;">
	<li><label><input type="checkbox"> Я понимаю, что <code>break</code> завершает цикл, а не метод.</label></li>
	<li><label><input type="checkbox"> Я понимаю, что <code>continue</code> пропускает остаток текущей итерации.</label></li>
	<li><label><input type="checkbox"> Я обновляю счётчик перед <code>continue</code> в <code>while</code>.</label></li>
	<li><label><input type="checkbox"> Я знаю, что обычный <code>break</code> выходит только из ближайшего цикла.</label></li>
	<li><label><input type="checkbox"> Я умею использовать метку для выхода из вложенных циклов.</label></li>
	<li><label><input type="checkbox"> Я применяю guard clauses, когда они делают код проще.</label></li>
</ul>
</div>

</div>
</div>
<p>&nbsp;</p>
