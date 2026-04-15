## Task 1: Check Ownership:
       1- cd ~ 
       2- ls -l 
     ##Difference Between Owner and Group :
        Owner : The user who owns the file and has primary control over it.
        Group : A set of users who share access permissions to the file.

## Task 2: Basic chown Operations:sudo chown tokyo devops-file.txt
 ##create file & Check current owner:
   1- touch devops-file.txt
   2- ls -l
 ##change owner:
   1- sudo chown tokyo devops-file.txt
   2- ls -l devops-file.txt
   3- sydo chown berlin devops-file.txt
   4- ls -l devops-file.txt

## Task 3: Basic chgrp Operations:
  ##create file:
    1- touch teams-notes.txt
    2- ls -l 
  ##create group:
    1- sudo groupadd heist-team
  ##Change group:
    1-sudo chgrp heist-team teams-notes.txt
    2- ls -l team-notes.txt

## Task 4: Combined Owner & Group Change: sudo chown owner:group filename
  ##create file:
    1- touch project-config.yaml
  ##Change owner + group:
    1- sudo chown professor:heist-team project-config.yaml
    2- ls -l project-config.yaml
  ##create directory & change owner:
    1- mkdir app-logs
    2- sudo chown berlin:heist-team app-logs
    3- ls -l all-logs

## Task 5: Recursive Ownership:
  ##Create directory structure:
    1- mkdir -p heist-project/vault
    2- mkdir -p heist-project/plans
    3- touch heist-project/vault/gold.txt
    4- touch heist-project/plans/strategy.conf
  ##create group:
    1- sudo groupadd planners 
  ##Apply recursive ownership:
    1- sudo chown -R professors:planners heist-poject/
    2- la -lR heist-project/

## Task 6: Practice Challenge:
  ##create user:
    1- sudo useradd tokyo
    2- sudo useradd berlin
    3- sudo useradd nairobi
  ##create groups:
    1- sudo groupadd vault-team
    2- sudo groupadd tech-team
  ##create directory:
    1- mkdir bank-heist
  ##Create 3 files inside:
    1- touch bank-heist/access-codes.txt
    2- touch bank-heist/blueprints.pdf
    3- touch bank-heist/escape-plan.txt
  ##Set different ownership:
    1- sudo chown tokyo:vault-team bank-heist/access-codes.txt
    2- sudo chown berlin:tech-team bank-heist/blueprints.pdf
    3- sudo chown nairobi:vault-team bank-heist/escape-plan.txt
  ##verify:
     1- ls -l bank-heist/
     
    

    
    
   
    

    
     
