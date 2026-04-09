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
             3- enable docker : sudo systemctl enable docker.
             4- check docker service : docker --version

      ## PART 5 : Install NGINX :
             1- Install Nginx : sudo apt install nginx -y
             2 - Start nginx : sudo systemctl start nginx
             3- enable nginx : sudo systemctl enable nginx 
             4 - check nginx : sudo systemctl status nginx

     ## PART 6 : Test website :
             1- open browser : http:// ip address
             2- see : Welcome to nginx!
     ## screenshot needed :

     ##PART 7 : View logs :
             1- Nginx logs are stored in : /var/log/nginx/
             2- check log : cat /var/log/nginx/access.log

    ## PART 8 : Save logs to file :
             1- Create log file : cp /var/log/nginx/access.log ~/nginx-log.txt 
             2- verify log file : cat ~/nginx-log.txt
    ## Screenshot needed :

    ## PART 9 : Download log file to local machine : scp -i my-key.pem ubuntu@YOUR_SERVER_IP:~/nginx-logs.txt .

## Commands Used :
                ssh -i geet-key.pem ubuntu@server-ip
                sudo apt update
                sudo apt install docker.io -y
                sudo systemctl start docker
                sudo apt install nginx -y
                sudo systemctl start nginx
                systemctl status nginx
                cat /var/log/nginx/access.log
                cp /var/log/nginx/access.log ~/nginx-logs.txt
                scp -i my-key.pem ubuntu@server-ip:~/nginx-logs.txt .

## Challenges Faced:
               1- i could not access the nginx page from browser.
               2- port 80 is not allowed in the security group after adding http rule the page is accessible.

## What I Learned:
              1- How to install and manage services
              2- How to view and extract logs
              3- Basic cloud security.
              4- Download Log File to Local Machine.

         
             
       
