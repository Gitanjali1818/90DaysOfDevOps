## Day 18 – Shell Scripting: Functions & intermediate Concepts:


## Task 1: Basic Functions:
   1- vim functions.sh
        #!/bin/bash
         #function to greet user
         #function to add two numbers
         #function call

         greet() {
           echo "Hello, $1"
           }
           add () {
            sum=($1+$2)
             echo "sum = $sum"
             }
             greet Geet
              add 10 20
       2- chmod 775 function.sh
       3- ./functions.sh
     OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-18$ ./functions.sh
                                                hello, Geet
                                                sum = 10+20


## Task 2: Functions with Return Values:
   1- vim disk_check.sh 
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
    2- chmod 755 disk_check.sh
    3- ./disk_check.sh

    OUTPUT:  ubuntu@ip-172-31-44-56:~/2026/day-18$ ./disk_check.sh
                        =======DISK USAGE======
             Filesystem      Size  Used Avail Use% Mounted on
                       /dev/root       6.7G  3.0G  3.7G  46% /

                        ====CHECK MEMORY=====
                     total        used        free      shared  buff/cache   available
      Mem:           908Mi       380Mi       141Mi       2.8Mi       517Mi       528Mi
      Swap:             0B          0B          0B
      
## Task 3: Strict Mode — set -euo pipefail
      vim strict_demo.sh
         #!/bin/bash

         set -euo pipefail 

         echo "Testing set -u"
         echo "$NAME"

         echo "Testing set -e"
         mkdir test
         false

         echo "Testing pipefails"
         cat file.txt | grep "abc"


     ## What Happens? ##
     1-OUTPUT: Testing set -u
              ./strict_demo.sh: line 6: NAME: unbound variable
              1-after define a name variable,
              OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-18$ ./strict_demo.sh
                      Testing set -u
                      Gitanjali
                      Testing set -e        

     2- set -e : Script exits immediately when a command fails.
       OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-18$ ./strict_demo.sh
               Testing set -u
               Gitanjali
               Testing set -e
               mkdir: test: File exists
            1- after adding rm -rf test command.
            OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-18$ ./strict_demo.sh
                    Testing set -u
                    Gitanjali
                    Testing set -e
                    created dir successfully

     3- set -o pipefail : If cat file.txt fails, the pipeline may still succeed.
                          With pipefail, failure of any command in pipeline causes entire pipeline to fail. 

     ## DOCUMENTS:
     1- set -u: Treat undefined variables as errors.
     2- set -e: Exit immediately if any command returns a non-zero status.
     3- set -o pipefail: Pipeline returns failure if any command inside it fails.

     ##Edited Script:
        #!/bin/bash

         set -euo pipefail

         NAME="Gitanjali"

         echo "Testing set -u"
         echo "$NAME"

        echo "Testing set -e"
        rm -rf test
        mkdir test
        echo "created dir successfully"

        false

        echo
        echo "Testing pipefails"
        cat file.txt | grep "abc"
        echo "This line will not execute"
      


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

           show_local () {

           echo "Outside functions"
           echo "${message:- variable not accesible}"
           }
           echo

           show_global
           echo "Outside functions:"
           echo "$text"


    OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-18$ ./local_demo.sh
            Inside function
            outside function
            variable not accesible

            Global variable
            Outside functions
            Global variable
          



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

       #CPU PROcesses
         cpu_processes() {
         echo
         echo "=====CPU PROCESSES====="
         ps aux --sort%=-cpu | head
         }

       #Top 5 CPU processes
         main () {
           system_info
           show_uptime
           disk_usage
           memory_usage
           }
           main
     OUTPUT:                      =====CPU PROCESSES=====
             USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
             root           3  0.0  0.0      0     0 ?        S    Jul01   0:00 [pool_workqueue_release]
             root           4  0.0  0.0      0     0 ?        I<   Jul01   0:00 [kworker/R-rcu_gp]
             root           5  0.0  0.0      0     0 ?        I<   Jul01   0:00 [kworker/R-sync_wq]
             root           6  0.0  0.0      0     0 ?        I<   Jul01   0:00 [kworker/R-kvfree_rcu_reclaim]
             root           7  0.0  0.0      0     0 ?        I<   Jul01   0:00 [kworker/R-slub_flushwq]
             root           8  0.0  0.0      0     0 ?        I<   Jul01   0:00 [kworker/R-netns]
             root          10  0.0  0.0      0     0 ?        I<   Jul01   0:00 [kworker/0:0H-kblockd]
             root          13  0.0  0.0      0     0 ?        I<   Jul01   0:00 [kworker/R-mm_percpu_wq]
             root          16  0.0  0.0      0     0 ?        S    Jul01   0:00 [rcu_exp_par_gp_kthread_worker/0]
                                ======SYSTEM INFO=====
             hostname : ip-172-31-44-56
                 tr: missing operand
                Try 'tr --help' for more information.
                OS :

                          ====UPTIME====
                up 3 days, 21 hours, 44 minutes

                 =====TOP 5 FILE SYSTEM USAGE====
         Filesystem       Size  Used Avail Use% Mounted on
        /dev/root        6.7G  3.0G  3.7G  46% /
        tmpfs            455M     0  455M   0% /dev/shm
        tmpfs            182M  948K  181M   1% /run
        efivarfs         128K  3.3K  120K   3% /sys/firmware/efi/efivars
        tmpfs            455M     0  455M   0% /tmp

                  =====MEMORY USAGE=====
               total        used        free      shared  buff/cache   available
               Mem:           908Mi       375Mi       182Mi       2.8Mi       481Mi       533Mi
               Swap:             0B          0B          0B


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

    
         
            
         
      
         


         

           
           
     
     
     
     
                          

                         
        
    
    



    
     
       
