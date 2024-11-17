# WeLang Interpreter Library
WeLangInterpreter — это библиотека для интерпретации и выполнения программ на языке WeLang. Этот язык поддерживает базовые операции над переменными и регистрами, такие как создание, присваивание, арифметические операции и вывод.

## Установка
Подключение библиотеки

Скачайте файл WeLangLibrary.dll и сохраните его в вашей папке проекта.

В вашем проекте C# добавьте ссылку на DLL:

В VS нажимите на "Зависимости" и создайте там ссылку с WeLangLibary.dll

Добавьте using WeLangLibrary; в начале вашего файла для доступа к функционалу библиотеки.

## Использование
### Пример использования
Пример программы на WeLang, которая создает переменную, задает ей значение, добавляет к ней число, загружает значение в регистр и выводит его:
```
using System;
using WeLangLibrary;

class Program
{
    static void Main()
    {
        var interpreter = new WeLanguageInterpreter();
        interpreter.DebugMode = true; // Включить режим отладки для вывода шагов интерпретации

        string weLangProgram = @"
        var.create myVar
        var.set myVar = '123'
        mov myVar, 10
        add myVar, 5
        load R1 myVar
        print myVar
        ";

        interpreter.ParseAndExecute(weLangProgram);
    }
}
```
Основные команды
var.create <имя>: Создает переменную с указанным именем.
var.set <имя> = '<значение>': Устанавливает строковое значение переменной.
mov <имя>, <значение>: Устанавливает числовое значение переменной.
add <имя>, <значение>: Добавляет числовое значение к значению переменной.
load <регистр> <переменная>: Загружает значение переменной в указанный регистр.
store <переменная> <регистр>: Сохраняет значение регистра в переменную.
print <имя>: Выводит значение переменной на экран.
Встроенные регистры
R1: Доступный регистр, который используется в командах load и store.
## Обработка ошибок
Если в программе есть ошибка, например, если указана несуществующая переменная, интерпретатор выведет соответствующее сообщение об ошибке.

## Режим отладки
Режим отладки можно включить, установив свойство DebugMode в true. В этом режиме интерпретатор будет выводить дополнительные сообщения, описывающие шаги выполнения программы.
```
interpreter.DebugMode = true;
```
## Получение значений переменных
Чтобы получить значение переменной, используйте метод GetVariableValue.

object value = interpreter.GetVariableValue("myVar");
## Лицензия
Эта библиотека распространяется по лицензии MIT.

## Обратная связь
Если у вас есть вопросы или вы хотите внести свой вклад, пожалуйста, создайте issue на GitHub.