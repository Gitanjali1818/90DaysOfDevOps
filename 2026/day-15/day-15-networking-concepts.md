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
               - Public IPs: Accessible over the internet. Google DNS 8.8.8.8
               - Private IPs:Used within internal networks. 192.168.1.10

           3- private IP ranges: 
                1- 10.0.0.0 to 10.255.255.255
                2- 172.16.0.0 to 172.16.255.255
                3- 192.168.0.0 to 192.168.255.255

           4- Run: ip addr show
              output: add ip in real senirio

## Task 3: CIDR & Subnetting:
           1- What does /24 mean in 192.168.1.0/24?
              - It means the first 24 bits are network bits, leaving 8 bits for host addresses.

           2- How many usable hosts in a /24? A /16? A /28?
              ## Usable Hosts:
                 1- /24 → 256 total → 254 usable
                 2- /16 → 65,536 total → 65,534 usable
                 3- /28 → 16 total → -14 usable         

           3- why do we subnet?
              - To divide a large network into smaller networks for better management, security, and efficient IP usage.

           4- CIDR Table:
              CIDR	      Subnet Mask	       Total IPs	     Usable Hosts
             
               /24	     255.255.255.0	      256	           254
               /16	     255.255.0.0	        65536	          65534
               /28	     255.255.255.240	       16	            14

## Task 4: Ports – The Doors to Services:
         1- What is a port? Why do we need them?
            -A port is a communication endpoint that helps identify specific services running on a system.
      
                     
                  
          





          
