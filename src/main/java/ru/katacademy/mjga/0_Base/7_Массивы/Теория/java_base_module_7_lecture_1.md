<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50;">Массивы в Java: создание и базовые операции</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть за 30 секунд</h3>

<ul>
	<li>Массив <code>int[]</code> имеет фиксированную длину после создания</li>
	<li><code>array.length</code> показывает длину массива</li>
	<li>Индексация начинается с нуля: первый элемент имеет индекс <code>0</code></li>
	<li>Выход за границы приводит к <code>ArrayIndexOutOfBoundsException</code> или <code>IndexOutOfBoundsException</code></li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>

<p>Для лучшего понимания массивов в Java прослушайте аудиоподкаст:</p>
<p style="margin: 15px 0;"><a href="https://drive.google.com/file/d/1EQYxMkq9KDfi8hkIWCcXcbEg-l-bh-CS/view?usp=sharing" style="display: inline-block; background: #1565c0; color: white; padding: 10px 20px; text-decoration: none; border-radius: 5px; font-weight: bold;" target="_blank">🎧 Прослушать о массивах</a></p>
<p style="font-size: 14px; color: #666; margin-top: 10px;"><em>Откроется в новой вкладке. Рекомендуется прослушать перед изучением материала для общего понимания или после — для закрепления.</em></p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎯 Чему вы научитесь</h4>

<ul>
	<li>✅ Понимать, что массив имеет фиксированную длину</li>
	<li>✅ Создавать массивы через литерал и через <code>new</code></li>
	<li>✅ Читать и изменять элементы по индексу</li>
	<li>✅ Перебирать массивы классическим циклом и enhanced for</li>
</ul>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">📚 Предпосылки</h4>

<p>Перед этой темой важно уверенно владеть переменными, методами, условными операторами и циклами. Массивы почти всегда обрабатываются через цикл, поэтому ошибки в границах цикла быстро приводят к ошибкам выполнения.</p>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">Что значит ошибка выхода за границы</h4>
<p style="margin: 0;"><code>ArrayIndexOutOfBoundsException</code> и <code>IndexOutOfBoundsException</code> &mdash; это ошибки времени выполнения. Они появляются, когда программа обращается к несуществующему индексу, например к <code>numbers[5]</code> у массива длиной 5.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. Массив: фиксированная длина и быстрый доступ по индексу</h2>

<p>Массив в Java хранит элементы одного типа и имеет фиксированную длину. Длина задаётся в момент создания и не меняется. Если нужно добавить ещё один элемент, создают новый массив большего размера и копируют данные.</p>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🔎 Что такое <code>import java.util.Arrays</code></h4>

<p><code>Arrays</code> &mdash; это готовый вспомогательный класс из стандартной библиотеки Java для работы с массивами. Чтобы использовать его короткое имя <code>Arrays</code>, в начале файла пишут <code>import java.util.Arrays;</code>.</p>

<p style="margin-bottom: 0;">В этой теме он нужен прежде всего для красивого вывода массива через <code>Arrays.toString(numbers)</code>. Без этого Java выведет не содержимое массива, а служебную строку объекта. Позже мы также используем <code>Arrays.copyOf</code> и <code>Arrays.copyOfRange</code> для копирования массивов.</p>
</div>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};

        numbers[0] = 15;

        System.out.println("Длина: " + numbers.length);
        System.out.println("Первый элемент: " + numbers[0]);
        System.out.println("Массив: " + Arrays.toString(numbers));
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #0c4a6e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Длина: 5
Первый элемент: 15
Массив: [15, 20, 30, 40, 50]</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">2. Значения по умолчанию</h2>

<p>Если массив создаётся через <code>new</code>, Java заполняет его значениями по умолчанию. Для <code>int</code> это <code>0</code>, для <code>boolean</code> &mdash; <code>false</code>, для ссылочных типов &mdash; <code>null</code>.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] scores = new int[4];
        boolean[] flags = new boolean[3];
        String[] names = new String[2];

        System.out.println(Arrays.toString(scores));
        System.out.println(Arrays.toString(flags));
        System.out.println(Arrays.toString(names));
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #0c4a6e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>[0, 0, 0, 0]
[false, false, false]
[null, null]</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">3. Перебор массива</h2>

<p>Классический цикл удобен, когда нужен индекс. Enhanced for удобен, когда нужно только значение элемента.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    public static void main(String[] args) {
        int[] numbers = {3, 7, 2, 9};

        for (int i = 0; i &lt; numbers.length; i++) {
            System.out.println("index=" + i + ", value=" + numbers[i]);
        }

        int sum = 0;
        for (int value : numbers) {
            sum += value;
        }

        System.out.println("sum=" + sum);
    }
}</code></pre>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">✅ Чек-лист самопроверки</h4>

<ul style="margin-bottom: 0;">
	<li><label><input type="checkbox"> Я понимаю, что длина массива не меняется после создания</label></li>
	<li><label><input type="checkbox"> Я умею получать длину массива через <code>array.length</code></label></li>
	<li><label><input type="checkbox"> Я помню, что первый индекс равен <code>0</code></label></li>
	<li><label><input type="checkbox"> Я выбираю enhanced for, когда индекс не нужен</label></li>
</ul>
</div>
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
