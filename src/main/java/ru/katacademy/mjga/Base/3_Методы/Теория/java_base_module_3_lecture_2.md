<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<p>&nbsp;</p>
<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">

<h1 style="text-align: center; color: #2c3e50; margin-top: 0;">Java Base, Модуль 3, Лекция 2<br />Методы с параметрами</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть лекции</h3>
<ul>
	<li><strong>Параметры</strong> &mdash; входные данные метода.</li>
	<li>В Java тип параметра пишется перед именем: <code>int age</code>, <code>String name</code>.</li>
	<li>При вызове метода передаются <strong>аргументы</strong> &mdash; конкретные значения.</li>
	<li>Количество, порядок и типы аргументов должны соответствовать параметрам.</li>
	<li>Параметры видны только внутри метода.</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Содержание</h2>
<ul>
	<li><a href="#why">Зачем нужны параметры?</a></li>
	<li><a href="#syntax">Синтаксис параметров</a></li>
	<li><a href="#call">Вызов метода с аргументами</a></li>
	<li><a href="#value">Передача значений</a></li>
	<li><a href="#naming">Именование параметров</a></li>
	<li><a href="#mistakes">Частые ошибки</a></li>
	<li><a href="#quiz">Проверь себя</a></li>
</ul>

<h2 id="why" style="color: #34495e; margin-top: 30px;">Зачем нужны параметры?</h2>
<p>Метод без параметров всегда делает одно и то же. Параметры позволяют передавать в метод разные данные и получать разное поведение при одинаковой логике.</p>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">Без параметров и с параметрами</h4>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>static void sayHello() {
    System.out.println("Привет!");
}

static void sayHelloTo(String name) {
    System.out.println("Привет, " + name);
}</code></pre>
</div>

<h2 id="syntax" style="color: #34495e; margin-top: 30px;">Синтаксис параметров</h2>
<p>Параметры перечисляются в круглых скобках после имени метода:</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>static void methodName(тип1 параметр1, тип2 параметр2) {
    // тело метода
}</code></pre>

<p><strong>Пример с одним параметром:</strong></p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    static void greet(String name) {
        System.out.println("Привет, " + name);
    }

    public static void main(String[] args) {
        greet("Алексей");
        greet("Мария");
    }
}</code></pre>
<div style="background: #f0f0f0; border-left: 3px solid #666; padding: 10px; margin: 10px 0;">
<strong>Ожидаемый вывод:</strong>
<pre style="margin: 5px 0 0 0;">Привет, Алексей
Привет, Мария</pre>
</div>

<p><strong>Пример с параметрами разных типов:</strong></p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    static void introduce(String name, int age) {
        System.out.println(name + ", возраст " + age + " лет");
    }

    public static void main(String[] args) {
        introduce("Иван", 25);
        introduce("Елена", 32);
    }
}</code></pre>

<div style="background: #fff3cd; border-left: 4px solid #ffc107; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">Важно про синтаксис Java</h4>
<p style="margin: 0;">В Java тип пишется перед каждым параметром: <code>int a, int b</code>. Тип нельзя указывать один раз после нескольких имён параметров.</p>
</div>

<h2 id="call" style="color: #34495e; margin-top: 30px;">Вызов метода с аргументами</h2>
<p>При вызове нужно передать значения для всех параметров:</p>
<ul>
	<li><strong>Количество совпадает:</strong> два параметра &mdash; два аргумента.</li>
	<li><strong>Порядок важен:</strong> первый аргумент идёт первому параметру.</li>
	<li><strong>Типы совместимы:</strong> в <code>int</code> нельзя передать строку.</li>
</ul>

<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    static void printInfo(String city, int population, double area) {
        System.out.println("Город: " + city);
        System.out.println("Население: " + population);
        System.out.println("Площадь: " + area);
        System.out.println("---");
    }

    public static void main(String[] args) {
        printInfo("Москва", 12500000, 2561.5);

        String cityName = "Санкт-Петербург";
        int people = 5400000;
        double squareKm = 1439.0;
        printInfo(cityName, people, squareKm);
    }
}</code></pre>

<h2 id="value" style="color: #34495e; margin-top: 30px;">Передача значений</h2>
<p>Для простых типов вроде <code>int</code>, <code>double</code>, <code>boolean</code> метод получает копию значения. Если изменить параметр внутри метода, переменная снаружи не изменится.</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>public class Main {
    static void increment(int n) {
        n = n + 1;
        System.out.println("Внутри increment: " + n);
    }

    public static void main(String[] args) {
        int x = 10;
        System.out.println("До вызова: " + x);
        increment(x);
        System.out.println("После вызова: " + x);
    }
}</code></pre>
<div style="background: #f0f0f0; border-left: 3px solid #666; padding: 10px; margin: 10px 0;">
<strong>Ожидаемый вывод:</strong>
<pre style="margin: 5px 0 0 0;">До вызова: 10
Внутри increment: 11
После вызова: 10</pre>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">✅ Почему это удобно?</h4>
<p style="margin: 0;">Метод не может случайно изменить внешнюю переменную простого типа. Это делает код предсказуемее.</p>
</div>

<h2 id="naming" style="color: #34495e; margin-top: 30px;">Именование параметров</h2>
<p>Имена параметров должны объяснять смысл данных:</p>
<pre style="background: #1e293b; color: #e2e8f0; padding: 15px; border-radius: 5px;"><code>// Плохо
static void process(int a, String b, boolean c) { }

// Лучше
static void printUserInfo(int age, String name, boolean isActive) { }

// Для простых математических методов короткие имена допустимы
static void printSum(int a, int b) { }</code></pre>

<h2 id="mistakes" style="color: #34495e; margin-top: 30px;">Частые ошибки</h2>
<table style="width: 100%; border-collapse: collapse;">
	<tbody>
		<tr style="background: #ffebee;"><th style="padding: 10px; border: 1px solid #ef9a9a;">Ошибка</th><th style="padding: 10px; border: 1px solid #ef9a9a;">Как исправить</th></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;"><code>static void sum(a, b int)</code></td><td style="padding: 10px; border: 1px solid #ef9a9a;">В Java пишите <code>static void sum(int a, int b)</code>.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Передали аргументы в неправильном порядке</td><td style="padding: 10px; border: 1px solid #ef9a9a;">Сверьте порядок параметров в объявлении метода.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Передали слишком мало или много аргументов</td><td style="padding: 10px; border: 1px solid #ef9a9a;">Количество аргументов должно совпадать с количеством параметров.</td></tr>
		<tr><td style="padding: 10px; border: 1px solid #ef9a9a;">Используете параметр вне метода</td><td style="padding: 10px; border: 1px solid #ef9a9a;">Параметр существует только внутри метода.</td></tr>
	</tbody>
</table>

<h2 id="quiz" style="color: #34495e; margin-top: 30px;">Проверь себя</h2>
<ul>
	<li>Чем параметр отличается от аргумента?</li>
	<li>Как объявить метод с параметрами <code>String name</code> и <code>int age</code>?</li>
	<li>Почему порядок аргументов важен?</li>
	<li>Изменится ли внешняя переменная <code>int</code>, если поменять параметр внутри метода?</li>
	<li>Что произойдёт, если вызвать метод с неправильным количеством аргументов?</li>
</ul>

</div>
</div>
<p>&nbsp;</p>
