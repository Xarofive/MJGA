<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<p>&nbsp;</p>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">

<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">Java Base, Модуль 3, Лекция 3<br />Возвращаемые значения методов</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть лекции</h3>
<ul>
	<li>Методы могут не только выполнять действия, но и возвращать результат.</li>
	<li>Тип возвращаемого значения пишется перед именем метода: <code>static int square(int n)</code>.</li>
	<li>Для возврата используется ключевое слово <code>return</code>.</li>
	<li>Возвращаемое значение можно сохранить в переменную, вывести или использовать в выражении.</li>
	<li>Если метод возвращает значение, он не должен быть объявлен как <code>void</code>.</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Содержание</h2>
<ul>
	<li><a href="#why">Зачем возвращать значения?</a></li>
	<li><a href="#syntax">Синтаксис возврата</a></li>
	<li><a href="#usage">Использование результата</a></li>
	<li><a href="#examples">Примеры методов с возвратом</a></li>
	<li><a href="#mistakes">Частые ошибки</a></li>
	<li><a href="#quiz">Проверь себя</a></li>
</ul>

<h2 id="why" style="color: #34495e; margin-top: 30px;">Зачем возвращать значения?</h2>
<p>Метод может быть действием: напечатать текст, показать меню, вывести баннер. Но часто метод нужен как вычислитель: принять данные, посчитать результат и вернуть его вызывающему коду.</p>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">Метод-действие и метод-вычисление</h4>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>// Метод-действие: ничего не возвращает
static void printGreeting(String name) {
    System.out.println("Привет, " + name);
}

// Метод-вычисление: возвращает строку
static String makeGreeting(String name) {
    return "Привет, " + name;
}</code></pre>
</div>

<h2 id="syntax" style="color: #34495e; margin-top: 30px;">Синтаксис возврата</h2>
<p>Чтобы метод возвращал значение, нужно указать тип результата перед именем метода и вернуть значение через <code>return</code>.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>static типВозврата methodName(параметры) {
    return значение;
}</code></pre>

<p><strong>Пример: квадрат числа</strong></p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    static int square(int n) {
        return n * n;
    }

    public static void main(String[] args) {
        int result = square(5);
        System.out.println("Квадрат числа 5 равен: " + result);
        System.out.println("Квадрат числа 7: " + square(7));
    }
}</code></pre>
<div style="background: #f0f0f0; border-left: 3px solid #666; padding: 10px; margin: 10px 0;">
<strong>Ожидаемый вывод:</strong>
<pre style="margin: 5px 0 0 0;">Квадрат числа 5 равен: 25
Квадрат числа 7: 49</pre>
</div>

<h2 id="usage" style="color: #34495e; margin-top: 30px;">Использование результата</h2>
<p>Результат метода можно:</p>
<ul>
	<li>сохранить в переменную: <code>int x = doubleNumber(3);</code></li>
	<li>вывести сразу: <code>System.out.println(doubleNumber(4));</code></li>
	<li>передать в другой метод: <code>addTen(doubleNumber(5));</code></li>
	<li>использовать в выражении: <code>doubleNumber(6) + doubleNumber(7)</code>.</li>
</ul>

<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    static int doubleNumber(int x) {
        return x * 2;
    }

    static int addTen(int x) {
        return x + 10;
    }

    public static void main(String[] args) {
        int doubled = doubleNumber(3);
        System.out.println("Удвоенное: " + doubled);
        System.out.println("Прямо в println: " + doubleNumber(4));

        int result = addTen(doubleNumber(5));
        System.out.println("Композиция методов: " + result);

        int total = doubleNumber(6) + doubleNumber(7);
        System.out.println("Сумма удвоенных: " + total);
    }
}</code></pre>

<h2 id="examples" style="color: #34495e; margin-top: 30px;">Примеры методов с возвратом</h2>
<h3 style="color: #34495e;">Работа со строками</h3>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    static String exclaim(String text) {
        return text + "!";
    }

    static String greet(String name) {
        return "Здравствуйте, " + name;
    }

    static String formatPrice(double price) {
        return String.format("%.2f руб.", price);
    }

    public static void main(String[] args) {
        System.out.println(exclaim("Ура"));
        System.out.println(greet("Александр"));
        System.out.println(exclaim(greet("Мария")));
        System.out.println("Цена: " + formatPrice(99.90));
    }
}</code></pre>

<h3 style="color: #34495e;">Математические методы</h3>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    static int cube(int n) {
        return n * n * n;
    }

    static double average(double a, double b) {
        return (a + b) / 2.0;
    }

    static boolean isEven(int n) {
        return n % 2 == 0;
    }

    public static void main(String[] args) {
        System.out.println("Куб 3: " + cube(3));
        System.out.println("Среднее: " + average(10.5, 20.5));
        System.out.println("10 четное? " + isEven(10));
        System.out.println("7 четное? " + isEven(7));
    }
}</code></pre>

<h2 id="mistakes" style="color: #34495e; margin-top: 30px;">Частые ошибки</h2>
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #ffebee;"><th style="padding: 10px; border: 1px solid #ef9a9a;">Ошибка</th><th style="padding: 10px; border: 1px solid #ef9a9a;">Как исправить</th></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Метод объявлен как <code>void</code>, но должен вернуть значение</td><td style="padding: 10px; border: 1px solid #ef9a9a;">Укажите тип результата: <code>static int sum(...)</code>.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Забыли <code>return</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;">Метод с типом возврата обязан вернуть значение.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Возвращается неправильный тип</td><td style="padding: 10px; border: 1px solid #ef9a9a;">Если объявлен <code>int</code>, возвращайте целое число, а не строку.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Метод считает результат, но печатает его вместо возврата</td><td style="padding: 10px; border: 1px solid #ef9a9a;">В вычислительных методах используйте <code>return</code>, а вывод делайте отдельно.</td></tr>
	</tbody>
</table>

<div style="background: #fff3cd; border-left: 4px solid #ffc107; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">Замечание про несколько значений</h4>
<p style="margin: 0;">В Java метод возвращает одно значение. Если нужно вернуть несколько данных, обычно используют объект, массив или специальный класс-результат. В базовом модуле работаем с одним возвращаемым значением.</p>
</div>

<h2 id="quiz" style="color: #34495e; margin-top: 30px;">Проверь себя</h2>
<ul>
	<li>Где в Java указывается тип возвращаемого значения метода?</li>
	<li>Чем <code>void</code> отличается от <code>int</code> в объявлении метода?</li>
	<li>Что делает ключевое слово <code>return</code>?</li>
	<li>Можно ли сохранить результат метода в переменную?</li>
	<li>Почему вычислительный метод лучше возвращает значение, а не печатает его?</li>
</ul>

</div>
</div>
<p>&nbsp;</p>
