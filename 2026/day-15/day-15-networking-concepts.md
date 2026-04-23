## Day 15 – Networking Concepts: DNS, IP, Subnets & Ports

   ## Task 1: DNS – How Names Become IPs:
           1- what happens when you type google.com in a browser?
               1- Your computer asks: What is the IP address of google.com?
               2- DNS works like a phonebook: It converts the domain name (google.com) into an IP address (e.g., 142.x.x.x)       
               3- The DNS server finds the IP: It queries different servers (root → TLD → authoritative) to get the correct IP
               4- The IP is returned to your system
               5- The browser connects to that IP: And then the Google website loads

           2- DNS Record Types:
               1- A – Maps a domain name to an IPv4 address
               2- AAAA – Maps a domain name to an IPv6 address
               3- CNAME – Alias of one domain to another domain
               4- MX – Defines mail servers for a domain
               5- NS – Specifies authoritative name servers for a domain

               Cammand:
                    1- dig google.com
               Sample output:
                   - A Record IP: 
                   - TTL: 300 seconds

   ## Task 2: IP Addressing:
            1- What is an IPv4 address? & How is it structured? 
               An IPv4 address is a 32-bit number divided into 4 octets (e.g., 192.168.1.10), used to uniquely identify devices on a network.
               
            2- Difference between public and private IPs — give one example of each
               - Public IPs: 
               - Private IPs: 
    
          





          
