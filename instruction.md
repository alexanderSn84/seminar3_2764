# Инструкция по работе с системой контроля версий Git

Имя пользователя нужно, чтобы привязывать коммиты к имени. Это не то же самое, что имя пользователя учётной записи GitHub, с помощью которого выполняется вход в профиль на GitHub. Задать или изменить имя пользователя можно с помощью команды **git config**. Новое имя будет автоматически отображаться в последующих коммитах, отправленных на GitHub через командную строку. Если хотите скрыть своё реальное имя, можно использовать в качестве имени пользователя Git произвольный набор символов.

    *git config --global user.name "Alexander"*

    *git config --global user.email "alfasnig84@gmail.com"*

    *git --version*

![gitpro](https://git-scm.com/images/progit2.png)

## Инициализация репозитория

Для создания нового репозитория используется команда **git init**. Команду **git init** выполняют только один раз для первоначальной настройки нового репозитория. Выполнение команды приведет к созданию нового подкаталога .git в рабочем каталоге. Кроме того, будет создана новая главная ветка.

    *git init*

## Проверка состояния репозитория

Команда **git status** отображает состояние рабочего каталога и раздела проиндексированных файлов. С ее помощью можно проверить индексацию изменений и увидеть файлы, которые не отслеживаются Git.

    *git status*
    
## Добавления версионности

| Наименование | Описание |
| -- | -- |
| git add .\instruction.md | Добавить отдельный файл в область подготовленных файлов можно параметром add с указанием имени файла. |
| git add . | Добавить все файлы и папки в эту область, предоставив wildcard . вместо имени файла |

## Сохранение изменений

При создании коммита в репозитории можно добавить однострочное сообщение с помощью параметра **commit** с флагом **-m**. Само сообщение вводится непосредственно после флага, в кавычках.

    *git commit -m "Добавил заголовок файла"*

Также можно открыть текстовый редактор в терминале для написания полного сообщения коммита. Оно может состоять из нескольких строк текста, в котором подробно характеризуются изменения, внесённые в репозиторий.

    *git commit*

## История изменений

Команда отображает зафиксированные снимки. Он позволяет вам просматривать историю проекта, фильтровать ее и искать конкретные изменения. Хотя *git status* позволяет проверять рабочий каталог и промежуточную область, **git log** работает только с зафиксированной историей.

    *git log*

## Переключение между сохранениями

Для работы нужно указать не только интересующий вас коммит, но и вернуться в тот, где работаем, при помощи команды **git checkout master**.

    *git checkout*

## Сравнение версий

| Наименование | Описание |
| -- | -- |
| git diff | Можно просматривать список изменений, внесённых в репозиторий, используя параметр diff. По умолчанию отображаются только изменения, не подготовленные для фиксации. |
| git diff --staged | Для просмотра подготовленных изменений необходимо добавить флаг --staged. |
| git diff instruction.md | можно указать имя файла как параметр и просмотреть изменения, внесённые только в этот файл |

## Ветвление

git branch — создание, перечисление и удаление веток
Работа с ветками — очень легкая процедура в git, все необходимые механизмы сконцентрированы в одной команде.

Просто перечисляет существующие ветки, отметив активную:

    git branch

Создаёт новую ветку new-branch:

    git branch new-branch

Удаляет ветку, если та была залита (merged) с разрешением возможных конфликтов в текущую:

    git branch -d new-branch

Удаляет ветку в любом случае:

    git branch -D new-branch

Переименовывает ветку:

    git branch -m new-name-branch

Показывывает те ветки, среди предков которых есть определенный коммит:

    git branch --contains v1.2

Показывает коммит ответвления ветки new-name-branch от ветки master:

    git merge-base master new-name-branch

## Слияние веток

Для слияния 2 веток git репозитория используйте git merge .

Полезные параметры для git merge:

--squash — Создать один коммит вместо выполнения слияния. Если есть конфликт на ветках, то после его устранения на ветке прибавится 2 коммита (коммит с сливаемой ветки + коммит слияния), но указав этот аргумент прибавится только один коммит (коммит слияния).

-X [strategy] — Использовать выбранную стратегию слияния.
--abort — Отменить выполнение слияния.
