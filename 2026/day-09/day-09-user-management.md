##  Task 1: Create Users :
      ## Create Users And Set Password With Home Directories: 
          1- sudo useradd -m tokyo : Create tokyo user
             sudo passwd tokyo : create password
          2- sudo useradd -m berlin : create berlin user
             sudo passwd berlin : create password
          3- sudo useradd -m professor : create professor user
             sudo passwd professor : create password

      ## Verify users :
          1- cat /etc/passwd | grep tokyo : 
          2- ls /home/ :

## Task 2: Create Groups :
          1- sudo groupadd developers :
          2- sudo groupadd admins :

      ## Verify :
          1- cat /etc/group | grep developers :

## Task 3: Assign to Groups :
      ## Assign users :
          1- sudo usermod -aG developers tokyo
          2- sudo usermod -aG developers berlin
          3- sudo usermod -aG admins berlin
          4- sudo usermod -aG admins professor

      ## Verify group membership :
         1- groups tokyo
         2- groups berlin
         3- groups professor 

## Task 4: Shared Directory :
      ## Create directory :
        1- sudo mkdir -p /opt/dev-project
      
      ## Change group ownership :
        1- sudo chgrp developers /opt/dev-project

      ## Set permissions :
        1- sudo chmod 775 /otp/dev-project

      ## Test as users :
        1- sudo -u tokyo touch /opt/dev-project/file1.txt
        2- sudo -u berlin touch /opt/dev-project/file2.txt

      ## Verify :
        1- ls -l /opt/dev-project

## Task 5: Team Workspace :
      ## Create user :
        1- sudo useradd -m nairobi 
        2- sudo passwd nairobi

      ## create group :
        1- sudo groupadd project-team

      ## Add users :
        1- sudo usermod -aG project-team nairobi
        2- sudo usermod -aG project-team tokyo

      ## Create directory :
        1- sudo mkdir -p /opt/team-workplace

      ## Set group + permissions :
        1- sudo chgrp project-team /opt/team-workplace
        2- sudo chmod 755 /opt/team-workplace 

      ## Test :
        1- sudo -u nairobi touch /opt/team-workplace/text.txt


## Documentation :
            # Day 09 Challenge
      
       ## Users & Groups Created
         1-Users: tokyo, berlin, professor, nairobi
         2- Groups: developers, admins, project-team
         
       ## Group Assignments
         1- tokyo → developers
         2- berlin → developers, admins
         3- professor → admins
         4- nairobi → project-team

       ## Directories Created
        1- /opt/dev-project (developers, 775)
        2- /opt/team-workspace (project-team, 775)

       ## Commands Used
          - useradd -m
          - passwd
          - groupadd
          - usermod -aG
          - chmod
          - chgrp

      ## Issue faced :
         While trying to create a file:
           1- sudo -u nairobi touch /opt/team-workplace/file3.txt :- Error:Permission denied
      ## Investigation :
           1- Checked directory permissions:ls -ld /opt/team-workplace
              output : drwxrwxr-x 2 root root ...
      ## Root Cause
           - Directory owner = root
           - Directory group = root ❌        
           - User `nairobi` belongs to group `project-team`  
      ## Conclusion :
          Since the directory belongs to `root` group, the user `nairobi` does not have write access.

     ## Solution
         - Changed group ownership:sudo chgrp project-team /opt/team-workplace    

     ## What I Learned
       1- How to manage users and groups
       2- How permissions work in shared directories.
       3- How to test access using sudo -u
       4- Directory group ownership must match user group
       5- Permissions alone are not enough
       6- Always check:
          - ls -ld <directory>
          - groups <user>
 
       


               
       


      
        
  
        

        
         
          
          












          
