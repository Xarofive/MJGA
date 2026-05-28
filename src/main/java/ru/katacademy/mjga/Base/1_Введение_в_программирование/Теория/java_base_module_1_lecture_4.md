<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title></title>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif;">
<h1 style="text-align: center; color: #2c3e50; border-bottom: 3px solid #3498db; padding-bottom: 15px;">Java Base: Базовая структура программы на Java</h1>

<p><strong>Java Base, Модуль 1, Лекция 4</strong></p>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #495057; margin-top: 0;">📌 TL;DR — Суть лекции</h4>

<ul>
	<li>Java-программа — это набор инструкций, которые выполняет компьютер.</li>
	<li>Код Java обычно находится внутри классов.</li>
	<li>Метод <code>main()</code> — точка входа в программу.</li>
	<li><code>System.out.println()</code> выводит текст в консоль.</li>
	<li>После этой лекции вы сможете написать и запустить простую полную Java-программу.</li>
</ul>
</div>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">Содержание</h4>

<ol>
	<li><a href="#what-is-program">Что такое программа на Java</a></li>
	<li><a href="#elements">Основные элементы программы</a></li>
	<li><a href="#simple-program">Простая программа на Java</a></li>
	<li><a href="#output">Вывод данных</a></li>
	<li><a href="#practice">Закрепление знаний</a></li>
	<li><a href="#whats-next">Что дальше?</a></li>
</ol>
</div>

<h2 id="what-is-program" style="color: #34495e; margin-top: 30px;">Что такое программа на Java</h2>

<p>Программа на Java — это набор инструкций, который сообщает компьютеру, какие действия нужно выполнить.</p>

<p>Программы могут быть разной сложности, но даже самая простая Java-программа обычно состоит из нескольких обязательных элементов:</p>

<ul>
	<li><strong>класс</strong>;</li>
	<li><strong>метод <code>main()</code></strong>;</li>
	<li><strong>команды внутри метода</strong>;</li>
	<li><strong>вывод информации на экран</strong>.</li>
</ul>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<p><strong>Важно:</strong> в Java код обычно начинается с класса, например <code>public class Main</code>. Поэтому даже самая маленькая программа на Java выглядит немного подробнее, чем просто одна команда вывода.</p>
</div>

<h2 id="elements" style="color: #34495e; margin-top: 30px;">Основные элементы программы</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">1. Класс</h4>

<p>Класс — основа Java-программы. Почти весь Java-код находится внутри классов.</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
public class Main {

}</pre>

<p>Если класс объявлен как <code>public class Main</code>, файл должен называться <code>Main.java</code>.</p>
</div>

<div style="background: #e0f2f1; border: 1px solid #80cbc4; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #00695c; margin-top: 0;">2. Метод main()</h4>

<p><code>main()</code> — это точка входа в программу. С этого метода JVM начинает выполнение кода.</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
public static void main(String[] args) {
    // код программы
}</pre>

<p><code>String[] args</code> — параметры запуска программы. Сейчас достаточно писать эту часть как в примере; подробнее параметры разберём позже.</p>
</div>

<div style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #495057; margin-top: 0;">3. Команды программы</h4>

<p>Команда или инструкция — это действие, которое должна выполнить программа.</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
System.out.println("Hello Kata Academy");</pre>
</div>

<h2 id="simple-program" style="color: #34495e; margin-top: 30px;">Простая программа на Java</h2>

<p>Рассмотрим готовый пример простой программы на Java:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
public class Main {

    public static void main(String[] args) {
        System.out.println("Hello Kata Academy!");
        System.out.println("Hello My First Program with Java!");
    }
}</pre>

<h3 style="color: #34495e; margin-top: 25px;">Что происходит в программе</h3>

<ul>
	<li>Создаём класс <code>Main</code>.</li>
	<li>Создаём метод <code>main()</code>, который является точкой входа.</li>
	<li>Пишем команды внутри <code>main()</code>.</li>
	<li>Выводим две строки текста с помощью <code>System.out.println()</code>.</li>
</ul>

<h2 id="output" style="color: #34495e; margin-top: 30px;">Вывод данных</h2>

<p>Для вывода текста в Java часто используют <code>System.out.println()</code>.</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
System.out.println("Hello Kata Academy");</pre>

<p><code>println</code> выводит текст и переносит курсор на новую строку.</p>

<p>Есть похожая команда <code>print</code>:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
System.out.print("Hello ");
System.out.print("Java");</pre>

<p>Она выводит текст без переноса строки. Результат будет таким:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
Hello Java</pre>

<h2 id="practice" style="color: #34495e; margin-top: 30px;">Закрепление знаний</h2>

<p>После этой лекции вы сможете выполнить первые практические задачи курса:</p>

<ul>
	<li>написать текст в двойных кавычках;</li>
	<li>использовать <code>System.out.println()</code>;</li>
	<li>создать класс <code>Main</code>;</li>
	<li>создать метод <code>main()</code>;</li>
	<li>запустить первую полную программу на Java.</li>
</ul>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">Мини-задание</h4>

<p>Создайте программу, которая выводит две строки:</p>

<pre style="margin: 0; font-family: 'SF Mono', Monaco, Consolas, monospace; line-height: 1.5;">
Hello Kata Academy
I am learning Java</pre>
</div>

<h2 id="whats-next" style="color: #34495e; margin-top: 30px;">Что дальше?</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p><strong>Теперь можно переходить к небольшим практическим задачам на вывод текста и метод <code>main()</code>.</strong></p>

<p>Дальше вы будете чаще писать код руками: создавать файл, запускать программу и исправлять простые ошибки.</p>
</div>
</div>
