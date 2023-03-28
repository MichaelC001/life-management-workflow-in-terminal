# life management workflow in terminal
### 1. Principle and feature
**Philosophy** <br />
This workflow is just a methodology and philosophy, you can develop your own workflow based on it, you don't necessarily have to use the same software or tools as me. My workflow just requires only two system build-in function (hard links, soft links) and a file manager, so that I could paly the same workflow in any device.<br />

**Purpose** <br />
The purpose of this workflow is to **solve problems** in my life and **develop my passions** through **lifelong learning**.<br />

**Feature**<br />
1. note tags
2. search and edit
3. read it later 
4. easy integrated with anki
5. backup any file with one click
6. chatgpt integrated
7. 

### 2.Hark link and soft link
The core tool used in this workflow is the system build-in function: hard link and soft link.<br />

**hard link** <br />
```
ln original_file new_file
```
This command creates a new link to the original file, so that any changes made to either file will be **automatically synchronized**, resulting in both files being **exactly the same**.<br />
The hard link only works for files.Delete one file will not affect another linked file.

### 3.Journal folder structure and tag system
My workflow is based on daily Journal.<br />
It is a file based system, all notesmare orgnized in folder structure <br />
**one folder one day**, **one entry one file**.
<p align="left">
<img src="/src/folder_structure.png" alt="Journal folder structure]" width="500">
</p>

Notebook folder stucture
```
Notebook
├── Journal
│    ├── 2302
│    └── 2303
│         ├── 28-Tue
│         ├── 29-Wed
├── Cycle
│    ├── Week
│    │     ├── Week 01
│    └── Season
├── Anki
├── Reading
├── Type
│   ├── video
│   ├── picture
│   ├── pdf
│   ├── text
│   ├── script
├── Tags
│   ├── #work
│   ├── #curiosity
│   ├── #health
│   ├── #passion
│   ├── #principle
│   ├── #realationship
├── Attachments

```
**Tag system**
Yes, we can use hard links and ripgrep to build a note tag system. To tag a note, just and #tag in the markdown note file in any daily folder.<br />
Every md files are stored in Journal folder, and all other folder like "type" or "tags" are diffrent view, I can create whatever view I want by a auto-run script, It will delete all the files in the folder, and will re-create **hard links** to any thing match certain type or tags. 

For example, in the folder /type/pdf, there is a script folder_type.fish , it will delete all file in this folder at everyday 00:01AM, then search all files under Journal folder, and create hard links of each unique pdf file in this folder. So I could access all my pdf files in this folder, I could hightlight it, and all the change will sync to the linked file in Journal folder automaticlly.

Another example, in the folder /tag/#work, there is a script folder_tag.fish (and all the other tag foder like #health, is hard linked to the save folder_tag.fish),  it will delete all file in this folder at everyday 00:01AM, then search all md files under Journal folder, and create hard links of each unique md files with the text "#work" in this folder. So I could access all my work journals in this folder, I could edit it, and all the change will sync to the linked file in Journal folder automaticlly.

Another example, I want to view all notes metioned "digital" temporarily (tag/digital/ is not exist), I could use the script snf (search and file), It will create a folder named .tmp/food-date-time/, this script will find out all notes metioned "food" under Journal folder and hard linked them in this folder. I could sort or edit all food notes in LF file manager, and this change will sync to the files in the original Journal folder, then I could exit this folder and do another search for "work "and edit thme. Every day I will run an auto script to delete the tmp folder, just delete one of these hard links, all the original files and changes in the Journal folder are still there.

<p align="left">
<img src="/src/snf.gif" alt="snf script]" width="500">
</p>

