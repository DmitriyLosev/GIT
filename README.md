# Инструкция по работе с GIT ![Logo](images/logo.jpg "logo")
## Что такое git
Git - это консольная утилита, для отслеживания и ведения истории изменения файлов, в вашем проекте. Чаще всего его используют для кода, но можно и для других файлов. Cистема контроля версий (VCS), которая позволяет отслеживать и фиксировать изменения в коде: вы можете восстановить код в случае сбоя или откатить до более ранних версий.
## Установка GIT

_Установливаем git на своё устройство:_

**Linux** — нужно просто открыть терминал и установить приложение при помощи пакетного менеджера вашего дистрибутива. Для Ubuntu команда будет выглядеть следующим образом:
sudo apt-get install git

**Windows** — мы рекомендуем git for windows, так как он содержит и клиент с графическим интерфейсом, и эмулятор bash. Необходимо скачать программу с сайта, нажимаем [сюда](https://git-scm.com/downloads), выбираем свою операционную систему, загружаем файл и устанавливаем на своё устройство.

**OS X** — проще всего воспользоваться homebrew. После его установки запустите в терминале:
brew install git

## Первоначальная настройка GIT
У гита есть настройка пользователя, от которого будет идти работа. Это разумная и необходимая вещь, так как когда создается коммит, гит берет именно эту информацию для поля Author

В состав Git входит утилита git config, которая позволяет просматривать и настраивать параметры, контролирующие все аспекты работы Git, а также его внешний вид.

Чтобы настроить имя пользователя и пароль для всех проектов, нужно прописать следующие команды:

    git config --global user.name ”Ivan Ivanov”
    git config --global user.email ivan.ivanov@gmail.com

Если вы хотите проверить используемую конфигурацию, можете использовать команду **git config --list**, чтобы показать все настройки
## Создание git репозитория
<img align="right" src="images/repo.jpg">

Чтобы создать новый репозиторий, нам нужно открыть терминал, зайти в папку нашего проекта и выполнить команду **git init**. Это включит приложение в этой конкретной папке и создаст скрытую директорию .git, где будет храниться история репозитория и настройки.
**git status** — это еще одна важнейшая команда, которая показывает информацию о текущем состоянии репозитория: актуальна ли информация на нём, нет ли чего-то нового, что поменялось, и так далее. 
Если нужно скопировать существующий репозиторий, существует команда **git clone**, далее указываем _<адрес репозитория>_.

## Запись изменений в репозиторий

Rаждый файл в вашем рабочем каталоге может находиться в одном из двух состояний: под версионным контролем (_отслеживаемые_) и нет (_неотслеживаемые_). _Отслеживаемые файлы_ — это те файлы, которые были в последнем снимке состояния проекта; они могут быть неизменёнными, изменёнными или подготовленными к коммиту. Если кратко, то отслеживаемые файлы — это те файлы, о которых знает Git.

_Неотслеживаемые файлы_ — это всё остальное, любые файлы в вашем рабочем каталоге, которые не входили в ваш последний снимок состояния и не подготовлены к коммиту. Когда вы впервые клонируете репозиторий, все файлы будут отслеживаемыми и неизменёнными, потому что Git только что их извлек и вы ничего пока не редактировали.

Как только вы отредактируете файлы, Git будет рассматривать их как изменённые, так как вы изменили их с момента последнего коммита. Вы индексируете эти изменения, затем фиксируете все проиндексированные изменения, а затем цикл повторяется.

![Цикл состояния файлов](https://git-scm.com/book/en/v2/images/lifecycle.png)

Основной инструмент, используемый для определения, какие файлы в каком состоянии находятся — это команда **git status**
Для того чтобы начать отслеживать (добавить под версионный контроль) новый файл, используется команда **git add** <имя файла>

Зачастую, у вас имеется группа файлов, которые вы не только не хотите автоматически добавлять в репозиторий, но и видеть в списках неотслеживаемых. К таким файлам обычно относятся автоматически генерируемые файлы (различные логи, результаты сборки программ и т. п.). В таком случае, вы можете создать файл **.gitignore**. с перечислением шаблонов соответствующих таким файлам.

Теперь, когда ваш индекс находится в таком состоянии, как вам и хотелось, вы можете зафиксировать свои изменения. Запомните, всё, что до сих пор не проиндексировано — любые файлы, созданные или изменённые вами, и для которых вы не выполнили git add после редактирования — не войдут в этот коммит. Они останутся изменёнными файлами на вашем диске. В нашем случае, когда вы в последний раз выполняли git status, вы видели что всё проиндексировано, и вот, вы готовы к коммиту. Простейший способ зафиксировать изменения — это набрать команду **git commit -m** "описание ихменений в кавычках"
## Просмотр истории коммитов и перемещение по ним

После того, как вы создали несколько коммитов или же клонировали репозиторий с уже существующей историей коммитов, вероятно вам понадобится возможность посмотреть что было сделано — историю коммитов. Одним из основных и наиболее мощных инструментов для этого является команда **git log**.

* По умолчанию (без аргументов) **git log** перечисляет коммиты, сделанные в репозитории в обратном к хронологическому порядке — последние коммиты находятся вверху.

* Более компактный вид списка коммитов можно получить с помощбю команды **git logg --oneline**

Для переключения на нужный коммит используется команда **git checkout**.
После переключения, все файлы в проекте станут такими, какими они были в данном коммите.
_Пример_

    git checkout _имя коммита_

Имя комита - это хеш (обозначение) коммита, причем можно указывать не весь хеш, а несколько начальных символов хеша

Второй способ, вы можете использовать HEAD (другими словами, ваше текущее положение) в качестве ссылки:

    git checkout HEAD~3
После HEAD указываем на сколько коммитов мы хотим перейти назад

## Журнал Изменений

Для просмотра всей истории всех веток в виде дерева, необходимо ввести команду **git log --graff**

![Пример](https://devblogs.microsoft.com/devops/wp-content/uploads/sites/6/2019/11/git-log-graph-fast.png)
## Работа с удалённым репозиторем

Для того, чтобы внести вклад в какой-либо Git-проект, вам необходимо уметь работать с удалёнными репозиториями. Удалённые репозитории представляют собой версии вашего проекта, сохранённые в интернете или ещё где-то в сети. У вас может быть несколько удалённых репозиториев, каждый из которых может быть доступен для чтения или для чтения-записи. Взаимодействие с другими пользователями предполагает управление удалёнными репозиториями, а также отправку и получение данных из них. Управление репозиториями включает в себя как умение добавлять новые, так и умение удалять устаревшие репозитории, а также умение управлять различными удалёнными ветками, объявлять их отслеживаемыми или нет и так далее.

Для того, чтобы просмотреть список настроенных удалённых репозиториев, вы можете запустить команду **git remote**

 Если вы клонировали репозиторий, то увидите как минимум **origin** — имя по умолчанию, которое Git даёт серверу, с которого производилось клонирование.

 Вы можете также указать ключ -v, чтобы просмотреть адреса для чтения и записи, привязанные к репозиторию:

    git remote -v
Если у вас больше одного удалённого репозитория, команда выведет их все.

Для того, чтобы добавить удалённый репозиторий и присвоить ему имя (shortname), просто выполните команду git remote add <shortname> <url>:
## Получение изменений из удалённого репозитория — Fetch и Pull
Lля получения данных из удалённых проектов, следует выполнить:

    git fetch [remote-name]
Данная команда связывается с указанным удалённым проектом и забирает все те данные проекта, которых у вас ещё нет. После того как вы выполнили команду, у вас должны появиться ссылки на все ветки из этого удалённого проекта, которые вы можете просмотреть или слить в любой момент.

Если ветка настроена на отслеживание удалённой ветки, то вы можете использовать команду **git pull** чтобы автоматически получить изменения из удалённой ветки и слить их со своей текущей. Этот способ может для вас оказаться более простым или более удобным. К тому же, по умолчанию команда **git clone** автоматически настраивает вашу локальную ветку master на отслеживание удалённой ветки master на сервере, с которого вы клонировали репозиторий.

## Отправка изменений в удаленный репозиторий (Push)
Когда вы хотите поделиться своими наработками, вам необходимо отправить их в удалённый репозиторий. Команда для этого действия простая: git push <remote-name> <branch-name>. Чтобы отправить вашу ветку master на сервер origin (повторимся, что клонирование обычно настраивает оба этих имени автоматически), вы можете выполнить следующую команду для отправки ваших коммитов:

    git push origin master
    
Эта команда срабатывает только в случае, если вы клонировали с сервера, на котором у вас есть права на запись, и если никто другой с тех пор не выполнял команду push. Если вы и кто-то ещё одновременно клонируете, затем он выполняет команду push, а после него выполнить команду push попытаетесь вы, то ваш push точно будет отклонён. Вам придётся сначала получить изменения и объединить их с вашими и только после этого вам будет позволено выполнить push.

## Ветки в git

Ветки в git предназначены для введения параллелной работы от основного проекта для тестирования новых параметров или черновой работы. Так же часто используется для совместной работы команды при одновременном создании или внесении изменений.

* Создать ветку нужно с помощью команды **git branch** _имя ветки_
* Переключится на ветку используем команду **git checkout** _имя ветки_
* Создать ветку и сразу перейти на ней можно с помощью команды **git checkout -b**_ имя ветки_
## Работа с ветками

1. Как переименовать ветку

Чтобы переименовать локальную ветку, выполним команду:

    git branch -m <old-name> <new-name>

2. Удаление локальной ветки

Чтобы удалить локальную ветку, выполните одну из команд:

    git branch -d branch_name
    git branch -D branch_name
Флаги:
-D сокращение для —delete –force удаляет ветку независимо от того, слиты ли ее изменения
-d сокращение для —delete

3. Удаление ветки из удаленного репозитория

Чтобы удалить удаленную ветку, можно использовать две записи.
Либо через двоеточие, как мы уже делали при переименовании ветки:

    git push origin :branch_name

Либо с флагом —delete:

    git push origin --delete branch_name

4. Как слить ветки

Cливают некоторую ветку (например, ветку-branch) в ветку master. Для этого сначала перейдем в ветку master (в ту ветку, в которую вливаем изменения) и выпоняем команду **git merge branch_name(имя ветки которую хотим слить)**



    _Слияние веток не всегда происходит гладко, иногда требуется разрешить конфликты вручную. Для этого надо отредактировать конфликтые файлы, выполнить их commit_.

# GitHub
![github](https://habrastorage.org/r/w1560/storage2/145/277/c3e/145277c3ef9795a38135b6718eb7169c.png)

Github позиционируется как веб-сервис хостинга проектов с использованием системы контроля версий git, а также как социальная сеть для разработчиков. Пользователи могут создавать неограниченное число репозиториев, для каждого из которых предоставляется wiki, система issue tracking-а, есть возможность проводить code review и многое другое. GitHub на данный момент является самым популярным сервисом такого рода.

Расположен по адресу [GitHub](https://github.com/)
## Создание и настройка


## Fork



# Команды

