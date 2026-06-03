<div style="max-width: 900px; margin: 0 auto; padding: 20px; background: #f8f9fa;">
<div style="background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); overflow-x: auto;">
<h1 style="text-align: center; color: #2c3e50;">Базовые паттерны работы с массивами</h1>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h3 style="color: #2e7d32; margin-top: 0;">📌 TL;DR &mdash; Суть за 30 секунд</h3>

<ul>
	<li>Фильтрация массива: сначала считаем подходящие элементы, затем создаём <code>int[]</code> нужной длины</li>
	<li>Трансформация: создаём новый массив той же длины и записываем преобразованные значения</li>
	<li>Вставка и удаление в массиве создают новый массив, потому что длина массива фиксирована</li>
	<li>Для копирования частей массива удобно использовать <code>System.arraycopy</code></li>
	<li>Реверс на месте: два указателя навстречу и обмен через временную переменную</li>
	<li>Дедупликация отсортированного массива: сравниваем текущий элемент с предыдущим</li>
	<li>Разбиение на группы: идём по массиву шагом <code>groupSize</code> и копируем диапазон</li>
</ul>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎧 Аудиообъяснение темы</h4>

<p><strong>Заглушка для аудио.</strong> Здесь позже будет ссылка на подкаст по паттернам обработки массивов в Java.</p>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">📚 Предпосылки</h4>

<p>Для успешного изучения темы полезно уверенно понимать массивы, индексы, циклы <code>for</code> и enhanced for, условные операторы и методы. В этой лекции мы работаем только с массивами: динамические структуры данных будут отдельной темой позже.</p>
</div>

<div style="background: #fff3cd; border: 1px solid #ffeaa7; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #856404; margin-top: 0;">Коротко про <code>System.arraycopy</code> и <code>Math.min</code></h4>
<p><code>System.arraycopy(src, srcPos, dst, dstPos, length)</code> копирует <code>length</code> элементов из массива <code>src</code> в массив <code>dst</code>. В этой лекции он нужен как готовый способ быстро скопировать часть массива.</p>
<p style="margin-bottom: 0;"><code>Math.min(a, b)</code> возвращает меньшее из двух чисел. Например, <code>Math.min(10, 7)</code> вернёт <code>7</code>.</p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 15px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">🎯 Чему вы научитесь</h4>

<ul>
	<li>✅ Реализовывать агрегации: сумму, среднее, минимум и максимум</li>
	<li>✅ Искать первый элемент по условию</li>
	<li>✅ Фильтровать массив без изменения исходных данных</li>
	<li>✅ Выполнять трансформацию массива</li>
	<li>✅ Вставлять и удалять элементы с сохранением порядка</li>
	<li>✅ Переворачивать массив на месте</li>
	<li>✅ Разбивать массив на группы фиксированного размера</li>
	<li>✅ Дедуплицировать отсортированный массив</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">1. Агрегации: сумма, среднее, экстремумы</h2>

<p>Агрегация &mdash; это процесс сведения множества значений к одному результату. Для минимума и максимума важно заранее проверить, что массив не пустой.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    public static void main(String[] args) {
        int[] numbers = {15, 8, 42, 3, 27, 11};

        if (numbers.length == 0) {
            System.out.println("Массив пуст");
            return;
        }

        int sum = 0;
        int min = numbers[0];
        int max = numbers[0];

        for (int value : numbers) {
            sum += value;
            if (value &lt; min) {
                min = value;
            }
            if (value &gt; max) {
                max = value;
            }
        }

        int average = sum / numbers.length;

        System.out.println("Сумма: " + sum);
        System.out.println("Среднее: " + average);
        System.out.println("Минимум: " + min);
        System.out.println("Максимум: " + max);
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #0c4a6e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Сумма: 106
Среднее: 17
Минимум: 3
Максимум: 42</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">2. Поиск первого элемента по условию</h2>

<p>Если нужен индекс, используйте классический цикл. Значение <code>-1</code> удобно использовать как признак &laquo;не найдено&raquo;.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">public class Main {
    public static void main(String[] args) {
        int[] values = {3, 7, 2, 15, 8, 21, 4};
        int threshold = 10;

        int firstIndex = -1;
        for (int i = 0; i &lt; values.length; i++) {
            if (values[i] &gt; threshold) {
                firstIndex = i;
                break;
            }
        }

        if (firstIndex != -1) {
            System.out.println("Первый &gt; " + threshold + ": values[" + firstIndex + "] = " + values[firstIndex]);
        }
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #0c4a6e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Первый &gt; 10: values[3] = 15</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">3. Фильтрация: создание нового массива</h2>

<p>Фильтрация создаёт новый массив с элементами, удовлетворяющими условию. Так как длина массива фиксирована, сначала нужно узнать размер результата.</p>

<p>В примере снова используется <code>import java.util.Arrays;</code>, потому что результат удобно вывести через <code>Arrays.toString(filtered)</code>. Это не новая структура данных, а стандартный помощник для массивов.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] original = {12, 5, 8, 19, 3, 14, 7, 20, 1};
        int minValue = 10;

        int count = 0;
        for (int value : original) {
            if (value &gt;= minValue) {
                count++;
            }
        }

        int[] filtered = new int[count];
        int index = 0;
        for (int value : original) {
            if (value &gt;= minValue) {
                filtered[index] = value;
                index++;
            }
        }

        System.out.println("Фильтр &gt;= " + minValue + ": " + Arrays.toString(filtered));
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #0c4a6e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Фильтр &gt;= 10: [12, 19, 14, 20]</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">4. Трансформация</h2>

<p>Трансформация создаёт новый массив, где каждый элемент получен из исходного по правилу. В примере ниже строим массив квадратов.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};

        int[] squares = new int[numbers.length];
        for (int i = 0; i &lt; numbers.length; i++) {
            squares[i] = numbers[i] * numbers[i];
        }

        System.out.println("Исходный: " + Arrays.toString(numbers));
        System.out.println("Квадраты: " + Arrays.toString(squares));
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #0c4a6e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>Исходный: [1, 2, 3, 4, 5]
Квадраты: [1, 4, 9, 16, 25]</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">5. Вставка элемента</h2>

<p>У массива фиксированная длина, поэтому вставка создаёт новый массив на один элемент больше. Нужно скопировать часть до позиции вставки, записать новый элемент и скопировать хвост.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] data = {10, 20, 30, 40, 50};
        int insertIndex = 2;
        int insertValue = 25;

        int[] result = new int[data.length + 1];
        System.arraycopy(data, 0, result, 0, insertIndex);
        result[insertIndex] = insertValue;
        System.arraycopy(data, insertIndex, result, insertIndex + 1, data.length - insertIndex);

        System.out.println("После вставки: " + Arrays.toString(result));
    }
}</code></pre>

<div style="background: white; padding: 10px; border-radius: 5px; margin-top: 10px;">
<h5 style="color: #0c4a6e; margin-top: 0;">📋 Ожидаемый вывод:</h5>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 0;">
<code>После вставки: [10, 20, 25, 30, 40, 50]</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">6. Удаление с сохранением порядка</h2>

<p>Удаление одного элемента из массива тоже создаёт новый массив. Порядок оставшихся элементов сохраняется.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] data = {10, 20, 30, 40, 50};
        int indexToRemove = 2;

        if (indexToRemove &gt;= 0 &amp;&amp; indexToRemove &lt; data.length) {
            int[] result = new int[data.length - 1];
            System.arraycopy(data, 0, result, 0, indexToRemove);
            System.arraycopy(data, indexToRemove + 1, result, indexToRemove, data.length - indexToRemove - 1);

            System.out.println("После удаления: " + Arrays.toString(result));
        }
    }
}</code></pre>

<p>Удаление всех элементов, равных значению, можно сделать тем же фильтрующим приёмом: сначала посчитать элементы, которые нужно оставить, затем создать массив результата.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] numbers = {1, 3, 3, 5, 3, 7, 9, 3};
        int toRemove = 3;

        int count = 0;
        for (int value : numbers) {
            if (value != toRemove) {
                count++;
            }
        }

        int[] result = new int[count];
        int index = 0;
        for (int value : numbers) {
            if (value != toRemove) {
                result[index] = value;
                index++;
            }
        }

        System.out.println("После удаления всех " + toRemove + ": " + Arrays.toString(result));
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">7. Реверс на месте</h2>

<p>Реверс на месте не создаёт новый массив. Два указателя идут навстречу друг другу и меняют элементы местами.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] data = {1, 2, 3, 4, 5};

        int left = 0;
        int right = data.length - 1;
        while (left &lt; right) {
            int temp = data[left];
            data[left] = data[right];
            data[right] = temp;
            left++;
            right--;
        }

        System.out.println("После реверса: " + Arrays.toString(data));
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">8. Разбиение на группы</h2>

<p>Разбиение на группы делит массив на части фиксированного размера. Последняя группа может быть короче остальных.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] data = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11};
        int groupSize = 3;

        if (groupSize &lt;= 0) {
            System.out.println("Размер группы должен быть &gt; 0");
            return;
        }

        for (int i = 0; i &lt; data.length; i += groupSize) {
            int end = Math.min(i + groupSize, data.length);
            int[] group = Arrays.copyOfRange(data, i, end);
            System.out.println("Группа: " + Arrays.toString(group));
        }
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">9. Дедупликация отсортированного массива</h2>

<p>Если данные уже отсортированы, дубликаты стоят рядом. Поэтому достаточно сравнивать текущий элемент с предыдущим.</p>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] sorted = {1, 1, 2, 3, 3, 3, 4, 5, 5};

        if (sorted.length == 0) {
            System.out.println("[]");
            return;
        }

        int count = 1;
        for (int i = 1; i &lt; sorted.length; i++) {
            if (sorted[i] != sorted[i - 1]) {
                count++;
            }
        }

        int[] unique = new int[count];
        unique[0] = sorted[0];
        int index = 1;
        for (int i = 1; i &lt; sorted.length; i++) {
            if (sorted[i] != sorted[i - 1]) {
                unique[index] = sorted[i];
                index++;
            }
        }

        System.out.println("Уникальные: " + Arrays.toString(unique));
    }
}</code></pre>

<h2 style="color: #34495e; margin-top: 30px;">Типичные ошибки</h2>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #991b1b; margin-top: 0;">❌ Ошибка 1: пытаться расширить массив</h4>

<p>Массив имеет фиксированную длину. Для вставки, удаления или фильтрации создавайте новый массив нужного размера.</p>
</div>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #991b1b; margin-top: 0;">❌ Ошибка 2: некорректные границы при копировании</h4>

<p>Метод <code>Arrays.copyOfRange(array, from, to)</code> не включает индекс <code>to</code>. При ручном доступе к элементам проверяйте, что индекс находится в диапазоне от <code>0</code> до <code>array.length - 1</code>.</p>
</div>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #991b1b; margin-top: 0;">❌ Ошибка 3: копировать ссылку вместо данных</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0;">
<code class="language-java">int[] original = {1, 2, 3};
int[] alias = original;
alias[0] = 999;

System.out.println(original[0]); // 999</code></pre>

<p>Для независимой копии используйте <code>Arrays.copyOf(original, original.length)</code>.</p>
</div>

<div style="background: #fee2e2; border: 1px solid #ef4444; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #991b1b; margin-top: 0;">❌ Ошибка 4: пустой массив в агрегации</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0;">
<code class="language-java">// Неправильно: ошибка на пустом массиве
int[] data = {};
int min = data[0];

// Правильно:
if (data.length == 0) {
    System.out.println("Массив пуст");
    return;
}</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Шпаргалка</h2>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">// ФИЛЬТРАЦИЯ В НОВЫЙ МАССИВ
int count = 0;
for (int value : original) {
    if (value &gt;= 10) {
        count++;
    }
}

int[] filtered = new int[count];
int index = 0;
for (int value : original) {
    if (value &gt;= 10) {
        filtered[index] = value;
        index++;
    }
}

// РЕВЕРС МАССИВА НА МЕСТЕ
int left = 0;
int right = data.length - 1;
while (left &lt; right) {
    int temp = data[left];
    data[left] = data[right];
    data[right] = temp;
    left++;
    right--;
}

// ЧАСТЬ МАССИВА И КОПИЯ
int[] part = Arrays.copyOfRange(data, from, to);
int[] copy = Arrays.copyOf(data, data.length);</code></pre>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Практические упражнения</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">📝 Упражнение 1: фильтр &gt;= K</h4>

<p><strong>Задача:</strong> создайте новый массив, содержащий только элементы исходного массива, которые больше или равны заданному <code>K</code>.</p>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">📝 Упражнение 2: удалить все X</h4>

<p><strong>Задача:</strong> удалите все элементы, равные <code>X</code>, с сохранением порядка, вернув новый массив.</p>
</div>

<div style="background: #fff3e0; border: 1px solid #ff9800; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #e65100; margin-top: 0;">📝 Упражнение 3: реверс на месте</h4>

<p><strong>Задача:</strong> переверните массив на месте.</p>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">📝 Упражнение 4: вставка элемента</h4>

<p><strong>Задача:</strong> вставьте число <code>25</code> на позицию <code>2</code> в массив <code>[10, 20, 30, 40]</code>. Результат: <code>[10, 20, 25, 30, 40]</code>.</p>
</div>

<div style="background: #e8f5e9; border: 1px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #2e7d32; margin-top: 0;">📝 Упражнение 5: дедупликация</h4>

<p><strong>Задача:</strong> удалите дубликаты из отсортированного массива <code>[1, 1, 2, 3, 3, 4, 4, 4, 5]</code>. Результат: <code>[1, 2, 3, 4, 5]</code>.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Квиз</h2>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">🧩 Квиз 1: что выведет код?</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code class="language-java">int[] data = {1, 2, 3};
data[0] = data[2];
System.out.println(Arrays.toString(data));</code></pre>

<details><summary style="cursor: pointer; color: #6a1b9a; font-weight: bold;">Показать ответ</summary>
<p><strong>Ответ:</strong> <code>[3, 2, 3]</code>.</p>
</details>
</div>

<div style="background: #f3e5f5; border: 1px solid #ce93d8; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #6a1b9a; margin-top: 0;">🧩 Квиз 2: что выведет код?</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 10px; margin: 10px 0;">
<code class="language-java">int[] data = {1, 2, 3, 4, 5};
int[] part = Arrays.copyOfRange(data, 2, 4);
System.out.println(part.length);</code></pre>

<details><summary style="cursor: pointer; color: #6a1b9a; font-weight: bold;">Показать ответ</summary>
<p><strong>Ответ:</strong> <code>2</code>. Индекс <code>4</code> не включается, поэтому в массив попадают элементы с индексами <code>2</code> и <code>3</code>.</p>
</details>
</div>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<h4 style="color: #1565c0; margin-top: 0;">📦 Полезные методы стандартной библиотеки Java</h4>

<pre style="background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 5px; padding: 15px; margin: 10px 0; overflow-x: auto;">
<code class="language-java">Arrays.copyOf(array, array.length);       // независимая копия массива
Arrays.copyOfRange(array, from, to);      // часть массива
Arrays.sort(array);                       // сортировка массива
Arrays.equals(a, b);                      // сравнение массивов по элементам
System.arraycopy(src, srcPos, dst, dstPos, length); // быстрое копирование диапазона</code></pre>

<p><code>Arrays.sort</code> сортирует массив на месте, то есть меняет исходный массив. <code>Arrays.equals</code> сравнивает массивы по элементам, а не по ссылкам.</p>
<p style="margin-bottom: 0;">Ручные реализации важны для понимания алгоритмов и работы с индексами. Стандартные методы помогают сделать код короче, когда механизм уже понятен.</p>
</div>

<h2 style="color: #34495e; margin-top: 30px;">Что дальше</h2>

<p>Вы освоили ключевые паттерны обработки массивов. Эти знания понадобятся в задачах со строками, таблицами, статистикой, фильтрацией пользовательских данных и подготовкой отчётов.</p>

<h2 style="color: #34495e; margin-top: 30px;">Итоги</h2>

<div style="background: #e3f2fd; border: 1px solid #90caf9; border-radius: 8px; padding: 20px; margin: 20px 0;">
<p>Вы освоили базовые паттерны работы с массивами в Java:</p>

<ul>
	<li>✅ Фильтрация без изменения исходных данных</li>
	<li>✅ Трансформация данных в новый массив</li>
	<li>✅ Вставка элементов с сохранением порядка</li>
	<li>✅ Удаление элементов с сохранением порядка</li>
	<li>✅ Реверс массива на месте</li>
	<li>✅ Разбиение данных на группы</li>
	<li>✅ Дедупликация отсортированных данных</li>
</ul>
</div>

<h2 style="color: #34495e; margin-top: 30px;">✅ Чек-лист самопроверки</h2>

<div style="background: #e8f5e9; border: 2px solid #4caf50; border-radius: 8px; padding: 20px; margin: 20px 0;">
<ul style="list-style: none; padding-left: 0;">
	<li><label><input type="checkbox"> Я умею фильтровать массив в новый массив</label></li>
	<li><label><input type="checkbox"> Я понимаю, почему для фильтрации массива часто нужен первый проход для подсчёта</label></li>
	<li><label><input type="checkbox"> Я умею вставлять элемент с сохранением порядка</label></li>
	<li><label><input type="checkbox"> Я умею удалять элемент с сохранением порядка</label></li>
	<li><label><input type="checkbox"> Я могу перевернуть массив без дополнительного массива</label></li>
	<li><label><input type="checkbox"> Я проверяю размер группы перед разбиением массива</label></li>
	<li><label><input type="checkbox"> Я проверяю границы перед обращением по индексу</label></li>
	<li><label><input type="checkbox"> Я не копирую массив простым присваиванием, если нужна независимая копия</label></li>
	<li><label><input type="checkbox"> Я проверяю пустой массив перед доступом к первому элементу</label></li>
	<li><label><input type="checkbox"> Я умею дедуплицировать отсортированный массив</label></li>
</ul>
</div>
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 8px; padding: 20px; margin: 24px 0; text-align: center;"><h3 style="margin-top: 0;">🚀 Навык разблокирован</h3><p style="margin-bottom: 0;">После этой лекции вы сможете применять материал темы в Java-задачах.</p></div>

</div>
</div>
