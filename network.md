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
 - zero config --- default config for any device if you dont change anything
 - 

