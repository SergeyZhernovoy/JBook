# Java Базовый Курс

## Занятие 2

Второе занятие в рамках `Java` курса.

В [прошлый раз](./intro.md) мы затронули следующие темы и ответили на вопросы:

* Почему `Java`?
* Ключевое слово `static` в `Java`.
* Типы данных в `Java`
* Циклы и условные операторы

Также были предложены на выбор несколько заданий - для знакомства с языком и синтаксисом.

В рамках этого занятия мы разберем домашнее задание и поговорим про `ООП` принципы.

## Введение

В начале проведем некоторую проверку прошлого материала.

### Проверка знаний

---

**Вопрос**:

Каков результат работы кода:

```java
public class Test {
    public static final int NUMBER = 14;

    public static void main(String[] args) {
        Test test = null;
        System.out.println(test.NUMBER);
    }
}
```

Варианты ответа:

1. 14
2. Будет ошибка компиляции
3. Будет ошибка во время выполнения кода
4. Ничего не произойдет

**Ответ**:

Проверьте ваш ответ воспроизведя пример.

Если вы ответили неправильно, то вам следует еще раз посмотреть часть про [static](./intro.md) и прочесть [полную заметку](../start/static_java.md) об этом.

---

**Вопрос**:

Перечислите на какие виды делятся типы данных в `Java`?
Перечислите пару примеров из каждой группы.

**Ответ**:

В `Java` существует разделение на ссылочные и примитивные типы данных.

Примитивных типов в `Java` всего 8: `byte`, `short`, `char`, `int`, `long`, `float`, `double`, `boolean`.
Все остальное - это ссылочные типы.

Пример ссылочного типа: `java.lang.String`.

---

## Что такое конструктор

Прежде чем мы перейдем непосредственно к теме `ООП` давайте разберем такой вопрос: "А что такое конструктор и для чего он нужен?".

Конструктор в `Java` играет непосредственную роль при создании объекта.

Имя конструктора аналогично имени класса, а сам синтаксис схож с синтаксисом метода. Однако, конструктор - это не совсем метод, так как у него полностю отсутствует возвращаемое значение.

```java
public class Hello {
    // конструктор
    public Hello() {
        // тело конструктора
    }
}
```

В `Java` у каждого класса есть конструктор, даже если вы явно не объявили его, то `Java` автоматически добавит его за вас - такой конструктор называется `конструктор по умолчанию`.

Поэтому конструкция типа:

```java
public class Hello {
}
```

Будет эквивалентна:

```java
public class Hello {
    public Hello() {
    }
}
```

---

**Вопрос**:

Мы уже поняли, что если не объявить конструктор самому, то `Java` сделает нам конструктор по-умолчанию. А если я все-таки объявлю свой собственный конструктор, будет ли у меня конструктор по-умолчанию?

**Ответ**:

Нет, не будет.

Как только вы объявляете хотя бы один конструктор, то ответственность за работу с конструкторами, а значит и за то, как будут создаваться объекты этого класса `Java` с себя снимает.

---

**Вопрос**:

Хорошо, а что если мне нужен и пустой конструктор, похожий на конструктор по-умолчанию, и еще парочка конструкторов, принимающих значения в качестве аргументов?

**Ответ**:

В таком случае, вам следует явно объявить каждый конструктор, который вам нужен.

---

Как правило конструктор применяется для присвоения значений свойствам объектам, либо для совершения еще каких-то действий, например, вызова методов или инициализации классов, которые необходимы для создания полностью сформированного объекта.

Для примера рассмотрим класс:

```java
public class Person {
    int age;

    // конструктор устанавливающий возраст объекту класса Person
    public Person(int age) {
        this.age = age;
    }
}
```

И его использование:

```java
public class Test {
    public static void main(String[] args) {
        Person p = new Person(24);
        System.out.println(p.age);  // 24
    }
}
```

## ООП

Как уже говорилось на первом занятии, `Java` является объектно-ориентированным языком. Поэтому в основном(за исключениями примитивных типов данных) мы оперируем `объектами` и `классами`.

Парадигма объектно-ориентированного подхода стоит на четырех столпах(слонах?), без которых она не представляла бы такого интереса и не стала бы такой популярной.

> Некоторые добавляют еще несколько понятий, но четырех основных, на мой взгляд, достаточно.

Итак, основные идеи:

* Инкапсуляция
* Абстракция
* Наследование
* Полиморфизм

Это то, что надо знать и представлять.

Четыре принципа `ООП` – это как четыре ножки стула. Убери хотя бы одну, и вся система станет неустойчивой.

Читаем об этом [здесь](../oop/intro.md)

После того, как вы прочли материалы выше мы можем продолжить. Позже я советую перечитать еще раз все материалы, чтобы более глубоко усвоить информацию.

Для закрепления попробуйте ответить на вопросы:

* Зачем нужен `private` конструктор у класса?
* Что значит отношение `is a`? А `has a`?
* Что такое `пакет`?
* Существует ли в `Java` ввозможность множественного наследования?
* Зачем нужна `инкапсуляция`?
* Привдеите пример использования `наследования`?

## Практика

Сразу стоит сказать, что эти задачи довольно просты и направлены только на то, чтобы вы ближе познакомились с синтаксисом и привыкли к нему.

### Наследники

Опишите класс `Student`, у которого есть возраст, имя, принадлежность к ВУЗу.
Опишите также класс `Person`, у которого есть возраст и имя.
Опишите класс `Employee`, у которого есть возраст, имя, зарплата и наименование ВУЗа, который он закончил.

Попробуйте связать все три класса в иерархию, постарайтесь избежать дублирования кода.

> При этом не забудьте про [правильное оформление](../start/code_style.md) вашего кода.

## Остерегайтесь

Остерегайтесь опасной практики, когда один класс становится ответственен за большое количество задач.

Очень часто начинающие разработчики на `Java` объявляют у класса большое количество методов и атрибутов, которые не относятся к классу.

Например, класс `MailSender`, ответственный за рассылку писем, становится ответственен еще и за проверку, за добавление или удаление заголовков у рассылаемых писем.

Такой код будет работать, но это плохая практика. Старайтесь разносить разные области ответсвенности по разным классам.

Здесь можно руководствоваться принципом - пусть класс делает что-то одно, но делает это хорошо, чем когда он делает много задач, но делает все плохо.

Пусть `MailSender` будет ответственен только за рассылку писем, а за проверку будет ответственен другой класс, также как и за добавление/удаление заголовков.

Старайтесь думать над тем, как разбить вашу большую задачу на составляющие.

Выделяйте области ответственности и **делегируйте** их разным классам.

Для более подробного ознакомления с принципами, которые помогут вам писать более правильно читайте [здесь](../oop/SOLID.md)