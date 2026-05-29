<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<p>&nbsp;</p>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">

<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">Java Base, Модуль 3, Лекция 1<br />Создание и вызов методов в Java</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть лекции</h3>
<ul>
	<li><strong>Метод</strong> &mdash; это переиспользуемый блок кода с именем.</li>
	<li>В Java методы объявляются внутри класса.</li>
	<li>Для простых задач курса используем <code>static</code>-методы в классе <code>Main</code>.</li>
	<li>Метод без результата объявляется с типом <code>void</code>.</li>
	<li>Вызов метода выглядит так: <code>methodName();</code> &mdash; скобки обязательны.</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>
<p><strong>Аудио по методам в Java будет добавлено позже.</strong></p>
<p style="margin: 15px 0;"><span style="display: inline-block; background: #1565c0; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold;">🎧 Аудио будет добавлено</span></p>
<p style="font-size: 14px; color: #666; margin-top: 10px;"><em>Пока изучайте материал по тексту и запускайте примеры в IntelliJ IDEA.</em></p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Содержание</h2>
<ul>
	<li><a href="#why">Зачем нужны методы?</a></li>
	<li><a href="#syntax">Базовый синтаксис метода</a></li>
	<li><a href="#call">Вызов метода</a></li>
	<li><a href="#order">Где объявлять методы</a></li>
	<li><a href="#naming">Правила именования</a></li>
	<li><a href="#mistakes">Частые ошибки</a></li>
	<li><a href="#practice">Практические упражнения</a></li>
	<li><a href="#quiz">Проверь себя</a></li>
</ul>

<h2 id="why" style="color: #34495e; margin-top: 30px;">Зачем нужны методы?</h2>
<p>До этого большая часть кода находилась внутри метода <code>main</code>. Для маленьких примеров это нормально, но в реальных программах код быстро становится длинным и сложным.</p>
<p>Методы помогают разбивать программу на понятные части:</p>
<ul>
	<li><strong>Переиспользование:</strong> один раз написали код и вызываем его много раз.</li>
	<li><strong>Читаемость:</strong> имя метода объясняет, что делает блок кода.</li>
	<li><strong>Поддержка:</strong> если логику нужно изменить, меняем её в одном месте.</li>
</ul>

<div style="background: #f0f9ff; border: 1px solid #0284c7; border-radius: 8px; padding: 15px; margin: 16px 0;">
<h4 style="color: #0c4a6e; margin-top: 0;">💡 Метод как команда</h4>
<p>Метод можно воспринимать как отдельную команду программы. Например, метод <code>printHeader</code> отвечает только за вывод заголовка, а <code>printMenu</code> &mdash; только за вывод меню.</p>
</div>

<h2 id="syntax" style="color: #34495e; margin-top: 30px;">Базовый синтаксис метода</h2>
<p>Самый простой метод в Java для текущего курса выглядит так:</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>static void methodName() {
    // код метода
}</code></pre>
<p>Разберём по частям:</p>
<ul>
	<li><code>static</code> &mdash; позволяет вызывать метод из <code>static main</code> без создания объекта.</li>
	<li><code>void</code> &mdash; метод ничего не возвращает.</li>
	<li><code>methodName</code> &mdash; имя метода.</li>
	<li><code>()</code> &mdash; список параметров. Пока он пустой.</li>
	<li><code>{ }</code> &mdash; тело метода.</li>
</ul>

<h3 style="color: #34495e;">Пример: метод без параметров</h3>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    static void greet() {
        System.out.println("Привет от метода greet!");
    }

    public static void main(String[] args) {
        greet();
    }
}</code></pre>
<div style="background: #f0f0f0; border-left: 3px solid #666; padding: 10px; margin: 10px 0;">
<strong>Ожидаемый вывод:</strong>
<pre style="margin: 5px 0 0 0;">Привет от метода greet!</pre>
</div>

<h2 id="call" style="color: #34495e; margin-top: 30px;">Вызов метода</h2>
<p>Чтобы метод выполнился, его нужно вызвать. Вызов метода &mdash; это имя метода и круглые скобки:</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>greet(); // правильный вызов
greet;   // ошибка: так метод не вызывается</code></pre>

<div style="background: #ffebee; border: 1px solid #ef5350; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #c62828; margin-top: 0;">⚠️ Важно</h4>
<p style="margin: 0;">Скобки обязательны даже у метода без параметров. Запись <code>greet();</code> означает: выполнить метод прямо сейчас.</p>
</div>

<h3 style="color: #34495e;">Многократный вызов</h3>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    static void sayHello() {
        System.out.println("Hello!");
    }

    public static void main(String[] args) {
        sayHello();
        sayHello();
        sayHello();
    }
}</code></pre>
<div style="background: #f0f0f0; border-left: 3px solid #666; padding: 10px; margin: 10px 0;">
<strong>Ожидаемый вывод:</strong>
<pre style="margin: 5px 0 0 0;">Hello!
Hello!
Hello!</pre>
</div>

<h3 style="color: #34495e;">Комбинирование нескольких методов</h3>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    static void greet() {
        System.out.println("Привет!");
    }

    static void separator() {
        System.out.println("---");
    }

    public static void main(String[] args) {
        greet();
        separator();
        greet();
    }
}</code></pre>

<h2 id="order" style="color: #34495e; margin-top: 30px;">Где объявлять методы</h2>
<p>В Java методы объявляются внутри класса, но не внутри других методов. В задачах курса используйте класс <code>Main</code>.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    public static void main(String[] args) {
        printLine();
        System.out.println("Середина");
        printLine();
    }

    static void printLine() {
        System.out.println("----------");
    }
}</code></pre>

<div style="background: #fff3cd; border-left: 4px solid #ffc107; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">Нельзя объявлять метод внутри main</h4>
<pre style="background: #1e293b; color: #e2e8f0; padding: 12px; border-radius: 5px;"><code>public static void main(String[] args) {
    static void helper() { // ошибка
        System.out.println("help");
    }
}</code></pre>
</div>

<h2 id="naming" style="color: #34495e; margin-top: 30px;">Правила именования</h2>
<ul>
	<li>Имена методов пишут в стиле <code>camelCase</code>: <code>printMenu</code>, <code>drawSeparator</code>.</li>
	<li>Имя должно начинаться с буквы, символа <code>_</code> или <code>$</code>, но в учебном коде используйте буквы.</li>
	<li>Имя метода должно объяснять действие: <code>calculateTotal</code> лучше, чем <code>f1</code>.</li>
	<li>Регистр важен: <code>printMenu</code> и <code>PrintMenu</code> &mdash; разные имена.</li>
</ul>

<h2 id="mistakes" style="color: #34495e; margin-top: 30px;">Частые ошибки</h2>
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #ffebee;"><th style="padding: 10px; border: 1px solid #ef9a9a;">Ошибка</th><th style="padding: 10px; border: 1px solid #ef9a9a;">Как исправить</th></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Забыли скобки при вызове</td><td style="padding: 10px; border: 1px solid #ef9a9a;">Пишите <code>greet();</code>, а не <code>greet;</code>.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Объявили метод внутри <code>main</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;">Методы должны быть внутри класса, но вне других методов.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Забыли <code>static</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;">В этом модуле пишите <code>static void methodName()</code>.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Два метода с одинаковой сигнатурой</td><td style="padding: 10px; border: 1px solid #ef9a9a;">Переименуйте один из методов или измените параметры.</td></tr>
	</tbody>
</table>

<h2 id="practice" style="color: #34495e; margin-top: 30px;">Практические упражнения</h2>
<ul>
	<li>Создайте метод <code>greet()</code>, который выводит <code>Привет!</code>, и вызовите его три раза.</li>
	<li>Создайте метод <code>divider()</code>, который выводит строку из дефисов.</li>
	<li>Создайте метод <code>printMenu()</code>, который выводит три пункта меню.</li>
</ul>

<h2 id="quiz" style="color: #34495e; margin-top: 30px;">Проверь себя</h2>
<ul>
	<li>Что такое метод?</li>
	<li>Зачем нужен тип <code>void</code>?</li>
	<li>Почему в учебных задачах методы объявляются со словом <code>static</code>?</li>
	<li>Можно ли объявить метод внутри <code>main</code>?</li>
	<li>Что произойдёт, если забыть скобки при вызове метода?</li>
</ul>

</div>
</div>
<p>&nbsp;</p>
