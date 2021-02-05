# Markup launguage
Normal text
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
****
