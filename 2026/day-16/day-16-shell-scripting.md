## Day 16 – Shell Scripting Basics:
   1- shebang - #!/bin/bash 
   2- why shebang matters :
          without shebang system may use default shell this can break your script.

   3- Variables, echo, read
   4- if-else condition

## Task 1: Your First Script:
   1- Create a file hello.sh & Print Hello, DevOps! using echo.Make it executable and run it.
     Bash command: vim hello.sh
     Script:    #!/bin/bash
                  echo "hello, Devops!"
     Bash command: chmod +X hello.sh
                   ./hello.sh

     Output:              

    2-  What happens if you remove the shebang line?
        1- Without shebang the system decides which shell to use.
        2- Most of the time it uses the default shell.
        3- Bash and sh are different, some commands run in bash but not in sh.
           so script may be fail OR give unexpected output.

## Task 2: Variables: 
    1- Create variables.sh with your NAME, your ROLE.
       Bash command: vim variables.sh
       Script: #!/bin/bash
               NAME: Geet
               ROLE: "DevOps Engineer"
               echo "Hello, I am $NAME and I am a $ROLE"
       Bash command: ./variables.sh

       Output:

    2- using single quotes vs double quotes:
       Script: echo 'hello $NAME'
       (Output: Hello $NAME) 
               echo "hello $NAME"
       (Output: Hello Geet)

## Task 3: User Input with read:
     1- Create read.sh. Asks the user for their name & Asks for their favourite tool.
        Script: #!/bin/bash
                   read -p "Enter your name:" NAME
                   read -p "Enter your favourite tool:" TOOL

                   echo "Hello $name, your favourite tool is $tool"

        Output:

## Task 4: If-Else Conditions:
     1- Create check_number.sh. Takes a number using read & Prints whether it is positive, negative, or zero.
        Script: 
     
        
       

               
       
    
           
   
