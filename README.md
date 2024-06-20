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

'git status' shows only the following statuses:

'staged' # changes to be committed
'modified' # changes not staged for commit
'untracked' untracked files
