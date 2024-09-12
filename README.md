Use PyCharm when you work with Git

##Работа с git при создании проекта с нуля
1) Создаем проект
2) /venv/ не трогать!
3) Создаем первый файл (условно main.py)
4) Включаем VCS:
VCS -> Enable Version Control Integration... Git -> OK
5) Создаем файл .gitignore, нажимаем Cancel (не отслеживать)
6) Заполняем .gitignore: /venv/, /.idea/-папка с настройками среды
7) Выделяем нужные файлы и добавляем в VCS (add)
8) Делаем первый комит init
9) Прогоняем тесты
10) Пушим проект на гитхаб, во всплывающем окне указываем ссылку на гитхаб Define remote -> вставка. ОК

##Работа нового сотрудника с проектом
1) Склонировать проект из репозитория
2) Создать викт окр в соотв с ридми
3) Установить reqs.txt
4) Сделать запуск тестов (см.ридми)

###Выполнение первого задания

Вам приходит первый таск в Jira (тикет), например: Создай ф-ю "делить"
1) Создаем ветку (копию мэйна)
2) Называем ветку по стандартам компании
3) Пишем необходимый код
4) Делаем коммит энд пуш (в комменте к комиту указываем номер таски)
5) На github создаем pull request
6) На github-е создается docker-образ и на нем прогоняются более масштабные тесты [Pipeline]
7) Ждем комментариев/лайков от 2-х членов команды и наставника (тимлида)
8) Исправляем недочеты в коде
9) Прогоняем все тесты
10) Делаем комит и пуш
11) ВНОВЬ Ждем комментариев/лайков от членов команды и от наставнка(тимлида)
12) Если все в порядке, тимлид закроет обсуждение конкретного вопроса
13) При необходимости тимлид может открывать любое кол-во обсуждений твоего кода
14) Когда все обсуждения закрыты, тимлид делает squash merge
(При этом все коммиты объединяются в один, после чего происходит merge-слияние)
(После этого ветку, в которой производилась работа над таской, как правило удаляют)

###КОНФЛИКТ ИЗМЕНЕНИЙ

Ситуация: пока мы делали свою таску, некий Вася также изменил файл с которым мы работали, и не просто изменил, но сделал это намного раньше нас, так что его изменения попали в ВЕТКУ МЭЙН на гитхабе.
При этом наша локальная ветка МЭЙН, от которой мы отталкивались в процессе своей работы над таской, оказалась устаревшей. 
При этом мы уже даже могли создать пулл реквест...но гитхаб не даст нам его замерджить, так как укажет, что существует КОНФЛИКТ.
Что делать?
НЕОБХОДИМО "ПОДТЯНУТЬ" НОВЫЙ МЭЙН 
(Подтяни последние правки, подтяни мастер)

###Как подтянуть последние правки

Переходим на локальный компьютер и в пайчарме апдейтим мэйн
Для этого мы выбираем Main в правом нижнем углу и нажимаем update
Теперь нам нужно слить актуальную ветку main с нашей feature-веткой, после чего порешать все конфликты у себя на локальном компе
Merge 'main'[свежий] into 'feature/TIK-003'

### Работа на локале в окне Conflicts

Есть 3 варианта решения:
1) Accept Yours (Принять наши правки, отбросив все что написал Вася) ОПАСНО!
2) Accegt Theirs (Принять его правки, отбросив все что написали мы) ГЛУПО!
3) Merge (Попытаться замерджить)
Двойной щелчок по конфликту покажет нам где именно существует конфликт
Окно Слева		/	Окно по центру	/	Окно справа
(Наш локальный код)	/	Итоговый код	/	(Код Васи)

Разруливаем конфликт, принимая либо свой вариант кода, либо Васин, либо комбинируем наши с ним варианты, либо что-то вообще переписываем заново
Нажимаем Apply (принять)

Теперь прогоняем снова все тесты.
[зеленый шарик справа снизу означает что наша ветка теперь отличается от той, что на гитхабе]
После этого пушим результат нашего разрешения данного конфликта

Далее на гитхабе ждем пока пройдут все тесты (Pipeline должен стать зеленым)
Теперь зовем команду, чтобы она посмотрела и сделала код ревью
Если все ОК, то делаем Squash and merge

Открываем гитхаб
Переходим в ветку main
[Синий шарик справа внизу означает что есть на гитхабе правки, кот нужно подтянуть]
Что мы и делаем.