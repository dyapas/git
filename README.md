# git

## Install Git
Reference: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

## Basic Configuration:
1. **System level Configuration**: Applies to all users:
    - `Linux`: /etc/gitconfig
    - `Windows`: \Program Files\Git\etc\gitconfig
    - To change the config at System level: `git config --system`
2. **User level Configuration**:
    - `Linux`: ~/.gitconfig
    - `Windows`: $HOME\.gitconfig
    - To change the config at User level: `git config --global`
3. **Project level**:
    - my_project/.git/config
    - To change the config at Project level: `git config`
### To change/Update/set config:
```git
git config --global user.name "Sathi Dyapa"
git config --global user.name "xyz@gmail.com"
```
- To list the current configuration list ( system level ): `git config --list`
- to check the individual property: ex: `git config user.name`
```
$ git config user.name
 Sathi Dyapa

$ git config user.email
dyapas325@gmail.com
 ```
- to set editor as vscode:  `git config --global core.editor "code --wait"
- to unset: `git config --global --unset core.editor`
### Git Help: 
- `git help` is used to get more about the different commands in git
- to check git version: 
```
$ git --version
git version 2.24.1.windows.2
```
- To initialize the project: `git init`
- the folder '.git' contains all the files and folders required by git to perform git operations and keep track of changes.
 ```
$ ls -la .git/
total 22
drwxr-xr-x 1 user group   0 Feb  7 16:10 .
drwxr-xr-x 1 user group   0 Feb  7 14:18 ..
-rw-r--r-- 1 user group 281 Feb  7 16:10 config
-rw-r--r-- 1 user group  73 Feb  5 10:52 description
-rw-r--r-- 1 user group  20 Feb  7 14:06 HEAD
drwxr-xr-x 1 user group   0 Feb  5 10:52 hooks
-rw-r--r-- 1 user group 470 Feb  7 15:08 index
drwxr-xr-x 1 user group   0 Feb  5 10:52 info
drwxr-xr-x 1 user group   0 Feb  5 10:53 logs
drwxr-xr-x 1 user group   0 Feb  7 15:08 objects
drwxr-xr-x 1 user group   0 Feb  5 10:58 refs
```
- take a look at .git/config file: User level config. We dont need to make any changes to any of these files. 
```
$ cat .git/config 
[core]
        repositoryformatversion = 0
        filemode = false
```
### Common steps:
    1. Make changes to the files in project
    2. Add changes to the repo : `git add <filename|all>`
    3. commit changes to the repo: `git commit -m "<commit message>"`
 
- A shot single-line summery ( less than 50 characters)
- to view the commit logs/logs: issue `git log` in project folder . Newest commit on the top .
- to limit the commit logs: `git log -n <NumberOfLinesToView>`
    - ex: `git log -n 5` ==> to view last 5 commit messages
- To limit the logs by time ( use --since): `git log --since=<date>`
```
git log --since=2021-02-01
commit b5845b24baa9fab85a1e25c12d685a6429f53fa5 (HEAD -> wip, wip/wip)
Author: Sathi Dyapa <abc@gmail.com>
Date:   Fri Feb 5 10:55:50 2021 -0500
```
- To search for a specific commit message: `git log --grep="<Search string>"`
- to limit the last `X` number of lines until `Date`: `git log --until=<Date/YYYY-MM-DD> -n <Num>`
```
git log --since=2019-03-01 --until=2019-03-31 --author="Karen" --grep="refactor" -n 5
```
## Git Three Trees architecture: 
- Working ==> Staging ==> Repository
    - when we perform `add` command , it will add the copy/file to the staging area and we issue commit it will save the changes to repository.

- **Git Workflow**: 
    - Working ==> Staging ==> Repository
    - each commit will create checksum and git uses SHA-1 hash algorithm to create checksum .
    - checksum is a 40 character hexadecimal string.
- **HEAD Pointer**:
    - Git maintains a reference variable and its called ` HEAD`
- **ADD Files**:
    - `git status` command will give information of current status like on which branch the user currently working and what files changed etc.
    - `git add` will add new or edited files to the staging area.
- **View Changes with diff**:
    - `git diff` provides us the changes made to the files in the current folder
    - to view only the content changed use `git diff --color-words` 
- **To View only Staged Changes**: 
    - `git diff --staged` : gives the details of diff between staged area and repository.
    - `--staged` is an alias for `--cached`
```
$ git diff --staged
diff --git a/first_file.txt b/first_file.txt
index da0db80..1c032ca 100644
--- a/first_file.txt
+++ b/first_file.txt
@@ -1 +1,3 @@
 First test file
+Added this to see diff feature
+on git


$ git diff --cached
diff --git a/first_file.txt b/first_file.txt
index da0db80..1c032ca 100644
--- a/first_file.txt
+++ b/first_file.txt
@@ -1 +1,3 @@
 First test file
+Added this to see diff feature
+on git
```
- to `unstage` : `git restore --staged <file>` to restore.
- **DELETE**: To delete file .
    1. `git rm <file/s>`
    2. `git commit -m <commit message for deleted file>`
- **Move/rename**: to move or rename:
    1. `git mv origFile RenamedFile`
    2. `git commit -m <commit message for moved/renamed file>`
- To add and commit the updated/added files to the repository at the same time: `git commit -am "Add and commit changes"` (No changes will be pushed to staging and instead it directly saves the changes to repo directly)
- To view a previously committed change: `git sdiff how <SHA ID of the commit> --color-words`
- to get the difference b/w two different commit's: `git show <SHA1 Of Commit-1>..<SHA1 Of Commit-1>`
    - Note: `..`(two DOT's) are mandatory between SHA's of two commits and no space b/w `..`(two DOT's and SHA ID's

## Undo Working Directory Changes:
- to restore/discard changes in working directory:  `git restore <file>`
or
- `git checkout -- <File>` 
## Undo Staging changes (Unstage Files):
- To unstage the file from Staging Area to work area again.
    - `git reset HEAD <file>` or
    - `git restore --staged <file>`

## Amend commits:
- we can only amend/edit the latest commit. NOT the older one's. 
- usage: `git commit --amend -m "Commit Message"`
- it will remove the previous commit message and SHA and replaces with latest commit message
- `git commit --amend` can only be used to edit the `current HEAD`. we would need to use `git rebase -i HEAD~n` to access all commits between HEAD and the `nth` commit prior to HEAD

## Remove Untracked files::
- `git clean` command with `-f` option is used for cleaning/removing untracked files.
```
git clean -n ==> for dry-run before actually removing it completely.
git clean -f ==> to remove untracked files completely.
```
- The `git reset` command will unstage files.
- `git checkout` command will return all unstaged files to the repository version
- to preview a list of only untracked files to be deleted ==> `git clean -n`
- Q1. A client has decided they want to revert one page of their website generated by about.php to a version they had in the commit with SHA 53daff9b. Which process should you use?
```
git checkout 53daff9b -- about.php and then git commit -am "Reverts about.php to version live in January 2019"
```
- `.gitignore` file used to specify if we wanted git to ignore/untrack any files/folder etc.
- [A collection of .gitignore templates](https://github.com/github/gitignore)

# Markdown Cheatsheet
Normal text
## Testing Git WIP
# This is Heading ( single pound sign # for Heading)
## This is Sub Heading ( two ## 's for sub heading)

``` ## This is Sub Heading ( two ## 's for sub heading) ```


***
To inlcude the text as Italics start with underscore("_") and Text and end with underscore("_") -- No spaces between starting  "_" and text and ending underscore 

```ex: _This is Italics example_```

_Hi , This is Sathi Dyapa_
***

***

**BOLD Letters**
```
To make the text in BOLD/Strong we need to use two astric symbols (**) bewtween the text and again .. no spaces b/w text and **

ex: **This is BOLD Letter example**
```
***

****
to scratch a text two tilde signs and text 2 tilde signs ```~~<Text Here>~~```

~~1000~~ 999

****
## Links
[Ansible Docs](www.ansible.com)
```
[Text to dislay in place of URL or Link](actual URL or Link here)  
ex: [ansible docs](ansible.com)
```
*****


## To display commands in b/w texts we use sinble back tick ``` `copy` ```

This is ansible `copy` command

ex2: user `for` loop

## To insert code in b/w lines we need to use 3 back ticks ()and followed by type of language code sinppet we wanted in show .. then code .. then end with 3 back ticks (```)

Below is the yaml code 

```yaml
- name: "This is Sample Playbook"
  hosts: Dev
  Tasks:
   name: "display Time"
   cmd: date
```
*****

## Tables
| This | is | Table |
| ---- | ----| ---- |
|col-1 | col-2 | col -3|

```
## how to create the above table -- see below -- pipe "|" symbol  and min 3 of dashes ( ---- ) required
| This | is | Table |
| ---- | ----| ---- |
|col-1 | col-2 | col -3|

```
***
## List
1. list one
2. list two
3. List three

## to have bullet list .. we use "-" (dash)
- This is Sample bullet
- second bullet 


## To inser Quotes -- Greater than symbol followed by Quote we wanted to insert  `  >Quote Here`
>The More you learn the more you strong
***

## To insert an Images
```same as Links but "!" comes extra ![SampleText](URL for the Image)```

ex: ![Bird](https://asia.olympus-imaging.com/content/000107506.jpg)
- [More Info](https://www.foxinfotech.in/2019/12/github-markdown-add-an-image-to-readme-md-file.html#:~:text=GitHub%20Markdown%3A%20Add%20an%20Image%20to%20README.md%20File,...%203%20Add%20an%20Image%20from%20External%20Resource)
****
