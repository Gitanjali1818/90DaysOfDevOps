## Day 14 – Networking Fundamentals & Hands-on Checks:
## Quick notes:
   ##  OSI vs TCP/IP models:
       1- OSI (7 layers): Physical → Data Link → Network → Transport → Session → Presentation → Application
       2- TCP/IP Models : Network → Internate  → Transport  → Application
       3- OSI is conceptual; TCP/IP is practical

## Where things sit :
   1- IP - Internate
   2- TCP/UDP - Transport layer
   3- HTTP/HTTPS - Application layer
   4- DNS - Application layer

## Example :
   EX: curl https://example.com : → Application (HTTP) over Transport (TCP) over Internet (IP)

## Hands-on Checklist :
   1- Identity : hostname -I - 
      Observation : hows my system’s private IP
      Conclusion :
   2- Reachability : ping google.com
      Observation :
      Conclusion :
   3- Path : traceroute google.com
      Observation
      Conclusion
   4- Ports : ss -tulpn
      Observation : 
      Conclusion :
   5- Name resolution - nslookup google.com
      Obervation :
      Conclusion :
   6- HTTP check : curl -I https://google.com
      Observation :
      Conclusion :
   7- Connections snapshot : netstat -an | head
      Observation :
      Conclusion :

## MINI TASK: Port Probe & Interpret:
   1- Identify Port
      Test:
           nc -zv localhost 22
           Output: Connection successful
           Conclusion: Port is reachable
           If NOT reachable → Next checks:
                              systemctl status ssh
                              firewall (ufw / iptables)
 2- Reflection: 
     1- Fastest signal when broken?
         ping → quickly tells if host is reachable.
         curl → best for checking application/service health
         
     2- If DNS fails?
         Check Application layer (DNS)
         Then verify /etc/resolv.conf or DNS server
         
     3- If HTTP 500 error?
         - Issue at Application layer
         - Check server logs (nginx, app logs)

 3- Real Incident Follow-ups
         - Check logs: journalctl -u <service>
         - Verify ports/firewall: ss -tulpn, ufw status 
        
                              

            
    
      
      
    
   
        
