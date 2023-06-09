thttp://networking-ctfd-1.server.vta:8000/challenges
ssh student@10.50.38.54 -X
password
student18
# Networking
## Mathmatics
 - All networking is all done using binary mathmatics
 - bit=1/0
 - nibble = 4 bits (Mostly done with hex)
 - bytes are 8 bits 
 - bases are 2 10 16 or 64 
## Encapsulation/Decapsulation
 - Packets are done in layers made by headers/footers
 - layer 1 is every bit in a packet ( unreadable until you decapsulate t othe net layer )
 - ![image](https://user-images.githubusercontent.com/126014616/229798864-794ec34c-4411-4da7-95af-0c28527af74d.png)
### Physical Layer(1)
 - Mostly done using cat5 wires (pulse = on, no pulse = off )
 - any physical device
### Data Link Layer(2)
 #### MAC
  - gives unique identifier for local area networks
  - Macs are shown in th ethernet header
  - format= destination mac/source mac address/ethetype(ipv4/arp/ipv6/vlantags)/(payload/data/sdu)/(crc/fcs)
  - vlan tags can have mutltiple tags for
  - easy to spoof because it is clear text (must be on that network)
  - truncs are used to encapsulate all vlans on a single port on a switch - recieving switch strips away and sends packet to appropriate vlan
  - arp header-- string of hex 
  - ![image](https://user-images.githubusercontent.com/126014616/229802802-7364c263-f878-420f-afcc-f12073555522.png)
 #### Layer 2 switching technologies
  - fast forward - only destination mac
  - fragment free - first 64 bytes
  - store and forward - entire frame and fcs
  - Q-in-Q - 2 vlan tags has tag 0x88a8 (standard double tag) or 0x9100 (non standard double tag) --- attackable using double tags
  - STP (spanning tree protocol) --  ![image](https://user-images.githubusercontent.com/126014616/229817793-04b1fe71-d4c6-4d19-89cb-796cc0282fc5.png)
  - cdp/fdp/lldp (all proprietary to company)
  - ![DTP_Chart](https://user-images.githubusercontent.com/126014616/229817932-2f472f68-9980-4403-b43e-b0218db539c4.png)
  - vtp (vlan trunking protocol) automates vlan for all switches
  - switches have port security --- assign mac address to ports-- runs check on all attempted connection to a port -- if unknown mac port can shutdown/restrict/protect 
 

### Network Layer(3)
 #### Ipv4
 - ![IPv4_Header](https://user-imgoogle.com/search?q=-+!%5BIPv4_Header%5D(ages.githubusercontent.com/126014616/229803046-3318b3a7-07c5-467f-82fd-b73a69c2d2df.png)
 - DSCP/ECN is in the same byte!! 
 - 3 important flags=== fragmentation mf (more fragments) df (dont fragments) offset
 - tracks fragments through fragment offset -- df means no more is coming but it still has fragment offset
 - can inject a packet with a lower frag offset for malicious activity
 #### IPV6
  - ![IPv6_Header](https://user-images.githubusercontent.com/126014616/229807099-773dfce7-b7a2-4793-9d94-67c8a690a2fc.png)
  - ipv6 to replace ipv4 due to running out of addresses
  - ![IPv4_vs_IPv6_Header](https://user-images.githubusercontent.com/126014616/229807420-b3a8b18b-0467-42e2-aaa0-619659599dc9.png)
 #### ICMP
 - catch all for all other layer 3 
 - ![ICMPHeader](https://user-images.githubusercontent.com/126014616/229808590-0b5106b8-8356-4ffa-90f2-8963e6b29668.png)
 - most common is ping
 - type/code (byte 0 and 1 ) tells us the type (ex. ping)
 - iana.org
 - zero config --- default config for any device if you dont change anything apipa/slack
 #### Layer 3 routing technology
  - ![image](https://user-images.githubusercontent.com/126014616/229819334-1960a685-4fa1-4e75-bc74-cf85a4c9402a.png)
  - ![image](https://user-images.githubusercontent.com/126014616/229821180-465c09fb-7e93-4d56-b91f-3ef03cd34529.png)
  - routing -- used to move packets not used by users
  - routed -- user based applications that are done on the device 
  - dynamic routing 
  - ![Dynamic_Routing](https://user-images.githubusercontent.com/126014616/229823601-09289269-7c35-49b0-9070-eddfccc727eb.jpg)
  - ![Routing Protocol Comparison](https://user-images.githubusercontent.com/126014616/229824994-c520f271-f3c4-4638-bf1d-acf43dc073a5.png)
  
### Transport Layer (4)
  - TCP/UDP
  - identify traffic through port (ex. 22,23,443)
  #### TCP 
  - reliable, has tcp fla byte for handshake
  - cwr,ece,urg,ack,psh,rst,syb,fin "Collection of Exceptionally Unskilled Attackers Pester Real Security Folks"
  - ![TCPHeader](https://user-images.githubusercontent.com/126014616/230082054-343ed444-dcca-4641-94d9-429a5d728282.png)
  - ![TCPchart](https://user-images.githubusercontent.com/126014616/230082085-95367a84-0f53-40bb-95e3-cf231585e6e8.png)
  #### UDP 
  - connectionless, quick,fast,non-reliable
  - ![UDPHeader](https://user-images.githubusercontent.com/126014616/230082748-7be849d8-402a-465f-9cd0-16c0cd5dca27.png)
 ### Session Layer (5)
  - Maintains connection
  - SOCKS,NetBIOS,PPTP/L2TP,RPC
  - Uses proxy to maintain connections
 ### Presentation Layer (6)
 - traslates code into human readable 
 - translation,formating,encoding,encryption,compression
 ### Application Layer (7)
 - user seen layer
 - ftp  20/21 -- active/passive mode 
 - ![ftp_active](https://user-images.githubusercontent.com/126014616/230085838-96b9aacd-1a80-43ab-b250-9f1ba17ff12e.png)
 - active mode can be messed up from tunneling/firewals/NAT;s 
 - ![ftp_passive](https://user-images.githubusercontent.com/126014616/230086332-c15e5bf9-67ee-4241-87c9-d2f47d4ad688.png)
 - passive mode fixes old problems
 - ssh 22 -- client server protocol 
 - uses asymetric(initial connection)/semetric(data) exchanges 
 - supports data stream channeling
 ## Traffic Sniffing
 ### Capture Library
   - libpcap,winpcap,npcap
## Packet Creation/Socket Programming
 ### Sockets
 - Stream Sockets - Connection oriented and sequenced; methods for connection establishment and tear-down. Used with TCP, SCTP, and Bluetooth
 - Datagram Sockets - Connectionless; designed for quickly sending and receiving data. Used with UDP.
 - Raw Sockets - Direct sending and receiving of IP packets without automatic protocol-specific formatting. --- KERNEL SPACE
# Network Reconnaissance
- network recon
  - active
  - passive
    - lowrisk
    - not straight forward
    - more time consuming
    - identificaton info
      - ip addresses and sub-domains
      - external and 3rd party sites
      - people and tech
      - contact of interest
      - Vulnerabilities
    - tools
      - WHOIS queries
      - job site listings
      - phone numbers
      - google seraches
      - passive os finger printing
    - passive external
      - Information gathered outside of the network using passive methods
      - Allows for more efficient attacks and plans
      - DNS
        - resolves hostname to ip addresses
        - RFC 3912
      - dig
        - Typically between primary and secondary DNS servers
        - If allowed to transfer externally hostnames, IPs, and IP blocks can be determined
      - zone transfers
        - returns DNS info
        - supplements base queries
     #### NETWORK SCANNING
     - Scanning Approach
       - Aim
          - Wide range target scan
          - Target specific scan
       - Method
          - Single source scan
          - Distributed scan
          -Broadcast Ping and Ping sweep
       - ARP scan
       - SYN scan
       - Full connect scan
       - Null scan
       - FIN scan
       - XMAS tree scan
       - UDP scan
       - ACK/Window scan
       - RPC scan
       - FTP scan
       - decoy scan
       - OS fingerprinting scan
       - version scan
       - Protocol ping
       - Discovery probes
       - ![image](https://user-images.githubusercontent.com/126014616/230615009-e49010de-470b-49cc-af32-bff074cec97c.png)
  ## DATA TRANSFER
   - TFTP
     - UDP 
     - small and simple communication
     - no terminal communication
     - not secure (no authentication/encyption)
   - FTP
      - ACTIVE
           - TCP
           - authenticates through clear text sign in
           - insecure 
           - has anonymous account
      - PASSIVE
      
   - SFTP
      - TCO 
      - uses symmetric/assymetric encryption
      - add ftp to ssh 
      - interactive terminal
   - SCP
      (see slides..)
      
   ## Traffic Redirection
   - using tools 
      - netcat
         - swiss army knife 
         ```
         listener (recieve file) nc 10.2.0.2 9001 > newfile.txt
         client(sends file) nc 10.2.0.2 9001 < file.txt 
         
         # on client relay
         mknod mypipe p
         nc 10.1.0.2 9002 0< mypipe | nc 10.2.0.2 9001 1> mypipe
         
         
         # on listener2( sends info)
         nc -l -p 9002 < infile.txt
         
         #on listener1(recieves info
         nc -l -p > outfile.txt
         
         #if nc is not on box
         cat file.txt > /dev/tcp/10.2.0.2/1111
         ```
     
# Network Analysis
 ## Fingrprinting and host Identifications
    - P0f /etc/p0f/p0f.fp
    - looks at ttl, fragmentation, ip header, window size, and tcp options
    
 - fsd
 
# Filtering Devices, Mechanisms
 - ![image](https://user-images.githubusercontent.com/126014616/232497046-e9cf5a7c-547f-4166-ba64-d80e02d31611.png)
 ## Whitelist
  - If not on list, denied access  (considered more restrictive)
 ## Blacklist
  - denied access only to whats on list (considered less restrictive)
 - ![image](https://user-images.githubusercontent.com/126014616/232517643-844eacfb-a9ac-4044-b73c-f13fd229cb9d.png)
 - 

# Tunneling
 ### ssh
  - ssh -p <optional alt port> <user>@<pivot ip> -L <local bind port>:<tgt ip>:<tgt port>  
 
  - ssh student@172.16.1.15 -L 1111:172.16.40.10:22 -NT
  - ssh student@localhost -p 1111 -L 2222:172.16.82.106:80 -NT
  - firefox localhost:2222
  - ssh -p 111 mike@localhost -D 9050 (on box before target to scan/use tools on target)

  - REVERSE 
  - IH> telnet localhost 1116 
  - Clarence> ssh jim@jim-ip -R 1199:localhost:22
  - IH> ssh -p 1115 jim@localhost -L 1117:localhost:1119
  - IH> ssh -p 1117 clarence@localhost

         

 
 # Ssh tunneling alias
     
         ```
         vim .ssh/config
         Host ihost
         HostName vim 10.50.38.54
         User student
         Port 2
         ForwardX11 yes
         ssh-keygen -t ed25519
         ssh-copy-id
         vim .bash_aliases
         alias ihost='ssh ihost terminator&'
         ihost
         ``` 
 
 
``` 
sudo nft add chain ip CCTC  input { type filter hook input priority 0 \; policy accept \; }
sudo nft add chain ip CCTC output { type filter hook output priority 0 \; policy accept \; }
sudo nft insert rule ip CCTC input tcp dport {22, 23, 80, 3389} ct state {new, established} accept
sudo nft insert rule ip CCTC input tcp sport {22, 23, 80, 3389} ct state {new, established} accept
sudo nft insert rule ip CCTC output tcp dport {22, 23, 80, 3389} ct state {new, established} accept
sudo nft insert rule ip CCTC output tcp sport {22, 23, 80, 3389} ct state {new, established} accept
sudo nft insert rule ip CCTC input saddr 10.10.0.40 icmp type {echo-reply, echo-request} accept
sudo nft insert rule ip CCTC output dadd 10.10.0.40 icmp type { echo-repy, echo-request} accp
sudo nft insert rule ip CCTC input tcp dport {5050, 5150} ct state {new, established} accept
sudo nft insert rule ip CCTC input tcp sport {5050, 5150} ct state {new, established} accept
sudo nft insert rule ip CCTC input udp sport {5050, 5150} ct state {new, established} accept
sudo nft insert rule ip CCTC input udp dport {5050, 5150} ct state {new, established} accept
sudo nft insert rule ip CCTC output tcp dport {5050, 5150} ct state {new, established} accept
sudo nft insert rule ip CCTC output udp dport {5050, 5150} ct state {new, established} accept
sudo nft insert rule ip CCTC output tcp sport {5050, 5150} ct state {new, established} accept
sudo nft insert rule ip CCTC output udp dport {5050, 5150} ct state {new, established} accept
sudo nft add chain ip CCTC  input { type filter hook input priority 0 \; policy drop \; }
sudo nft add chain ip CCTC output { type filter hook output priority 0 \; policy drop \; }
 ```
 
 
 - standard acl goes closest to destinationn
 - extended acl goes closesnt to sources 
