# Unit Testing, JUnit, Mockito

## Используемые библиотеки

- [junit-jupiter-api](https://mvnrepository.com/artifact/org.junit.jupiter/junit-jupiter-api)
    Назначение: Эта библиотека предоставляет API для написания тестов с использованием JUnit. Она включает в себя аннотации и классы, необходимые для создания тестов.

- [junit-jupiter-engine](https://mvnrepository.com/artifact/org.junit.jupiter/junit-jupiter-engine)
    Назначение: Эта библиотека является основным пакетом для выполнения тестов, написанных с использованием JUnit Jupiter API. Она обеспечивает выполнение тестов и интеграцию с различными инструментами тестирования.

- [mockito-core](https://mvnrepository.com/artifact/org.mockito/mockito-core)
    Назначение: Mockito Core используется для создания макетов (mock) объектов в тестах. Это позволяет изолировать тестируемый код от его зависимостей и проверять взаимодействие между объектами.

### Модульное тестирование (Unit Testing)

Модульные тесты (Unit Tests) предназначены для тестирования наименьших единиц кода, таких как функции, классы или
структуры данных. Основные преимущества модульных тестов заключаются в их скорости и возможности автоматизации проверки
приложения. Помимо модульных тестов существуют интеграционные тесты, которые проверяют взаимодействие нескольких
компонентов системы.

### Методы модульного тестирования

Существует несколько подходов к покрытию кода при модульном тестировании:

- **Тестирование белого ящика**: проверка ввода и вывода через пользовательский интерфейс.
- **Тестирование черного ящика**: проверка поведения различных функций без знания их внутренней реализации.
- **Тестирование серого ящика**: комбинация методов белого и черного ящика для оценки рисков и методов.

### Пирамида Майка Кона

Майк Кон предложил пирамиду автоматизации тестирования, которая помогает командам выбрать оптимальный подход к
автоматизации:

- **Unit tests/Component Tests (Programmer Tests)**
- **API/Service Layer**
- **Business Rules**
- **Functional Tests**
- **Workflow Tests**
- **Through the UI**

### Аннотации JUnit

1. @Test - обозначает метод как тестовый.
2. @BeforeEach - метод выполняется перед каждым тестом.
3. @AfterEach - метод выполняется после каждого теста.
4. @BeforeAll - метод выполняется один раз перед всеми тестами в классе.
5. @AfterAll - метод выполняется один раз после всех тестов в классе.
6. @Disabled - отключает тест или тестовый класс.
7. @DisplayName - задает пользовательское имя для теста или тестового класса.
8. @Nested - позволяет создавать вложенные тестовые классы.
9. @Tag - помечает тесты для фильтрации при выполнении.
10. @Timeout - задает временное ограничение для выполнения теста.
11. @RepeatedTest - позволяет повторять тест несколько раз.
12. @ParameterizedTest - обозначает параметризованный тест.
13. @TestFactory - обозначает метод, который генерирует динамические тесты.
14. @ExtendWith - используется для регистрации расширений.

#### Основные методы класса Assertions

1. assertEquals() - проверяет равенство ожидаемого и фактического значений.
2. assertNotEquals() - проверяет неравенство ожидаемого и фактического значений.
3. assertTrue() - проверяет, что условие истинно.
4. assertFalse() - проверяет, что условие ложно.
5. assertNull() - проверяет, что объект равен null.
6. assertNotNull() - проверяет, что объект не равен null.
7. assertSame() - проверяет, что две ссылки указывают на один и тот же объект.
8. assertNotSame() - проверяет, что две ссылки указывают на разные объекты.
9. assertArrayEquals() - проверяет равенство массивов.
10. assertThrows() - проверяет, что код выбрасывает ожидаемое исключение.
11. fail() - принудительно проваливает тест.
12. assertTimeout() - проверяет, что выполнение кода укладывается в заданный временной лимит.

### Шаги тестирования

1. Разработчик анализирует компонент и его работу, продумывает логику теста.
2. Пишется тест с использованием JUnit, определяются ожидаемые результаты.
3. Тест принимает различные входные данные для проверки компонента.
4. Определяются сообщения об ошибках и порядок выполнения тестов.
5. Тест запускается, проверяются результаты, при необходимости пишутся дополнительные тесты.

### Mockito

Mockito — это популярная библиотека для создания макетов объектов в Java-тестировании. Она позволяет создавать и настраивать макеты объектов для тестов, что упрощает разработку тестов, исключая внешние зависимости.

#### Преимущества Mockito

- **Без ручного написания кода**: разработчикам не нужно писать код макетов.
- **Поддержка возвратных значений**: Mockito поддерживает возврат значений.
- **Безопасное рефакторинг**: тесты не ломаются при изменении методов интерфейсов.
- **Поддержка исключений**: Mockito позволяет обрабатывать исключения.
- **Поддержка аннотаций**: создание макетов с помощью аннотаций.
- **Поддержка порядка вызовов**: проверка порядка вызовов методов.

#### Типы тестовых объектов

- **Заглушки (test stub)**: подменяют внешние зависимости, возвращая заранее определённые результаты.
- **Шпионы (test spy)**: фиксируют обращения к ним для проверки правильности вызовов.
- **Фикции (mock object)**: обладают расширенной функциональностью и заранее заданным поведением.

### Пример использования Mockito

```java
import static org.mockito.Mockito.*;

import java.util.List;

import org.junit.jupiter.api.Test;
import org.mockito.Mockito;

public class MockitoTest {
  @Test
  public void testMockito() {
    List<String> mockedList = mock(List.class);

    when(mockedList.get(0)).thenReturn("first-element");

    System.out.println(mockedList.get(0)); // вывод: first-element
  }
}
```

Этот пример показывает, как создать макет объекта и задать его поведение с помощью Mockito.

### Заключение

Модульное тестирование с использованием JUnit и Mockito является важной частью разработки качественного программного обеспечения. Эти инструменты позволяют автоматизировать тестирование, исключать внешние зависимости и обеспечивать высокую скорость выполнения тестов.
