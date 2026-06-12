## Day 20 – Bash Scripting Challenge: Log Analyzer and Report Generator

    1- vim log_analyzer.sh
    2- #!/bin/bash
        #Log analyzer and report generator

          #Validate input
           if [ $# eq 0 ]; then
            echo "Usage: $0 <log file>" 
            exit 1
           fi

              LOGFILE="$1"
           if [! $LOGFILE ]; then
             echo "Error: file 'LOGFILE' does not exits."
             exit 1
           fi
         #Date for file report  
   
