# Definition:

> A network (in French " #Réseau ") is a set of equipment connected to each other to exchange information. 

In addition to ==computer resources==, the implementation of a network requires ==infrastructure== such as physical links (cables, radio waves, etc.) and transmission and ==interconnection equipment== (network card, router, switch, etc.). A computer network also requires the implementation of communication ==protocols== to define in a standardized way how information is exchanged between network equipment. 

# Network types. 
## LANs:

> LAN means Local Area Network. It is a set of computers belonging to the same organization and connected to each other in a small geographical area by a network. 

It is a home or business network. The size of a local network can reach up to 100 or even 1000 users. 

## The MAN:

> The MAN (Metropolitan Area Network) interconnect several LAN geographically close (at most a few tens of km) at significant flows. Thus a MAN allows two remote nodes to communicate as if they were part of the same local network.. 

A MAN is made up of switches or routers interconnected by high-speed links (usually in optical fiber). 

## WAN:

> A WAN (Wide Area Network) interconnects multiple LAN across large geographic distances. 

WAN operate through routers that allow you to "choose" the most appropriate route to reach a network node.. 

The most known WAN is Internet.. 
![](asset/image/types%20de%20réseaux.png)

# Internet access methods. 

Currently, the 3 most used methods of Internet access are ADSL, optical fiber and radio waves (2G, 3G, 4G, etc.). 

## ADSL:  
  
> Asymmetric Digital Subscriber Line (ADSL) is a  digital communication. It allows to use a telephone line  to transmit and receive digital data in a independent of conventional telephone service (i.e. analogue).  
  
## Optical fiber:  
  
> An optical fiber is a very fine glass or plastic wire that has the property to be a conductor of light and serves in the transmission of data by light.  
  
### The FTTH:  
  
--- Fiber To The Home: The fiber network goes to the home.  
  
### The FTTB:  
  
--- Fiber To The Building: The fiber network goes to the building. The rest of the connection is made using existing cables in the building (telephone, ADSL). The speed is therefore greatly reduced.  
  
## Radio waves:  
  
>A radio wave is an electromagnetic wave with a frequency of less than 300 GHz. The data transmission is therefore done in the air through relay antennas.  
  
Cell towers are essential for a mobile phone to work. When a call is received, the relay antenna transforms the electromagnetic waves that pass through the air into an electrical signal. The signal then flows through cables as digital data. The phenomenon occurs in the direction  
reverse when the relay antenna transmits the signal.  
  
As soon as the mobile is turned on, a dialogue is established between the terminal and the nearest antenna to allow a transmission or reception of call. Between the mobile phone and the relay antenna, the call is routed through the air. The same phenomenon occurs when accessing the mobile Internet.


| Standard | Generation | Frequency Band | Throughput | |
| :----------------- | :---- | :----------------- | :---- | :-- |
| GSM | 2G | Low volume digital data or voice transfer. | 9.6 kbps | 9.6 kbps |
| GPRS | 2.5G | Moderate volume digital data or voice transfer. | 21-171 kbps | 48 kbps |
| EDGE | 2.75G | Simultaneous voice and digital data transfer. | 43-345 kbps | 171 kbps |
| UMTS | 3G | Simultaneous high-speed digital voice and data transfer. | 0.1-2 Mbps | 384 Kbps |
| LTE | 4G | Simultaneous high-speed digital voice and data transfer. | 10-300 Mbps | 5-75 Mbps |

# Hardware within a LAN

![](asset/image/Matériels%20LAN.png)

## The HUB:
> A HUB (also called a hub) is a hardware element that concentrates network traffic from multiple hosts and regenerates the signal. Its sole purpose is to retrieve binary data arriving on a port and broadcast it on all ports.

## The switch:
> The switch is an interconnecting device. Also called a switch, it analyses the frames arriving on its input ports and filters the data in order to route them only on the appropriate ports (we speak of switching or switched networks).

## Modem

>A modem (modulator-demodulator) is a device that allows digital data to be transmitted over analog communication channels. It modulates digital data into an analog signal suitable for transmission over telephone lines or cable connections. At the receiving end, it demodulates the analog signal back into digital data.
## The router:
>A router is an intermediate element in a computer network providing packet routing. Its role is to transfer packets from one network interface to another, at best, according to a set of rules.

The router allows for example to connect a home network (LAN) to the Internet (WAN).

# Addressing

Communication between two computers can be compared to sending a postal mail between a sender (toto) and a recipient (titi).

If Toto wants to send a letter to Titi he needs a `mailing address`

The French postal network consists of sub-networks: `the regions`.
The regions themselves are composed of sub-networks: `cities`.
The cities themselves are composed of sub-networks: `the streets`.
The streets form a network of houses identified by an ==N°==.

![](asset/image/Adressage.png)

If PC1 wants to send a message to PC2 it needs a network address (IP address)

> The IP address works according to the same principle as the postal address, it makes it possible to locate the machine on a network of computers, which can be composed of subnets. The IP address of the machine contains all this information.

## Gateway

A gateway serves as an entry and exit point between two different networks, allowing data traffic to flow between them. In home or office networks, a router often functions as the gateway. It manages the connection between the local network (LAN) and the external network (usually the internet). The router directs data between devices on the local network and to the outside world.
## IP / MAC address:

The IP address (like Internet Protocol) is a "logical" address assigned to a machine manually by the network administrator or automatically by a Dynamic Host Configuration Protocol (DHCP) server. This address is used to communicate within a network. It is editable.

Each network interface (network card, Wi-Fi interface, Bluetooth, etc.) also has a physical address that is not modifiable and “hard-listed” by the manufacturer. This is the Media Access Control (MAC) address, which uniquely identifies the card across all networks.
A MAC address is a 48-bit number represented in hexadecimal by 6 bytes.
MAC address example: `F4-6D-04-AF-64-62'

The first half of the MAC address (24 bits) typically represents the manufacturer (OUI - Organizationally Unique Identifier), and the second half (24 bits) is assigned uniquely by the manufacturer to each network interface.

On Windows to get the physical (MAC) and logical (IP) addresses of the network interfaces of your PC you can type the command: `ipconfig/all'

### Uniqueness and Purpose

MAC addresses are globally unique. No two NICs should have the same MAC address. This uniqueness is crucial in local networks to ensure that data is sent to the correct device. When a device wants to communicate with another on the local network, it uses the recipient's MAC address to direct the data precisely.

MAC addresses operate at the data link layer (Layer 2) of the OSI model and are essential for LAN communication.

### IP Protocol
On Windows, it is the ARP protocol (Address Resolution Protocol) that establishes the correspondence between physical address and IP address.
To display the ARP table entries enter: 'arp –a'.

## Address #IP:
### Public / Private Address:

Public addresses are those that can be used for an Internet connection. They are assigned by the IANA (Internet Assigned Numbers Authority) with whom you must register through an ISP (Internet Service Provider).

Unless you have a #proxy (proxy server) or a #NAT (Network Address Translation) service, any computer on a local network that wants to connect to the Internet must have its own IP address.

Thanks to the #NAT service, only one public #IP address is needed (it is assigned to the router that allows network-to-local access to the internet). Network computers must then have their own
private #IP addresses to communicate with each other and with the #NAT server.

### Format:  
> There are version 4 (32-bit, 4-byte) and version 6 (128-bit, 16-byte #IPs.  
  
Version 4 is currently the most used: it is generally represented in decimal notation with four numbers between 0 and 255, separated by points, which gives for example: 172.16.254.1  
(the address shown in the image below).  
  
![](asset/image/example%20ip.png)  
  
The number of public #IP Version 4 addresses officially reached saturation on February 3, 2011. The transition from IPv4 to IPv6 is underway.  
  
### Class:  
>In the #IP network definition system version 4 ( #IPv4), the #IP addresses were divided into classes, according to the number of bytes that represent the network, itself determined by the first bits of the #IP address.  

![clase IP](https://imgs.search.brave.com/aWCrjzCCrl7IO8oVWyP6H85e7RVun-WmBHlCPk7K7dA/rs:fit:500:0:0/g:ce/aHR0cHM6Ly93d3cu/aW5ldGRvYy5uZXQv/YXJ0aWNsZXMvYWRy/ZXNzYWdlLmlwdjQv/aW1hZ2VzL2NsYXNz/ZXMtYWRyZXNzZXMt/aXB2NC5wbmc)

Due to the migration to #IPv6, this notion of class is now obsolete.  
  
The #IP address of a device contains both a network identifier (NetID) and a device identifier (HostID)  
  
![](asset/image/separation%20ip.png)  
  
Depending on the number of devices that can be connected to a network, the #IP addresses belong to class A, B or C. The format of a #IP address according to its class is as follows:  
  
![](asset/image/class%20ip.png)  
  
The network’s #IP address is a #IP address with all bits from the “Host ID” part to 0. It is therefore a reserved address and not attributable to any equipment.  
  
Another combination is reserved. This is the one where all the bits of the "Host ID" part are at 1. This address is the broadcast address ( #broadcast) and is used to designate all the hosts of the network.  
  
![](asset/image/global%20rule%20adresse.png)  
`class B`  
  
| network id | host id | network address | broadcast address |  
| :--------- | :------ | :-------------- | :----------------- |  
| 172.16 | 25.105 | 172.16.0.0 | 172.16.255.255 |

### Subnet Mask:
>A #IP address is always associated with a «subnet mask», it is thanks to this that we can extract from the #IP address, the N° of the machine and the network/ subnet to which it belongs.

By default, when there are no sub-networks, the masks are:
- In Class A: ==255.0.0.0==
-  Class B: ==255.255.0.0==
-  Class C: ==255.255.255.0==

To determine the network address from a #IP address, the following logical operation is performed:
Network address = (Address #IP) AND (mask)

Address #IP = 10.121.58.12
AND
mask = 255.0.0.0
Equal
Network address = 10.0.0.0

To summarize:

![](asset/image/Class%20ip.png)

# CIDR Notation

## CIDR Overview

Classless Inter-Domain Routing (CIDR) is a method used to allocate IP addresses and route IP packets efficiently. It departs from the traditional class-based IP addressing system and allows for more flexible allocation.

## CIDR Notation Format

CIDR notation represents an IP address and its associated routing prefix. The format is: `IP address/network prefix length`. For example, `192.168.1.0/24` indicates that the IP address range from 192.168.1.0 to 192.168.1.255 is part of the same network, with a subnet mask of 255.255.255.0 (24 bits).

## Purpose and Benefits

CIDR allows network administrators to allocate IP addresses more flexibly, optimizing address distribution and routing. It provides finer control over address allocation than the traditional class-based system, which leads to more efficient use of IP addresses and improved internet routing.
# Network architectures
## Client-server architecture:
>In this environment, "client" computers contact a "server" computer to use an application service, a database, a connection to another network, etc... The «server» machine is in powerful general.

#### A client/server system operates as follows:

- The client makes a request to the server through its IP address and port, which designates a particular service of the server.
- The server receives the request and responds using the address of the client machine and its port.

![](asset/image/architecture%20client%20serveur%20schema.png)

#### Benefits:  
  
- *Centralized resources*: since the server is at the centre of the network, it can manage resources common to all users, such as a centralized database, to avoid redundancy and contradiction problems.  
- *Better security*: because the number of entry points allowing access to data is less important.  
- *Server-level administration*: since clients are of little importance in this model, they need less administration.  
- *A scalable network*: thanks to this architecture it is possible to delete or add clients without disrupting the network operation and without major changes.  
  
![](asset/image/architecture%20client%20server.png)  
#### Disadvantages:  
  
- High cost due to server technicality.  
- A weak link: the server is the only weak link in the client/server network, since the entire network is architected around it.  
  
### Architecture equals (workgroup):  
  
>In this architecture, there is no dedicated server. Thus, each computer is a bit server and a bit client. This means that each computer in the network is free to share its resources. These resources are not centralized.  
  
#### Benefits:  
  
- Reduced cost due to lack of server.  
- Extreme simplicity.  
  
![](asset/image/architecture%20égal%20à%20égal.png)
#### Disadvantages:  
  
- Administration more difficult due to lack of centralisation.  
- Security more difficult to ensure.  
  
# Physical topology of a network  
A computer network consists of computers connected to each other through communication lines (network cables, etc.) and hardware (network cards, as well as other equipment to ensure the smooth flow of data). The physical arrangement, that is, the spatial configuration of the network, is called a physical topology. The following topologies are generally distinguished:

- Bus topology
- Star topology
- Mesh topology
- Ring topology
- Tree topology

## Bus topology:
>In a bus topology all computers are connected to the same transmission line via cable. The word «bus» refers to the physical line that connects the machines of the network.

This topology is extremely vulnerable since if one of the connections is faulty, the entire network is affected.
![](topologie%20bus.png)

## Star topology:
>In a star topology, the network computers are connected to a central hardware system: either a hub (hub) or a switch (switch).

If a link fails, the network can still work.
We meet this kind of topology in high schools for example.
![](asset/image/topologie%20en%20étoile.png)
## Mesh topology:
>A mesh topology corresponds to several point-to-point links (e.g.
such as the Internet). Information may travel the network on various routes.

![](asset/image/topologie%20mailée.png)
# Communication
Communication between two computers can be compared to the sending of postal mail between a sender and a recipient.

### IP Address

1. In order for Computer A to send a message to Computer B, it must know its address. Both computers have a unique address on the network that identifies them. This is their IP address. 
![](asset/image/electronic%201.png)

2. By analogy, when a company A wants to send a letter to another company B it must know its mailing address. 
![](asset/image/traditional%201.png)

### Notion of port

1. There may be multiple programs running at the same time on the same computer:
- a browser
- an email software
- Note review software;
- …. 
![](asset/image/electronic%202.png)

2. In company B the mail is addressed to a particular department:
- Accounting department
- customer service
- management
- ….
![](asset/image/traditional%202.png)

Each software has a unique number called port. This number is transmitted along with the IP address. The received data is then directed to the “right” recipient. A computer has 65,535 ports. The first 1023 are reserved (http:80, ftp: 21, etc.)We write on the letter the address of the company
but also the recipient service.

### Protocol Concept  
1. Both computers can also exchange data because they use the same communication protocols. For example:  
- Sending a message with OUTLOOK and reading it with GMAIL because the encoding of the message is recognized by both software.  
- Sending data from one computer to another  
- …  
![](asset/image/electronic%203.png)  
  
2. Mail sent by the company (A) arrives at the company (B) by:  
- Envelope size meets standard  
- The elements of the address comply with the rules set by the mail forwarding companies (street number, postal code, etc.)  
![](asset/image/traditional%203.png)  
  
We also respect COMMUNICATION PROTOCOLS.  
  
# The TCP / IP model  
  
TCP/IP stands for Transmission Control Protocol/Internet Protocol.  
  
>TCP/IP represents in a way all the rules of communication on the Internet and is based on the notion of IP addressing, that is, providing an IP address to each machine in the network in order to be able to route data packets.  
  
The TCP/IP protocol system was broken down into 4 modules performing a specific task one after the other. So we have a stratified system, which is why we talk about a 'layered model'.  
  
Each layer has a specific task. Once this task is completed, it transmits the information to the neighbouring layer:  
  
Above during a reception  
  
Below during a broadcast  
  
>The Transmission Control Protocol (TCP) transport protocol takes care of to break down the information into segments. The Internet Protocol (IP) network protocol is responsible for identifying packets with IP addresses.


![](asset/image/modèle%20TCP%20ip.png)
![](asset/image/modele%20tcp%20ip%20example.png)
![](asset/image/modele%20tcp%20ip%20example%202.png)

# Data encapsulation
>On emission, the information of a layer is «inserted» in the neighboring layer, as «Data». This phenomenon is repeated layer by layer as shown in the diagram opposite. This process is called: ENCAPSULATION

![](asset/image/encapsulation.png)

# The OSI model
There are other models describing the transmission of information. Among these, there is one, competitor of the TCP/IP model and more detailed: it is the OSI model.

The working principle is exactly the same as the one observed previously
The Open Systems Interconnect (OSI) model is broken down into 7 layers.

'How is the communication between machines? Analogie Homme / Machine'

![](asset/image/modèle%20iso.png)

# Communication protocols
### Physical layer:
>This layer is responsible for transmission and conversion between bits and electrical or optical signals.

### Bluetooth:  
Bluetooth is a wireless personal area network technology (referred to as WPAN for Wireless Personal Area Network), a low-range wireless network technology that allows devices to be connected without a wired connection. Unlike IrDa technology (infrared link), Bluetooth devices do not require a direct line of sight to communicate, which makes it more flexible to use and allows communication from one room to another, over small spaces.  
  
### USB:  
The USB bus (Universal Serial Bus) is, as its name suggests, based on a serial architecture. However, it is a much faster input-output interface than standard serial ports.  
  
The USB 1.0 standard offers two modes of communication:  
- 12 Mb/s in high-speed mode,  
- 1.5 Mb/s at low speed.  
The USB 2.0 standard provides speeds of up to 480 Mbit/s.  
The USB 3.0 standard provides speeds of up to 4.8 Gbit/s.  
  
## Link layer:  
>The data link layer handles the local delivery of frames between devices on the same LAN.  
  
### Ethernet:  
Two main types of RJ45 cabling:  
  
- 'Straight wiring: It allows communication between a machine and a network device (switch, router, etc.). '  
- 'Cross wiring: It allows communication between one machine and another machine. '  
  
### WIFI:  
Wi-Fi (Wireless Fidelity) is a set of wireless communication protocols.  
  
>A Wi-Fi network allows several computer devices (computer, router, smartphone, Internet decoder, etc.) to be connected via radio waves within a computer network to enable data transmission between them.

### CPL:
Communication by online carrier currents (or powerlines) allows you to build a computer network on the electrical network of a home or office, or even a neighborhood or group of offices.

### The I²C bus:
Designed by Philips for home automation and home electronics applications, the I²C bus connects a microprocessor and different circuits.

### The CAN bus:
The CAN (Controller Area Network) bus is a serial system bus widely used in many industries, including the automotive industry. It implements an approach known as multiplexing, which consists in connecting to the same cable (a bus) a large number of computers that will communicate in turn.

## Network Layer:
>The network layer builds an end-to-end communication channel from communication channels with its direct neighbors.

Its main functional contributions are therefore:
- The routing:
Determination of a path to connect the 2 remote machines.
- Relaying:
Retransmission of a PDU (Protocol Data Unit) whose destination is not local to bring it closer to its final destination.
• Flow control:
Congestion control in a network.

### IP:
See chapter on IP addressing.

#### IPv4: 
IPv4 (Internet Protocol version 4) is the first version of Internet Protocol (IP) to have been widely deployed, and still forms the basis of most Internet communications in 2016.

#### IPv6: 
With 128-bit instead of 32-bit addresses, IPv6 has a much larger address space than IPv4. This considerable amount of addresses allows greater flexibility in the allocation of addresses and better aggregation of routes in the Internet routing table. Address translation (NAT), which has been made popular by the lack of IPv4 addresses, is no longer necessary.

### ARP:  
> The Address Resolution Protocol (ARP) is a protocol that translates a network layer protocol address (typically an IPv4 address) into a MAC address (typically an Ether address), or even any bonding layer material.  
  
## Transport layer:  
>The transport layer manages end-to-end communications between processes.  
  
### UDP:  
The User Datagram Protocol (UDP) is one of the main telecommunication protocols used by the Internet.  
UDP does not guarantee the correct delivery of datagrams at their destination, nor their order of arrival. It is also possible that datagrams are received in several copies.  
  
### TCP:  
Transmission Control Protocol (literally, «transmission control protocol»), abbreviated TCP, is a reliable transport protocol.  
TCP and UDP uses a port number to identify applications. Each end (client/server) of the TCP or UDP connection has a 16-bit port number (1 to 65535) assigned to the application  
transmitter or receiver.  
  
## Session layer:  
It ensures:  
- Session setup, maintenance and release: allows two application processes on different computers to establish, use and terminate a connection, called a session.  
- Session support: performs functions that allow these processes to communicate over the network, implement security procedures, name recognition, recording and so on.  
  
Main Session Protocol for Microsoft: NetBios  
Main session protocol for Apple: AppleTalk  
  
## Presentation layer:  
>The presentation layer is responsible for encoding application data.

Layers 1 to 5 carry raw bytes without worrying about their meaning. But what needs to be transported in practice is text, numbers and sometimes arbitrarily complex data structures. A routing protocol for example must carry a graph representing at least  
partially the network topology. The role of the presentation layer is therefore to convert the application data manipulated by the programs into byte strings.  
  
### ASCII:  
The American Standard Code for Information Interchange (ASCII) ([askiː]) is a computer-based standard for character encoding that appeared in the 1960s. This is the most influential character encoding standard to date. ASCII defines 128 7-bit codes, comprising 95 printable characters: the Arabic numerals from 0 to 9, the  
lowercase letters and capitals from A to Z, and mathematical and punctuation symbols.  
  
*See course information coding. *  
  
### Unicode:  
The Unicode standard consists of a directory of 128 172 characters. It takes the basis of ASCII coding.  
  
## Application layer:  
>The application layer serves as a window for users and application processes to access network services.  
  
This layer contains many often needed functions:  
- Redirection of devices and resource sharing  
- Remote access to files  
- Access to remote printer  
- Communication between processes  
- Network management  
- Directory services  
- Email (for example, email)  
- Virtual network terminals;  
  
### DHCP:  
> Dynamic Host Configuration Protocol (DHCP) is a protocol whose role is to automatically configure a station’s IP settings, including automatically assigning an IP address and a subnet mask.

### DNS:
>The Domain Name System (DNS) is a service to translate a domain name into information of several types associated with it, including IP addresses of the machine with this name.

### SMTP:
>Simple Mail Transfer Protocol (SMTP) is a protocol used to transfer email (email) to email servers.

### HTTP:
>The HyperText Transfer Protocol, better known as HTTP, is a client-server communication protocol developed for the World Wide Web.

HTTPS (with S for secured, or «secure») is the variant of HTTP secured by the use of SSL or TLS protocols.

The best known HTTP clients are web browsers that allow a user to access a server containing the data.

### FTP:
>File Transfer Protocol (FTP) is a communication protocol for file sharing. It allows you to copy files from one computer to another computer on the network, or to delete or modify files on that computer.

## Address Resolution Protocol (ARP)

The Address Resolution Protocol (ARP) is a fundamental protocol used in computer networking. Its primary purpose is to map an IP address (Layer 3) to a MAC address (Layer 2) in a local network. This markdown explains ARP, how it works, and its significance in networking.

### Overview

- **Acronym**: ARP stands for Address Resolution Protocol.
    
- **Layer**: ARP operates at the Link Layer (Layer 2) of the OSI model.
    
- **Objective**: ARP is used to map an IP address (32-bit) to a MAC address (48-bit).
    

### How ARP Works

1. **Address Mapping Request**: When a device in a local network wants to communicate with another device, it first checks its ARP cache (a table storing IP-MAC mappings). If the mapping is not found, it sends an ARP request packet containing the target IP address to the broadcast address.
    
2. **ARP Request Packet**:
    
    - **Sender MAC**: MAC address of the requester.
        
    - **Sender IP**: IP address of the requester.
        
    - **Target MAC**: Set to all zeros (unknown).
        
    - **Target IP**: IP address being queried.
        
3. **ARP Response**: The device with the corresponding IP address responds with an ARP reply packet containing its MAC address.
    
4. **Updating ARP Cache**: The requester updates its ARP cache with the received IP-MAC mapping for future use.
    

### ARP Cache Poisoning (ARP Spoofing)

ARP cache poisoning, also known as ARP spoofing, is a cyberattack where a malicious actor associates their MAC address with the IP address of another device in the network. This can lead to various security breaches, including interception of data.

### ARP Table (ARP Cache)

The ARP table or cache is a local table maintained by each device, storing recently resolved IP-MAC mappings. Entries in the table expire after a certain time.

### ARP Commands

- **`arp`**: Command to display and modify the ARP cache on a device.
    
    - **`arp -a`**: Displays the ARP table (on Windows).
        
    - **`arp -d <ip_address>`**: Deletes an entry from the ARP table (on Windows).
        

### Significance of ARP

- **Efficient Communication**: ARP ensures devices can efficiently communicate with each other within a local network by resolving IP addresses to MAC addresses.
    
- **Local Network Operation**: ARP operates within a local network and is crucial for devices to communicate over Ethernet or similar link layer technologies.
    

Understanding ARP is vital for network administrators and anyone involved in network troubleshooting and security, as it forms a fundamental part of the networking infrastructure.