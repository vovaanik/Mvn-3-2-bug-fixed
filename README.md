24 сентября 2020 было проведено автоматическое тестирование JAVA-приложения расчета бонуса новым клиентам.

В работе программы выявлена ошибка, составлен баг-репорт.
Описываемая программа запускалась в оболочке JetBrains\IntelliJ IDEA Community Edition 2020.2.
Действия проводились с использованием метода service.calculate в системе сборки MAVEN.
Проводилось позитивное функциональное тестирование на соответствие ожидаемого результата реальному.

Описание процесса тестирования:
-Загружаем программу AdoptOpenJDK\jdk-11.0.8.10-hotspot
-Загружаем программу JetBrains\IntelliJ IDEA Community Edition 2020.2
-Загружаем программу расчета бонуса из архива по ссылке: bonus-service.zip

Последовательность действий:
1.Открываем скачанный архив как Maven проект.
2.Открываем файлы Main.java и BonusService.java.
3.Запускаем команду Maven : mvn clean compile spotbugs:check
4.Наблюдаем ошибку : [ERROR] Return value of BonusService.calculate(long, boolean) ignored, but method has no side effect [Main] At Main.java:[line 8]

Ожидаемый результат:
30
Process finished with exit code 0

Фактический результат:
[ERROR] Return value of BonusService.calculate(long, boolean) ignored, but method has no side effect [Main] At Main.java:[line 8]

Таким образом, в данной программе обнаружен БАГ, на что составлен соответствующий баг-репорт. 
Ссылка на баг-репорт:https://github.com/vovaanik/Mvn-3-2-bug-fixed/issues/1

ВЫВОД: в коде программы необходимо устранить ошибку, 
то есть вместо наименования переменных ( amount, registered)  в метод service.сalculate нужно ввести конкрентные значения переменных ( 1000_60, true).


Тестирование производилось в следующем окружении:

WINDOWS 10 x 64
Java jdk-11.0.8.10
IntelliJ IDEA Community Edition 2020.2
GIT Version 2.28.0
