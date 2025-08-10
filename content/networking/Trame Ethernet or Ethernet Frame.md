# Ethernet frame and IP datagram  
  
## Ethernet Frame  
  
An Ethernet frame is a data packet format used for communication in a local area network (LAN). It is composed of several fields, each playing a specific role in the data transmission process.  
  
![](asset/image/trame%20ethernet.PNG)  
### Ethernet Frame Fields  
  
1. **Preambule (7 bytes):** A bit pattern used to synchronize the receiver with the signal.  
  
2. SFD (1 bytes) The term "SFD" in networking and data communication often stands for "Start Frame Delimiter."  
  
3. **Destination Address (6 bytes):** The physical address (MAC) of the destination.  
  
4. **Source Address (6 bytes):** The MAC address of the sender.  
  
5. **Type (2 bytes):** Specifies the protocol encapsulated in the frame (IPv4, ARP, etc.).  
  
6. **Data (46-1500 bytes):** The actual data to be transmitted, ranging from 46 to 1500 bytes.  
  
7. **FCS, CRC (4 bytes):** Frame checksum for error detection.  
  
### EtherType Table (Ethernet Frame Type)  
  
|EtherType (Hex)|Protocol|  
|---|---|  
|0x0800|IPv4|  
|0x0806|ARP|  
|0x86DD|IPv6|  
|0x8100|VLAN Tagging|  
|0x0800|PPPoE Discovery|  
|...|...|  
  
## IP Datagram  
  
An IP datagram is a data packet used in IP networks to route information from one host to another.  
![](asset/image/datagramme%20ip.PNG)  
### IP Datagram Fields  
  
1. **Version (4 bits):** Indicates the version of the IP protocol used (IPv4 or IPv6).  
	  
1. **IHL (4 bits):** IP header length in 32 bit words. (note: minimum value is 5)  
	  
1. **Type of Service (8 bits):** Indicates the processing priority and type of service.  
	  
1. **Total Length (16 bits):** Total length of datagram in bytes.  
	  
1. **Identification (16 bits):** Identifies the datagram during fragmentation.  
	  
1. **Flags (3 bits):** Controls the fragmentation of datagrams.
	
1. **Fragment Offset (13 bits):** Indicates the position of a fragment in the original datagram.
    
8. **Time to Live (8 bits):** Indicates the maximum number of jumps before expiration.
    
9. **Protocol (8 bits):** Indicates the encapsulated protocol (TCP, UDP, ICMP, etc.).
    
10. **Header checksum (16 bits):** IP header checksum.
    
11. **Source Address (32-bit):** Sender’s IP address.
    
12. **Destination address (32-bit):** Recipient IP address.
    
13. **Options (0-320 bits):** Optional options for specific features.
    
14. **Data:** The data to be transmitted in the datagram. (here segment tcp)
    

These Ethernet frame and IP datagram concepts are essential for understanding how computer networks work and how data is transmitted from one host to another. For successful communication, it is crucial that the various fields are correctly configured and interpreted.