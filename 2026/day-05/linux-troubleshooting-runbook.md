# Linux troubleshooting runbook :
                                Service : DOCKER
                                Process : SSHD

# Enviornmental Basics:
                        uname -a : shows the kernal version and system architecture.
                        cat/etc/os-release : Confirm linux distribution and version.

# Filesystem Sanity: 
                        mkdir ~/runbook-demo : created directory.
                        cp /etc/hosts tem/runboook-demo-host-copy : File copied successfully & renamed the file is host-copy.

# CPU & Memory : 
                       top : Shows the CPU, memory usage live.
                       htop: we can kill the process with funtion keys and scroll easily with arrow keys.
                       ps -o pid,pcpu,pmem,comm -p $(pgrep sshd) : Docker process using very low CPU ans memory.(PID 862)
                       free -h : system have sufficient free memory.

#  Disk / IO : 
                       df -h : Disk usage below critical level, roots partition has available space.
                       du -sh /var/log: log directory size checked. (61M)

#  Network: 
                      ss -tulpn | grep docker: blank output.
                      curl -I localhost: local network connectivity works.(HTTP/1.1 200 OK)

#  Logs:  
                      journalctl -u docker.service -n 50: docker service log checked.
                      tail -n 50 /var/log/auth.log: Authentication logs show successful.

#  If this worsens: 
                     1- Restart docker Service : sudo systemctl restart docker
                     2- log level verbose: /etc/ssh/sshd_config
                     3- Trace SSH process: strace -p sshd_pid
                      
                      
                       
                       
                       
                        
                                
                             
