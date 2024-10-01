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

Функциональный интерфейс — это интерфейс, содержащий один абстрактный метод. Он может иметь и другие методы, но они должны быть `default` или `static`. Чтобы указать, что интерфейс является функциональным, можно использовать аннотацию `@FunctionalInterface` но она необязательна.

Основные функциональные интерфейсы в пакете `java.util.function`:

### 1. **Function\<T, R>**

* Принимает один аргумент типа `T` и возвращает результат типа `R` .
* Метод: `R apply(T t)`
* **Пример:** Преобразование строки в её длину.

<table data-full-width="true"><thead><tr><th width="168">С использованием:</th><th width="787">Code:</th><th data-hidden></th></tr></thead><tbody><tr><td>Cсылки на метод</td><td><pre class="language-java"><code class="lang-java">Function&#x3C;String, Integer> func = String::<a data-footnote-ref href="#user-content-fn-1">length</a>;
int length = func.apply("Hello, World!"); // Пример использования функции
</code></pre></td><td></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java"><code class="lang-java">Function&#x3C;String, Integer> func = <a data-footnote-ref href="#user-content-fn-2">s -> s.length();</a>
<strong>int length = func.apply("Hello, World!"); // Пример использования функции
</strong></code></pre></td><td></td></tr><tr><td>Анонимной реализации интерфейса <strong><code>Function</code></strong></td><td><pre class="language-java"><code class="lang-java">Function&#x3C;String, Integer> func = new Function&#x3C;>() {
    @Override
    public Integer apply(String s) {
        return s.length();
    }
};
int length = func.apply("Hello, World!"); // Пример использования функции
</code></pre></td><td></td></tr><tr><td>Отдельного класса, который реализует интерфейс <strong><code>Function</code></strong></td><td><pre class="language-java"><code class="lang-java">class StringLengthFunction implements Function&#x3C;String, Integer> {
    @Override
    public Integer apply(String s) {
        return s.length();
    }
}
// Использование
Function&#x3C;String, Integer> func = new StringLengthFunction();
int length = func.apply("Hello, World!"); // Пример использования функции
</code></pre></td><td></td></tr></tbody></table>

#### **2. BiFunction\<T, U, R>**

* Принимает два аргумента типов `T` и `U`, возвращает результат типа `R`.
* Метод: `R apply(T t, U u)`
* Пример: Сложение двух чисел.

<table data-full-width="true"><thead><tr><th width="194">С использованием:</th><th>Code:</th></tr></thead><tbody><tr><td>Cсылки на метод</td><td><pre class="language-java"><code class="lang-java">BiFunction&#x3C;Integer, Integer, Integer> sum = Integer::sum;
System.out.println(sum.apply(5, 3)); // Результат: 8
</code></pre></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java" data-overflow="wrap"><code class="lang-java">BiFunction&#x3C;Integer, Integer, Integer> sum = (a, b) -> a + b; System.out.println(sum.apply(5, 3)); // Результат: 8
</code></pre></td></tr><tr><td>Анонимной реализации интерфейса<br><strong>BiFunction</strong></td><td><pre class="language-java"><code class="lang-java">import java.util.function.BiFunction;
// Реализация интерфейса BiFunctio
class SumFunction implements BiFunction&#x3C;Integer, Integer, Integer> {
@Override
public Integer apply(Integer a, Integer b) {
return a + b;
}
}
public class Main {
public static void main(String[] args) {
// Использование реализации интерфейса
BiFunction&#x3C;Integer, Integer, Integer> sum = new SumFunction();
System.out.println(sum.apply(5, 3)); // Результат: 8
}
}
</code></pre></td></tr><tr><td>Отдельного класса, который реализует интерфейс <strong>BiFunction</strong></td><td><pre class="language-java"><code class="lang-java">public class SumFunction implements BiFunction&#x3C;Integer, Integer, Integer> {
// Реализация метода apply@Overridepublic Integer apply(Integer a, Integer b) {    return a + b;}public static void main(String[] args) {    // Используем класс SumFunction    SumFunction sum = new SumFunction();    System.out.println(sum.apply(5, 3)); // Результат: 8}
}
</code></pre></td></tr></tbody></table>

**3. Consumer**

* Принимает один аргумент типа `T` и не возвращает результата.
* Метод: `void accept(T t)`
* Пример: Вывод строки на консоль.

<table data-full-width="true"><thead><tr><th width="207">С использованием:</th><th>Code:</th></tr></thead><tbody><tr><td>Cсылки на метод</td><td><pre class="language-java" data-overflow="wrap" data-full-width="true"><code class="lang-java">Consumer&#x3C;String> print = System.out::println;
print.accept("Hello, world!"); // Результат: Hello, world!
</code></pre></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java" data-full-width="true"><code class="lang-java">Consumer print = s -> System.out.println(s); 
print.accept("Hello, world!"); // Результат: Hello, world!
</code></pre></td></tr><tr><td>Анонимной реализации интерфейса<br><strong>Consumer</strong></td><td><pre class="language-java"><code class="lang-java">import java.util.function.Consumer;
public class Main {
public static void main(String[] args) {
// Анонимная реализация интерфейса Consumer
Consumer&#x3C;String> print = new Consumer&#x3C;String>() {
@Override
public void accept(String s) {
System.out.println(s);
}
};
    print.accept("Hello, world!"); // Результат: Hello, world!}
}
</code></pre></td></tr><tr><td>Отдельного класса, который реализует интерфейс <strong>Consumer</strong></td><td><pre class="language-java" data-overflow="wrap" data-full-width="true"><code class="lang-java">import java.util.function.Consumer;
public class PrintConsumer implements Consumer&#x3C;String> {
// Реализация метода accept@Overridepublic void accept(String s) {    System.out.println(s);}public static void main(String[] args) {    // Используем класс PrintConsumer    PrintConsumer print = new PrintConsumer();    print.accept("Hello, world!"); // Результат: Hello, world!}
}
</code></pre></td></tr></tbody></table>

**4. BiConsumer\<T, U>**

* Принимает два аргумента типов `T` и `U`, не возвращает результата.
* Метод: `void accept(T t, U u)`
* Пример: Вывод двух строк на консоль.

<table data-full-width="true"><thead><tr><th width="201">С использованием:</th><th>Code:</th></tr></thead><tbody><tr><td>Cсылки на метод</td><td><pre class="language-java"><code class="lang-java">BiConsumer&#x3C;String, String> printBoth = PrintBoth::print;
printBoth.accept("Hello", "world!"); // Результат: Hello world!
</code></pre></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java" data-full-width="true"><code class="lang-java">BiConsumer&#x3C;String, String> printBoth = (s1, s2) -> System.out.println(s1 + " " + s2);
printBoth.accept("Hello", "world!"); // Результат: Hello world!
</code></pre></td></tr><tr><td>Анонимной реализации интерфейса<br><strong>BiConsumer</strong></td><td><pre class="language-java"><code class="lang-java">public static void main(String[] args) {
    // Анонимная реализация BiConsumer
    BiConsumer&#x3C;String, String> printBoth = new BiConsumer&#x3C;String, String>() {
        @Override
        public void accept(String s1, String s2) {
            System.out.println(s1 + " " + s2);
        }
    };
// Вызов метода acceptprintBoth.accept("Hello", "world!"); // Результат: Hello world!
}
</code></pre></td></tr><tr><td>Отдельного класса, который реализует интерфейс <strong>BiConsumer</strong></td><td><pre class="language-java"><code class="lang-java">public class PrintBothConsumer implements BiConsumer&#x3C;String, String> {
// Реализация метода accept@Overridepublic void accept(String s1, String s2) {    System.out.println(s1 + " " + s2);}public static void main(String[] args) {    // Используем класс PrintBothConsumer    PrintBothConsumer printBoth = new PrintBothConsumer();    printBoth.accept("Hello", "world!"); // Результат: Hello world!}
}
</code></pre></td></tr></tbody></table>

**5. Supplier**

* Не принимает аргументов, но возвращает объект типа `T`.
* Метод: `T get()`
* Пример: Возвращает строку "Hello".

<table data-full-width="true"><thead><tr><th width="213">С использованием:</th><th>Code:</th></tr></thead><tbody><tr><td>Cсылки на метод</td><td><pre class="language-java"><code class="lang-java">Supplier&#x3C;String> supplier = HelloSupplier::getHello;
System.out.println(supplier.get()); // Результат: Hello
</code></pre></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java" data-overflow="wrap" data-full-width="true"><code class="lang-java">Supplier supplier = () -> "Hello"; System.out.println(supplier.get()); // Результат: Hello
</code></pre></td></tr><tr><td>Анонимной реализации интерфейса<br><strong>Supplier</strong></td><td><pre class="language-java"><code class="lang-java">public class Main {
    public static void main(String[] args) {
        // Анонимная реализация интерфейса Supplier
        Supplier&#x3C;String> supplier = new Supplier&#x3C;String>() {
            @Override
            public String get() {
                return "Hello";
            }
        };
    System.out.println(supplier.get()); // Результат: Hello}
}
</code></pre></td></tr><tr><td>Отдельного класса, который реализует интерфейс <strong>Supplier</strong></td><td><pre class="language-java"><code class="lang-java">public class HelloSupplier implements Supplier&#x3C;String> {
// Реализация метода get@Overridepublic String get() {    return "Hello";}public static void main(String[] args) {    // Используем класс HelloSupplier    HelloSupplier supplier = new HelloSupplier();    System.out.println(supplier.get()); // Результат: Hello}
}
</code></pre></td></tr></tbody></table>

**6. Predicate**

* Принимает один аргумент типа `T` и возвращает `boolean`.
* Метод: `boolean test(T t)`
* Пример: Проверка, является ли число четным.

<table data-full-width="true"><thead><tr><th width="217"></th><th></th></tr></thead><tbody><tr><td>Cсылки на метод</td><td><pre class="language-java"><code class="lang-java">Predicate&#x3C;Integer> predicate = EvenPredicate::isEven;
System.out.println(predicate.test(4)); // Результат: true
</code></pre></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java"><code class="lang-java">Predicate&#x3C;Integer> isEven = n -> n % 2 == 0;
System.out.println(isEven.test(4)); // Результат: true
</code></pre></td></tr><tr><td>Анонимной реализации интерфейса<br><strong>Predicate</strong></td><td><pre class="language-java"><code class="lang-java">import java.util.function.Predicate;
<strong>public class EvenPredicateExample {
</strong>    public static void main(String[] args) {
        // Анонимная реализация интерфейса Predicate
        Predicate&#x3C;Integer> isEven = new Predicate&#x3C;Integer>() {
            @Override
            public boolean test(Integer n) {
                return n % 2 == 0;
            }
        };
    System.out.println(isEven.test(4)); // Результат: true}
}
</code></pre></td></tr><tr><td>Отдельного класса, который реализует интерфейс <strong>Predicate</strong></td><td><pre class="language-java"><code class="lang-java">import java.util.function.Predicate;
<strong>public class IsEvenPredicate implements Predicate&#x3C;Integer> {
</strong>
// Реализация метода test
@Override
public boolean test(Integer n) {
return n % 2 == 0;
}
public static void main(String[] args) {    // Используем класс IsEvenPredicate    IsEvenPredicate isEven = new IsEvenPredicate();    System.out.println(isEven.test(4)); // Результат: true}
}
</code></pre></td></tr></tbody></table>

**7. BiPredicate\<T, U>**

* Принимает два аргумента типов `T` и `U`, возвращает `boolean`.
* Метод: `boolean test(T t, U u)`
* Пример: Проверка, если два числа равны.

<table data-full-width="true"><thead><tr><th width="219"></th><th></th></tr></thead><tbody><tr><td>Cсылки на метод</td><td><pre class="language-java"><code class="lang-java">BiPredicate&#x3C;Integer, Integer> biPredicate = EqualityPredicate::isEqual;
System.out.println(biPredicate.test(5, 5)); // Результат: true
</code></pre></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java"><code class="lang-java">BiPredicate&#x3C;Integer, Integer> isEqual = (a, b) -> a.equals(b);
System.out.println(isEqual.test(5, 5)); // Результат: true
</code></pre></td></tr><tr><td>Анонимной реализации интерфейса<br><strong>BiPredicate</strong></td><td><pre class="language-java"><code class="lang-java">import java.util.function.BiPredicate;
public class EqualPredicateExample {
public static void main(String[] args) {    // Анонимная реализация BiPredicate    BiPredicate&#x26;#x3C;Integer, Integer> isEqual = new BiPredicate&#x26;#x3C;Integer, Integer>() {        @Override        public boolean test(Integer a, Integer b) {            return a.equals(b);        }    };    System.out.println(isEqual.test(5, 5)); // Результат: true}
}
</code></pre></td></tr><tr><td>Отдельного класса, который реализует интерфейс <strong>BiPredicate</strong></td><td><pre class="language-java"><code class="lang-java">import java.util.function.BiPredicate;
public class EqualPredicate implements BiPredicate&#x3C;Integer, Integer> {
// Реализация метода test@Overridepublic boolean test(Integer a, Integer b) {    return a.equals(b);}public static void main(String[] args) {    // Используем класс EqualPredicate    EqualPredicate isEqual = new EqualPredicate();    System.out.println(isEqual.test(5, 5)); // Результат: true}
}
</code></pre></td></tr></tbody></table>

**8. UnaryOperator**

* Наследуется от `Function<T, T>`. Принимает и возвращает объект одного и того же типа.
* Метод: `T apply(T t)`
* Пример: Увеличение числа на 1.

<table data-full-width="true"><thead><tr><th width="223"></th><th></th></tr></thead><tbody><tr><td>Cсылки на метод</td><td><pre class="language-java"><code class="lang-java">UnaryOperator&#x3C;Integer> increment = IncrementOperator::increment;
System.out.println(increment.apply(5)); // Результат: 6
</code></pre></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java"><code class="lang-java">UnaryOperator&#x3C;Integer> increment = n -> n + 1;
System.out.println(increment.apply(5)); // Результат: 6
</code></pre></td></tr><tr><td>Анонимной реализации интерфейса<br><strong>UnaryOperator</strong></td><td><pre class="language-java"><code class="lang-java">import java.util.function.UnaryOperator;
public class IncrementExample {
public static void main(String[] args) {
// Анонимная реализация интерфейса UnaryOperator
UnaryOperator&#x3C;Integer> increment = new UnaryOperator&#x3C;Integer>() {
@Override
public Integer apply(Integer n) {
return n + 1;
}
};
    System.out.println(increment.apply(5)); // Результат: 6}
}
</code></pre></td></tr><tr><td>Отдельного класса, который реализует интерфейс <strong>UnaryOperator</strong></td><td><pre class="language-java"><code class="lang-java">import java.util.function.UnaryOperator;
public class IncrementOperator implements UnaryOperator&#x3C;Integer> {
// Реализация метода apply@Overridepublic Integer apply(Integer n) {    return n + 1;}public static void main(String[] args) {    // Используем класс IncrementOperator    IncrementOperator increment = new IncrementOperator();    System.out.println(increment.apply(5)); // Результат: 6}
}
</code></pre></td></tr></tbody></table>

**9. BinaryOperator**

* Принимает объект типа `T` и возвращает целое число (`int`).
* Метод: `int applyAsInt(T value)`
* Пример: Преобразование строки в её длину.

<table data-full-width="true"><thead><tr><th width="225"></th><th></th></tr></thead><tbody><tr><td>Cсылки на метод</td><td><pre class="language-java"><code class="lang-java">ToIntFunction&#x3C;String> stringLength = StringLengthFunction::getStringLength;
System.out.println(stringLength.applyAsInt("Hello")); // Результат: 5
</code></pre></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java" data-overflow="wrap"><code class="lang-java">ToIntFunction&#x3C;String> stringLength = s -> s.length();
System.out.println(stringLength.applyAsInt("Hello")); // Результат: 5
</code></pre></td></tr><tr><td>Анонимной реализации интерфейса<br><strong>BinaryOperator</strong></td><td><pre class="language-java"><code class="lang-java">import java.util.function.ToIntFunction;
public class Main {
public static void main(String[] args) {
// Анонимная реализация интерфейса ToIntFunction
ToIntFunction&#x3C;String> stringLength = new ToIntFunction&#x3C;String>() {
@Override
public int applyAsInt(String s) {
return s.length();
}
};
    System.out.println(stringLength.applyAsInt("Hello")); // Результат: 5}
}
</code></pre></td></tr><tr><td>Отдельного класса, который реализует интерфейс <strong>BinaryOperator</strong></td><td><pre class="language-java"><code class="lang-java">import java.util.function.ToIntFunction;
public class StringLengthFunction implements ToIntFunction&#x3C;String> {
// Реализация метода applyAsInt@Overridepublic int applyAsInt(String s) {    return s.length();}public static void main(String[] args) {    // Используем класс StringLengthFunction    StringLengthFunction stringLength = new StringLengthFunction();    System.out.println(stringLength.applyAsInt("Hello")); // Результат: 5}
}
</code></pre></td></tr></tbody></table>

**10. ToIntFunction**

* Принимает объект типа `T` и возвращает целое число (`int`).
* Метод: `int applyAsInt(T value)`
* Пример: Преобразование строки в её длину.

<table data-full-width="true"><thead><tr><th width="228"></th><th></th></tr></thead><tbody><tr><td>Cсылки на метод</td><td><pre class="language-java"><code class="lang-java">ToIntFunction&#x3C;String> stringLength = StringLength::getLength;
System.out.println(stringLength.applyAsInt("Hello")); // Результат: 5
</code></pre></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java" data-overflow="wrap" data-full-width="true"><code class="lang-java">ToIntFunction&#x3C;String> stringLength = s -> s.length();
System.out.println(stringLength.applyAsInt("Hello")); // Результат: 5
</code></pre></td></tr><tr><td>Анонимной реализации интерфейса<br><strong>ToIntFunction</strong></td><td><pre class="language-java"><code class="lang-java">import java.util.function.ToIntFunction;
public class Main {
public static void main(String[] args) {
// Анонимная реализация ToIntFunction
ToIntFunction&#x3C;String> stringLength = new ToIntFunction&#x3C;String>() {
@Override
public int applyAsInt(String s) {
return s.length();
}
};
    System.out.println(stringLength.applyAsInt("Hello")); // Результат: 5}
}
</code></pre></td></tr><tr><td>Отдельного класса, который реализует интерфейс <strong>ToIntFunction</strong></td><td><pre class="language-java"><code class="lang-java">import java.util.function.ToIntFunction;
public class StringLengthFunction implements ToIntFunction&#x3C;String> {
// Реализация метода applyAsInt@Overridepublic int applyAsInt(String s) {    return s.length();}public static void main(String[] args) {    // Используем класс StringLengthFunction    StringLengthFunction stringLength = new StringLengthFunction();    System.out.println(stringLength.applyAsInt("Hello")); // Результат: 5}
}
</code></pre></td></tr></tbody></table>

[^1]: Сигнатура метода `length()`

    ```java
    public int length();
    ```

    Метод `length()` используется для получения длины строки (количества символов в строке). Он является методом класса `String` и возвращает значение типа `int`, количество символов в строке.

    Вызывается у объектов типа **`String`**

    ![](<../.gitbook/assets/image (5).png>)

[^2]: Реализует метод: `R apply(T t);` где **s** - это параметр **t**, который является типом `String`, тип R в данном случае должен быть `int`.

    ![](<../.gitbook/assets/image (4).png>)
