## Day 21 – Shell Scripting Cheat Sheet: Build Your Own Reference Guide

## Task 1: Basics: Document the following with short descriptions and examples:

      1- Shebang (#!/bin/bash): tells the system to run the script using the Bash shell.
      2- Running a script: 
         * Make executable: chmod +x script.sh
         * Run : ./script.sh OR bash script.sh
      3- Comments:
         * Single-line comment: #This is a comment.
         * Inline comment: echo "Hello" 
            OUTPUT: Hello
      4- Variables: 
         * Declare: NAME="DevOps"
         * Use: $NAME
                '$NAME'
                "NAME"
      5- Reading user input:
          1- read -p "Enter Name:" NAME
          2- echo "hello $NAME"

      6- Command-line arguments: 
          1- $0 : Script name
          2- $1 : Frist arguments
          3- $# : Number of arguments
          4- $@ : All arguments
          5- $? : Exit status


## Task 2: Operators and Conditionals:
      1- String comparisons:
         NO   DOCUMENTS    EXAMPLE               EXPLANATION
          1-    =         [ "$a" = "$b" ]      Are both strings equal?
          2-   !=         [ "$a" != "$b" ]     Are both strings different?
          3-   -z         [ -z "$var" ]        Is the variable empty.
          4-   -n         [ -n "$var" ]        Does the variable caintaning something.

      2- Integer comparisons:
         NO   DOCUMENTS    EXAMPLE                  EXPLANATION
          1-    -eq       [ "$a" -eq "$b" ]      Are both numbers equal
          2-    -ne       [ "$a" -ne "$b" ]      Are the two numbers different
          3-    -lt       [ "$a" -lt "$b" ]      Ia a is less that b
          4-    -gt       [ "$a" -gt "$b" ]      Is a is greater than b
          5-    -le       [ "$a" -le "$b" ]      Is a is less than OR equal to b
          6-    -ge       [ "$a" -ge "$b" ]      Is a is greater than OR equal to b

      3- File test operators:
         NO   DOCUMENTS    EXAMPLE               EXPLANATION
          1-     -f       [ -f file ]          Is it a regular file?
          2-     -d       [ -d dir ]           It is a directory?
          3-     -e       [  -e file ]         Does the file or directory exist?
          4-     -r       [ -r file ]          Can the file be read?
          5-     -w       [ -w file ]          Can the file be written to?
          6-     -x       [ -x file ]          Can the file be exicuted?
          7-     -s       [ -s file]           Is the file non-empty (size > 0)?

      4- if, elif, else syntax:
         if [ -f file.txt ]; 
          then
             echo "EXISTS"
         elif [ -d Backup ];
           then
             echo "DIRCTORY'
         else  
             echo "NOT FOUND"
         fi

       5- Logical operators:
          

             
             
          

            
          
