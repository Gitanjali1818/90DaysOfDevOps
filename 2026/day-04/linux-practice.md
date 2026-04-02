# Process commands: 
                  1- ps aux- shows the all running process in details.
                  2- pgrep docker -PID od running docker processes.
                  3- top- shows the CPU, memory, usage live.
                  4- htop- You can kill processes easily with function keys.You can scroll using arrow keys.

# service commands:
                 1- systemctl status docker: Show the status of docker.(active or not).
                 2- systemctl list-units: list all active services managed by systemd.

# log commands:
                 1- journalctl -u docker- shows the system log related to services. 
                 2- tail -n 50 /var/log/syslog- last 50 lines of the system log file.

# Mini troubleshooting steps: Docker process:
                 1- check the process is running: pgrep docker- Checks whether the Docker process is running by showing its PID.
                 2- check the status of service: systemctl status docker- showe the service is active,inactice or failed.
                 3- Restart the service if it is not working- sudo systemctl restart docker: restart the docker.
                 4- Check service logs for errors- journactl -u docker- Desplay logs related to service to identify the errors.
                 5- View recent system logs- sudo tail -n 50 /var/log/syslog- Shows the latest 50 log entries to help find system problems.
                 6- Confirm the service is active again- systemctl is-active docker- verify the docker service is currently running.
                 
                  
