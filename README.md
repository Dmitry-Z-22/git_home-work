# Мини-курс с шпаргалками по Git

## Как не потеряться
В командной строке вы тоже всегда находитесь в какой-то папке — просто этого не видно. Узнать, где вы сейчас, поможет команда pwd (от англ. print working directory — «показать рабочую папку»). Она выводит путь к текущей .
```
$ pwd
/c/Users/%USERNAME%
/Users/%USERNAME% 
```
С помощью терминала вы всегда можете перейти к домашней директории. Для этого нужно ввести команду cd (от англ. change directory — «сменить директорию») и символ ~ — обозначение домашней директории. Не забудьте про Enter для выполнения.
```
$ cd ~
```
## Вывести содержимое директории — ls
Файловая система компьютера состоит из папок, или директорий. В них могут находиться другие папки и файлы.
Когда вы открываете папку через графический интерфейс операционной системы, вы сразу видите её содержимое. В случае с консолью для отображения файлов и папок используют команду — ls (от англ. list directory contents — «отобразить содержимое директории»).

## Сменить директорию — cd

Следующая важная команда — cd (от англ. change directory — «сменить директорию»). Вы познакомились с ней в прошлом уроке. Она меняет текущую рабочую директорию на ту, которая указана в качестве параметра: cd имя_папки.
```
/projects
    /github
                /open-source-project
    /practicum
                /my-project
```
Допустим, вы находитесь в директории /projects. Если ввести команду cd github, она перенесёт вас в директорию /projects/github.
```
$ pwd
/projects # сейчас мы здесь

$ cd github # переходим в папку github

$ pwd
/projects/github # теперь мы здесь! 
```
Обратите внимание: если в названии папки есть пробелы, при вводе нужно использовать кавычки.
```
$ cd "Фотографии с дня рождения"
```
Чтобы вернуться в родительскую директорию — то есть на уровень выше, — вместо названия папки нужно написать две точки: ...
```
$ pwd
/projects/github # сейчас мы здесь

$ cd .. # переходим на уровень выше

$ pwd
/projects # мы вернулись! 
```
Есть ещё одна команда с точкой. Чтобы обратиться к текущей директории, можно использовать .. Но это нужно довольно редко — например, для запуска скриптов и программ, которые принимают папку в качестве параметра.
```
$ pwd
/projects/github # сейчас мы здесь

$ cd . # переходим в текущую директорию

$ pwd
/projects/github # ничего не поменялось 
```
Также cd позволяет перемещаться сразу через несколько директорий. Для этого нужно разделить их названия знаком /.
```
$ pwd
/projects # сейчас мы здесь

$ cd github/open-source-project # переходим через несколько директорий

$ pwd
/projects/github/open-source-project # переместились сразу в папку open-source-project внутри github
```
## Дополнительные возможности ls
У многих команд консоли есть дополнительные опции. Например, если вы вызовете ls, то увидите список обычных файлов в директории. Но можно вызвать ls с флагом -a и вывести расширенный список. В нём отобразятся все скрытые файлы, которые начинаются с символа . (например, файлы конфигурации). В том числе два особых файла . и .., которые обозначают текущую и родительскую директории.
```
$ ls # вывели список файлов
file.txt
photo.png

$ ls -a # вывели список, в котором отображаются скрытые файлы ., .. и .git
.
..
.git
file.txt
photo.png
```
А ещё, как и другие команды, ls может работать с символом домашней директории (~) и предыдущей директории (..). Например, ls ~ выведет содержимое домашней директории вне зависимости от того, что показывает pwd. А ls .. покажет содержимое родительской директории.

## **Операции с папками и файлами: создание, копирование, перемещение**

## Создание файлов и директорий — touch, mkdir
Чтобы создать файл, нужно ввести в консоль команду touch (англ. «коснуться») с именем файла в качестве параметра: touch %ИМЯ_ФАЙЛА%.
```
$ touch my-new-file.txt # создали файл my-new-file.txt
```
Хорошей практикой при создании файла считается указывать его расширение (в примере — .txt). Это позволит операционной системе выбрать подходящую программу, чтобы открыть файл. А ещё поможет другому человеку понять, какое содержимое находится внутри. 
Для создания директорий через терминал используют другую команду — mkdir (от англ. make directory — «создать директорию»).
```
$ mkdir new-dir # создали директорию new-dir
```
Можно создать целую структуру директорий одной командой с помощью флага -p.
```
$ mkdir -p dir1/dir-inside/dir-deeper-inside
# создали папку dir-deeper-inside в папке dir-inside, которая находится в папке dir1
```
По умолчанию touch и mkdir создают файлы и папки в текущей рабочей директории. Например, если вы находитесь в директории abs, команда touch file.txt создаст файл именно там: abs/file.txt.
Также можно использовать обе команды вместе с символом домашней директории (~) или родительской директории (..). Например, команда mkdir ~/my-git-projects создаст папку my-git-projects внутри домашней директории.
А команда touch ../../file.txt создаст файл file.txt на две папки выше по иерархии. Допустим, если вы находитесь в директории projects/git/hello, команда touch ../../file.txt создаст файл по такому пути: projects/file.txt.

## Копирование файлов — cp
Для копирования файлов через терминал существует команда cp (от англ. copy — «копировать»). В простом виде cp принимает два параметра: что копируем и куда копируем.
```
$ cp что_копируем куда_копируем

$ cp index.html src/
# скопировали index.html в папку src
```
Но можно указать сразу несколько файлов.
```
$ cp что_копируем что_копируем что_копируем куда_копируем

$ cp index.html style.css script.js src/
# скопировали три файла (index.html, style.css и script.js) в папку src
```
Попробуйте вместе с нами! Откройте консоль и создайте папку first-project где угодно на компьютере. Внутри папки создайте два файла: data.txt и table.csv.
```
$ mkdir first-project   
$ touch first-project/data.txt first-project/table.csv
```
Эта запись равноценна поочерёдному вызову следующих команд.
```
$ mkdir first-project  
# создали папку

$ touch first-project/data.txt
# создали первый файл

$ touch first-project/table.csv
# создали второй файл 
```
Теперь скопируйте файл data.txt в домашнюю директорию.
```
$ cd first-project  
# перешли в директорию

$ cp data.txt ~
# скопировали файл в домашнюю директорию
```
Перейдите в домашнюю директорию ~ и посмотрите её содержимое.
```
$ cd ~ # перешли в домашнюю директорию

$ pwd # посмотрели, где мы
/Users/%USER_NAME%

$ ls # файл скопирован, ура!
data.txt
<...>
```
## Перемещение файлов и папок — mv

Копирование создаёт копию файла или папки. Но иногда вместо копии нужно удалить файл в одном месте и создать в другом. Для этого есть команда mv (от англ. move — «переместить»).
Синтаксис команды mv аналогичен синтаксису cp. После имени команды указывают список файлов и папок, которые нужно переместить, а затем — папку, в которую нужно выполнить перемещение.
Создайте папку very-important-files внутри директории first-project. Перейдите в first-project командой cd.
Затем переместите файл table.csv в папку very-important-files и проверьте результат.
```
$ mv table.csv ./very-important-files
# сначала указываем имя файла, который хотим переместить, потом путь — куда перемещаем 

$ cd very-important-files
$ ls
table.csv 
# перешли в папку very-important-files и проверили, что всё сработало
```
## **Операции с папками и файлами: чтение и удаление**

## Чтение файлов — cat
Чтобы прочитать файл, в консоль нужно ввести cat (от англ. concatenate and print — «объединить и распечатать») вместе с именем файла. Команда распечатает то, что содержится в нём.
```
$ cat myfile.txt # распечатали содержимое файла myfile.txt
file-content-1
file-content-2
```
Команда cat работает только с текстовыми файлами. Вывести этой командой файл другого типа (например, изображение) не получится.

## Удаление файлов и папок — rm, rmdir, rm -r

Чтобы удалить файл, нужно напечатать команду rm (от англ. remove — «удалить») и передать ей имя файла.
```
$ rm example.txt # удалили файл example.txt из текущей папки
```
Удалить папку можно командой rmdir (от англ. remove directory — «удалить директорию»). Не забудьте указать имя папки.
```
$ rmdir images # команда удалит папку images из текущей директории, 
               # если папка images пуста
```

Если в папке, которую вы пытаетесь стереть, есть какие-то файлы, то командная строка не удалит её и выведет сообщение о том, что папка не пуста (англ. Directory not empty).

Это защита от случайного удаления нужных файлов. Если папку всё-таки нужно удалить вместе со всем её содержимым, можно использовать команду rm так.

```
$ rm -r images # удалили папку images со всем её содержимым из текущей директории
```

В этом случае команда rm -r (-r — от англ. recursive, «рекурсивный») рекурсивно удаляет файлы и папки. Это значит, что удаление будет последовательно применяться к каждому из элементов в этой папке — пока не сотрёт их все. Затем команда удалит пустую директорию.
Например, есть папка "ФОТО", внутри которой — файлы и папка "Фотографии с дня рождения". Если вызвать команду rm -r для "ФОТО", то сначала будут удалены все файлы и папки внутри неё (в том числе папка "Фотографии с дня рождения"), а после — сама директория "ФОТО".

```
💡 Будьте осторожны: удаление объектов командами rm и rmdir необратимо — в этом случае файлы и папки не попадают в корзину и исчезают навсегда.
```

## **Эффективная работа с командной строкой**

## Выполняйте сразу несколько команд

Команды в терминале необязательно вбивать и выполнять по очереди. Их можно указывать не по одной, а сразу списком. Для этого их нужно разделить двумя амперсандами (&&).
```
$ mkdir second-project && cd second-project && touch index.html style.css
# создаём папку second-project,
# переходим в папку second-project
# и создаём в ней два файла: index.html и style.css
```

## Вызывайте команды из буфера

Допустим, вчера вы создали пять новых файлов, а сегодня решили добавить к ним ещё один, но не можете вспомнить название нужной команды. На этот случай у терминала есть собственная память. Она называется буфером (от англ. buffer — «посредник»). В буфере хранятся все команды, которые вызывались до этого. По их списку можно перемещаться. 
Чтобы обратиться к последней введённой команде, нажмите на клавиатуре стрелку вверх (↑). Если нажать ещё раз, появится предпоследняя команда; ещё раз — предпредпоследняя; и так далее. Чтобы вернуться — например, от предпоследней команды к последней, — нажмите стрелку вниз (↓).

## Используйте автозаполнение

Необязательно заучивать все команды наизусть. Если нужно найти какую-нибудь из них, достаточно вспомнить, с каких букв она начинается. Можно набрать их в командной строке и дважды нажать клавишу Tab. Терминал покажет список всех команд, которые начинаются с этих символов.
Tab автоматически дописывает не только команды, но и пути. Начните печатать имя папки или файла (они должны быть в той же директории) и нажмите Tab. Терминал заполнит имя автоматически.
Если этого не происходит, значит, есть несколько файлов или папок, которые начинаются так же. Нажмите Tab ещё раз, и вы увидите их список. Терминал не знает, как ему дозаполнить такой ввод и что именно выбрать, поэтому показывает все варианты, чтобы вы могли уточнить запрос.
Рассмотрим пример. Перейдём в домашнюю директорию /Users/Username с помощью автозаполнения Tab.

```
$ cd /Users/ # перешли в папку Users

$ cd U[Tab] # ввели первую букву имени пользователя и нажали Tab
# имя папки Username подставится автоматически

$ pwd # теперь проверим, где мы сейчас находимся 
/Users/Username # мы в папке Username!
```
Вместо того чтобы печатать полное имя папки — Username, мы набрали только его первую букву — U, нажали клавишу Tab, и консоль допечатала всё за нас.
Есть ещё один способ использовать Tab при навигации в другую директорию. Если ввести cd с названием папки, а затем нажать Tab, в консоль в качестве подсказки выведутся все возможные пути.

```
$ cd ~/[Tab] # вывели список директорий, чтобы понять, куда переходить
Applications/  Downloads/     Library/       Parallels/     Public/        diagrams/      memes/         python/
Desktop/       Dropbox/       Movies/        Pictures/      bin/           docs/          papers/        tmp/
Documents/     Exercism/      Music/         Postman/       books/         go/            projects/
```

Если вывод будет слишком большой, консоль спросит, нужно ли показать все возможные варианты.

```
$ cd ~/[Tab] 
zsh: do you wish to see all 426 possibilities (429 lines)? # точно хотите увидеть все 426 варианта (429 линий)?
```
Чтобы подтвердить вывод, нужно нажать y, а чтобы отменить автодополнение — n.

## Применяйте команды для быстрой навигации

Напомним основные:
pwd — проверить, где мы находимся;
ls — посмотреть список файлов/папок в директории;
cd — перейти в выбранную папку.
С помощью этих команд можно быстро перемещаться между каталогами и изучать их содержимое.
А ещё можно почти мгновенно перемещаться в ключевые папки. Допустим, вы хотите увидеть содержимое корневой директории (англ. root directory). Это верхняя в иерархии папка, в которой хранится всё, что есть на вашем жёстком диске. Дальнейшие действия зависят от типа операционной системы.
Чтобы попасть в корневую директорию Windows, нужно перейти на соответствующий диск. Например, cd c:/ + Enter или cd /c + Enter.
```
$ cd c:/ # переместились в корневую директорию
$ ls
Documents and Settings/     Windows/
Program Files/              Users/
Program Files (x86)/

# содержимое корневой директории Windows
```

В домашнюю директорию можно попасть так же быстро. Вы уже знаете, как это сделать. Символ «тильда» (~) по умолчанию хранит ссылку на домашнюю директорию. Поэтому, чтобы переместиться в неё, достаточно напечатать ~ и нажать Enter.

```
$ cd ~
$ pwd 
/Users/Username

$ cd ~/Documents # папка Documents хранится в домашней директории
$ pwd
/Users/Username/Documents
```

## **Установка Git**

## Windows

Если вы пользователь Windows, то Git у вас уже есть. Вы установили его в составе пакета Git for Windows вместе с командной строкой.
Убедитесь в этом. Откройте консоль и выполните эту команду.
```
$ git version
```

## **Настройка Git**

## Работа с файлом настройки .gitconfig

Сейчас вы работаете в одиночку, но в дальнейшем вам может понадобиться использовать Git в команде. Чтобы участникам проекта было понятно, кто и какие изменения вносил, нужно представиться и указать имя пользователя и адрес электронной почты.
Вы можете указать любую электронную почту и любое имя. Сделать это можно с помощью команды git config (от англ. configuration — «конфигурация», «настройка») с ключом --global (англ. «глобальный»). При этом не имеет значения, в какой директории вы находитесь прямо сейчас: вызов git config --global сработает везде.
В качестве значения user.name нужно указать своё имя или никнейм. Для настройки параметра user.email указывают электронную почту.
```
$ git config --global user.name "User Namovich" 
# имя или ник нужно написать латиницей и в кавычках

$ git config --global user.email username@yandex.ru
# здесь нужно указать свой настоящий email
```

Все глобальные настройки Git хранит в файле .gitconfig в домашней директории. Команда запишет в этот файл указанные имя и почту. Чтобы убедиться в этом, можно вызвать команду для чтения файлов.
```
$ cat ~/.gitconfig
```
Другой способ проверки — вывести содержимое файла конфигурации Git той же командой git config с флагом --list (англ. «список»).

```
$ git config --list
```
В ответ командная строка покажет текущие значения настроек.
```
user.name=Username
user.email=username@yandex.ru
```

## **Шпаргалка. Базовые команды в консоли**

## Навигация
- pwd (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;
- ls (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;
- ls -a — покажи также скрытые файлы и папки, названия которых начинаются с символа .;
- cd first-project (от англ. change directory, «сменить директорию») — перейди в папку first-project;
- cd first-project/html — перейди в папку html, которая находится в папке first-project;
- cd .. — перейди на уровень выше, в родительскую папку;
- cd ~ — перейди в домашнюю директорию (/Users/Username);
- cd / — перейди в корневую директорию.
## Работа с файлами и папками
### Создание
- touch index.html (англ. touch, «коснуться») — создай файл index.html в текущей папке;
- touch index.html style.css script.js — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;
- mkdir second-project (от англ. make directory, «создать директорию») — создай папку с именем second-project в текущей папке.
### Копирование и перемещение
- cp file.txt ~/my-dir (от англ. copy, «копировать») — скопируй файл в другое место;
- mv file.txt ~/my-dir (от англ. move, «переместить») — перемести файл или папку в другое место.
### Чтение
- cat file.txt (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла file.txt.
### Удаление
- rm about.html (от англ. remove, «удалить») — удали файл about.html;
- rmdir images (от англ. remove directory, «удалить директорию») — удали папку images;
- rm -r second-project (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку second-project и всё, что она содержит.

## Полезные возможности

- Команды необязательно печатать и выполнять по очереди. Можно указать их списком — разделить двумя амперсандами (&&).
- У консоли есть собственная память — буфер с несколькими последними командами. По ним можно перемещаться с помощью клавиш со стрелками вверх (↑) и вниз (↓).
- Чтобы не вводить название файла или папки полностью, можно набрать первые символы имени и дважды нажать Tab. Если файл или папка есть в текущей директории, командная строка допишет путь сама.

Например, вы находитесь в папке dev. Начните вводить cd first и дважды нажмите Tab. Если папка first-project есть внутри dev, командная строка автоматически подставит её имя. Останется только нажать Enter.

```
💡 Команд так много — как их запомнить?
 Терминал — мощный инструмент с практически бесконечным количеством команд и параметров. Не переживайте, если не можете запомнить их все. Использовать поисковики или заглядывать в шпаргалку — абсолютно нормально. Даже специалисты с большим опытом часто обращаются к интернету, чтобы вспомнить вариации той или иной команды.
```
