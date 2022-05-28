## The Command Line :
- A command line, or terminal, is a text based interface to the system presents you with a prompt
- "bash" stand for Bourne again shell one of the most common shells that defines how terminal will look after exeuting
## Basic Navigation
- **pwd** is an abbreviation for Print Working Directory and refers to our current working address
- **ls** is an abbreviation for list and it tells us what is in our current location
- **Absolute paths** specify a location (file or directory) in relation to the root directory
- **Relative paths** specify a location (file or directory) in relation to where we currently are in the system
- **~(tilde)** a shortcut for your home directory
- **. (dot)** a reference to your current directory.
- **.. (dotdot)** a reference to the parent directory
- **cd** is an abbreviation for change directory and it takes [location] argument
## A bout Files :
- we can say that almost everything is a file include text , keyboard and monitor
- **file [path]** to find the type of the file like :
  - file.exe - an executable file, or program
  - file.txt - a plain text file
  - file.png, file.gif, file.jpg - an image
- **ls -a or --all** to list the contents of a directory, including hidden files
- To skip space issues in directories or files names we can use one of the following teqniuqes:

  **1. Quotes :** using quotes around the entire item like **'student profile'**

  **2. Escape Characters :** using backslash ( \ ) like **student \ profile**

  **3. Tab comletion :** that will encounter the space in the directory name then the terminal will automatically escape any spaces in the name

## Manual Pages :
- **man [command to look up]** it will give me all details about the command I am looking for also how to use it
- **man -k [search term]** to search in manual pages about what command you may want to use 
-  long hand command line options begin with two dashes ( -- ) and short hand options begin with a single dash ( - )

## File Manipulation :
- **mkdir [options] [Directory]** is an abbreviation for make a directory which end with Creating a directory with the name I choose

  - Options that used with mkdir command:
  
    **1) -p** which tells mkdir to make parent directories as needed

    **2) -v** print a message for each created directory
- **rmdir [options] [Directory]** is an abbreviation for remove directory (a directory must be empty before) also it supports the -v and -p options
- **touch [options] [filename]** Update the access and modification times of each FILE to the current time and it will create a blank file if doesn't exist
- **cp [options] [source] [destination]** to make a duplicate of a file or directory 
  - **-r option** stands for recursive and it alow me to duplicate multiple directories

- **mv [options] [source] [destination]** move (rename) files and directories

- **rm [options] [file]** which stands for remove thats mean remove file or directory and that's work with empty and non empty directories
  - **-r option** it allows us to remove directories and all files and directories contained within
  - **-i option** will prompt you before removing each file and directory and give you the option to cancel the command




## Referances :
[Bash Command Line Tutorials](https://ryanstutorials.net/linuxtutorial/)

[Cheat Sheet](https://ryanstutorials.net/linuxtutorial/cheatsheet.php)

