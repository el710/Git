
### Manual 

# How Git helps

*Ничто не возникает само по себе, если нет причины...*

## Причины - решения

> 
**Нам нужно иметь возможность хранить историю разработки и сохранения версий и иметь возможность распараллелить работу в команде.**
>
>>
как вариант - Git. 

Git использует ветви и реперные точки.

Реперная точка (commit) - сохраненное состояние разработки

Ветвь - цепочка комитов сохраненных последовательно друг за другом.

Главная ветвь в git - master, на GitHub - main

HEAD - указатель на активный комит на выбраной ветке

Git работает только с файлами **сохраненными** на диске 


- [ *git --version* ] – **вывод версии git**
```
"а кто-нибудь вообще устанавливал сюда Git, а то у меня склероз..."

$ git --version
git version 2.38.0.windows.1
```
---

# Как указать, какие материалы нам надо отслеживать

- [ *git init* ] - **инициализация репозитория в директории с материалами**
- [ *git add < file1, file2 ... dir/ >* ] – **указание файлов/директории, которые будут отслеживаться в последующих комитах**
```
user: проследите пожалуйста за этой директорией (Папка ушел на работу...)
Git: Хорошо сынок, я устрою себе тут репозиторий.

$ git init
Initialized Git repository in ...

$git add git.md
и тишина...
```
---

# Что сейчас происходит в репозитории

- [ *git status* ] – **вывод состояния**
```
как дела в репозитории?

$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>...
```

- [ *git log* ] – **вывод истории/списка версий**
- [ *git log --oneline* ] – **сокращенный вывод**
- [ *git log --graph* ] - **плюс графика ветвей**

```
ну и что вы тут натворили, пока меня не было?

$ git log
commit a6d435a11e6bd6cfe454f4562f45344a736251e4 (HEAD -> master)
Author:...

$ git log --oneline
296f826 (HEAD -> conclusions, tables, quotes, master, links) fix today master
8e777c2 upgrade merge msater+lists
71b15eb upgrade links develop
b9d129e upgrade links master
103a290 Merge branch 'images'
...
```
- [ *git diff* ] – **вывод изменений между текущим состоянием и последней зафиксированной версией**

```
говоришь ничего не трогал, а это кто наворотил...

$ git diff
diff --git a/git.md b/git.md
index 7640a74..55d614c 100644
--- a/git.md
+++ b/git.md
@@ -133,4 +133,8 @@ Switched to branch 'master'
 $ git diff
```
- [ *git branch* ] – **вывод списка ветвей**
- [ *git branch -all* ] – **вывод списка всех ветвей включая удаленные (GitHub)**

```
$ git branch
* master
```
---
# Как сохранить текущее состояние - создать комит (реперную точку/версию)

- [ *git commit –m “имя”* ] – **зафиксировать версию с новым именем**
- [ *git commit –am “имя версии”* ] -  **фиксация версии со всеми файлами в репозитории, которые уже отслеживались**
  
в комит не включаются файлы, которые никогда не были добавлены *git add ...*
```
теперь добровольцы - комсомольцы

$ git commit -m "комсомольцы"
[master f595b46] комсомольцы
 1 file changed, 9 insertions(+), 1 deletion(-)

___или___

всех под одну…

$ git commit -am "гребенка"
[master a6d435a] гребенка
 2 files changed, 1 insertion(+), 5 deletions(-)
 delete mode 100644 test.md
```
---
# Как подредактировать комит (реперную точку)

- [ *git rebase -i < hash id of version > * ] - **изменить комит**
- [ *git rebase -i --abort* ] - **отменить изменения комита**
- [ *git commit --amend* ] - **изменить метку комита в редакторе**
- [ *git commit --amend -m < новая метка >* ] - **изменить метку комита**
---

# Как создать новую ветку развития
- [ *git branch < branch name >* ] - **создание ветви от текущего комита текущей ветки**
```
$ git branch start_formating
и тишина...
```
---

# Как перейти в нужное состояние (комит)

- [ *git checkout  < hash id of commit >* ] - **переход на комит по hash id**
- [ *git checkout < name of branch >* ] - **переход на последний комит в выбранной ветке**
```
$ git checkout start_formating
Switched to branch 'start_formating'
D       git.md
```
- [ *git checkout < name of branch >^* ] - **возврат на один комит назад в выбранной ветке**
- [ *git checkout < name of branch >~n* ] - **возврат на n комитов назад в выбранной ветке**
- [ *git checkout master* ] - **переход на последний комит основной ветки**

  При *checkout* указатель HEAD смещается на указанный коммит, или на последний комит в указаной ветке

```
сейчас покажу как надо было программировать

$ git checkout a6d4
Note: switching to 'a6d4'.
You are in...

___или___

сынок, не путайся тут со своими правками

$ git checkout master
Switched to branch 'master'

```
---

# Как отменить последние комиты (реперные точки) 

- [ *git reset < hash id of version >* ] - **откат до выбранной версии**
- [ *git reset --hard < hash id of version >* ] - **откат до выбранной версии и откат правок в документе**

  при этом лучше иметь резерв, вдруг придется вернуть...
---

# Как перенести ветку к нужному комиту 

- [ *git branch -f < name of branch > < id commit >~n* ] - **крайним комитом ветки будет комит на n коммитов назад от укзанного**
---

# Как связать локальный репозиторий с репозиторием на GitHub.com

- [ *git remote add origin < html-link >* ] - **связать текущий реп с удаленным**.

  Удаленный реп должен уже существовать на GitHub
```
git remote add origin https://github.com/el710/Git.git
```
-
# Как слить данные с GitHub.com
- [ *git pull < html-link > < branch >* ] - **слить ветку**
- [ *git pull --set-upstream origin master*] - **слить ветку master как основную**

```
$ git pull
remote: Enumerating objects: 36, done.
remote: Counting objects: 100% (32/32), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 18 (delta 9), reused 18 (delta 9), pack-reused 0
Unpacking objects: 100% (18/18), 1.68 KiB | 1024 bytes/s, done.
From https://github.com/el710/p-Csharp
   abdbfb6..d2084b5  master     -> origin/master
Updating abdbfb6..d2084b5
Fast-forward
 arrays/Program.cs             | 2 +-
 online_work/Program.cs        | 4 +---
 task_015 IsWeekend/Program.cs | 2 +-
 task_021 Distance/Program.cs  | 3 +--
 4 files changed, 4 insertions(+), 7 deletions(-)
```
---




*git merge <branch name> - **сливаем выбранную ветку в ту, в которой находимся**
```
$ git merge start_formating
Updating f0097e1..73ad725
Fast-forward
 markdown syntax.md | 13 ++++++++++++-
 1 file changed, 12 insertions(+), 1 deletion(-)
```

*git branch -d|-D <branch to delete>* - **удаление ветки**
```
мягко, когда все сохранено:
$ git branch -d start_formating
Deleted branch start_formating (was 73ad725)

брутально:
$ git branch -D lists
```

файл .gitignore в репозитории содержит перечень файлов
не отслеживаемых git-ом


### По поводу слияния...

при слиянии ветвей бывают конфликты

   При слиянии ветвей различаются данные в одинковых строках документа
   Например:
   ```
   Есть ветка которую ведет Вася.
   
   $ git commit -am "Вася: я доработал раздел про ссылки. Check it out"
   [links 987b6ef] Вася: я доработал раздел про ссылки. Check it out
   1 file changed, 6 insertions(+)
   
   А в это время мастер:

   $ git commit -am "Для Васи: напиши что то типа такого"
   [master e6a08a1] Для Васи: напиши что то типа такого
   1 file changed, 4 insertions(+)

   В день D мастер сливает ветви и

   $ git merge links
   Auto-merging markdown syntax.md
   CONFLICT (content): Merge conflict in markdown syntax.md
   Automatic merge failed; fix conflicts and then commit the result.

   а теперь думаем - кто виноват и что делать... чтоб такого больше не было




   ```
