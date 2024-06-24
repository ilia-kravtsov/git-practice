# Git guide

## Git is...

Git is the version control system which helps to observe all the changes into the project.

## Abbreviations

### Global Abbreviations

Git # _Global Information Tracker_ || _Goddamn Idiotic Truckload_ <br>
VCS # _Version Control System_ <br>
SCM # _Source Control Management_ <br>
GUI # _Graphical User Interface_ <br>
CLI # _Command line Interface_ <br>
SSH # _Secure Shell_ <br>

### Commands Abbreviations

pwd # _print working directory_ <br>
cd # _change directory_ <br>
ls # _list directory contents_ <br>
cd # _change directory_ <br>
mkdir # _make directory_ <br>
cp # _copy_ <br>
mv # _move_ <br>
cat # _concatenate and print_ <br>
rm # _remove_ <br>
rmdir # _to remove directory_ <br>
-r # _recursive_ <br>
git init # _initialize_ <br>
-f # _force_ <br>
-m # _message_ <br>
-v # _verbose_ <br>

## Gitbash download for Windows

[Gitbash](https://git-scm.com/download/win) <br>

## Terminal launching

**Linux** - Ctrl+Alt+T <br>
**macOs** - Cmd+Space then enter - terminal <br>
**Windows** - just launch Gitbash wherever you want <br>

'$' - the program is wating for your commands sir <br>

## Git commands

```
pwd # to know where you are right now

ls # to show the content of the current directory
ls -a # to show the content including the hidden files and folders
ls ~ # to show the content of the home directory
ls .. # to show the content of the parent directory

cd ~ # path to your home directory
cd projects # to go to the projects folder
cd "the best projects ever made" # "" - for spaces in names
cd .. # to go to an above level
cd . # to go to current directory
cd firstFolder/secondFolder/thirdFolder # to go throughout the folder's structure

touch my-new-file.txt # to create new file

mkdir new-dir # to create new directory
mkdir -p dir1/dir-inside/dir-deeper # to create the structure of the folders at once

cp whatCopy whereCopy # to copy
cp index.html style.css script.js src/ # we have copied three files into src folder at once

mv whatMove whereMove # to move
mv table.csv ./src # just an example

cat myfile.txt # to see the content of the file, it works only with text files

rm example.txt # to remove the file
rmdir images # to remove the directory, it works only for empty directories
rmdir -r images # to remove the directory with the content inside

&& # to accomplish several commands at once
mkdir second-project && cd second-project && touch index.html style.css

↑ # the last || next entered command
↓ # previous entered command

Tab # to supplement the entering command

cd ~/[Tab] # to see all the directories in home
cd / # to go to the root directory
cd c:/ # to go to the root directory in Windows
```

## Git installing

### Windows

```
git version # to check if the Git has already been installed
```

### macOS

```
/usr/bin/git # to install
brew install git # to install
```

## Git settings

```
git config --global user.name "your name" # to enter your name
git config --global user.email youremail@yandex.ru # to enter your email
```

All the global settings the Git saves in .gitconfig in the home directory

```
cat ~/.gitconfig # to ensure your global settings
git config --list # to see your global file content (email name)
```

## Create repository

```
git init # to make a repository instead of a folder, in the git folder all the information will be save
rm -rf .git # to make reverse from git init command if you made a mistake
```

if you delete .git folder you will have only your local version of the project

```
git status # to check the condition of the repository
git add --all # to prepare your new || modified files for commit
git add . # to add all the current folder
```

green color of the file - the file is new or git know everything about all the changes in the file <br>
red color of the file - git doesn't know about the file or the file has been modified

```
git commit -m 'description of what changes in the project have done' #  to fix the version of your project
git log # to see all the commits
```

## Github

Github is a platform for storing your projects and its versions and where you can share your project with others or to use the projects of other programmers

## SSH

Computers are sharing data in the network, they follow to different network protocol

Secure Shell Protocol provides the secure sharing of the data in the network

SSH uses two types of the key:
private key and public key

private key # is keeping in your computer it's secret
public key # is available for everybody and it is used for encrypt data

```
ls -la .ssh/ # to see the list of the ssh keys
```

### SSH generation

```
ssh-keygen -t ed25519 -C "your-email-connected to the github" # to create ssh key
ssh-keygen -t rsa -b 4096 -C "your-email-connected to the github" # to create ssh key if you see a mistake after first command
ls -a ~/.ssh # to check if the keys were truly generated
```

.pub # with the public ssh key
no .pub # your little secret

### SSH Github connection

after ssh-keygen command in the directory ~/.ssh will be created to files id_ed25519 and id_ed25519.pub or id \_rsa and id_rsa.pub depends on your previous command respectively

macOS

```
pbcopy < ~/.ssh/id_rsa.pub # to copy key content
pbcopy < ~/.ssh/id_ed25519.pub # for ed25519
```

Windows

```
clip < ~/.ssh/id_rsa.pub # to copy key content
clip < ~/.ssh/id_ed25519.pub # for ed25519
ssh -T git@github.com # to check the accuracy of the ssh key after Github
```

## Linking the local and remote repository

copy your ssh from your repository in Github

```
git remote add origin git@github.com:%accont_name%/first-project.git
```

origin # standard name to connect with the main remote repo

```
git remote -v # to ensure that repoes are connected
if success:
origin    git@github.com:%account_name%/%Project-name%.git (fetch)
origin    git@github.com:%account_name%/%Project-name%.git (push)
```

```
git push -u origin main || master # for the first push
git push # to send the changes into remote repo after commit
```

```
git log --oneline # to get the short version of the log
q # to quite from log watching
```

## Stasuses

untracked || tracked, staged и modified

untracked # git knows about that file but it doesn't watch for its changes

staged # the status of the file after git add . command
staging area also called as index or cache and the status of the file called indexed || cached

tracked # the opposite of the untracked status, the file has tracked status after git commit command and git add . command

modified # means that git has compared the content of the file with the last saved version and found the differences.
For instance, if the file was commited and then changed afte that

it all means that when the file has staged or modified status it is implied that file has tracked status as well

## The classic file way

```
untracked => git add --all || . =>  staged (prepared for commit) + tracked (monitored) => git commit -m 'some commit' => tracked =>
=> changes ? modified : tracked ;

more detailed version:

1. we have created a file, that means that Git doesn't monitor the content of the file, hence it's status is untracked (unmonitored)
2. git add . # means that we have add the file into staging area, thus the file has 'staged' + 'tracked' statuses
Perhaps, we have changed the file again, therefore the file has 'staged' + 'modified' + 'tracked' statuses
Then we must say git add . again in order to convert 'modified' status and receive just 'staged' and 'tracked' statuses
3. git commit -m 'some commit' # the file has 'tracked' status
4. if we have changed our file again, thus we've received 'modified' and 'tracked' statuses
5. git add . to add the file again into staging area, statuses 'staged' and 'tracked'
6. git commit -m 'some commit', statuses: 'tracked'
```

## Use of git status

```
'git status' shows only the following statuses:

'staged' # changes to be committed
'modified' # changes not staged for commit
'untracked' untracked files
```

## Jira

```
Jira # a system for organization projects and tasks

LGS # logistics
239 # task number
git commit -m "LGS-239: "Complement the list with new numbers"

Conventional commits: <type>: <message>

<type> examples:
feat # 'feature' for new functionality
fix # for mistakes correction

for instance:
git commit -m "feat: something new adding"
```

## how to correct the commit

```
--amend # to correct the commite that have already made, it works only with HEAD commit (the latest commit)

git commit --amend

git commit --amend # to complement a commit with new files

touch main.html
touch common.css
git add main.html
git commit -m 'main.html adding'
git add common.css
git commit --amend --no-edit # complementing of the previous commit with the new common.css file --no-edit means that the commit message needs to be save like in initial version

just like that you can add any changes into the file which has already added into commit

git add main.html
git commit --amend --no-edit

So what do we need to choose? a new commit or a new --amend? It depends on the situation

git commit --amend -m 'New message' if you want to add a new message to the commit which has already been made

if you forget to point out the --no-edit or -m flag Git will suggest you to correct the commit manually

^X # means Ctrl+X to save the new message in nano
```

## Returning from staging area to 'untracked'

```
How to implement the 'unstage' of the changes

git restore --staged <file>

you've created and changed some file and added it into staging area with the help of git add but then if you need to return it, to eliminate it you can use:

git restore --staged <file> # to undo the adding into staging area - to send back into 'untracked'

restore means recover

to send back all the files into 'untracked' you can use:

git restore --staged . # roll back all the files in the directory

## Roll back the commit

git reset --hard <commit hash> # to roll back the version of the project to <commit hash> version

for instance:

git log --oneline

7b972f5 (HEAD -> master) style: добавить комментарии, расставить отступы
b576d89 feat: добавить массив Expenses и цикл для добавления трат # вот сюда и вернёмся
4b58962 refactor: разделить analyzeExpenses() на countSum() и saveExpenses()

git reset --hard b576d89

HEAD is now at b576d89 feat: добавить массив Expenses и цикл для добавления трат
```

7b972f5 has just been deleted

## Rolling back the changes which didn't get neither in staging nor into commit

```
git restore <file> # to roll back changes to a file that cannot be changed
```

## Conclude

```
git restore --staged <file> # to return from 'staged' || 'modified' into 'untracked'
git reset --hard <commit hash> # to roll back the history until the hash with <commit hash> number
git restore <file> # to roll back the changes into the file until the last saved version
```

## Watching for the changes into the commits

```
git diff # to see the difference

git diff doesn't show the changes into 'staged files only in 'modified'

to see the changes in 'staged' files you need to use flag --staged

git diff --staged # to see the changes in 'staged'files comparatively to the latest committed versions
```

## Comparing the commits

```
echo 'hello!' # to show on the console what you give it as a parametr
hello!


However with >>

echo 'second line of the file' >> file.txt # it will write the line into the file

$ cat file.txt
Первая строка файла

$ echo "Вторая строка файла" >> file.txt
$ cat file.txt
Первая строка файла
Вторая строка файла

Likewise > will also redirect the out of the command into the file, but it will erase all the content in the file at first.

$ cat file.txt
Первая строка файла
$ echo "Новая строка" > file.txt
$ cat file.txt
Новая строка

git diff eba6256 4577927 # to see the difference between two commits
git diff <the end of the tale> <beginning>
```
## The ingnoring of the files in Git

```
.gitignore files are acceptable only for new untracked files. If the file has already got in the staging area or in the commit, then the rules didn't influence at him

if the line begins with '#' then it's a comment and .gitignore won't consider it

# here is an example of the comment
# it means nothing for the .gitignore file
# but they could be useful to comprehend, why this or that rule was added

.DS_Store # to ignore all the files with the name of .DS_Store

.DS_Store # for macOS

* # corresponds to any line including the empty one

for instance: 

*.jpeg # to ignore all the files which ends in .jpeg

docs/*/tmp # to ignore all the files 'tmp' in all subfolders the docs folder

if you set a rule which consists only of a *, then Git will ignore all the files
```
### The question mark ?

The question mark corresponds to any one character

```
file?.txt # to ingnore files: fileA.txt, file1.txt, however not the file12.txt because there are two characters after 'file' name, not one.
```
### Square brackets []

The square brackets, as a question mark, corresponds to one character
In this case, the symbol is not any, but only from the list that is indicated in parentheses.

```
file[0-2].txt # to ignore all the files file0.txt, file1.txt, file2.txt, however to point out that file3.txt won't be ignored

it's also possible to set [abc] or [a-z] range
```
### Slash /

if the thumb in .gitignore starts with '/' then Git will ignore all the files and catalogs only in the root directory

```
/ # it points at catalogs 
/todo.txt # to ignore todo.txt in the root of the repo, so that subdir/todo.txt is still being tracked
todo.txt # to ignore todo.txt in all of the folders
build/ # to ignore the build folder, however is build is a simple file this command will be ignored

# ignore files "docs/current/tmp", "docs/old/tmp",
# also "docs/old/saved/a/b/c/d/tmp"
# and even "docs/tmp", because zero of inluded folders are already invested
docs/**/tmp

# игнорировать только "docs/current/tmp" и "docs/old/tmp"
# файл "docs/old/saved/a/b/c/d/tmp" не попадает в правило
docs/*/tmp 

** # has the same effect as *
```

### Exclamation mark !

```
Any rule in the .gitignore file can be inverted with the help of '!'

*.jpeg # to ignore all the JPEG files

!doge.jpeg # all the JPEG files except doge
```

### .gitignore example

```
# to ignore all the files in the build catalog
build/

# to ignore all the .log files
*.log

# do not ignore *.log files in examples
!examples/**/*.log 
```

Files in the .gitignore doesn't appear after git status command, otherwise they would be clogged the output

```
git status --ignored # if you still need to display all ignored files add '--ignored'
```
To ignore all the files except .tex and .pdf
**
!**.tex
!**.pdf

## Cloning the repo

The process of the copying of the remote repo in your local PC called 'cloning'

```
git clone git@github.com:yandex-praktikum/git-clone-lesson.git # copy from 'Copy' => 'SSH'
```

git clone # automatically connected the local and the remote repositories

```
git remote -v # to ensure that the repositories are connected together
```

## Fork

In contrast to 'cloning' 'fork' doesn't load the alien repository on your PC but it will copy that repo into your Github account 

Fork - "развилка", "ответвление", "вилка :D" doesn't connect directly to the Git

In process of 'Fork' creates all the files copy, commits and branches history. That copy saves in your Github account

Reasons to use fork:
  You want to add your personal contribute to the project, however you don't have the rule rights to change that repository (open source).
  Then you can do 'fork' add necessary fixes and then send a request to include these changes in the original project 

  You want to develop the project regardless of its initial version. Let's say the creators of the project made up their mind that they won't add functionality, that you need. In this case, you can make a 'fork' and add it by yourself.

chmod +x check.sh # this command will make the file executable

./check.sh # this command will implement the script

## Branch. What is it?

Imagine: your work project has been launched and it already has users. You have an idea how to speed it up. But we need to conduct an experiment — change the code and see if the program will run faster. In the process, it is important to cooperate with colleagues and not break anything — branches will help in this.

```
Branch - it's an isolated project development flow
```

Branches allow you to make an experiment with the Git project, however at the same time to save up the repository in a stable condition. Each member of the team can work in his own branch and not bother the others: commits which will be executed by him won't be visible from other branches. And when the work is done the branches can be merged.

Branches are useful even if you are working alone — for example, on a website. Before writing new functionality, you should create a separate branch for it. Branches also allow one person to switch between several tasks at once.

The main, stable version of the project is keeping in the main branch 'main' or 'master'. It appears automatically during the repository creation process. Often, all the news branches in the repo depart from main, although this is not the rule

### To look at the project branches

```
git branch # to check if the main branch has appeared

* # indicates in what branch you are right now
```

## Branches creating

```
git branch <the branch name>
```

The branch name can consist of letters, numbers and also includes any of these characters: . - _ /. Those symbols don't make much sense. For instance: feature/add-branch-info could be called as feature_add-branch-info or feature-add-branch

git branch feature/add-branch-info # we have created a new branch 
git branch # we have looked at the other branches
  
  feature/add-branch-info  # a new one has appeared
* main                     # * means we are in the main branch 

### Branch naming

To create the branch name we will use pointers, sush as:
feature || bugfix
after that there will be a slash / and then some description of the task
/adding-branch-info # no spaces in that description!

### Switching from one branch to another

```
git checkout <branch name> # to switch to another branch
Bash answer: Switched to branch <branch name>

git branch
* feature/add-branch-info
  main

git checkout -b <branch name> # to create a branch and switch to it immediately
```

