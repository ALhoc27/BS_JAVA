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

1. **Function\<T, R>**
   * Принимает один аргумент типа `T` и возвращает результат типа `R` .
   * Метод: `R apply(T t)`
   * Пример: Преобразование строки в её длину.

`R apply(T t)`

```java
R apply(T t);
```

<table data-full-width="true"><thead><tr><th width="204">С использованием:</th><th width="696">Code:</th><th data-hidden></th></tr></thead><tbody><tr><td>Cсылки на метод</td><td><pre class="language-java" data-full-width="true"><code class="lang-java">Function&#x3C;String, Integer> func = String::<a data-footnote-ref href="#user-content-fn-1">length</a>;
</code></pre></td><td></td></tr><tr><td>Лямбды-выражения</td><td><pre class="language-java"><code class="lang-java">Function&#x3C;String, Integer> func = s ->s.<a data-footnote-ref href="#user-content-fn-2">length()</a>;
</code></pre></td><td></td></tr><tr><td>Анонимной реализации интерфейса <code>Function</code></td><td><pre class="language-java"><code class="lang-java">Function&#x3C;String, Integer> func = new Function&#x3C;String, Integer>() {
    @Override
    public Integer apply(String s) {
        return s.<a data-footnote-ref href="#user-content-fn-3">length()</a>;
    }
};
</code></pre></td><td></td></tr><tr><td>Отдельного класса, который реализует интерфейс <code>Function</code></td><td><pre class="language-java"><code class="lang-java">class StringLengthFunction implements Function&#x3C;String, Integer> {
    @Override
    public Integer apply(String s) {
        return s.<a data-footnote-ref href="#user-content-fn-4">length()</a>;
    }
}
// Использование
Function&#x3C;String, Integer> func = new StringLengthFunction();а
</code></pre></td><td></td></tr></tbody></table>

[^1]: Сигнатура метода `length()` для строки в Java выглядит так:

    ```java
    public int length();
    ```

    Метод `length()` в Java используется для получения длины строки (количества символов в строке). Он является методом класса `String` и возвращает значение типа `int`, представляющее количество символов в строке.

[^2]: Сигнатура метода `length()` для строки в Java выглядит так:

    ```java
    public int length();
    ```

    Метод `length()` в Java используется для получения длины строки (количества символов в строке). Он является методом класса `String` и возвращает значение типа `int`, представляющее количество символов в строке.

[^3]: Сигнатура метода `length()` для строки в Java выглядит так:

    ```java
    public int length();
    ```

    Метод `length()` в Java используется для получения длины строки (количества символов в строке). Он является методом класса `String` и возвращает значение типа `int`, представляющее количество символов в строке.

[^4]: Сигнатура метода `length()` для строки в Java выглядит так:

    ```java
    public int length();
    ```

    Метод `length()` в Java используется для получения длины строки (количества символов в строке). Он является методом класса `String` и возвращает значение типа `int`, представляющее количество символов в строке.
