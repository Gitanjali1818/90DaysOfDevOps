## Processes & Services:
        ##Processes & services:
             1- ps aux | grep nginx
             2- systemctl status nginx
             3- journalctl -u nginx.service -n 50
         ##Observations:
             ps - showing running process PID. 
             systemctl status - show service state (active/inactive).
             journalctl - show recent log if debugging.
             
         ##File skills:
             1- echo "hello its devops" >> file.txt
             2- chmod 755 file.txt
             3- chown tokyo file.txt
         ##Observations:
            echo >> - appends contents.
            chmod - changes permision
            chown - change owner

         ##Cheat sheet refresh :
             1- ls -l - check file & permissions
             2- cd - nevigate directories
             3- cp - copy file
             4- mkdir - create directories
             5- rm - delete files

          ##User/group sanity:
             1- sudo useradd tokyo
             2- sudo chown berlin file1.txt
             3- id tokyo
             4- ls -l file1.txt

## Mini Self-Check:
          ##Most Useful Commands:
             1- ls -l - check permissions quickely.
             2- systemctl status - check the status of service.
             3- chown - change owner.
             
           ##How to Check Service Health:
              1- sytemctl status nginx
              2- ps aux | grep nginx
              3- journalctl -u nginx.services

            ##Safe Ownership & Permission Change:
              1- sudo chown owner:group file.txt
              2- sudo chmod 755 file.txt

            ##Focus for Next 3 Days:
              1- practice chmod
              2- more handson with services
              3- improve troubleshooting skills

              
                        
             

             

             
             
         


             
      
          
