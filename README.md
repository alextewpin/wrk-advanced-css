# Гайд по автоматизации работы с CSS

### Общие замечания

Гайд предназначен для продвинутых верстальщиков и не предназначен для фронтенд-разработчиков. Последние предпочтут более мощные инструменты для сборки, такие как Webpack.

Гайд предполагает работу с консолью. Это легче на nix-системах, включая OS X и сложнее на Windows. Символ `$` означает, что команду нужно ввести в консоль. Сам символ вводить не надо. Запускайте команды из папки проекта.

### Зачем это нужно?

CSS примитивен и с ростом сайта его становится сложно поддерживать. Автоматическая сборка, для сравнения, позволяет:
* Импортировать файлы друг в друга
* Использовать переменные для цветов и размеров
* Вкладывать правила друг в друга
* Расставлять префиксы вроде `-webkit` и `-moz`
* Минифицировать файлы

Автоматизация сборки и знакомство с инструментами разработчиков — первый шаг в перекатывании из верстки в программирование.
 
### Как это работает?
1. Файлы стилей пишутся в специальном синтаксисе, который использует программа [Sass](http://sass-lang.com). Он называется `SCSS`.
2. За файлами следит сборщик, в данном случае [Gulp](http://gulpjs.com). Когда они изменяются, то он проходит по проекту, склеивает `SCSS` вместе, конвертирует их в привычный `CSS` и складывает в другую папку.
3. После отладки запускаем Gulp с другими параметрами и получаем один минифицированный CSS-файл.
4. ...
5. PROFIT!

### Установка окружения

Поставьте на компьютер [Node.js](https://nodejs.org/en/). Это платформа, которая выполняет JavaScript где угодно, в том числе напрямую в ОС. Вместе с Node.js автоматически ставится [npm](https://www.npmjs.com) — менеджер пакетов, который облегчит работу с кучей стронних приложений.

### Установка проекта

Скачайте zip-архив и распакуйте. Продвинутым рекомедую поставить [Git](https://git-scm.com) и разобраться с клонированием репозитория из командной строки.

### Установка модулей

Gulp придется установить глобально, т.е. не в папку проекта, а на всю систему:
```
$ npm install gulp -g
```

После этого поставим остальные зависимости:
```
$ npm install
```

Они установятся в папку node_modules. Здесь это модули для Gulp — они работают с SCSS, расставляют префиксы, минифицируют файлы и т.д.

### Запуск сборки

```
$ gulp
```
Обратите внимание, что даже после сборки Gulp остался висеть в консоли. Теперь он следит за измениями в папке `src` и перезапустит сборку, если ее содержимое изменися.

Собранный проект находится в папке `dev`.
