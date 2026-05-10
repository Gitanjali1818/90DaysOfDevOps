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
      OUTPUT:


      2- 
             
      
        
            



   
    











    

     
    



   
