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
### To change/Update config:
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




    