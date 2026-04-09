## Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment
       ## PART 1: Launch Cloud Instance.
          ## Step 1 - create server:
             IN AMAZONE WEB SERVICE :
             1- open EC2 dashboard
             2- Launch instance
             3- select OS : ununtu 24.04 
             4- instance tyep : T2.micro (frees tier)
             5- create key pair :geet-key.pem
             Download it.
          ## Step 2 - Configure security group 
             1- allow SSH -22 & HTTP - 80

       ## PART 2: Connect via SSH :
             1-In terminal: chmod 400 geet-key.pem
             2- Connect -ssh -i my-key.pem ubuntu@3.25.45.100
       ## SCREEN SHORT NEED

       ##PART 3: Update server :
             1- sudo apt update
             2- sudo apt upgrate -y

       ## PART 4 : Install docker :
             1- Install docker :sudo apt install docker.io -y 
             2- Start docker :  sudo systemctl start docker.
       
