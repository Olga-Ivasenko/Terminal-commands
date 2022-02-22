## **Linux terminal (GitBash) commands**
## Part 1: Windows Git Terminal

**1. Посмотреть где я**
```bash
pwd
```
**2. Создать папку**
```bash
cd MainDirectory
mkdir Dir1
```
**3. Зайти в папку**
```bash
cd Dir1
```
**4. Создать 3 папки**
```bash
cd ..	//go back to MainDirectory
mkdir Dir2 Dir3 Dir4
```
**5. Зайти в любоую папку**
```bash
cd Dir2
```
**6. Создать 5 файлов (3 txt, 2 json)**
- to create several files at once:
```bash
touch f1.txt f2.txt f3.txt f4.json f5.json
```
- to create several files with same name and different ending:
```bash
mk name{1,2,3}.txt
```
- to create just one file
```bash
> filename.txt
OR
touch filename.txt
```
**7. Создать 3 папки**
- to create folders with different names:
```bash
mkdir dir_one dir_two dir_three
```
- to create folders with same name and different ending:
```bash
mkdir folder{1,2,3}
```
Result is the same

**8. Вывести список содержимого папки**
- Standard for list of not-hidden folders and files with indication of type / for folders
```bash
ls
```
- If to see detailed with date of creation & right: 
```bash
ls -lh
```
! this command for some installs is not workable !

- If to see detailed with date of creation & right & hidden files: 
```bash
ls -la
```
- to see reversal list of content:
```bash
ls -r
```
- to see content of this folder and subfolders:
```bash
ls -R
```
**More options are available, see `ls --help`**


**9. + Открыть любой txt файл**
- open in default editor:
```bash
start filename.txt
```
- open with nano util:
```bash
nano filename.txt
```
- open with vim util:
```bash
vim filename.txt
```

**10. + написать туда что-нибудь, любой текст**
- start: ```Hello world!```
- nano: ```Next challenge to everybody!```
- vim: ```i => We will achieve it!```

**11. + сохранить и выйти**
- start: ```Ctrl + S => Alt + F4 or Alt + F4 and Enter on Save```
- nano: ```Ctrl + S & Ctrl + X or can be Ctrl + X => Y in input row```
- vim: ```Esc + : + wq + Enter```

**12. Выйти из папки на уровень выше**
```bash
cd ..
```
************
**13. переместить любые 2 файла, которые вы создали, в любую другую папку**
```bash
> we are in MainDirectory:
cd Dir2
mv filename1.txt filename2.txt ../Dir3
```

**14. скопировать любые 2 файла, которые вы создали, в любую другую папку**
- copy to the directory in same folder:
```bash
cp filename3.txt filename4.json folder1
```
- copy to the level UP directory:
```bash
cp filename3.txt filename4.json ../
```
- copy from one folder to another within same directory:
- ```
cp Dir2/filename3.txt filename4.json Dir3
```
- copy whole folder with my files to another folder:
- ```
cp -r Dir3 Dir4
```

**15. Найти файл по имени**
- if we know the file name:
```bash
find -name "f2.txt"
```
- if we do not know the name but extension:
```bash
find -name "*.txt"
```
- if we do not know extension but the name:
```bash
find  -name "f2.*"
```
**and all other variants can be replaced with * **

- search for files only:
```bash
find  -type f
``
- search with exception:
```bash
find  -not  -name "*.txt" -type f
```
- finding exactly  file and name:
```bash
find -name "*.txt" -type f 
```

**16. просмотреть содержимое в реальном времени (команда grep) изучите как она работает**
- permanent real time monitoring:
```bash
tail -f f1.txt
```
***Important:
Information will appear only in case file was edited and saved. Bette use script with opening file & saving new data***

> **Input:**
  hello everybody!
  is smth strange here?

 To stop command:
```bash
Ctrl+C or Ctrl+Z
```
- change request real time monitoring:
```
Tailf filename.txt
```
For some application versions can be used:
```bash
tail –F filename.txt
```
- Just to see file content up-to-time:
```bash
cat filename
```
	- if we want to see content of whole file in Terminal:
```bash
cat filename.txt
```
	- if we want to see several files content:
```bash
cat filename.txt filename.json
```
- grep
	- string with needed content:
```bash
grep "will" filename.txt
```
	- string with needed content & row number:
```bash
grep  -n "will" filename.txt
```
	- string with needed content & case-insensitive (L = l, Q = q):
```bash
grep -i "WILL" filename.txt
```
	- string with needed content & row number &  case-insensitive (L = l, Q = q):
```bash
grep –n -i "WILL" filename.txt
```
***we can combine several options in one command to define more exact request***

- tail & grep combinations:
	- looking for patterned words only with no caps sensitivity: 
```bash
tail -f filename.txt | grep -i "who"
```
> *result:*
who is looking for me?
hello who is here

	- Looking for several words with no caps sensitivity
```bash
tail -f filename.txt | grep -i -e "who" -e "hello"
```
> *res:*
hello everybody!
who is looking for me?
hello who is here
who really is here

	- Looking for several words with no caps sensitivity and with only last 4 rows actuality:
```bash
tail -f -n 4 filename.txt | grep -i -e "who" -e "hello"
```
> *res:*
hello who is here
who really is here


**17. вывести несколько первых строк из текстового файла**
- to see first 2 rows:
```bash
cat filename.txt | sed -n 1,2p
```
- to see qty of rows by default (10):
```bash
head filename.txt
```
- to see exact number of rows -n we need to see:
```bash
head -3 filename.txt
```

**18. вывести несколько последних строк из текстового файла**
- to see qty of rows by default (10):
```bash
tail filename.txt
```
- to see exact number of rows -n we need to see:
```bash
tail -5 filename.txt
```
- to see exact row & its number with requested info with no caps sensitivity:
```bash
ag –i “next” filename.txt
```

**19. просмотреть содержимое длинного файла (команда less) изучите как она работает**
- to delete multiple spaces:
```bash
less -s filename.txt
```
- to see row number:
```bash
less -N filename.txt
```
- to see whole original file by pages:
```bash
less filename.txt ()
```
- to mark every starting row:
```bash
less -w filename.txt
```
***and many other options. Main advantage is to possibility to control file with hotkeys***


**20. вывести дату и время**
***Depending on format of data we need, commands to be adopted:***
- for MM/DD/YY HH:MM:SS
```bash
date +"%D %T"
```
- for YYYY-MM-DD HH:MM
```bash
date +"%Y-%m-%d %h-%m"
```
- for DD-MM-YY HH:MM:SS
```bash
date +"%d-%m-%y %T"
```
- for YYYY FullMonthName DD
```bash
date +”%Y %b %m”
```
- for FullWeekDayName, ShortMonth DD, YYYY HH:MM PM/AM
```bash
date +”%A, %b %d, %Y %I:%M %p”
```
***changing % and letter we are setting needed format of timing***


******************

## **Задание * **
**1a. Отправить http запрос на сервер**
http://162.55.220.72:5005/terminal-hw-request

***Attention: this metod works by default with request GET only (!)***
1) to check if URL is workable
```bash
curl “URL”
```
> Result: Status 200 (Done)

2) to change data via URL, not body
```bash
curl "http://162.55.220.72:5005/get_method?name="Olga"&age=49"
```
> Result: Status 200 (Done)

3) method POST is not workable for this server:
```bash
curl -X POST –d
```
> Result: => status 405 METHOD NOT ALLOWED


**1в) Отправить http запрос на сервер** http://162.55.220.72:5005/object_info_3?name=Vadim&age=32&salary=1000

1) to change data via URL, not body
```bash
curl --location --request GET 'http://162.55.220.72:5005/object_info_3?name=Olga&age=49&salary=2000'
```
> Result: Status 200 (Done)

2) method POST is not workable for this server:
```bash
curl -X POST –d
```
> Result: status 405 METHOD NOT ALLOWED


**2. Написать скрипт который выполнит автоматически пункты 3, 4, 5, 6, 7, 8, 13**

- simple type directly in Terminal:
```bash
cd TestDir_3; mkdir TestDir_11 TestDir_12 TestDir_13; cd TestDir_11; touch f1.txt f2.txt f3.txt f4.json f5.json; mkdir folder1 folder2 folder3; ls; mv f1.txt f2.txt folder1
```

- if we want to specify correct running directly in Terminal:
```bash
cd TestDir_3 && mkdir TestDir_11 TestDir_12 TestDir_13 && cd TestDir_11 && touch f1.txt f2.txt f3.txt f4.json f5.json && mkdir folder1 folder2 folder3 && ls && mv f1.txt f2.txt folder1
```

- SCRIPT via file:
	- Create Script file:
[Myscript](https://github.com/Olga-Ivasenko/Terminal-commands/blob/c24dab16c672d6de273d65f7cfe1754cbdeb8e98/myscript.txt)

	- COMMANDS TO EXECUTE
```bash
Creat file: touch
Save file named: myscript
Make file executable: chmod +x ./myscript.txt
Execute: ./myscript.txt
```

## Part 2: Linux WM Ubunta Terminal
## Attention: ***`same`*** meant this command is the same for Windows

**1. Посмотреть где я**

***same***
```bash
pwd
```
**2. Создать папку**

***same***
```bash
cd MainDirectory
mkdir Dir1
```
**3. Зайти в папку**

***same***
```bash
cd Dir1
```
**4. Создать 3 папки**

***same***
```bash
cd ..	//go back to MainDirectory
mkdir Dir2 Dir3 Dir4
```
**5. Зайти в любоую папку**

***same***
```bash
cd Dir2
```
**6. Создать 5 файлов (3 txt, 2 json)**

***same***
- to create several files at once:
```bash
touch f1.txt f2.txt f3.txt f4.json f5.json
```
- to create several files with same name and different ending:
```bash
mk name{1,2,3}.txt
```
- to create just one file
```bash
> filename.txt
OR
touch filename.txt
```
**7. Создать 3 папки**

***same***
- to create folders with different names:
```bash
mkdir dir_one dir_two dir_three
```
- to create folders with same name and different ending:
```bash
mkdir folder{1,2,3}
```
Result is the same

**8. Вывести список содержимого папки**
- Standard for list of not-hidden folders and files without indication of type / for folders
```bash
ls
```
- Standard for list of not-hidden folders and files with indication of type / for folders
```bash
l or l -p
```
- to see list of directory content with hidden files:
```bash
ls -a
```
- If to see detailed with date of creation & right & hidden files
```bash
ls -l
```
- to see reversal list of content:
```bash
ls -r
```
- to see content of this folder and subfolders:
```bash
ls -R
```
**More options are available, see `ls --help`**


**9. + Открыть любой txt файл**
- open iwith gedit util:
```bash
gedit filename.txt
```
- open with nano util:
```bash
nano filename.txt
```
- open with vim util:
```bash
vim filename.txt
```

**10. + написать туда что-нибудь, любой текст**
- gedit: ```Hello world!```
- nano: ```Next challenge to everybody!```
- vim: ```i => We will achieve it!```

**11. + сохранить и выйти**
- gedit: ```Ctrl + S => Alt + F4 or Alt + F4 and Enter on Save```
- nano: ```Ctrl + S & Ctrl + X or can be Ctrl + X => Y in input row```
- vim: ```Esc + : + wq + Enter```

**12. Выйти из папки на уровень выше**

***same***
```bash
cd ..
```
************
**13. переместить любые 2 файла, которые вы создали, в любую другую папку**

***same***
```bash
> we are in MainDirectory:
cd Dir2
mv filename1.txt filename2.txt ../Dir3
```

**14. скопировать любые 2 файла, которые вы создали, в любую другую папку**

***same***
- copy to the directory in same folder:
```bash
cp filename3.txt filename4.json folder1
```
- copy to the level UP directory:
```bash
cp filename3.txt filename4.json ../
```
- copy from one folder to another within same directory:
```bash
cp Dir2/filename3.txt filename4.json Dir3
```
- copy whole folder with my files to another folder:
```bash
cp -r Dir3 Dir4
```

**15. Найти файл по имени**

***same***
- if we know the file name:
```bash
find -name "f2.txt"
```
- if we do not know the name but extension:
```bash
find -name "*.txt"
```
- if we do not know extension but the name:
```bash
find  -name "f2.*"
```
***and all other variants can be replaced with***

- search for files only:
```bash
find  -type f
``
- search with exception:
```bash
find  -not  -name "*.txt" -type f
```
- finding exactly  file and name:
```bash
find -name "*.txt" -type f
```

**16. просмотреть содержимое в реальном времени (команда grep) изучите как она работает**
- permanent real time monitoring:
```bash
tail -f f1.txt
```
***Important:
Information text Is appearing in Terminal only after saving data in file and Ctrl+Z stopping the command***

> **Input:**
  hello everybody!
  is smth strange here?

 To stop command:
```bash
Ctrl+C or Ctrl+Z
```
- change request real time monitoring:

***same***
```
Tailf filename.txt
```
For some application versions can be used:
```bash
tail –F filename.txt
```
- Just to see file content up-to-time:

***same***
```bash
cat filename
```
	- if we want to see content of whole file in Terminal:
```bash
cat filename.txt
```
	- if we want to see several files content:
```bash
cat filename.txt filename.json
```
- **grep**

***same***
a) string with needed content:
```bash
grep "will" filename.txt
```
b) string with needed content & row number:
```bash
grep  -n "will" filename.txt
```
c) string with needed content & case-insensitive (L = l, Q = q):
```bash
grep -i "WILL" filename.txt
```
d) string with needed content & row number &  case-insensitive (L = l, Q = q):
```bash
grep –n -i "WILL" filename.txt
```
***we can combine several options in one command to define more exact request***

- tail & grep combinations:
***same***
a) looking for patterned words only with no caps sensitivity: 
```bash
tail -f filename.txt | grep -i "who"
```
> *result:*
who is looking for me?
hello who is here

b) Looking for several words with no caps sensitivity
```bash
tail -f filename.txt | grep -i -e "who" -e "hello"
```
> *res:*
hello everybody!
who is looking for me?
hello who is here
who really is here

c) Looking for several words with no caps sensitivity and with only last 4 rows actuality:
```bash
tail -f -n 4 filename.txt | grep -i -e "who" -e "hello"
```
> *res:*
hello who is here
who really is here


**17. вывести несколько первых строк из текстового файла**

***same***
- to see first 2 rows:
```bash
cat filename.txt | sed -n 1,2p
```
- to see qty of rows by default (10):
```bash
head filename.txt
```
- to see exact number of rows -n we need to see:
```bash
head -3 filename.txt
```

**18. вывести несколько последних строк из текстового файла**

***same***
- to see qty of rows by default (10):
```bash
tail filename.txt
```
- to see exact number of rows -n we need to see:
```bash
tail -5 filename.txt
```
- to see exact row & its number with requested info with no caps sensitivity:
```bash
ag –i “next” filename.txt
```

**19. просмотреть содержимое длинного файла (команда less) изучите как она работает**

***same***
- to delete multiple spaces:
```bash
less -s filename.txt
```
- to see row number:
```bash
less -N filename.txt
```
- to see whole original file by pages:
```bash
less filename.txt ()
```
- to mark every starting row:
```bash
less -w filename.txt
```
***and many other options. Main advantage is to possibility to control file with hotkeys***


**20. вывести дату и время**

***same***

***Depending on format of data we need, commands to be adopted:***
- for MM/DD/YY HH:MM:SS
```bash
date +"%D %T"
```
- for YYYY-MM-DD HH:MM
```bash
date +"%Y-%m-%d %h-%m"
```
- for DD-MM-YY HH:MM:SS
```bash
date +"%d-%m-%y %T"
```
- for YYYY FullMonthName DD
```bash
date +”%Y %b %m”
```
- for FullWeekDayName, ShortMonth DD, YYYY HH:MM PM/AM
```bash
date +”%A, %b %d, %Y %I:%M %p”
```
***changing % and letter we are setting needed format of timing***


******************

## **Задание * **
**1a. Отправить http запрос на сервер**
http://162.55.220.72:5005/terminal-hw-request

***same***

***Attention: this metod works by default with request GET only (!)***
1) to check if URL is workable
```bash
curl “URL”
```
> Result: Status 200 (Done)

2) to change data via URL, not body
```bash
curl "http://162.55.220.72:5005/get_method?name="Olga"&age=49"
```
> Result: Status 200 (Done)

3) method POST is not workable for this server:
```bash
curl -X POST –d
```
> Result: => status 405 METHOD NOT ALLOWED


**1в) Отправить http запрос на сервер** http://162.55.220.72:5005/object_info_3?name=Vadim&age=32&salary=1000

***same***

1) to change data via URL, not body
```bash
curl --location --request GET 'http://162.55.220.72:5005/object_info_3?name=Olga&age=49&salary=2000'
```
> Result: Status 200 (Done)

2) method POST is not workable for this server:
```bash
curl -X POST –d
```
> Result: status 405 METHOD NOT ALLOWED


**2. Написать скрипт который выполнит автоматически пункты 3, 4, 5, 6, 7, 8, 13**

- simple type directly in Terminal:
```bash
cd TestDir_3; mkdir TestDir_11 TestDir_12 TestDir_13; cd TestDir_11; touch f1.txt f2.txt f3.txt f4.json f5.json; mkdir folder1 folder2 folder3; ls; mv f1.txt f2.txt folder1
```

- if we want to specify correct running directly in Terminal:
```bash
cd TestDir_3 && mkdir TestDir_11 TestDir_12 TestDir_13 && cd TestDir_11 && touch f1.txt f2.txt f3.txt f4.json f5.json && mkdir folder1 folder2 folder3 && ls && mv f1.txt f2.txt folder1
```

- SCRIPT via file:
	- Create Script file:
[Myscript](https://github.com/Olga-Ivasenko/Terminal-commands/blob/c24dab16c672d6de273d65f7cfe1754cbdeb8e98/myscript.txt)

	- COMMANDS TO EXECUTE
```bash
Creat file: touch
Save file named: myscript
Make file executable: chmod +x myscript.txt
Execute: ./myscript.txt
```