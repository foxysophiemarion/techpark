# Установка шаблона
Следите за тем, чтобы сама папка и её родительские папки не
содержали в названии кириллицу, пробелы, символы # и !
Если вы до этого момента не пользовались сборщиками GULP,
WEBPACK и пакетным менеджером NPM, следует скачать и установить
Node.js. Качайте версию рекомендованную для большинства.
Далее, открываем терминал в этой папке проекта. Терминал может быть
встроен или открыт отдельно от редактора. Рекомендую использовать
терминал GIT Bash.
Если вы до этого момента не пользовались сборщиком GULP введите в
терминал команду __npm i gulp-cli -g__ это установит GULP в систему
глобально.
После завершения установки GULP введите в терминале команду __npm i__

*В процессе установки в терминале могут возникать сообщение с
пометкой __WARN__ на желтом фоне. Эти сообщения можно
игнорировать. Но, если вы получаете сообщение __ERR!__ красным
цветом — это критическая ошибка и её нужно исправлять*

Часто может возникнуть ошибка зависимостей устанавливаемых
пакетов (плагинов), и в NPM выше 7й версии это приводит к
критической ошибке и остановке инсталляции.
Чтобы решить проблему выполните команду __npm i --legacy-peer-deps__,
это запустит процесс установки игнорируя подобные несовместимости.

### После успешной установки, у вас появится папка node_modules и файл package-lock.json


# Запуск шаблона и режимы работы
### Шаблон может выполнять несколько сценариев:

1. Режим разработчика. Команда запуска __npm run dev__
2. Режим продакшена. Команда запуска __npm run build__
3. Режим продакшена и отправка результата на сервер по FTP.
Команда запуска __npm run deploy__
4. Режим продакшена и создание ZIP-архива с результатом. Команда
запуска __npm run zip__
5. Режим продакшена без создания WEBP изображений и действий
связанных с этим форматом. Команда запуска __npm run devbuild__

### Дополнительные команды:
1. Ручное создание SVG спрайта. Команда запуска __npm run sprite__

2. Конвертация шрифтов с принудительной перезаписью файла
стилей. Команда запуска __npm run fonts__

### Режим разработчика
В режиме разработчика выполняются только необходимые для
процесса разработки задачи:

* Конвертация шрифтов и запись в файл стилей
* Конвертация SCSS файлов в CSS файлы, переименование псевдонимов
* Сборка HTML файлов, переименование псевдонимов
* При использовании PUG, файлы преобразовываются в HTML, переименовываются псевдонимы
* Собираются JS файлы
* Запускается локальный сервер, открывается браузер с индексной
страницей.
* Запускается наблюдатель за изменением фалов. При каждом
изменении файла браузер обновляет страницу (кроме страницы-
содержания)
* Копируются файлы из указанной папки
* HTML CSS JS файлы результата не записываются на диск (папка dist не
создается), это увеличивает скорость работы


### Режим продакшена
В режиме продакшена выполняется финализация проекта, а именно:

* Конвертация шрифтов и запись в файл стилей
* Конвертация изображений в WEBP формат. Сжатие и оптимизация
JPG PNG SVG картинок
* Конвертация SCSS файлов в CSS файлы, переименование
псевдонимов, группировка медиа-запросов, добавляются вендорные
префиксы для обеспечения кроссбраузерности, обрабатывается
подключение WEBP изображений, производится сжатие и
оптимизация конечного файла (также создается несжатая копия)
* Сборка HTML файлов, переименование псевдонимов, обрабатывается
подключение WEBP изображений
* При использовании PUG, файлы преобразовываются в HTML,
переименовываются псевдонимы, обрабатывается подключение
WEBP изображений
* Собираются JS файлы, производится сжатие и оптимизация
конечного файла. В результат попадает только используемый код.
Итогом задачи будет создание двух файлов: сжатого app.min.js
(подключен к HTML) и не сжатого app.js для дальнейшего
редактирования другими специалистами.
* Копируются файлы из указанной папки
* Все файлы с результатом записываются на диск (обычно в папку dist),
локальный сервер не запускается




# Запуск в режиме разработчика
__npm run dev__

После запуска система выполнет все задачи режима разработчика
описанные выше. Результатом работы должна стать открытая в
браузере страница содержания.
## Возможные ошибки и их решения

* У вас установлен Node.js и Python последней версии
* Терминал открыт с правами администратора
* В названиях папок на всем пути к проекту нет символа # или !
* Папки и файлы должны быть названы латиницей без пробелов
* Тег img и его содержимое должны быть записаны в одну строку без
переносов
* В атрибуте src должен быть указан путь к существующей картинке без
пробелов

При ошибке связанной с node-sass запустите команду __npm rebuild nodesass__
При ошибке связанной с Python запустите команду __npm install -gwindows-build-tools__

# Подготовка редактора к комфортной работе с шаблоном
## Настройка псевдонимов
Нужно установить плагин __Path Autocomplete__. После установки открываем настройки редактора __(settings.json)__, для этого жмем F1 в редакторе и в строке поиска пишем __Open Settings__ и жмем на ссылку __Open Settings (JSON)__.

В этот файл нужно аккуратно вставить следующий код:
``` 
},
"path-autocomplete.pathMappings": {
"@img": "${folder}/src/img", // alias for images
"@scss": "${folder}/src/scss", // alias for scss
"@js": "${folder}/src/js", // alias for js
},
```

*Важно соблюдать синтаксис JSON, обращайте внимания на
запятые:*

После этого можно использовать псевдонимы при
подключении файлов, например:
```
<img src="@img/bg.webp" alt="Image">
```

# Настройка сниппетов

Сниппеты — это короткие коды которые могут вызывать готовые
заготовки кода любого объема. Это колоссально повышает скорость
разработки.
Чтобы добавить набор сниппетов из шаблона к себе в редактор
выполняем следующие действия:

1) Открываем файл snnipets.txt из архива ЧФ и копируем все
содержимое
2) В редакторе VS Code переходим в настройки (шестеренка) -> User
Snippets ->New Global Snippets File пишем название, например заменяем содержимое на скопированное из snnipets.txt
3) При обновлении шаблона и сниппетов создавать новый файл не
нужно, следует открыть существующий и обновить содержимое




