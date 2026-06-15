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
          NO   DOCUMENTS          EXAMPLE                              EXPLANATION
          1-    &&         [ -f file ] && echo "Found"     if the file exists then print "Found"
          2-    ||         [ -f file ] || echo "Missing"   If the does not exists then print "Missing"
          3-    !          ! [ -f file ]                   Is the file NOT present?

      6- Case statements:  case ... esac
          case $choice in 
           1) 
             echo "Start" 
             ;;
           2) 
              echo "Stop" 
              ;; 
           *) 
              echo "Invalid" 
              ;; 
           esac

## Task 3: Loops:
       1- for loop: 
           1- List-based
             for i in 1 2 3
               echo "$i"
             done
           2- C-Style
             for ((i=1;i<=5:i++))
              do
               echo "$i"
             done
             
       2- while loop:
          count=1
           while [ $count -le 5 ]
           do 
              echo $count
              ((count++))
           done

      3- Untill loop:
         count=1
          untill [ $count -ge 5 ]
          do
             echo $count
             ((count++))
          done

      4- Loop control:
           1- Break
             for i in {1..10}
             do 
                 [ $i -eq 5 ] && break
                 echo $i
             done 
           2- Continue:
              for i {1..5}
              do
                 [ $i -eq 3 ] && continue
                 echo $i
              done

       5- Looping over files:
           for file in *.log
           do
             echo $file
           done

       6- Looping over command output:
            cat names.txt | while read line
            do
               echo &line
            done

## Task 4: Functions:
       1- Defining a function:
             greet() {
                echo "Hello"
             }

       2- Calling a function:
             greet

       3- Passing arguments to functions:
            sum() {
               echo $(($1+$2))
               }
             sum 10 20

       4- Return values:
            square() {
              echo (($1*$1))
              }
               result=$(square 5)

                Return code:
                  return 0

       5- Local variables:
            greet() {
              Local name="DevOps"
               echo $name
               }

## Task 5: Text Processing Commands:
       1- grep
           grep error file.log
           grep -i error file.log
           grep -r error
           grep -c error file.log
           grep -n error file.log
           grep -v error file.lof
           grep -E "error|warning" file.log
               
         
            
             
           
       
           
         
           
         
          
          

             
             
          

            
          
