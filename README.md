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



## Просмотр истории коммитов и перемещение по ним



## Журнал Изменений



## Работа с удалённым репозиторем



## Ветки в git



## Работа с ветками



# GitHub
## Создание и настройка



## Загрузка и выгрузка репозитория



## Fork



# Команды

