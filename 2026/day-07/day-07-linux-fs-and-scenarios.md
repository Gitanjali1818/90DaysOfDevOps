#  Part 1: Linux File System Hierarchy :
        1. / (root) : The root directory is the starting point of the entire Linux filesystem.
                      ## Example files/folders:
                                              No.     Folder                	What it contains
                                              1.      /bin	              basic system commands like ls, cp, mv
                                              2.      /etc                system configuration files.
                                              3.      /home	              user home directories.
                                              4.      /var	              logs and variable system data. 
                                             
                                                                         
         2. /home : Home directories for normal users.
                      ## Example files/folders :
                                              No.     Folder                  	What it contains
                                             1.      /home/user	          home directories of user name.
                                             2.      /home/ubuntu          home directories of ubuntu name.
                                             3.      /home/devops	        home directories of devops name.                 
                                    
        3. /root : home directories of root user. (sudo ls -la /root/)                               
                    ## Example files/folders : 
                                            No.       Folder               	 What it contains
                                            1.      /root/.bashrc          A configuration file for the bash shell.
                                            2.      /root/.ssh             Folder that stores SSH keys and SSH configuration.
                                            3.      /root/scripts	         A folder where the root user may store automation scripts.
                                     

        4. /etc :  Confugaration files for the operating system and install services.
                    ## Example files/folders :
                                            No.       Folder               	 What it contains
                                            1.      /etc/hostname         A file that store the system hostname.
                                            2.      /etc/passwd           this file contain a user account information.
                                            3.      /etc/nginx	          A directories containing configuration files for the Nginx web server.

        5. /var/log : This directory containing system and application log file used for monitoring and dibugging.
                     ## Example files/folders :
                                            No.       Folder               	 What it contains
                                            1.      /var/log/syslog         Gerneral system log.
                                            2.      /var/log/auth_log       Authentication logs.
                                            3.      /var/log/nginx	        logs related to Nginx web server.

        6. /tmp : Stores temperory files created by application and the system.
                    ## Example files/folders :
                                            No.       Folder               	       What it contains
                                            1.      /tmp/snap-private-tmp          A temporary file created by an application.
                                            2.      /tmp/cashe                     A temporary folder fo cashed data.

       7. /bin :  bin stands for binary. It contains importand cammand program that linux need to run basic task.
                   ## Example files/folders :
                                           No.       Folder               	 What it contains
                                           1.      /bin/cp                 copies files
                                           2.      /bin/rm                 delete files
                                           3.      /bin/mv                 move files
                                           4.      /bin/ls                 lists the files and directories

       8. /use/bin : It cantains user level exicutable program installed by the system.
                  ## Examples files/folders :
                                           No.       Folder               	 What it contains
                                           1.      /usr/bin/git                to manage git changes.
                                           2.      /usr/bin/vim                text editor used to create and edit the files.
                                           3.      /usr/bin/python             run python program and scripts.

      9. /opt : Stores Optional or third party applications.
                 ## Examples files/folders :
                                          No.       Folder               	 What it contains
                                           1.      /opt/docker               stores software install by google
                                           2.      /opt/nginx                stores nginx related files and tools
                                           3.      /opt/docker               stores docker related files and tools.


##  Scenarios 
   ##  Scenario 1 — Service Not Starting :
            ## Step 1- To check whether service is running, stop or failed.
                    (systemctl status docker)
            ## Step 2- To check the last 50 log entries for the service.
                    (journalctl -u docker -n 50)
            ## Step 3- To verify if the service is configured to start automatically during the boot.
                     (systemctl is-enabled docker.s)
            ## Step 4- To check the service is actually install on the system and managed by the systemd.
                     (systemctl list-units --type=service)

  ## Scenario 2 - High CPU usages: The Server is slow and might have a high CPU usage.
           ## Step 1- top - Shows real time CPU usage and running processes.
           ## Step 2- htop - Provides interactive view of processes and CPU usage.
           ## Step 3- ps aux --sort=-%cpu | head -10 - list the top 10 processes consuming the most CPU. 
           ## Step 4- kill -9 <PID> - To stop the problematic processes.

## Scenario 3 - Finding Service Logs: A developer asks where docker logs are.
          ## Step 1 - systemctl status docker: show the status of docker service.
          ## Step 2 - journalctl -u docker -n 50 docker: shows the last 50 log entries.
          ## Step 3 - journalctl -u docker -f : shows the real time logs to monitor the service.

## Scenario 4: File Permissions Issue: A script at /home/user/backup.sh is can not run.
         ## Step 1 - ls -l /home/user/backup.sh : to check the permission of file.
         ## Look for - rw-r--r-- backup.sh : Notice there is no exicution on file. 
         ## Step 2 - chmod +x /home/user/backup.sh : add execute permission.
         ## step 3 - ls -l /home/user/backup.sh : verify that exicute permission has been added.
         ## Step 4 - ./backup.sh : run the script.
         

