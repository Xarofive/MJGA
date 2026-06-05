<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50;">Массивы: объявление, создание и базовые операции</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть за 30 секунд</h3>

<ul>
	<li>Массив <code>int[]</code> имеет фиксированную длину после создания</li>
	<li>Для массива используется <code>array.length</code></li>
	<li>Простое присваивание массива копирует ссылку, а не элементы</li>
	<li>Для получения части массива используйте <code>Arrays.copyOfRange</code></li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎯 Чему вы научитесь</h4>

<ul>
	<li>✅ Понимать фиксированную длину массива</li>
	<li>✅ Создавать массивы через литерал и через <code>new</code></li>
	<li>✅ Безопасно работать с индексами и границами</li>
	<li>✅ Копировать массивы и получать подмассивы без изменения исходных данных</li>
</ul>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">📚 Предпосылки</h4>

<p>Для успешного изучения темы нужно понимать базовые типы данных, методы, возвращаемые значения, условные операторы и циклы. Массивы почти всегда обрабатываются циклом, поэтому важно внимательно относиться к началу, условию и шагу цикла.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. Массив: фиксированная длина</h2>

<p>Массив в Java &mdash; это контейнер фиксированной длины. Если вы создали <code>new int[5]</code>, в нём всегда будет ровно пять ячеек. Нельзя добавить шестой элемент в тот же объект массива. Можно только создать новый массив большего размера и скопировать туда старые значения.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] array = new int[3];
        array[0] = 10;
        array[1] = 20;
        array[2] = 30;

        System.out.println("Массив: " + Arrays.toString(array));
        System.out.println("Длина массива: " + array.length);
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #0c4a6e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Массив: [10, 20, 30]
Длина массива: 3</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">2. Длина массива</h2>

<p>У массива есть публичное поле <code>length</code>. Оно показывает количество ячеек массива и никогда не меняется после создания.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] scores = new int[5];
        scores[0] = 100;
        scores[1] = 200;

        System.out.println("Массив: " + Arrays.toString(scores));
        System.out.println("array.length = " + scores.length);
    }
}</code></pre>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 15px; margin: 20px 0;">
<p style="margin: 0;"><strong>⚠️ Важно:</strong> не обращайтесь к элементам массива за пределами доступных индексов. Для массива длиной 5 допустимы индексы от <code>0</code> до <code>4</code>. Индекс <code>5</code> уже недопустим.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">3. Создание массивов</h2>

<p>Если начальные значения известны заранее, используйте литерал массива. Если известен только размер, используйте <code>new</code>.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        String[] colors = {"красный", "зелёный", "синий"};

        int[] scores = new int[5];
        for (int i = 0; i &lt; scores.length; i++) {
            scores[i] = (i + 1) * 10;
        }

        System.out.println("Литерал массива: " + Arrays.toString(colors));
        System.out.println("Массив через new: " + Arrays.toString(scores));
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #0c4a6e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Литерал массива: [красный, зелёный, синий]
Массив через new: [10, 20, 30, 40, 50]</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">4. Подмассивы и копирование</h2>

<p>В Java выражение <code>copy = original</code> не копирует элементы массива. Оно создаёт вторую ссылку на тот же массив. Для независимой копии используйте <code>Arrays.copyOf</code>, а для части массива &mdash; <code>Arrays.copyOfRange</code>.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] data = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};

        int[] middle = Arrays.copyOfRange(data, 3, 7);
        int[] first = Arrays.copyOfRange(data, 0, 4);
        int[] last = Arrays.copyOfRange(data, 6, data.length);

        System.out.println("Исходный массив: " + Arrays.toString(data));
        System.out.println("data[3..7): " + Arrays.toString(middle));
        System.out.println("первые 4: " + Arrays.toString(first));
        System.out.println("с 6-го до конца: " + Arrays.toString(last));

        int[] fullCopy = Arrays.copyOf(data, data.length);
        fullCopy[0] = 999;

        System.out.println("После изменения копии:");
        System.out.println("оригинал: " + Arrays.toString(data));
        System.out.println("копия: " + Arrays.toString(fullCopy));
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #0c4a6e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Исходный массив: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
data[3..7): [3, 4, 5, 6]
первые 4: [0, 1, 2, 3]
с 6-го до конца: [6, 7, 8, 9]
После изменения копии:
оригинал: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
копия: [999, 1, 2, 3, 4, 5, 6, 7, 8, 9]</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Типичные ошибки</h2>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #991b1b; margin-top: 0;">❌ Ошибка 1: выход за границы</h4>

<p>Индексация начинается с нуля. Для массива из трёх элементов доступны индексы <code>0</code>, <code>1</code>, <code>2</code>. Индекс <code>3</code> вызовет ошибку времени выполнения.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0;">
<code class="language-java">// Неправильно:
int[] numbers = {1, 2, 3};
System.out.println(numbers[3]);

// Неправильно:
for (int i = 0; i &lt;= numbers.length; i++) {
    System.out.println(numbers[i]);
}</code></pre>
</div>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #991b1b; margin-top: 0;">❌ Ошибка 2: копирование ссылки вместо массива</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0;">
<code class="language-java">int[] original = {1, 2, 3};
int[] alias = original;
alias[0] = 999;

System.out.println(original[0]); // 999, потому что массив один и тот же</code></pre>

<p>Правильно: <code>int[] copy = Arrays.copyOf(original, original.length);</code></p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Шпаргалка</h2>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
	<code class="language-java">// === МАССИВЫ ===
int[] zeros = new int[5];
int[] numbers = {1, 2, 3};
int length = numbers.length;
int first = numbers[0];

// === КОПИИ ===
int[] copy = Arrays.copyOf(numbers, numbers.length);
int[] part = Arrays.copyOfRange(numbers, 1, 3);</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Практика внутри лекции</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">📝 Упражнение 1: сумма элементов</h4>

<p><strong>Задача:</strong> создайте массив из чисел <code>10, 20, 30, 40, 50</code>. Вычислите сумму всех элементов, используя цикл. Выведите сам массив, сумму и длину массива.</p>

<details><summary style="cursor: pointer; color: #1565c0; font-weight: bold;">Показать решение</summary>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin-top: 10px; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};

        int sum = 0;
        for (int value : numbers) {
            sum += value;
        }

        System.out.println("Массив: " + Arrays.toString(numbers));
        System.out.println("Сумма элементов: " + sum);
        System.out.println("Длина массива: " + numbers.length);
    }
}</code></pre>
</details>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Квиз: что выведет код?</h2>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">🧩 Вопрос 1: длина массива</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code class="language-java">int[] numbers = new int[2];
numbers[0] = 10;
System.out.println(numbers.length);</code></pre>

<details><summary style="cursor: pointer; color: #6a1b9a; font-weight: bold;">Показать ответ</summary>
<p><strong>Ответ:</strong> <code>2</code>. Длина массива равна количеству ячеек, а не количеству вручную заполненных значений.</p>
</details>
</div>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">🧩 Вопрос 2: ссылка или копия</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code class="language-java">int[] a = {1, 2, 3};
int[] b = a;
b[1] = 99;
System.out.println(a[1]);</code></pre>

<details><summary style="cursor: pointer; color: #6a1b9a; font-weight: bold;">Показать ответ</summary>
<p><strong>Ответ:</strong> <code>99</code>. Переменные <code>a</code> и <code>b</code> указывают на один и тот же массив.</p>
</details>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Итоги</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p>Вы разобрали базовые операции с массивами в Java: создание, чтение по индексу, копирование и получение части массива.</p>

<ul>
	<li>✅ Массив имеет фиксированную длину</li>
	<li>✅ Индексы начинаются с нуля</li>
	<li>✅ Подмассивы и копии нужно создавать явно</li>
	<li>✅ Простое присваивание массива не копирует данные</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Что дальше</h2>

<p>В следующей лекции вы продолжите работу с массивами и научитесь применять типовые паттерны обработки: агрегацию, фильтрацию, поиск, объединение, удаление диапазонов и разворот последовательности.</p>

<h2 style="color: #34495e; margin-top: 30px;">✅ Чек-лист самопроверки</h2>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<ul style="list-style: none; padding-left: 0;">
		<li><label><input type="checkbox"> Я могу объяснить, почему длина массива фиксирована</label></li>
	<li><label><input type="checkbox"> Я понимаю, что означает <code>array.length</code></label></li>
	<li><label><input type="checkbox"> Я не обращаюсь к индексу <code>array.length</code></label></li>
	<li><label><input type="checkbox"> Я умею создать независимую копию массива через <code>Arrays.copyOf</code></label></li>
	<li><label><input type="checkbox"> Я понимаю, что <code>Arrays.copyOfRange(array, from, to)</code> не включает индекс <code>to</code></label></li>
</ul>
</div>
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
