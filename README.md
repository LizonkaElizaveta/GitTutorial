# Шпаргалка по командам Git

+ [Ввведение](https://github.com/LizonkaElizaveta/GitTutorial/tree/master/#Введение)
+ [Основы Git](https://github.com/LizonkaElizaveta/GitTutorial/tree/master/#Основы-Git)
+ Ветвление в Git
+ Git на сервере
+ Распределенный Git
+ Инструменты Git
+ Настройка Git
+ Git изнутри

## Введение
Git — система управления версиями(СУВ). Главное отличие Git от других СУВ в том, что когда мы фиксируем текущую версию проекта, то Git сохраняет лишь слепок того как выглядят все файлы проекта на текущий момент. Если файл не менялся, то Git не сохраняет файлы снова, а делает ссылку на ранее сохраненный файл.

В Git почти все операции локальные, т.к. вся история проекта хранится локально на компьютере, которую не нужно скачивать с сервера. Когда сохраняется файл, Git вычисляет контрольную сумму и она становится индексом это файла. Механизм, используемый Git для вычисления контрольных сумм, называется SHA-1 хеш.
Это строка из 40 шестнадцатеричных знаков (0-9 и a-f), которая вычисляется на основе содержимого
файла или структуры каталога, хранимого Git.

**Три состояния файлов в Git**

+ Зафиксированное состояние (каталог Git) - файлы уже сохранены в вашей локальной базе.
+ Измененное состояние (рабочий каталог) - файлы, которые поменялись, еще не были зафиксированы.
+ Подготовленное состояние (область подготовленных файлов или индекс) - измененные файлы, отмеченные для включение в следующий коммит. 


**Цикл работы**
1. Изменяем файл в рабочем каталоге.
2. Подготавливаем файлы, добавляя слепки в индекс (указание для Git какие изменения нужно будет закоммитить).
3. Делаем коммит. Слепки сохраняются в каталог Git.


**Настройки**

Первое, что нужно сделать после установки Git - это указать имя пользователя и почту:

```bash
$ git config --global user.name "LizonkaElizaveta"
$ git config --global user.email liza_soft_1313@mail.ru
```
```bash
$ git config --list     # проверить используемые настройки

$ git config {ключ}     # проверить значение конкретного ключа
$ git config user.name

$ git help <команда>    # для получения помощи при использовании Git
$ git help config
 ```
## Основы Git

**Создание репозитория**
```bash
$ git init             # создать новый проект в текущей директории
$ git init folder-name # создать новый проект в указанной директории
```  
**Копирование существующего репозитория**
``` bash
$ git clone [url]
$ git clone git://github.com/schacon/grit.git
```
Команда создает католог с именем grit. Если нужно клонировать репозиторий в другой каталог, то:
``` bash
$ git clone git://github.com/schacon/grit.git FolderName
```
**Определение состояния/изменений файлов**
``` bash
$ git status
# On branch master
nothing to commit (working directory clean)
```
Это означает, что рабочий каталог чистый (в нем нет измененных файлов) и вы находитесь на ветке master. Если добавить новый файл в проект, которого не было раньше, то можно увидить неотслеживаемый (отсутствующий в предыдущем коммите) файл: 
``` bash
$ vim README
$ git status
# On branch master
# Untracked files:
# (use "git add <file>..." to include in what will be committed)
#
# README
nothing added to commit but untracked files present (use "git add" to track)
```
Git не станет явно добавлять этот файл, пока вы явно ему это не укажете.
``` bash
$ git diff            # сравнивает содержимое вашего рабочего каталога с содержимым индекса(посмотреть непроиндексированные изменения)
$ git diff --cached   # сравнивает индексированные изменения с последним коммитом
```
**Добавление новых файлов**
``` bash
git add .        # добавить в индекс все новые, изменённые, удалённые файлы из текущей директории и её поддиректорий
git add README   # добавить в индекс указанный файл (был изменён, был удалён или это новый файл)
```
**Игнорирование файлов**
``` bash
$ cat .gitignore # создается файл .gitignore, где будут хранится перечисленные шаблоны игнорируемых файлов
*.[oa]           # игнорируем файлы, заканчивающие на .о (объектные) и .а (архивные)
*~               # игнорируем файлы, заканчивающие на тильду (временные файлы)
````

**Фиксация  изменений**




