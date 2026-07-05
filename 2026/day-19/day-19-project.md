## Day 19 – Shell Scripting Project: Log Rotation, Backup & Crontab

## Task 1: Log Rotation Script
     1- vim log_rotate.sh
     2-  #!/bin/bash
           set -euo pipefail

     # Check argument
        if [ $# -ne 1 ]; then
           echo "Usage: $0 <log_directory>"
           exit 1
        fi   

        LOG_DIR="$1"

      # Count .log files older than 7 days  
          compressed_count=$(find "$LOG_DIR" -type f -name "*.log" -mtime +7 | wc -l)

      # Compress them
         find "$LOG_DIR" -type f -name "*.log" -mtime +7 -exec gzip {} \;

      # Count .gz files older than 30 days
         deleted_count=$(find "$LOG_DIR" -type f -name "*.gz" -mtime +30 | wc -l)   

      # Delete old archives
         find "$LOG_DIR" -type f -name "*.gz" -mtime +30 -delete

         echo "Compressed files : $compressed_count"
         echo "Deleted files    : $deleted_count"

     3- chmod +x log_rotate.sh
        sudo ./log_rotate.sh /var/log   
     
     4- OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-19$ sudo ./log_rotate.sh /var/log
                Compressed files : 3
                Deleted files    : 22

## Task 2: Server Backup Script:
      1- vim backup.sh
      2- #!/bin/bash
           set -euo pipefail
            if [ $# -ne 2 ]; then
                echo "usage: $0 <source_directory> <backup_destination>"
                exit 1
            fi 

            SOURCE_DIR="$1"
            DEST_DIR="$2"
            
      #Verify source directory
           if [ ! -d "SOURCE_DIR" ]; then
              echo "Error: Source directory does not exist."
              exit 1
           fi

       #Create destination if missing
            mkdir -p "DEST_DIR"

            TIMESTAMP=$(date +%Y-%m-%d-%H-%M-%S)
            ARCHIVE_NAME="backup-$TIMESTAMP.tar.gz"

            tar -czf "$DEST_DIR/$ARCHIVE_NAME" "$SOURCE_DIR"

       #Verify archive creation
          if [-f "$DEST_DIR/$ARCHIVE_NAME" ]; then
            size=$ ( du -h "$DEST_DIR/$ARCHIEVE_NAME" | cut -f1)

            echo "Backup created successfully."
            echo "Archive: $ARCHIVE_NAME"
            echo "Size: $size"
          else
            echo "backup creation failed."
            exit 1
          fi

       # Delete backups older than 14 days
           find "$DEST_DIR" -type f -name "backup-*.tar.gz" -mtime +14 -delete

    3- chmod +x backup.sh
        ./backup.sh /home/ubuntu/data /home/ubuntu/backups    


## Task 3: Crontab:

        1- Check current schedules
            crontab -l

        2- Run log_rotate.sh daily at 2 AM
            0 2 * * * /home/ubuntu/2026/day-19/log_rotate.sh /var/log/myapp  

        3- Run backup.sh every Sunday at 3 AM
             0 3 * * 0 /home/ubuntu/2026/day-19/backup.sh /home/ubuntu/data /home/ubuntu/backups

        4- Run health check every 5 minutes
              */5 * * * * /home/ubuntu/2026/day-19/health_check.sh


## Task 4: Combined Scheduled Maintenance Script:

    1- vim maintance.sh
        
    2-  #!/bin/bash

          set -euo pipefail

          LOG_FILE="var/log/maintance.log"

          log_message() {
            echo "$(date '+%Y-%m-%d %H:%M:%S') : $1" >> "$LOG_FILE"
            }

         log_message "maintance_started"

      #log roration
        if ./log_rotate.sh /var/log/myapp >> "$LOG_FILE" 2>$1 then;

           log_message "log rotation complete"
        else
           log_message "log rotation failed"
        fi

     #backup
       if ./back.sh /home/ubuntu/data /home/ubuntu/backups >> "$LOG_FILE" 2>$1 then;
        log_message "backup complete"
       else
         log_message "backup failed"
       fi

        log_message "maintance finished"

     3- chmod +x maintenance.sh

     4- Cron entry for maintenance script (Daily at 1 AM)
        0 1 * * * /home/ubuntu/2026/day-19/maintenance.sh


    OUTPUT:
      1- Log rotation
          Compressed files : 5
          Deleted files    : 2

       2- Backup
          Backup created successfully.
          Archive : backup-2026-06-11-11-30-15.tar.gz
          Size    : 18M

      3- Maintenance Log
         2026-06-11 01:00:01 : Maintenance started
         Compressed files : 5
         Deleted files : 2
         2026-06-11 01:00:10 : Log rotation completed
         Backup created successfully.
         Archive : backup-2026-06-11-01-00-10.tar.gz
         Size : 18M
         2026-06-11 01:00:12 : Backup completed
         2026-06-11 01:00:12 : Maintenance finished



## Documentation:

    1- day-19-project.md
    2- what i learned?
       1. Log Rotation
          -compress oldlog using gzip
          - remove older archieve with find -mtime
          - use file counts to display statistics.
       
       2. Backup Automation
          - Create timestamped backups using tar.
          -  Verify backup creation before proceeding.
          -  Automatically clean backups older than 14 days.
       
       3. Scheduling Jobs with Cron   
          - Use crontab -e to schedule scripts.
          - Understand cron syntax: 
              Minute
              Hour
              Day of Month
              Month
              Day of Week   

       4. Automate maintenance tasks without manual intervention.         

              


        
       
    
      
    
       
       
    
        

   
            

            

           
       
            

        

 

           


             
       
