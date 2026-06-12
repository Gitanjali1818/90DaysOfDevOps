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
             
             
             
               
   
