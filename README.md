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

1Основные функциональные интерфейсы в пакете `java.util.function`:

1. **Function\<T, R>**
   * Принимает один аргумент типа `T` и возвращает результат типа `R` .
   * Метод: `R apply(T t)`
   * Пример: Преобразование строки в её длину.

`R apply(T t)`

```java
R apply(T t)1;
```

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

[^1]: Сигнатура метода `length()`

    ```java
    public int length();
    ```

    Метод `length()` используется для получения длины строки (количества символов в строке). Он является методом класса `String` и возвращает значение типа `int`, количетсво символов в строке.

    <mark style="color:orange;">Вызывается у объектов типа</mark> <mark style="color:orange;">**`String`**</mark>

[^2]: Реализует метод:\
    <mark style="color:green;">R</mark> apply(T <mark style="color:blue;">t</mark>);\
    где **S** - это параметр <mark style="color:blue;">t</mark>, который является типом **String**, тип <mark style="color:green;">R</mark> в данном случае должен быть **int**.

    Метод \
    ![](<.gitbook/assets/Снимок экрана 2024-09-17 в 12.09.13.png>)
