<h1>GIT</h1>

- [Что такое Git и GutHub?](#что_такое_git_и_guthub)
- [Установка Git на компьютер](#установка_git_на_компьютер)
  - `git --version`
- [Создание репозиториев на GitHub](#создание_репозиториев_на_GitHub)
  - `git clone [url your repository]`
- [Инициализация проектов через Git](#инициализация_проектов_через_git)
  - `git init`
  - `git remote add origin [url your repository]`
  - `git remote rm origin`
  - `git remote -v`
- [Команда git config](#команда_git_config)
  - `git config`
  - `git config user.name`
  - `git config user.email`
  - `git config user.name "[your name]"`
  - `git config user.email "[your email]"`
- [Отправка изменений с компьютера на удаленный репозиторий](#отправка_изменений_с_компьютера_на_удаленный_репозиторий)
  - `git status`
  - `git add .`
  - `git commit -m "[your comment]"`
  - `git log`
  - `git log --oneline`
  - `git push [repository_link] [branch_name]`
  - `git branch`
- [Основные команды Git](#основные_команды_git)
  - `git reset [name_file]`
  - `git diff`
  - `git reset --hard`
- [Игнорирование файлов (.gitignore)](#игнорирование_файлов_gitignore)
- [Работа с ветками (создание, удаление)](#работа_с_ветками_создание_удаление)
  - `git branch [name_branch]`
  - `git branch -d [name_branch]`
  - `git checkout [name_branch]`
- [Слияние веток при помощи действия pull request](#слияние_веток_при_помощи_действия_pull_request)
  - `git pull [repository_link] [branch_name]`
- [Слияние веток при помощи команды git merge](#слияние_веток_при_помощи_команды_git_merge)
  - `git merge [branch_name]`
- [Решение конфликтов при слиянии веток](#решение_конфликтов_при_слиянии_веток)
  - `Accept Current Change`
  - `Accept Incoming Change`
  - `Accept Both Changes`
- [Процесс работы с репозиторием по методике GitFlow](#процесс_работы_с_репозиторием_по_методике_gitflow)
- [Создание SSH-ключа](#создание_ssh_ключа)
  - `ssh-keygen -o`
  - `cat [link_ssh_key]`
- [Добавление ключа в GitHub аккаунт](#дбавление_ключа_в_github_аккаунт)
  - `ssh add [link_ssh_key]`

---

<h2 name='что_такое_git_и_guthub'>Что такое Git и GutHub?</h2>

**GIT** - система контроля версий.

**GIT** даёт возможность разработчикам:
  - отслеживать изменения в файлах;
  - работать над одним проектом совместно с коллегами;
  - и др.

**GutHub** - облочное хранилище проектов (онлайн-хостинг репозиториев).

**GutHub** дает возможность разработчикам:
  - размещать проекты в облачном хранилище;
  - делиться написанным кодом с другими разработчиками;
  - ограничивать доступ к проекту (репозиторию);
  - и др.

<h2 name='установка_git_на_компьютер'>Установка Git на компьютер</h2>

[Установка Git](https://git-scm.com/downloads)

 - `git --version` - версия git

<h2 name='создание_репозиториев_на_GitHub'>Создание репозиториев на GitHub</h2>

---
>TODO - картинки создания репозитория на GitHUB

---

 - `git clone [url_your_repository]` - клонирование репозитория созданного на GitHub в компьютер ***[url your repository] заменить на ссылку своего репозитория***

  > Проверить все файлы установленные в нашем проекте, так же скрытые. В cmd команда (Windows) `ls ; ls -Hidden` или (Linux, MacOS) `ls -a` покажет скрытые файлы.

<h2 name='инициализация_проектов_через_git'>Инициализация проектов через Git</h2>

  - Создать папку проекта на компьютере.

  - `git init` - инициализация git в проекте.

  - Создать репозиторий на GitHub.

  - `git remote add origin [url_your_repository]` - привязать свой локальный проект к созданному репозиторию на GitHub ***[url your repository] заменить на ссылку своего репозитория***

  - `git remote rm origin` - отвязать локальный проект от репазитория на GitHub

  - `git remote -v` - проверить привязку проекта к удалённому репозиторию

<h2 name='команда_git_config'>Команда git config</h2>

  - `git config` - список параметров используемые с командой `config`
  
  - `git config user.name` - имя разработчика проекта

  - `git config user.email` - почта разработчика проекта

  - `git config user.name "[your_name]"` - изменить имя разработчика проекта ***[your name] заменить на свой name***

  - `git config user.email "[your_email]"` - изменить почту разработчика проекта ***[your email] заменить на свой email***
  
  > Команда `git config` очень важна, потому что любые изменения которые вы делаете в реперпозитории они привязаны к вашему имени и к вашему email. Это позволяет отслеживать какой разработчик какие изменения сделал. Обязательно перед началом разработки проверяйте что у вас хранится в `git config user.name` и `git config user.email`.

<h2 name='отправка_изменений_с_компьютера_на_удаленный_репозиторий'>Отправка изменений с компьютера на удаленный репозиторий</h2>

  - `git status` - просмотр в каких файлах были произведены изменения

  - `git add .` - добавить ВСЕ файлы для записи (добавить в stage)

  - `git commit -m "[your_comment]"` - записать изменения ***[your commit] заменить на ваш комментарий***

  > Комментарий должен отображать ту работу которую вы проделали.

  - `git log` - посмотреть запись (commit) с нужным комментарием (-m 'comment')

  - `git log --oneline` - посмотреть краткую запись команды `git log`

  -  `git push [repository_link] [branch_name]` - отправка изменений на удалённый репозиторий. ***[repository_link] заменить на url удалённого репозитория (или origin), [branch_name] заменить на название ветки проекта куда отправлять изменения***

  - `git branch` - просмотр всех созданных веток

<h2 name='основные_команды_git'>Основные команды Git</h2>

  - `git reset [name_file]` - удалить файлы из промежуточной области (stage). ***[name_file] заменить на название файла который ходим удалить из stage*** 

  - `git diff` - позволяет увидеть изменённые, удалённые или добавленные строки кода в файле сравнивая с прошлым сохранением (commit).

  > `q` - выход из лога git.

  - `git reset --hard` - отменяет все изменения в коде разработки возвращая файл к commit-у в котором ещё не сделаны изменения.

<h2 name='игнорирование_файлов_gitignore'>Игнорирование файлов (.gitignore)</h2>

 - [`.gitignore`](https://www.atlassian.com/ru/git/tutorials/saving-changes/gitignore) - файл с таким расширением даёт понять git, какие папки или расширения игнорировать (не записывать изменения) в git

`build`, `node_modules`, `.env`, `.idea` - частые папки и расширения добавляемые в файл.

<h2 name='работа_с_ветками_создание_удаление'>Работа с ветками (создание, удаление)</h2>

   - `git branch [name_branch]` - создание новой ветки от ветки на которой мы сейчас находимся (`git branch`). ***[name_branch] заменить на название новой ветки***

   - `git branch -d [name_branch]` - удаление выбранной ветки. ***[name_branch] заменить на название ветки которую хотим удалить***

  - `git checkout [name_branch]` - выбор ветки на которую хотим перейти. ***[name_branch] заменить на название ветки на которую хотим перейти***

<h2 name='слияние_веток_при_помощи_действия_pull_request'>Слияние веток при помощи действия pull request</h2>

  - `git pull [repository_link] [branch_name]` - скачивает изменения с удалённого репозитория. ***[repository_link] заменить на url удалённого репозитория (или origin), [branch_name] заменить на название ветки***

<h2 name='слияние_веток_при_помощи_команды_git_merge'>Слияние веток при помощи команды git merge</h2>

  - `git merge [branch_name]` - слияние двух веток. Переместить код с `[branch_name]` в ветку которая сейчас выбрана `git branch`. ***[branch_name] заменить на название ветки***

<h2 name='решение_конфликтов_при_слиянии_веток'>Решение конфликтов при слиянии веток</h2>

Изменения ветки в которую хотим добавить изменения отображаются **зелёным цветом**.

Изменения которые приходят с ветки которую хотим слить с текущей ветки отображаются **синим цветом**.

  - `Accept Current Change` - оставить изменения текущей ветки (зелёный цвет)
  - `Accept Incoming Change` - принять изменения входящей ветки (синий цвет)
  - `Accept Both Changes` - принять и оставить оба варианта

<h2 name='процесс_работы_с_репозиторием_по_методике_gitflow'>Процесс работы с репозиторием по методике GitFlow</h2>

<h2 name='создание_ssh_ключа'>Создание SSH-ключа</h2>

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/1%20%D1%81%D0%BE%D0%B7%D0%B4%D0%B0%D1%91%D0%BC%20%D0%BD%D0%BE%D0%B2%D1%8B%D0%B9%20%D1%80%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D0%B9.png" width="500">

> Рис.1 **"Создаём новый репозиторий"**

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/2%20%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%B0%D0%B8%D0%B2%D0%B0%D0%B5%D0%BC%20%D1%80%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D0%B9.png" width="500">

> Рис.2 **"Называем, настраиваем на приватный, добавляем файл README.md"**

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/4%20ssh-keygen%20-o.png" width="500">

> Рис.3 **"Создаём ssh ключ"**

  - `ssh-keygen -o` - создание ssh ключа

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/5%20%D1%81%D0%BE%D1%85%D1%80%D0%B0%D0%BD%D0%B5%D0%BD%D0%B8%D0%B5%20ssh%20%D0%BA%D0%BB%D1%8E%D1%87%D0%B0%20%D0%BD%D0%B0%20%D0%BA%D0%BE%D0%BC%D0%BF%D1%8C%D1%8E%D1%82%D0%B5%D1%80.png" width="900">

> Рис.4 **"Сохраняем ssh ключ"**

По умолчанию предлагают сохранить ключ в файле под именем *id_rsa*. Мы можем заменить это на своё имя. Назовём файл именем удалённого репозитория.

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/6%20%D0%B7%D0%B0%D0%B4%D0%B0%D1%82%D1%8C%20%D0%BF%D0%BE%D1%80%D0%BE%D0%BB%D1%8C%20%D0%B4%D0%BB%D1%8F%20%D0%BA%D0%BB%D1%8E%D1%87%D0%B0.png" width="900">

> Рис.5 **"Создаём пороль для файла хронящего ssh ключ"**

Пороль можно не создавать если в этом нет необходимости. Просто прожми enter. 

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/7%20%D0%BA%D0%BB%D1%8E%D1%87%20%D1%81%D0%BE%D0%B7%D0%B4%D0%B0%D0%BD%20%D0%B8%20%D1%81%D0%BE%D1%85%D1%80%D0%B0%D0%BD%D1%91%D0%BD.png" width="900">

> Рис.6 **"Сохранили файл с расширением .pub"**

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/8%20%D0%BF%D1%80%D0%BE%D1%81%D0%BC%D0%BE%D1%82%D1%80%20%D1%81%D0%BE%D0%B4%D0%B5%D1%80%D0%B6%D0%B8%D0%BC%D0%BE%D0%B3%D0%BE%20%D0%BA%D0%BB%D1%8E%D1%87%D0%B0.png" width="900">

> Рис.7 **"Просмотр содержимого файла .pub"**

  - `cat [link_ssh_key]` - просмотр shh ключа. ***[link_ssh_key] заменить на ссылку где сохранён ssh ключ***

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/9%20%D0%BA%D0%BE%D0%BF%D0%B8%D1%80%D1%83%D0%B5%D0%BC%20ssh%20%D0%BA%D0%BB%D1%8E%D1%87.png" width="900">

> Рис.8 **"Копируем ssh ключ для github"**

<h2 name='дбавление_ключа_в_github_аккаунт'>Добавление ключа в GitHub аккаунт</h2>

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/10%20%D0%B7%D0%B0%D1%85%D0%BE%D0%B4%D0%B8%D0%BC%20%D0%B2%20%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B8%20%D0%BD%D0%B0%20github.png" width="200">

> Рис.9 **"Заходим в настройки github своего аккаунта"**

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/11%20%D0%B2%D1%8B%D0%B1%D0%B8%D1%80%D0%B0%D0%B5%D0%BC%20ssh%20and%20gpg%20keys%20%D0%B8%20new%20ssh%20key.png" width="700">

> Рис.10 **"Выбираем пункт 'ssh and gpg keys' и нажимаем 'new ssh key'"**

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/12%20%D1%81%D0%BE%D1%85%D1%80%D0%B0%D0%BD%D1%8F%D0%B5%D0%BC%20%D0%BA%D0%BB%D1%8E%D1%87%20%D0%BD%D0%B0%20github.png" width="500">

> Рис.11 **"Задаём имя ключа на github и вставляем сам ключ"**

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/13%20%D0%B4%D0%BE%D0%B1%D0%BE%D0%B2%D0%BB%D1%8F%D0%B5%D0%BC%20ssh%20%D0%BA%D0%BB%D1%8E%D1%87%20%D0%BA%20%D0%BB%D0%BE%D0%BA%D0%B0%D0%BB%D1%8C%D0%BD%D0%BE%D0%BC%D1%83%20%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82%D1%83.png" width="900">

> Рис.12 **"Добавляем ключ на компьютер куда собираемся склонировать удалённый приватный репозиторий"**

  - `ssh add [link_ssh_key]` - добовление ssh ключа на компьютер куда планируем клонировать удалённый репозиторий. Нужно будет ввести пороль если при сохронении его задавали. ***[link_ssh_key] заменить на ссылку где сохранён ssh ключ без расширения файла .pub***

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/3%20%D0%BA%D0%BE%D0%BF%D0%B8%D1%80%D1%83%D0%B5%D0%BC%20%D1%81%D1%81%D1%8B%D0%BB%D0%BA%D1%83%20%D0%B4%D0%BB%D1%8F%20%D0%BA%D0%BB%D0%BE%D0%BD%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D1%8F%20%D1%80%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D1%8F.png" width="500">

> Рис.13 **"Копируем ссылку для клонирования удалённого репазитория"**

> <img src="https://github.com/SuvStreet/Totorial-Front-end/blob/main/assets/git/create%20ssh%20key/14%20%D0%BA%D0%BB%D0%BE%D0%BD%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5%20%D0%BF%D1%80%D0%B8%D0%B2%D0%B0%D1%82%D0%BD%D0%BE%D0%B3%D0%BE%20%D1%80%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D1%8F.png">

> Рис.14 **"Клонируем приватный репозиторий"**
