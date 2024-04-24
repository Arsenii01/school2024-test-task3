# Тестовое задание для отбора на Летнюю ИТ-школу КРОК по разработке

## Условие задания
Однажды теплым летним вечером вас посетила идея разработать свое расширение для браузера для построения ссылочного графа. Что это означает на практике — ваше расширение активируется на какой-либо web-странице сайта, определяет список уникальных внешних ссылок, после чего повторяет алгоритм для каждой ссылки. Максимальная глубина поиска, визуализация собранных данных и прочие вопросы вы сочли вторичными, а начать решено было с малого — с обходчика страниц, который бы находил уникальные ссылки.

В процессе проектирования вы решили немного упростить ваш mvp и в итоге поставили себе задачу следующим образом: реализовать поиск всех уникальных ресурсов (доменов) в рамках страницы, на которые есть ссылки. При этом, формулируя задачу, вы сделали следующие допущения:
- Доменом считается запись вида example.com;
- Поддомен, например, sub.example.com,  считается отдельным ресурсом;
- Протокол (при наличии) не имеет значения.

Требования к реализации:
1. Реализация должна содержать, как минимум, одну процедуру (функцию/метод), отвечающую за поиск уникальных ресурсов, и должна быть описана в readme.md в соответствии с чек-листом;
2. В качестве входных данных программа использует реальный html-файл (page.html)	, считав который, начинает выполнять поиск;
3. Процедура (функция/метод) поиска должна возвращать строку в формате json следующего формата:
   - {«sites»: [«mail.ru», «rbc.ru», «ria.ru»]}
4. Найденные в соответствии с условием задачи домены должны выводиться в нижнем регистре без указания протокола и «www» в алфавитном порядке.

## Автор решения
Мусаилов Арсений Сергеевич
## Описание реализации
Для парсинга всех уникальных доменов с page.html используются регулярные выражения и классы из пакета java.util.regex

Функция findUniqueDomains принимает в качестве параметра путь к html файлу, с помощью составленного паттерна ищет совпадения в заданном файле (при этом html файл читается просто как текст), и добавляет их в множество найденных доменов. После чего задаётся нужный формат json-строки, в которую помещаются все данные, и функция возвращает значение данной строки.
Функция находит домены на всех возможных языках, в том числе на кириллице.

main-метод печатает полученную строку в консоль.

## Инструкция по сборке и запуску решения
Для запуска на машине должна быть установлена Java не ниже версии 1.8.

Находясь в директории проекта, необходимо скомпилировать файл Main.java:
```
javac .\Main.java
```
После чего запустить программу, указав в качестве аргумента путь к html файлу, например:
```
java .\Main.java .\path\to\page.html
```
