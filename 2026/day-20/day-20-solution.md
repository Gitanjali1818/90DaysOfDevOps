## Day 20 – Bash Scripting Challenge: Log Analyzer and Report Generator:

## Task 1: Input and Validation:
        1- Accept the path to a log file as a command-line argument.
           - LOGFILE=$1
           - ./log_analyzer.sh sample_log.log
           - sample_log.log (it is the input)
           - first argument: $1 = sample_log.log
           - #!/bin/bash
             LOG_FILE=$1
         2- Exit with a clear error message if no argument is provided.
           - if [ $# -eq 0]; then
             echo "Error: no log file provided."
             echo "usage: ./log_analyzer.sh <log_file>"
             exit 1
             fi
            -Explanation: 
             1- $# gives the nu. of command line arguments
             2- If no argument is orivided, orint an error message and exit the script.
         3- Exit withCount the total number of lines containing the keyword ERROR or Failed a clear error message if the file doesn't exist
            -if [ ! -f "$LOGFILE"]; then
             echo "Error: FILE '$LOGFILE' does not exist."
             exit 1
             fi
            - Explanation: -f checks whether the file exists and is a regular file.


## Task 2: Error Count:
          1- Print the total error count to the console
             -grep -c "ERROR" "$LOGFILE"
             -grep -c counts the no. of lines containing the word ERROR.
          2- Count the total number of lines containing the keyword ERROR or Failed

## Task 3: Critical Events:
          1- Search for lines containing the keyword CRITICAL
             -grep -c "CRITICAL" "$LOGFILE"
          2- Print those lines along with their line number

## Task 4: Top Error Messages:
         1- Extract all lines containing ERROR
            - grep -c "ERROR" "$LOGFILE"
         2- Identify the top 5 most common error messages
           - grep "ERROR" "$LOGFILE" |awk '{$1=$2=$3=; print}' | sort | uniq -c | sort -rn | head -5
           -Explantion:
             - grep- select only ERROR lines
             - awk- Removes the data time and log level
             - sort- sorts the message alphabetically
             - uniq -c- counts how many times each message appears
             - sort -rn- sorts by count
             - head -5- shows the only top 5
            -OUTPUT:
         3- Display them with their occurrence count, sorted in descending order
            - grep "ERROR" "$LOGFILE" | awk '{$1=$2=$3="";print}' | sort |uniq -c | sort -rn
            -OUTPUT: 


## Task 5: Summary Report:
          1- Generate a summary report to a text file named log_report_<date>.txt (e.g., 
             log_report_2026-02-11.txt). The report should include:
            - ./log_analyzer.sh sample_log.log
            -OUTPUT:

## Task 6 (Optional): Archive Processed Logs:
         1- Create an archive/ directory if it doesn't exist
            -mkdir -p archive
         2- Move the processed log file into archive/ after analysis
            -mv "$LOG_FILE" archive/
         3- Print a confirmation message
           -echo "Log file moved to archive successfully."
        
          
## 1. log_analyzer.sh:
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
             TODAY=$(date +%Y-%m-%d)
             REPORT="log_report_${TODAY}.txt"
               echo "Analysing log file: $LOGFILE"
               echo

          #Total lines
             TOTAL_LINES=$( wc -l < "$LOGFILES")

          #Error count
             ERROR_COUNT=$(grep -Ei "ERROR|Failed" "$LOGFILE" | wc -l)

             echo "Total Errors: $ERROR_COUNT"
             echo
             echo "--- Critical Events ---"
             
             CRITICAL_EVENTS=$(grep -n "CRITICAL" "$LOGFILE")

             if [ -z "$CRITICAL_EVENTS" ]; then
               echo "No critical events found"
             else
               echo "$CRITICAL_EVENTS"
             fi

              echo
              echo "-----TOP 5 ERROR MESSAGE------"

              TOP_ERRORS=$(grep "ERROR" "$LOGFILE" /
                   | sed 's/.*ERROR //' \
                   | sort /
                   | unique -c /
                   | sort rn /
                   | head 05)

             if [ -z "$TOP_ERROS" ]; then
                echo "No error message found"
             else
                echo "$TOP_ERRORS"
             fi
           
           #Generate report
             {
             echo "==============================="
             echo "   LOG ANALYSYS REPORT"
             echo "==============================="
             echo "Date of analysy: $TODAY"
             echo "Log files      : $LOGFILE"
             echo "Total lines    : $TOTAL_LINES"
             echo "Error counts   : $ERROR_COUNT"

             echo
             echo "====Top 5 Error Message====="
            if [ -z "$TOP_ERRORS" ]; then
              echo "No ERROR message found"
            else
              echo "$TOP_ERRORS"
            fi

              echo
              echo "========Critical events======="
             if [ -z "$CRITICAL_EVENTS" ]  
               echo "No critical events found"
             else
               echo "$CRITICAL_EVENTS"
             fi

             } > "$REPORT"
                echo
                echo "Summary report generated: &Report"  

            # Optional Task - Archive log file
                mkdir -p archive

               mv "$LOGFILE" archive/

               echo "Processed log moved to archive/"

               

## 2. Sample Log File (sample_log.log):
     OUTPUT:


## 3. Running the Script:
     1- chmod +x log_analyzer.sh
     2- ./log_analyzer.sh sample_log.log
     3-  Sample output:
     4-  Generated Report (log_report_2026-07-29.txt

## DOCUMENTATION:
    
     
         
     
             
             
             
               
   
