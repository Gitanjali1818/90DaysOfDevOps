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
                          

                         
        
    
    



    
     
       
