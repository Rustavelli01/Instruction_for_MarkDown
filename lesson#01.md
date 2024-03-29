# Команды для Git-a
## Создать новый репозиторий
* git init создать новый проект в текущей директории
* git init folder-name # создать новый проект в указанной директории

* git log    ( git log --oneline)
* git commit   (-m ""  -am "")
* git checkout 
## Просмотр изменений
* git status              # показать состояние репозитория (отслеживаемые, изменённые, новые файлы и пр.)

* git diff                # сравнить рабочую директорию и индекс (неотслеживаемые файлы ИГНОРИРУЮТСЯ)
* git diff --color-words  # сравнить рабочую директорию и индекс, показать отличия в словах (неотслеживаемые файлы ИГНОРИРУЮТСЯ)
* git diff index.html     # сравнить файл из рабочей директории и индекс
* git diff HEAD           # сравнить рабочую директорию и коммит, на который указывает HEAD (неотслеживаемые файлы ИГНОРИРУЮТСЯ)
* git diff --staged       # сравнить индекс и коммит с HEAD
* git diff master feature # посмотреть что сделано в ветке feature по сравнению с веткой master
* git diff --name-only master feature # посмотреть что сделано в ветке feature по сравнению с веткой master, показать только имена файлов
* git diff master...feature # посмотреть что сделано в ветке feature с момента (коммита) расхождения с master
## Добавление изменений в индекс
* git add .        # добавить в индекс все новые, изменённые, удалённые файлы из текущей директории и её поддиректорий
* git add text.txt # добавить в индекс указанный файл (был изменён, был удалён или это новый файл)
* git add -i       # запустить интерактивную оболочку для добавления в индекс только выбранных файлов
* git add -p       # показать новые/изменённые файлы по очереди с указанием их изменений и вопросом об отслеживании/индексировании

## Удаление измненеий индекса 
* Git reset убрать из индекса все добавленные в него изменения (в рабочем директории все изменения сохраняются). Антипод git add
* Git reset readmi.txt - убрать из индекса изменения указанного файла (в рабочем директории изменения сохраняются)

## Отмена изменений 
* Git checkout text.txt ОПАСНО: отменить зменения в файле, вернуть состояние файла, имеющееся в индексе
* Git reset --hard - ОПАСНО: отменить изменения; Вернуть то, что в комите, на который указывает HEAD (незакомиченные изменения удалены из индекса и из рабочей директории, неотслживаемые файлы остануться на месте)
* Git clean -df - удалить неотслеживаемые файлы и директории

## Коммиты 
* git commit -m - зафиксировать в комите проиндексированные изменения(закомитить), добавить сообщения
* git commit -a -m - проиндексировать отслеживаемые файлы(ТОЛЬКО отслеживаемые файлы, но НЕ новые файлы) и закомитить, добавить сообщение

## Отмена коммитов и перемещение по истории
### Все коммиты, которые уже были отправлены в репозиторий ,должны замениться новыми комитами(git revert), что бы избежать проблем со старыми рпазработками у других участников проекта

* git revert HEAD --no-edit    # создать новый коммит, отменяющий изменения последнего коммита без запуска редактора сообщения
* git revert b9533bb --no-edit # то же, но отменяются изменения, внесённые коммитом с указанным хешем (b9533bb)
## Ветки
показать список веток
```sh
 git branch 
 ```   
 показать список веток и последний коммит в каждой         
```sh

git branch -v 
```
создать новую ветку с указанным именем на текущем коммите
   ```sh
git branch new_branch 
```

 создать новую ветку с указанным именем на указанном коммите
 ```sh
 git branch new_branch 5589877 
```
``` sh git branch -f master 5589877  # переместить ветку master на указанный коммит
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

перемещение по веткам
```sh
git checkout <имя ветки>
```

отображение всех веток
```sh
git branch
```
>>>>>>> new_file
