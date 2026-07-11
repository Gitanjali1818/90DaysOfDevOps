## Day 21 – Shell Scripting Cheat Sheet: Build Your Own Reference Guide

## Quick Reference Table:

       Topic	              Key Syntax	                   Example
      
      Variable	     VAR="value"      	           NAME="DevOps"
      Argument	     $1, $2	                         ./script.sh arg1
        If	            if [ condition ]; then	           if [ -f file ]; then
      For loop	     for i in list; do	           for i in 1 2 3; do
      Function	     name() { ... }	                  greet() { echo "Hi"; }
       Grep	            grep pattern file	           grep -i "error" log.txt
       Awk	            awk '{print $1}' file	           awk -F: '{print $1}' /etc/passwd
       Sed	            sed 's/old/new/g' file	           sed -i 's/foo/bar/g' config.txt

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
             do 
             for i in 1 2 3
               echo "$i"
             done
           ## OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ ./for_loop.sh
                      1
                      2
                      3  
           2- C-Style
             for ((i=1;i<=5;i++))
              do
               echo "$i"
             done
            ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ ./for_loop.sh
                      1
                      2
                      3
                      4
                      5
             
       2- while loop:
          count=1
           while [ $count -le 5 ]
           do 
              echo "$count"
              ((count++))
           done
         ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ ./while_loop.sh
                   1
                   2
                   3
                   4
                   5  

      3- Until loop:
         count=1
          until [ $count -ge 5 ]
          do
             echo "$count"
             ((count++))
          done
        ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ ./untill_loop.sh
                  1
                  2
                  3
                  4  
          

      4- Loop control:
           1- Break
             for i in {1..10}
             do 
                 [ $i -eq 5 ] && break
                 echo "$i"
             done
            ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ ./loop_control.sh
                      1
                      2
                      3
                      4 
           2- Continue:
              for i {1..5}
              do
                 [ $i -eq 5 ] && continue
                 echo $i
              done
            ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ ./loop_control.sh
                      1
                      2
                      3
                      4
                      1
                      2
                      3
                      4  

       5- Looping over files:
           for file in *.log
           do
             echo $file
           done
          ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20/task-3$ ./looping_over_files.sh
                    *.log 

       6- Looping over command output:
            cat names.txt | while read line
            do
               echo $line
            done

            ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20/task-3$ ./loopintg_over_command.sh
                       cat: names.txt: No such file or directory

## Task 4: Functions:
       1- Defining a function:
             greet() {
                echo "Hello"
             }
             greet
       ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20/task-4$ ./defining_function.sh
                 hello   

       2- Calling a function:
             greet

       3- Passing arguments to functions:
            sum() {
               echo $(($1+$2))
               }
             sum 10 20
         ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20/task-4$ ./passing_arguments.sh
                   30
                   
       4- Return values:
            #!/bin/bash
              square() {
              echo $(($1 * $1))
              } 
              result=$(square 5)
              echo "Square = $result"
              exit 0
       ##OUTPUT:ubuntu@ip-172-31-44-56:~/2026/day-20/task-4$ ./return_value.sh
                Square = 25
                
    5- Local variables:
         greet() {
              Local name="DevOps"
               echo $name
               }
               greet
           ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20/task-4$ ./local_variable.sh
                     Devops    

## Task 5: Text Processing Commands:
       1- grep:
           -grep error warn_logs.log
           -grep -i error warn_logs.log
           -grep -r error
           -grep -c error warn_logs.log
           -grep -n error warn_logs.log
           -grep -v error warn_logs.log
           -grep -E "error|warning" warn_logs.log

        2- awk:
            -print columns: awk '{print $1}' warn_logs.log
            -field separator: awk -F: '{print $1}' /etc/passwd
            -patterns: awk '/error/ {print}' warn_logs.log
            -BEGIN/END: awk 'BEGIN {print "start"} {print $1} END {print "done"}' warn_logs.log

        3- sed:
            -substitution: sed 's/old/new/g' warn_logs.log
            -Delete lines: sed '3d' warn_logs.log
            -In-place edit: sed -i 's/foo/bar/g' warn_logs.log

        4- cut:
            -cut -d: -f1 /etc/passwd

        5- sort:
            -alphabetical: sort warn_logs.log
            -numerical: sort-n warn_logs.log
            -reverse: sort -r warn_logs.log
            -unique: sort -u warn_logs.log
            

         6- uniq:  
             -deduplicate: uniq file.txt
             -count: uniq -c file.txt

         7- tr:
             -Lowercase to uppercase: echo "linux" | tr a-z A-Z
             -Delete characters: echo "abc123" | tr -d 0-9

         8- wc:
             -wc file.txt
             -line: wc -l file.txt
             -word: wc -w file.txt
             -chart count: wc -c file.txt

         9- head: first/last N lines
             -head file.txt
             -head -5 file.txt

         10-Tail: first/last N lines
            -tail file.txt
            -tail -5 file.txt
            -follow mode: tail -f app.log

## Task 6: Useful Patterns and One-Liners:
        1- delete files older than 7 days
             find . -type f -mtime +7 -delete
            
        2- Count lines in all .log files.
              wc -l *.log

        3- Replace a string across files.
             sed -i 's/localhost/server1/g' *.conf

        4- Check Service Status.
             systemctl status nginx

        5- disk usage with alerts.
            df -h | awk '$5+0 > 80'

        6- Parse JSON.
             jq '.name' file.json

        7- Real-Time Error Monitoring.
              tail -f app.log | grep ERROR


## Task 7: Error Handling and Debugging:
          1- Exit codes:
               success:
               Exit 0
               failure:
               exit 1
               Last command Status:
               echo $?

            2- set -e:
                exit on first error: set -e

            3- set -u:
                treat unset variables as error: set -u

            4- set -o pipefail:
                 catch errors in pipes: set -o pipefail

            5- set -x:
               debug mode: set -x

            6- Trap:
                Run cleanup forever exit
                    cleanup() {
                       rm -f temp.txt
                       }
                       trap cleanup EXIT.
                
                 
      
       

              
            
            
              
            
               
         
            
             
           
       

         
           
         
          
          

             
             
          

            
          
