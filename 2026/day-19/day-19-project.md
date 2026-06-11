## Day 19 – Shell Scripting Project: Log Rotation, Backup & Crontab

## Task 1: Log Rotation Script
     1- vim log_rotate.sh
     2-  #!/bin/bash
           set -euo pipefail

     # Check argument
        if [ $# -ne 1 ]; then
           echo "Usage: $0 <log_directory>
           exit 1
        fi   

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
        ./log_rotate.sh /var/log/myapp   


## Task 2: Server Backup Script:
      vim backup.sh
        #!/bin/bash
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
            size=$ ( du -h "$DEST_DIR/$ARCHIEVE_NAME" | cut -f1 )

            

           
       
            

        

 

           


             
       
