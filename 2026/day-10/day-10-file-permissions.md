## Day 10 – File Permissions & File Operations Challenge ##

## Task 1: Create files:
    ## Create Files :
      1- touch devops.txt
      2- echo "this is my devops notes file" > notes.txt
      3- vim script.sh 
         - echo "hello devops"
    ## check permission :
       1- ls -l 
        screenshot of showing permission.

## Task 2: Read Files:
      1- cat nots.txt
      2- vim -R scrip.sh
      3- head -5 /etc/passwd
      4- tail -5 /etc/passwd 

## Task 3: Understand Permissions:
      1- ls -l
         output:
           -rw-r--r--  devops.txt
           -rw-r--r--  notes.txt
           -rw-r--r--  script.sh

## Task 4: Modify Permissions:
     1- Make script executable
       -chmod +X scrip.sh
       - ./script.sh 
     2- Make devops.txt read-only
       - chmod -w devops.txt
     3- Set notes.txt to 640
       - chmod 640 notes.txt
     4- Create directory with 755
      - mkdir project
      - chmod 755 project
      -ls -l - verify
      - ls -ld project - verify

## Task 5: Test Permissions:
    1- Try writing to read-only file
      - echo "test">> devops.txt - 
        **Permission denied**
    2- Try executing without permission
      - chmod -X script.sh
      - ./script.sh
      **Permission denied**

## Documentation ##
     # Day 10 Challenge

     ## Files Created
         - devops.txt
         - notes.txt
         - script.sh
         - project/ (directory)

     ## Permission Changes

     ### devops.txt
        Before: -rw-r--r--
        After:  -r--r--r--
        → Read-only for all users

    ### notes.txt
       Before: -rw-r--r--
       After:  -rw-r-----
       → Owner: read/write, Group: read, Others: none

    ### script.sh
      Before: -rw-r--r--
      After:  -rwxr-xr-x
      → Executable by all users

    ### project directory
       Permissions: drwxr-xr-x (755)

    ## Commands Used
       - touch devops.txt
       - echo "text" > notes.txt
       - vim script.sh
       - cat notes.txt
       - vim -R script.sh
       - head -n 5 /etc/passwd
       - tail -n 5 /etc/passwd
       - chmod +x script.sh
       - chmod -w devops.txt
       - chmod 640 notes.txt
       - mkdir project
       - chmod 755 project
       - ls -l

    ## What I Learned
         1. Linux file permissions control access using read, write, execute.
         2. chmod can modify permissions using symbolic (+x, -w) and numeric (755, 640) modes.
         3. Without execute permission, scripts cannot run even if readable.
      
      
      
       
           
      

      
        

        
      
