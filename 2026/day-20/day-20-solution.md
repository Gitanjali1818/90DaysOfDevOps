## Day 20 – Bash Scripting Challenge: Log Analyzer and Report Generator:

##STEP-1
      ## 2026/
           └── day-20/
           ├── log_analyzer.sh
           ├── sample_log.log
           ├── sample_logs_generator.sh
           └── day-20-solution.md
        1- cd ~/2026/day-20
        2- vim sample_logs_generator.sh
        3- chmod +x sample_logs_generator.sh
        4- ./sample_logs_generator.sh sample_log.log 200
        5- ls
        6- OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ ls
                   sample_log.log  sample_logs_generator.sh
        7- cat sample_log.log
        8- head sample_log.log- Display only the first 10 lines
           ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ head sample_log.log
                     2026-07-15 10:14:16 [WARNING]  - 5257
                     2026-07-15 10:14:16 [DEBUG]  - 16434
                     2026-07-15 10:14:16 [ERROR] Out of memory - 13023
                     2026-07-15 10:14:16 [INFO]  - 25496
                     2026-07-15 10:14:16 [WARNING]  - 9675
                     2026-07-15 10:14:16 [WARNING]  - 16183
                     2026-07-15 10:14:16 [ERROR] Failed to connect - 5186
                     2026-07-15 10:14:16 [ERROR] Disk full - 8299
                     2026-07-15 10:14:16 [WARNING]  - 28638
                     2026-07-15 10:14:16 [DEBUG]  - 30509

        9- tail sample_log.log- Display the last 10 lines
            ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ tail sample_log.log
                      2026-07-15 10:14:16 [DEBUG]  - 21069
                      2026-07-15 10:14:16 [CRITICAL]  - 1465
                      2026-07-15 10:14:16 [DEBUG]  - 8780
                      2026-07-15 10:14:16 [CRITICAL]  - 6268
                      2026-07-15 10:14:16 [ERROR] Failed to connect - 32297
                      2026-07-15 10:14:16 [INFO]  - 9880
                      2026-07-15 10:14:16 [ERROR] Failed to connect - 26313
                      2026-07-15 10:14:16 [ERROR] Failed to connect - 21559
                      2026-07-15 10:14:16 [WARNING]  - 19874
                      2026-07-15 10:14:16 [WARNING]  - 29452

       ##STEP-2- Create the Script File
        1- touch log_analyzer.sh
        2- chmod +x log_analyzer.sh
        3- vim log_analyzer.sh 

        4- #!/bin/bash- At the top of the file, add....

## Task 1: Input and Validation:
        1- Accept the path to a log file as a command-line argument.
           - $1- $1 represents the first command-line argument.
           - ./log_analyzer.sh sample_log.log
           - sample_log.log (it is the input)
           - first argument: $1 = sample_log.log
           - #!/bin/bash
             LOG_FILE=$1
           ## Check if an Argument Was Provided
           - syntax:
                    if [ $# -eq 0 ]
                       then
                      echo "Please provide a log file."
                      exit 1
                   fi
             ($#- No. of arguments)
            - ./log_analyzer.sh
            - OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ ./log_analyzer.sh
                      Please provide a log file.
            - Stops the script because an error occurred.

            ## Check if the File Exists:
              -Syntax: LOG_FILE=$1
                     if [ ! -f "$LOGFILE" ]
                          then
                         echo "File does not exist."
                         exit 1
                      fi
                    (!- not)  
              - ./log_analyzer.sh sample_log.log
             - OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ ./log_analyzer.sh sample_log.log
                       (No output because validation pass and script reaches the end)



## Task 2: Error Count:
          1- Print the total error count to the console
             -grep -E "ERROR|Failed" sample_log.log
             
          2- Count the total number of lines containing the keyword ERROR or Failed
             -grep -c counts the no. of lines containing the word ERROR.     
             -grep -E "ERROR|Failed" sample_log.log
             ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ echo "Total Errors: $ERROR_COUNT"
                       Total Errors: 42

## Task 3: Critical Events:
          1- Search for lines containing the keyword CRITICAL
             - grep -nc "CRITICAL" sample_log.log
             ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ grep -nc "CRITICAL" sample_log.log
                       38
                        OR
           2- vim log_analyzer.sh
              ##SYNTAX:
                    echo "========Critical Events========"
                    grep -nc "CRITICAL" "$LOGFILE"
               - ./log_analyzer.sh sample_log.log
               ##OUTPUT: ========CRITICAL EVENTS========
                         38    
          
           2- Print those lines along with their line number
             - grep -nc "CRITICAL" sample_log.log
             ##OUTPUT: 38

## Task 4: Top Error Messages:
         1- Extract all lines containing ERROR
            - grep "ERROR" sample_log.log
            - grep -nc "ERROR" sample_log.log
            ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ grep -nc "ERROR" sample_log.log
                      42

         2- Identify the top 5 most common error messages
           - grep "ERROR" "sample_log.log" |awk '{$1=$2=$3="";print}' | sort | uniq -c | sort -rn | head -5
           -Explantion:
             - grep- select only ERROR lines
             - awk- Removes the data time and log level
             - sort- sorts the message alphabetically
             - uniq -c- counts how many times each message appears
             - sort -rn- sorts by count
             - head -5- shows the only top 5
            -OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ grep "ERROR" "sample_log.log" |awk '{$1=$2=$3="";print}' | sort | uniq -c | sort -rn | head -5
                     1    Segmentation fault - 30726
                     1    Segmentation fault - 26836
                     1    Segmentation fault - 24844
                     1    Segmentation fault - 13983
                     1    Segmentation fault - 1045

         3- Display them with their occurrence count, sorted in descending order
            - grep "ERROR" "sample_log.log" | awk '{$1=$2=$3="";print}' | sort |uniq -c | sort -rn
            -OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ grep "ERROR" "sample_log.log" | awk '{$1=$2=$3="";print}' | sort |uniq -c | sort -rn
                     1    Segmentation fault - 30726
                     1    Segmentation fault - 26836
                     1    Segmentation fault - 24844
                     1    Segmentation fault - 13983
                     1    Segmentation fault - 1045
                     1    Out of memory - 7370
                     1    Out of memory - 31532
                     1    Out of memory - 31157
                     1    Out of memory - 30486
                     1    Out of memory - 20347
                     1    Out of memory - 16605
                     1    Out of memory - 13023
                     1    Invalid input - 7745
                     1    Invalid input - 536
                     1    Invalid input - 5325
                     1    Invalid input - 28103
                     1    Invalid input - 22669
                     1    Invalid input - 21620
                     1    Invalid input - 1780
                     1    Invalid input - 15911
                     1    Failed to connect - 7779
                     1    Failed to connect - 5186
                     1    Failed to connect - 32297
                     1    Failed to connect - 28821
                     1    Failed to connect - 26313
                     1    Failed to connect - 21559
                     1    Failed to connect - 20382
                     1    Failed to connect - 20125
                     1    Failed to connect - 17632
                     1    Failed to connect - 16127
                     1    Failed to connect - 15190
                     1    Failed to connect - 1449
                     1    Failed to connect - 14254
                     1    Failed to connect - 13353
                     1    Failed to connect - 1122
                     1    Disk full - 8299
                     1    Disk full - 6251
                     1    Disk full - 6145
                     1    Disk full - 5586
                     1    Disk full - 30468
                     1    Disk full - 21898
                     1    Disk full - 15965


## Task 5: Summary Report:
          1- Generate a summary report to a text file named log_report_<date>.txt (e.g., 
             log_report_2026-02-11.txt). The report should include:
             1- Date of analysis- echo "Date of Analysis : $(date +%Y-%m-%d)" > "$REPORT"
                ##OUTPUT: -rw-rw-r-- 1 ubuntu ubuntu   30 Jul 15 12:07 log_report_2026-07-15.txt  
             2- Log file name- echo "Log File Name: sample_log.log" >> "$REPORT"
                ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ cat log_report_2026-07-15.txt
                          Date of Analysis : 2026-07-15
                          Log File Name: sample_log.log
             3- Total lines processed- echo "Total Lines Processed: $(wc -l < "$LOGFILE")" >> "$REPORT"
                ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ cat log_report_2026-07-15.txt
                          Date of Analysis : 2026-07-15
                          Log File Name: sample_log.log
                          Total Lines Processed: 200
             4- Total error count- echo "Total Error Count: $(grep -Ec "ERROR|Failed" "$LOGFILE")" >> "$REPORT"
                ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-20$ cat log_report_2026-07-15.txt
                          Date of Analysis : 2026-07-15
                          Log File Name: sample_log.log
                          Total Lines Processed: 200
                          Total Error Count: 42
             5- Top 5 error messages with their occurrence count-  echo "" >> "$REPORT"
                                                                   echo "Top 5 Error Messages:" >> "$REPORT"
                                                                   grep "ERROR" "$LOGFILE" | awk '{$1=$2=$3=""; print}' | sort | uniq -c | sort -rn | head -5 >> "$REPORT"
                ##OUTPUT: Top 5 Error Messages:
                          1    Segmentation fault - 30726
                          1    Segmentation fault - 26836
                          1    Segmentation fault - 24844
                          1    Segmentation fault - 13983
                          1    Segmentation fault - 1045

             6- List of critical events with line numbers-  echo "" >> "$REPORT"
                                                            echo "Critical Events:" >> "$REPORT"
                                                            grep -n "CRITICAL" "$LOGFILE" >> "$REPORT"
 
                 ##OUTPUT: 38 (There is a 38 lines so i only put no.)

## Task 6 (Optional): Archive Processed Logs:
         1- Create an archive/ directory if it doesn't exist
            -mkdir -p archive
         2- Move the processed log file into archive/ after analysis
            -mv "$LOG_FILE" archive/
         3- Print a confirmation message
           -echo "Log file moved to archive successfully."
        ## Final Run:
           -./log_analyzer.sh sample_log.log
           - cat log_report_2026-07-14.txt
        
          

