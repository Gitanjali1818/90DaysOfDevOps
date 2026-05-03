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

     Output: hello,devops!            

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
       

       Output: Hello, I am Geet and I am a DevOps Engineer

    2- using single quotes vs double quotes:
       Script: echo 'hello $NAME'
       (Output: hello, $NAME) 
               echo "hello $NAME"
       (Output: hello, Geet)

## Task 3: User Input with read:
     1- Create read.sh. Asks the user for their name & Asks for their favourite tool.
        Script: #!/bin/bash
                   read -p "Enter your name:" NAME
                   read -p "Enter your favourite tool:" TOOL

                   echo "Hello $name, your favourite tool is $tool"

        Output:hello, geet, your favourite tool is git

## Task 4: If-Else Conditions:
     1- Create check_number.sh. Takes a number using read & Prints whether it is positive, negative, or zero.
        Script: #!/bin/bash
               read -p "ente a number:" NUM
               if 
                  [$NUM -gt 0] then
                     echo "Positive number"
               elif [$NUM -lt 0] then
                     echo "Negative number"  
               else
                      echo "zero"
               fi

          OUTPUT:enter a number:5
                 positive number
                 enter a number:-6
                 negative number
                 enter a number:0
                 zero

      2- Create file_check.sh. Asks for a filename & Checks if the file exists using -f. Prints appropriate message
         Scripts: #!/bin/bash
              read -p "Enter a filename:" FILE
              if 
                  [-f "$FILE"]; then
                     echo "file exists"
             else
                     echo "file does not exists"
             fi

          OUTPUT:enter the file name:file_check.sh
                  file doesn't exists

## Task 5: Combine It All:
    1- Create server_check.sh. Store a service name in a variable. Asks the User, If y-runs then go to check systectl status, If no the print Skipped.
       Scripts: #!/bin/bash
                # This script takes the package name from user.
                 read -p "enter the $package_name:" package_name
                 sudo apt get update 
                 sudo apt install $package_name -y
                 echo "updating system and installing $package_name"
                 read -p "enter the $service_name:" service_name
                 sudo systemctl start $service_name
                 sudo systemctl status $service_name
       OUTPUT:   
              enter the :package_name: docker.io
              enter the :service_name: docker
                   ● ip-172-31-44-56
                     State: running
              
            
                 

               
         
        
          
               
              
                     
     
      
       

               
       
    
           
   
