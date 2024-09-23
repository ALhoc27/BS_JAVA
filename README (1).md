---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Функциональные интерфейсы

Функциональный интерфейс — это интерфейс, содержащий один абстрактный метод. Он может иметь и другие методы, но они должны быть `default` или `static`. Чтобы указать, что интерфейс является функциональным, можно использовать аннотацию `@FunctionalInterface`, но она необязательна.

Основные функциональные интерфейсы в пакете `java.util.function`:

#### 1.  **Function\<T, R>**

* Принимает один аргумент типа `T` и возвращает результат типа `R` .
* Метод: `R apply(T t)`
* Пример: Преобразование строки в её длину.

<table data-full-width="true"><thead><tr><th width="204">С использованием:</th><th width="696">Code:</th><th data-hidden></th></tr></thead><tbody><tr><td>Cсылки на метод</td><td><pre class="language-java" data-full-width="true"><code class="lang-java">Function&#x3C;String, Integer> func = String::<a data-footnote-ref href="#user-content-fn-1">length</a>;
int length = func.apply("Hello, World!"); // Пример использования функции
</code></pre></td><td></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java"><code class="lang-java">Function&#x3C;String, Integer> func = <a data-footnote-ref href="#user-content-fn-2">s ->s.length();</a>
int length = func.apply("Hello, World!"); // Пример использования функции
</code></pre></td><td></td></tr><tr><td>Анонимной реализации интерфейса <code>Function</code></td><td><pre class="language-java"><code class="lang-java">Function&#x3C;String, Integer> func = new Function&#x3C;String, Integer>() {
    @Override
    public Integer apply(String s) {
        return s.length();
    }
};
int length = func.apply("Hello, World!"); // Пример использования функции
</code></pre></td><td></td></tr><tr><td>Отдельного класса, который реализует интерфейс <code>Function</code></td><td><pre class="language-java"><code class="lang-java">class StringLengthFunction implements Function&#x3C;String, Integer> {
    @Override
    public Integer apply(String s) {
        return s.length();
    }
}
// Использование
Function&#x3C;String, Integer> func = new StringLengthFunction();
int length = func.apply("Hello, World!"); // Пример использования функции
</code></pre></td><td></td></tr></tbody></table>

#### **2.  BiFunction\<T, U, R>**

* Принимает два аргумента типов `T` и `U`, возвращает результат типа `R`.
* Метод: `R apply(T t, U u)`
* Пример: Сложение двух чисел.\


<table data-full-width="true"><thead><tr><th width="205">С использованием:</th><th>Code:</th></tr></thead><tbody><tr><td></td><td></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java" data-overflow="wrap"><code class="lang-java">BiFunction&#x3C;Integer, Integer, Integer> sum = (a, b) -> a + b; System.out.println(sum.apply(5, 3)); // Результат: 8
</code></pre></td></tr><tr><td></td><td></td></tr></tbody></table>

**3.  Consumer**

* Принимает один аргумент типа `T` и не возвращает результата.
* Метод: `void accept(T t)`
* Пример: Вывод строки на консоль.

<table data-full-width="true"><thead><tr><th width="207">С использованием:</th><th>Code:</th></tr></thead><tbody><tr><td></td><td></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java" data-overflow="wrap" data-full-width="true"><code class="lang-java">Consumer print = s -> System.out.println(s); print.accept("Hello, world!"); // Результат: Hello, world!
</code></pre></td></tr><tr><td></td><td></td></tr></tbody></table>

**4.  BiConsumer\<T, U>**

* Принимает два аргумента типов `T` и `U`, не возвращает результата.
* Метод: `void accept(T t, U u)`
* Пример: Вывод двух строк на консоль.

<table data-full-width="true"><thead><tr><th width="218">С использованием:</th><th>Code:</th></tr></thead><tbody><tr><td></td><td></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java" data-overflow="wrap" data-full-width="true"><code class="lang-java">Supplier supplier = () -> "Hello"; System.out.println(supplier.get()); // Результат: Hello
</code></pre></td></tr><tr><td></td><td></td></tr></tbody></table>

**5.  Supplier**

* Не принимает аргументов, но возвращает объект типа `T`.
* Метод: `T get()`
* Пример: Возвращает строку "Hello".

<table data-full-width="true"><thead><tr><th width="213">С использованием:</th><th>Code:</th></tr></thead><tbody><tr><td></td><td></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java" data-overflow="wrap" data-full-width="true"><code class="lang-java">Supplier supplier = () -> "Hello"; System.out.println(supplier.get()); // Результат: Hello
</code></pre></td></tr><tr><td></td><td></td></tr></tbody></table>

**6.  Predicate**

* Принимает один аргумент типа `T` и возвращает `boolean`.
* Метод: `boolean test(T t)`
* Пример: Проверка, является ли число четным.

<table data-full-width="true"><thead><tr><th width="217"></th><th></th></tr></thead><tbody><tr><td></td><td></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java"><code class="lang-java">Predicate&#x3C;Integer> isEven = n -> n % 2 == 0;
System.out.println(isEven.test(4)); // Результат: true
</code></pre></td></tr><tr><td></td><td></td></tr></tbody></table>

**7.  BiPredicate\<T, U>**

* Принимает два аргумента типов `T` и `U`, возвращает `boolean`.
* Метод: `boolean test(T t, U u)`
* Пример: Проверка, если два числа равны.

<table data-full-width="true"><thead><tr><th width="219"></th><th></th></tr></thead><tbody><tr><td></td><td></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java"><code class="lang-java">BiPredicate&#x3C;Integer, Integer> isEqual = (a, b) -> a.equals(b);
System.out.println(isEqual.test(5, 5)); // Результат: true
</code></pre></td></tr><tr><td></td><td></td></tr></tbody></table>

**8.  UnaryOperator**

* Наследуется от `Function<T, T>`. Принимает и возвращает объект одного и того же типа.
* Метод: `T apply(T t)`
* Пример: Увеличение числа на 1.



<table data-full-width="true"><thead><tr><th width="223"></th><th></th></tr></thead><tbody><tr><td></td><td></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java"><code class="lang-java">UnaryOperator&#x3C;Integer> increment = n -> n + 1;
System.out.println(increment.apply(5)); // Результат: 6
</code></pre></td></tr><tr><td></td><td></td></tr></tbody></table>

**9.  BinaryOperator**

* Принимает объект типа `T` и возвращает целое число (`int`).
* Метод: `int applyAsInt(T value)`
* Пример: Преобразование строки в её длину.

<table data-full-width="true"><thead><tr><th width="225"></th><th></th></tr></thead><tbody><tr><td></td><td></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java" data-overflow="wrap"><code class="lang-java">ToIntFunction&#x3C;String> stringLength = s -> s.length();
System.out.println(stringLength.applyAsInt("Hello")); // Результат: 5
</code></pre></td></tr><tr><td></td><td></td></tr></tbody></table>

**10.  ToIntFunction**

* Принимает объект типа `T` и возвращает целое число (`int`).
* Метод: `int applyAsInt(T value)`
* Пример: Преобразование строки в её длину.

<table data-full-width="true"><thead><tr><th width="228"></th><th></th></tr></thead><tbody><tr><td></td><td></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java" data-overflow="wrap" data-full-width="true"><code class="lang-java">ToIntFunction&#x3C;String> stringLength = s -> s.length();
System.out.println(stringLength.applyAsInt("Hello")); // Результат: 5
</code></pre></td></tr><tr><td></td><td></td></tr></tbody></table>

[^1]: Сигнатура метода `length()`

    ```java
    public int length();
    ```

    Метод `length()` используется для получения длины строки (количества символов в строке). Он является методом класса `String` и возвращает значение типа `int`, количетсво символов в строке.

    <mark style="color:orange;">Вызывается у объектов типа</mark> <mark style="color:orange;">**`String`**</mark>

[^2]: Реализует метод:12\
    <mark style="color:green;">R</mark> apply(T <mark style="color:blue;">t</mark>);\
    где **S** - это параметр <mark style="color:blue;">t</mark>, который является типом **String**, тип <mark style="color:green;">R</mark> в данном случае должен быть **int**.

    Метод\
    ![](<.gitbook/assets/Снимок экрана 2024-09-17 в 12.09.13.png>)
