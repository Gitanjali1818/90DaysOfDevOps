# Linux troubleshooting runbook :
                                Service : SSH
                                Process : SSHD

# Enviornmental Basics:
                        uname -a : shows the kernal version and system architecture.
                        cat/etc/os release : Confirm linux distribution and version.

# Filesystem Sanity: 
                        mkdir /tmp/runbook-demo : created directory.
                        cp /etc/hosts tem/runboook-demo-host-copy : File copied successfully.

# CPU & Memory : 
                       top : Shows the CPU, memory usage live.
                       htop: we can kill the process w:ith funtion keys and scroll easily with arrow keys.
                       ps -o pid, pcpu, pmem, comm -p 746 : SSH process using very low CPU ans memory.
                       free -h : system have sufficient free memory.

#  Disk / IO : 
                       df -h : Disk usage below critical level, roots partition has available space.
                       du -sh /var/log: log directory size checked.

#  Network: 
                      ss -tulpn | grep ssh: ssh service is listning on port 22.
                      curl -I localhost: local network connectivity works.

#  Logs:  
                      journalctl -u ssh -n 50: SSH service log checked.
                      tail -n 50 /var/log/auth.log: Authentication logs show successful.

#  If this worsens: 
                     1- Restart SSH Service : sudo systemctl restart ssh
                     2- log level verbose: /etc/ssh/sshd_config
                     3- Trace SSH process: strace -p sshd_pid
                      
                      
                       
                       
                       
                        
                                
                             
