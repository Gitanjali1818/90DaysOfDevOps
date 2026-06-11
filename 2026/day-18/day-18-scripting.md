## Task 1: Basic Functions:
    vim functions.sh
        #!/bin/bash
         #function to greet user
         #function to add two numbers
         #function call

         greet() {
           echo "Hello, $1
           }
           add () {
            sum=(( $1 + $2))
             echo "sum = $sum"
             }
             greet Geet
              add 10 20
     OUTPUT:


## Task 2: Functions with Return Values:
    vim disk_check.sh 
       #!/bin/bash
       check_disk() {
          echo "=======DISK USAGE======="
            df -h /
            }

       check_memory() {
          echo "========CHECK MEMORY======="
            free -h
            }

        #main section
         check_disk
         echo 
         check_memory

    OUTPUT:

## Task 3: Strict Mode — set -euo pipefail
      vim strict_demo.sh
         #!/bin/bash

         set -euo pipeline 

         echo "Testing set -u"
         echo "$NAME"

         echo "Testing set -e"
         mkdir test
         false

         echo "Testing pipefails"
         cat file.txt | grep "abc"


     ## What Happens? ##
     1- set -u : Undefined variable causes error.
       OUTPUT:

     2- set -e : Script exits immediately when a command fails.
       OUTPUT:

     3- set -o pipefail : If cat file.txt fails, the pipeline may still succeed.
                          With pipefail, failure of any command in pipeline causes entire pipeline to fail. 

     ## DOCUMENTS:
     1- set -u: Treat undefined variables as errors.
     2- set -e: Exit immediately if any command returns a non-zero status.
     3- set -o pipefail: Pipeline returns failure if any command inside it fails.


## Task 4: Local Variables:
    vim local_demo.sh
      #!/bin/bash
       #using local variables
       #without local variables

          show_local() {
           local message="Inside functions"
           echo "$messages"
           }

           show_global() {
           text="Global Variable"
           echo "$text"
           }

           show_local

           echo "Outside functions"
           echo "${message:- variable not accesible}"

           echo

           show_global
           echo "Outside functions:"
           echo "$text"


    OUTPUT:
          Inside Function
          Outside function:
          Variable not accessible

         Global Variable
         Outside function:
         Global Variable



## Task 5: Build a Script — System Info Reporter:
    vim system_info.sh
      #!/bin/bash

      set -euo pipefail

      #hostname and OS info

        system_info() {
          echo "========SYSTEM INFORMATION========"
            echo "hostname : $(hostname)"
            echo "OS : $(grep PRETTY_NAME /etc/os-release | cut -d= -f2 | tr -d '"')"
            }

       #uptime

          show_uptime() {
            echo
            echo "=========UPTIME========"
             uptime -p
             }

       #Disk Usage:
          disk_usage() {
          echo
          echo "=========TOP 5 FILESYSTEM USAGE======="
            df -h | head -n 6
            }

       #Memory Usage 
         memory_usage() {
           echo
           echo "========MEMORY USAGE======="
           free -h
           }

       #Top 5 CPU processes
         main () {
           system_info
           show_uptime
           disk_usage
           memory_usage
           cpu_processes

           }
           main


OUTPUT:








## What i learned:

     1- Functions make scripts reusable.
        1- Functions reduce duplicate code.
        2- Arguments are passed using $1, $2, etc.

     2- Local variables improve scope.
        1- Variables declared with local exist only inside functions.
        2- Prevent accidental modification of global variables.

     3- set -euo pipefail makes scripts safer.
        1- -e → Exit on command failure.
        2- -u → Error on undefined variables.
        3- pipefail → Detect failures inside pipelines.

    
         
            
         
      
         


         

           
           
     
     
     
     
                          

                         
        
    
    



    
     
       
