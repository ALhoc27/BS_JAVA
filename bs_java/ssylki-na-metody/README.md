# Ссылки на методы

Вызов метода через ссылку на метод в Java основан на функциональных интерфейсах. Ссылка на метод — это сокращение, которое позволяет использовать существующий метод в качестве аргумента в лямбд-выражении. Когда вы используете ссылку на метод, Java сопоставляет типы функционального интерфейса с сигнатурой метода, на который ссылаются.

### Основные шаги сопоставления:

1. **Функциональный интерфейс**: Это интерфейс, который имеет всего один абстрактный метод. Например, интерфейс `Function<T, R>` является функциональным интерфейсом, который принимает один аргумент типа `T` и возвращает результат типа `R`.
2. **Типы аргументов и возвращаемого значения**: Ссылка на метод должна соответствовать сигнатуре метода функционального интерфейса:
   * Аргументы, которые передаются в абстрактный метод интерфейса, должны соответствовать типам аргументов метода, на который ссылаются. (**или автоматический выводиться**)
   * Тип возвращаемого значения метода, на который ссылаются, должен соответствовать типу возвращаемого значения функционального интерфейса.  (**или автоматический выводиться**)

### Как Java сопоставляет сигнатуры

Рассмотрим на примере:

```java
import java.util.function.Function;

public class Main {
    public static void main(String[] args) {
        Function<String, Integer> getLength = String::length;  // Ссылка на метод
        Integer length = getLength.apply("Hello, World!"); // Применение функции
    }
}
```

**Шаг 1: Разбор функционального интерфейса**

* В интерфейсе `Function<T, R>`, метод `apply(T t)` принимает аргумент типа `T` (в нашем случае это `String`) и возвращает результат типа `R` (в нашем случае это `Integer`).
* Метод `apply()` функционального интерфейса имеет следующую сигнатуру:

```java
R apply(T t);
```

_Что означает: метод `apply()` принимает один аргумент типа `T` и возвращает значение типа `R`._

**Шаг 2: Сопоставление с методом `length()`**

* Метод `String::length` — это ссылка на метод, который принадлежит классу `String` и имеет следующую сигнатуру:

```java
int length();
```

_Этот метод не принимает аргументов и возвращает целое число (`int`), которое является длиной строки._

**Шаг 3: Как Java сопоставляет сигнатуры**

1. <mark style="background-color:orange;">**Аргументы**</mark><mark style="background-color:orange;">: Метод</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">`apply(String s)`</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">требует, чтобы ему был передан аргумент типа</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">`String`</mark><mark style="background-color:orange;">. Метод</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">`length()`</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">вызывается на экземпляре строки,</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">**то есть он подходит, поскольку его можно применить к объекту типа**</mark><mark style="background-color:orange;">** **</mark><mark style="background-color:orange;">**`String`**</mark><mark style="background-color:orange;">. Метод</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">`length()`</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">не принимает аргументов, но это согласуется с тем фактом, что</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">`apply()`</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">передаёт строку объекту, на котором вызывается</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">`length()`</mark><mark style="background-color:orange;">.</mark>
2. **Возвращаемое значение**: Метод `String.length()` возвращает значение типа `int`. Это соответствует типу `Integer`, который является возвращаемым значением для метода `apply()` в интерфейсе `Function<String, Integer>`. Java автоматически преобразует `int` в `Integer` (автоупаковка).
