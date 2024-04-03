# Инструкция по работе с Гит и удаленными репозиториями

## Что такое ГИТ?
Гит - это одна из реализаций распределенныъ систем контроля версий, имеющая как локальные, так и удаленные репозитории. Является самой популярной реальзацией систем контроля версий в мире.

## Подготовка репозитория
Для создания репозитория необходимо выполнить команду *git init* в папке с репозиторием и у Вас появится репозиторий (появится скрытая папка .git)

## Создание коммитов 

### Git add
Для добавления изменений в коммит используется команда *git add*. Чтобы использовать команду *git add* напишите *git add <имя файла>*

### Просмотр состояния репозитория
Для того чтобы просмотреть состояние репозитория используется команда #git status*. Для этого необходимо в папке   репозиторием написать , и Вы увидите были ли изменения в файлах или их не было.

### Создание коммитов
Добавить коммит в Git можно следующим образом. Для этого необходимо выполнить 2 команды. Первая команда git add -A добавляет все измененные файлы в индекс. А вторая команда создает коммит.

git add -A
git commit -m "Commit message."
Если вам нужно создать коммит, но добавлять в него не все измененные файлы, а только определенные, то при использовании команды git add необходимо указать через пробел добавляемые в индекс файлы. Например: git add goodfile.cpp goodfile.h
git commit -m "Commit message."
![Git commands](https://media.dev.to/cdn-cgi/image/width=1000,height=420,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fi%2Frixan4h4z8y94eq89som.png)

4 Fixes For Git Error: You Need To Resolve Your Current Index First

Git is a powerful version control system that helps developers manage their codebase efficiently. However, like any other tool, it can sometimes encounter errors that need to be resolved. One common error message that Git users may encounter is “You need to resolve your current index first.” This error typically occurs when there are conflicts between the changes in the repository and the changes in the working directory. 

1. Use the Git stash command: The Git stash command allows you to temporarily save your local changes and revert your working directory to the last committed state. To resolve the current index error using Git stash, follow these steps:

Run the command git stash to save your local changes.
After stashing, run git stash drop to remove the saved changes from the stash.
Finally, run git pull to fetch the latest changes from the remote repository.
2. Reset the index to the last commit: If you don’t need your local changes and want to discard them, you can reset the index to the last commit using the following steps:

Run git reset --hard HEAD to reset the index and discard all local changes.
After resetting, run git pull to fetch the latest changes from the remote repository.
3. Resolve conflicts manually: If you want to keep your local changes and manually resolve the conflicts, you can follow these steps:

Use the command git status to identify the files with conflicts.
Open each conflicting file in a text editor and look for the conflict markers (<<<<<<<, =======, and >>>>>>>).
Modify the conflicting lines to resolve the conflicts according to your requirements.
After resolving all conflicts, run git add <file> for each file to mark them as resolved.
Finally, run git commit to create a new commit with the resolved conflicts.
4. Use a merge tool: Git provides several merge tools that can help visualize and resolve conflicts more easily. If you prefer a graphical interface to handle conflicts, you can configure Git to use a merge tool such as KDiff3, P4Merge, or Beyond Compare. To set up a merge tool, follow these steps:

Run git config --global merge.tool <tool-name> to set the desired merge tool.
When conflicts occur, use the command git mergetool to launch the configured tool.
Use the merge tool to manually resolve the conflicts and save the changes.
After resolving all conflicts, run git commit to create a new commit with the resolved conflicts.
## Pictures - Как добавить изображение из файла
Первый способ, как отобразить локальное изображение в markdown документе, это использовать следующий код:

![Текст с описанием картинки](/images/picture.jpg)
Часть в квадратных скобках - это так называемый альтернативный текст, который важен по следующим причинам:

Для доступности. Программы чтения с экрана читают именно его. Например, для тех, кто плохо видит.
Этот текст будет отображаться вместо изображения, если файл изображения не может быть загружен.
Он обеспечивает контекст и описание изображения для поисковых систем, помогая им с поиском.

Часть в круглых скобках - это путь к файлу. Обрати внимание, что перед images стоит /. Без этого символа твой документ может отображаться нормально на твоем компьютере, но после загрузки на сервер в интернете она отображаться перестанет. Это одна из основных причин, почему так случается.

Другой способ, как отобразить локальное изображение в markdown публикации, это использовать тег image в тексте документа:

<image src="/images/picture.jpg" alt="Текст с описанием картинки">
Одним из преимуществ этого способа заключается в том, что так можно использовать дополнительные возможности для контроля изображения. Специфика зависит от ресурса, на котором ты публикуешь документ.
Любой из этих способов даст нужный результат, так что выбор за тобой.
## extra
Работа с локальным репозиторием
Из индекса и дерева проекта одновременно файл можно удалить командой git rm.
Удаляет из индекса и дерева проекта отдельные файлы:

git rm FILE1 FILE2
Хороший пример удаления из документации к git, удаляются сразу все файлы txt из папки:

git rm Documentation/\*.txt
Вносит в индекс все удаленные файлы:

git rm -r --cached .
Сбросить весь индекс или удалить из него изменения определенного файла можно командой git reset:

git reset
Удаляет из индекса конкретный файл:

git reset — EDITEDFILE
Команда git reset используется не только для сбрасывания индекса, поэтому дальше ей будет уделено гораздо больше внимания.