# Tips and Tricks with bash
**commands**
- **./** --> execute a program
- **whoami** --> prints username of current user
- **man** _command_ || _command_ **--help** --> prints additional information about command
- **clear** --> clears terminal screen CTRL+L -> runs **clear -x**
- **pwd** --> prints current working directory
- **ls** --> lists all the files inside the curent folder || ls /desktop
  - **ls -l** --> long listing format
  - **ls -a** --> not ignoring files starting with comma .
- **cd** --> change directory 
  - cd /c/users/danie
  - cd ..
  - cd ../../../
- **mkdir** --> creates new folder
  - mkdir folder_1 folder_2 for multiple new folders or nested folders like mkdir folder_1/folder_2
  - **mkdir -p** --> creates nested folder even if higher level of folder does not exist (doesnt need parrent directory)
- **touch** - to create empty file -> if file exists it is open in write mode
- **rmdir** --> deletes only empty directories
- **rm**  --> deletes files 
  - rm -v --> show deletion output
  - rm -r --> deletes everything recursively
  - rm -ri --> asks for every folder to delete
- **open/start/xdg-open** -> open folders or start application
- **mv** -> for moving file from one place to another or renaming the file
- **cp** -> for copying files
- **head** -> prints first ten lines of a file
  - head -n_NBR_ -> prints _NBR_ lines
- **tail** -> prints last ten lines of a file
- **date** -> prints current dat
- **cat** -> prints all the output of the file
- **less** ->  prints shorter output of a file
  - with /, you can search entire document
- **echo** -> it simply prints what was written eg. echo "xYz"
- **wc** -> it returns info about a file -> NBR_of_lines, NBR_of_words, NBR_of_bites


**if Rule**
starts with if
ends with fi
```
if _rule_
then
    _action_
elif
    _action_
else
    _action_
fi
```
may be used with various set of [operators](https://linuxhint.com/bash_operator_examples/)
```
if [ $age -gt 18 ] && [ $age -lt 29 ]
then
    echo "statement is True"
else
    echo "statement is False"
fi

if [ $age -gt 31 ] || [ $age -lt 29 ]
then
    echo "statement 1 is True"
elif [ $age=30 ]
then
    echo "statement 2 is True"
fi
```

**pipelines**
May take output of one command as an input to another command _command_ | command
**eg.**
ls -l | wc -l > output.txt
number of lines in pwd are redirected to output.txt