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

Начнем с регистрации. Идем по [ссылке](github.com/signup/free) и вводим свои данные.
После регистрации мы попадаем на Dashboard нашего аккаунта.

Cейчас у нас нет ни одного репозитория, и мы можем либо создать новый репозиторий, либо ответвиться (fork) от уже существующего чужого репозитория и вести собственную ветку разработки. Затем, при желании, свои изменения можно предложить автору исходного репозитория (Pull request)

Для создания нового репозитория:
1. Нажимаем на плюсик в верхнем левом углу из меню выбираем New repositiry.
2. В появившимся окне вводим Repository name
3. Выбираем видимость, общий или личный репозиторий и нажимаем create repository
4. Далее нам предлагают настройки для:

* синхронизации локального репозитория с удалённым
* создать новый удалённый репозиторий
* импортировать код из другого репозитория

## Fork

**Fork** - это копия репозитория

С помощью него создается точная копия оригинального репозитория, только в своём аккаунте на сервисе GitHub
В копии репозитория можно вносить свои собственные изменения, редактировать файлы или удалять директории.

Как только все изменения будут внесены, то можно поделиться ими - отправить авторам оригинального репозитория запрос на слияние вашего измененного репозитория с их оригинальным репозиторием. Такой запрос называется **pull request.**

Если авторам оригинального репозитория ваши изменения понравятся, то они могут внести их в свой собственый оригинальный репозиторий - принять запрос и выполнить слияние.

# Команды
git config --global user.name "Your Name" - _указать имя, которым будут подписаны коммиты_

git config --global user.email "e@w.com" -  _указать электропочту, которая будет в описании коммитера_

git config --global color.ui auto — _включить полезную подсветку командной строки._

git config --_global core.autocrlf true - включить преобразование окончаний строк из CRLF в LF_

git init  _создать новый репозиторий в текущей директории_

git init folder-name - _создать новый проект в указанной директории_

git clone адрес репозитория - _клонировать удаленный репозиторий в одноименную директорию_

## Просмотр изменений
git status              # показать состояние репозитория (отслеживаемые, изменённые, новые файлы и пр.)

git diff                # сравнить рабочую директорию и индекс (неотслеживаемые файлы ИГНОРИРУЮТСЯ)

git diff --color-words  # сравнить рабочую директорию и индекс, показать отличия в словах (неотслеживаемые файлы ИГНОРИРУЮТСЯ)

git diff index.html     # сравнить файл из рабочей директории и индекс

git diff HEAD           # сравнить рабочую директорию и коммит, на который указывает HEAD (неотслеживаемые файлы ИГНОРИРУЮТСЯ)

git diff --staged       # сравнить индекс и коммит с HEAD

git diff master feature # посмотреть что сделано в ветке feature по сравнению с веткой master

git diff --name-only master feature # посмотреть что сделано в ветке feature по сравнению с веткой master, показать только имена файлов

git diff master...feature # посмотреть что сделано в ветке feature с момента (коммита) расхождения с master

## Добавление изменений в индекс
git add .        # добавить в индекс все новые, изменённые, удалённые файлы из текущей директории и её поддиректорий

git add text.txt # добавить в индекс указанный файл (был изменён, был удалён или это новый файл)

git add -i       # запустить интерактивную оболочку для добавления в индекс только выбранных файлов

git add -p       # показать новые/изменённые файлы по очереди с указанием их изменений и вопросом об отслеживании/индексировании

## Удаление изменений из индекса
git reset            # убрать из индекса все добавленные в него изменения (в рабочей директории все изменения сохранятся), антипод git add

git reset readme.txt # убрать из индекса изменения указанного файла (в рабочей директории изменения сохранятся)

## Отмена изменений
git checkout text.txt      # ОПАСНО: отменить изменения в файле, вернуть состояние файла, имеющееся в индексе

git reset --hard           # ОПАСНО: отменить изменения; вернуть то, что в коммите, на который указывает HEAD (незакомиченные изменения удалены из индекса и из рабочей директории, неотслеживаемые файлы останутся на месте)

git clean -df              # удалить неотслеживаемые файлы и директории

## Коммиты
git commit -m "Name of commit"    # зафиксировать в коммите проиндексированные изменения (закоммитить), добавить сообщение

git commit -a -m "Name of commit" # проиндексировать отслеживаемые файлы (ТОЛЬКО отслеживаемые, но НЕ новые файлы) и закоммитить, добавить сообщение

## Отмена коммитов и перемещение по истории
Все коммиты, которые уже были отправлены в удалённый репозиторий, должны отменяться новыми коммитами (git revert), дабы избежать проблем с историей разработки у других участников проекта.

git revert HEAD --no-edit    # создать новый коммит, отменяющий изменения последнего коммита без запуска редактора сообщения

git revert b9533bb --no-edit # то же, но отменяются изменения, внесённые коммитом с указанным хешем (b9533bb)

## Временно переключиться на другой коммит

git checkout b9533bb # переключиться на коммит с указанным хешем (переместить HEAD на указанный коммит, рабочую директорию вернуть к состоянию, на момент этого коммита)

git checkout master  # переключиться на коммит, на который указывает master (переместить HEAD на коммит, на который указывает master, рабочую директорию вернуть к состоянию на момент этого коммита)

## Переключиться на другой коммит и продолжить работу с него

Потребуется создание новой ветки, начинающейся с указанного коммита.

git checkout -b new-branch 5589877   # создать ветку new-branch, начинающуюся с коммита c хешем 5589877 (переместить HEAD на указанный коммит, рабочую директорию вернуть к состоянию, на момент этого коммита, создать указатель на этот коммит (ветку) с указанным именем)

## Копирование коммита (перенос коммитов)
git cherry-pick 5589877          # скопировать на активную ветку изменения из указанного коммита, закоммитить эти изменения

git cherry-pick master~2..master # скопировать на активную ветку изменения из master (2 последних коммита)

git cherry-pick -n 5589877       # скопировать на активную ветку изменения из указанного коммита, но НЕ КОММИТИТЬ (подразумевается, что мы сами потом закоммитим)

git cherry-pick master..feature  # скопировать на активную ветку изменения из всех коммитов ветки feature с момента её расхождения с master (похоже на слияние веток, но это копирование изменений, а не слияние), закоммитить эти изменения; это может вызвать конфликт

git cherry-pick --abort    # прервать конфликтный перенос коммитов

git cherry-pick --continue # продолжить конфликтный перенос коммитов (сработает только после решения конфликта)

## История коммитов
git log master             # показать коммиты в указанной ветке

git log -2                 # показать последние 2 коммита в активной ветке

git log -2 --stat          # показать последние 2 коммита и статистику внесенных ими изменений

git log -p -22             # показать последние 22 коммита и внесенную ими разницу на уровне строк

git log --graph -10        # показать последние 10 коммитов с ASCII-представлением ветвления

git log --since=2.weeks    # показать коммиты за последние 2 недели

git log --after '2018-06-30' # показать коммиты, сделанные после указанной даты

git log index.html         # показать историю изменений файла index.html (только коммиты)

git log -5 index.html      # показать историю изменений файла index.html, последние 5 коммитов (только коммиты)

git log -p index.html      # показать историю изменений файла index.html (коммиты и изменения)

git log -G'myFunction' -p  # показать все коммиты, в которых менялись строки с myFunction (в кавычках регулярное выражение)

git log -L '/<head>/','/<\/head>/':index.html # показать изменения от указанного до указанного регулярных выражений в указанном файле

git log --grep fix         # показать коммиты, в описании которых есть буквосочетание fix (регистрозависимо, только коммиты текущей ветки)

git log --grep fix -i      # показать коммиты, в описании которых есть буквосочетание fix (регистроНЕзависимо, только коммиты текущей ветки)

git log --grep 'fix(ing|me)' -P # показать коммиты, в описании которых есть совпадения для регулярного выражения (только коммиты текущей ветки)

git log --pretty=format:"%h - %an, %ar : %s" -4 # показать последние 4 коммита с форматированием выводимых данных

git log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short # мой формат вывода, висящий на алиасе оболочки

git log master..branch_99  # показать коммиты из ветки branch_99, которые не влиты в master

git log branch_99..master  # показать коммиты из ветки master, которые не влиты в branch_99

git log master...branch_99 --boundary -- graph # показать коммиты из указанных веток, начиная с их расхождения (коммит расхождения будет показан)

## Ветки
git branch                 # показать список веток

git branch -v              # показать список веток и последний коммит в каждой

git branch new_branch      # создать новую ветку с указанным именем на текущем коммите

git branch new_branch 5589877 # создать новую ветку с указанным именем на указанном коммите

git branch -f master 5589877  # переместить ветку master на указанный коммит

git branch -f master master~2 # переместить ветку master на 2 коммита назад

git checkout new_branch    # перейти в указанную ветку

git checkout -b new_branch # создать новую ветку с указанным именем и перейти в неё

git checkout -B master 5589877 # переместить ветку с указанным именем на указанный коммит и перейти в неё

git merge hotfix           # влить в ветку, в которой находимся, данные из ветки hotfix

git merge hotfix -m "Горячая правка" # влить в ветку, в которой находимся, данные из ветки hotfix (указано сообщение коммита слияния)

git merge hotfix --log     # влить в ветку, в которой находимся, данные из ветки hotfix, показать редактор описания коммита, добавить в него сообщения вливаемых коммитов

git merge hotfix --no-ff   # влить в ветку, в которой находимся, данные из ветки hotfix, запретить простой сдвиг указателя, изменения из hotfix «останутся» в ней, а в активной ветке появится только коммит слияния

git branch -d hotfix       # удалить ветку hotfix (используется, если её изменения уже влиты в главную ветку)

git branch --merged        # показать ветки, уже слитые с активной

git branch --no-merged     # показать ветки, не слитые с активной

git branch -a              # показать все имеющиеся ветки (в т.ч. на удаленных репозиториях)

git branch -m old_branch_name new_branch_name # переименовать локально ветку old_branch_name в new_branch_name

git branch -m new_branch_name # переименовать локально ТЕКУЩУЮ ветку в new_branch_name

git push origin :old_branch_name new_branch_name # применить переименование в удаленном репозитории

git branch --unset-upstream # завершить процесс переименования

## Временное сохранение изменений без коммита
git stash     # временно сохранить незакоммиченные изменения и убрать их из рабочей директории

git stash pop # вернуть сохраненные командой git stash изменения в рабочую директорию

## Удалённые репозитории
git remote -v              # показать список удалённых репозиториев, связанных с локальным

git remote remove origin   # убрать привязку удалённого репозитория с сокр. именем origin

git remote add origin https://github.com:nicothin/test.git # добавить удалённый репозиторий (с сокр. именем origin) с указанным URL

git remote rm origin       # удалить привязку удалённого репозитория

git remote show origin     # получить данные об удалённом репозитории с сокращенным именем origin

git fetch origin           # скачать все ветки с удаленного репозитория (с сокр. именем origin), но не сливать со своими ветками

git fetch origin master    # то же, но скачивается только указанная ветка

git checkout --track origin/github_branch # создать локальную ветку 

github_branch (данные взять из удалённого репозитория с сокр. именем origin, ветка github_branch) и переключиться на неё

git push origin master     # отправить в удалённый репозиторий (с сокр. именем origin) данные своей ветки master

git pull origin            # влить изменения с удалённого репозитория (все ветки)

git pull origin master     # влить изменения с удалённого репозитория (только указанная ветка)

## Отслеживание файлов
.gitignore — текстовый файл, в котором задаются правила для исключения файлов из репозитория

## Синхронизация изменений
git fetch [bookmark] — загрузить всю историю с заданного удаленного репозитория.

git merge [bookmark]/[branch] — слить изменения локальной ветки и заданной удаленной.

git push — запушить текущую ветку в удаленную ветку.

git push [remote] [branch] — запушить ветку в указанный репозиторий и удаленную ветку.

git push [bookmark] :[branch] — в удаленном репозитории удалить заданную ветку.

git push -u origin master — если удаленная ветка не установлена как отслеживаемая, то сделать ее такой.

git pull — загрузить историю и изменения удаленной ветки и произвести слияние с текущей веткой.

git pull [remote][branch] — указать конкретную удаленную ветку для слияния.

git remote — посмотреть список доступных удаленных репозиториев.

git remote -v — посмотреть детальный список доступных удаленных репозиториев.

git remote add [remote][url] — добавить новый удаленный репозиторий.