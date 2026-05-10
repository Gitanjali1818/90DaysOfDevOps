## Day 17 – Shell Scripting: Loops, Arguments & Error Handling

## Task 1: For Loop : 

    1- Create for_loop.sh that: Loops through a list of 5 fruits and prints each one

        ##Script:
        
        #!/bin/bash
        fruits=("Mango" "Banana" "Apple" "Avacado" "Orange")
        for fruit in "${fruits[@]}"
        do
        echo "fruit: $fruit"
        done 
        Bash : chmod +x for_loop.sh
               ./for_loop.sh

        OUTPUT:
    
    2- Create count.sh that: Prints numbers 1 to 10 using a for loop

        ##Script:
        
        #!/bin/bash
        for i in {1..10}
        do
        echo $i
        done
        Bash: chmod +x count.sh
              ./count.sh

        OUTPUT:     

## Task 2: While Loop:

    1- Create countdown.sh that : 1- Takes a number from the user  
                                  2- Counts down to 0 using a while loop 
                                  3- Prints "Done!" at the end
                                  
       ##Script:
       
       #!/bin/bash   
       read -p "Enter a number: " number
       while [ $number gt 0 ]
       do
         echo $number
         number=$((number - 1))
       done
          echo "Done!"

       Bash : chmod +x countdown.sh
              ./countdown.sh

       OUTPUT:


## Task 3: Command-Line Arguments:

     1- Create greet.sh that: 1- Accepts a name as $1
                              2- Prints Hello, <name>!
                              3- If no argument is passed, prints "Usage: ./greet.sh "

     ## Script:

     #!/bin/bash
      if [ $# -eq 0]
      then 
         echo "usage: ./greet.sh <name>"
      else
          echo "hello, $1!"
      fi

      Bash: chmod +x greet.sh
             ./greet.sh
      OUTPUT:1-  1- ./greet.sh Gitanjali
                     O/P: Hello, Gitanjali!
                 2- ./greet.sh
                     O/P: "usage: ./greet.sh <name>"


      2- Create args_demo.sh that : 1- Prints total number of arguments ($#)
                                    2- Prints all arguments ($@)
                                    3- Prints the script name ($0)

         ##Script:
            #!/bin/bash

            echo "script name: $0"
            echo "total arguments: $#"
            echo "all arguments: $@"

            OUTPUT: 1- ./args_demo.sh dev prod test pre-prod
                     O/P: Script name: ./args_demo.sh
                           Total arguments: 4
                           All arguments: dev prod test pre-prod

## Task 4: Install Packages via Script:

       1- Create install_packages.sh that: 1- Defines a list of packages: nginx, curl, wget
                                           2- Loops through the list
                                           3- Checks if each package is installed (use dpkg -s or rpm -q)
                                           4- Installs it if missing, skips if already present
                                           5- Prints status for each package

      ##Script:
        #!/bin/bash

          #Exit if not root

          if [ "$EUID" -ne 0 ]
          then
              echo "Please run this script as a root"
           exit 1
           fi

           packages=("nginx" "curl" "wget")
            for package in "${package [@]}"
           do 
               if dpkg -s $packages  >= /dev/null
           then
               echo "$package is already installed. skipping..."
           else
               echo "$package is installed. Installing... "

               apt update -y
               apt install $package -y

              if [ $? -eq 0 ] 
                 then
                    echo "$package installed successfully."
                 else
                    echo "failed to installed $package."
                 fi
             fi   
           done   

           Bash: 1- chmod +x install_packages.sh
                 2- sudo ./install_packages.sh
                 
           OUTPUT: nginx is already installed. Skipping...
                   curl is already installed. Skipping...
                   wget is not installed. Installing...
                   wget installed successfully.  


## Task 5: Error Handling :
       1- Create safe_script.sh that: 1- Uses set -e at the top (exit on error)
                                      2- Tries to create a directory /tmp/devops-test
                                      3- Tries to navigate into it
                                      4- Creates a file inside
                                      5- Uses || operator to print an error if any step fails 

       ## Script:
          #!/bin/bash
             set -e
             mkdir /tmp/devops-test || echo "Directory already exists"  
             cd /tmp/devops-test || {
                  echo "Failed to navigate to directory"
                  exit 1
               }
              touch demo.txt || {
                 echo "failed to create file"
                 exit 1
              }
                echo "file created successfully"

            

          





                   
            

             
         

                                           

                                           



                  
            
            
      
        
            



   
    











    

     
    



   
