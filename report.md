# Отчёт о тестировании Credit Card Number Validator

## Краткое описание

20.08.2020 - 21.08.2020 было проведено тестирование установки и тестирование функциональности Credit Card Number Validator.

На тестирование затрачено: 3 часа

## В результате тестирования выявлены следующие дефекты:

1. [Ошибка валидной карты](https://github.com/GubinaIrina/java-1.2/issues/1)



## Описание процесса тестирования

1. Установить и запустить IntelliJ IDEA согласно [Руководство по установке IntelliJ IDEA](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/idea.md)
1. Вставить код в программу

```java
public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}
```

1. Проверить работу этой программы и запускать программу с разными тестовыми данными, меняя номер карты в строке

 String number = "5351719427810741";



## В качестве тестовых данных использовались данные:

1. [Руководство по установке IntelliJ IDEA](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/idea.md)

Приложение установлено под необходимую ОС и запущено
1. [Валидные номера карт](https://www.freeformatter.com/credit-card-number-generator-validator.html)

При вводе номера карты приложение выводит следующее сообщение:

Result is OK



## Тестирование производилось в следующем окружении:

- версия и разрядность ОС: Windows 10, 64-bit

- версия Java: 11.0.8