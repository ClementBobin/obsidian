# Legend of TCP and UDP protocol table cells for port numbers

|   |   |
|---|---|
|Cell|Description|
|Yes|Described protocol _is_ assigned by IANA for this port, and _is_: standardized, specified, or widely used for such.|
|Unofficial|Described protocol _is not_ assigned by IANA for this port, but _is_: standardized, specified, or widely used for such.|
|Assigned|Described protocol _is_ assigned by IANA for this port,[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2) but _is not_: standardized, specified, or widely used for such.|
|No|Described protocol _is not_: assigned by IANA for this port, standardized, specified, or widely used for such.|
|Reserved|Port is reserved by IANA,[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2) generally to prevent collision having its previous use removed.[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)[[4]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc7605-4) The port number may be available for assignment upon request to IANA.[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|

## Well-known ports

This is a [dynamic list](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_Lists#Dynamic_lists "Wikipedia:WikiProject Lists") and may never be able to satisfy particular standards for completeness. You can help by [adding missing items](https://en.wikipedia.org/wiki/Special:EditPage/List_of_TCP_and_UDP_port_numbers "Special:EditPage/List of TCP and UDP port numbers") with [reliable sources](https://en.wikipedia.org/wiki/Wikipedia:Reliable_sources "Wikipedia:Reliable sources").

The port numbers in the range from 0 to 1023 (0 to 210 − 1) are the _well-known ports_ or _system ports_.[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3) They are used by system processes that provide widely used types of network services. On [Unix-like](https://en.wikipedia.org/wiki/Unix-like "Unix-like") operating systems, a process must execute with [superuser](https://en.wikipedia.org/wiki/Superuser "Superuser") privileges to be able to bind a [network socket](https://en.wikipedia.org/wiki/Network_socket "Network socket") to an [IP address](https://en.wikipedia.org/wiki/IP_address "IP address") using one of the well-known ports.[[5]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-man-5-services-die.net-5)

Well-known ports

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|Port|TCP|UDP|SCTP|DCCP|Description|
|0|Reserved|   |||In programming APIs (not in communication between hosts), requests a system-allocated (dynamic) port[[6]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Port_0_Linux-6)|
|1|Yes|Assigned|||[TCP Port Service Multiplexer](https://en.wikipedia.org/wiki/TCP_Port_Service_Multiplexer "TCP Port Service Multiplexer") (TCPMUX). Historic. Both TCP and UDP have been assigned to TCPMUX by IANA,[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2) but by design only TCP is specified.[[7]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1078-7)|
|2|Assigned|   |||compressnet (Management Utility)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|3|Assigned|   |||compressnet (Compression Process)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|5|Assigned|   |||[Remote Job Entry](https://en.wikipedia.org/wiki/Remote_Job_Entry "Remote Job Entry")[[8]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc407-8) was historically using socket 5 in its [old socket form](https://en.wikipedia.org/wiki/Network_socket#History "Network socket"), while [MIB](https://en.wikipedia.org/wiki/Management_information_base "Management information base") [PIM](https://en.wikipedia.org/wiki/Protocol_Independent_Multicast "Protocol Independent Multicast") has identified it as TCP/5[[9]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc2896-9) and IANA has assigned both TCP and UDP 5 to it.|
|7|Yes|   |||[Echo Protocol](https://en.wikipedia.org/wiki/Echo_Protocol "Echo Protocol")[[10]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc862-10)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|9|Yes|   |Yes[[12]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc4960-12)|Assigned|[Discard Protocol](https://en.wikipedia.org/wiki/Discard_Protocol "Discard Protocol")[[13]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc863-13)|
|No|Unofficial|||[Wake-on-LAN](https://en.wikipedia.org/wiki/Wake-on-LAN "Wake-on-LAN")[[14]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-msft-tn-bb632665-14)|
|11|Yes|   |||Active Users ([systat](https://en.wikipedia.org/wiki/Systat_(protocol) "Systat (protocol)") service)[[15]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-systat-netstat-15)[[16]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-RFC866-16)|
|13|Yes|   |||[Daytime Protocol](https://en.wikipedia.org/wiki/Daytime_Protocol "Daytime Protocol")[[17]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc867-17)|
|15|Unofficial|No|||Previously [netstat](https://en.wikipedia.org/wiki/Netstat "Netstat") service[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2)[[15]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-systat-netstat-15)|
|17|Yes|   |||[Quote of the Day](https://en.wikipedia.org/wiki/QOTD "QOTD") (QOTD)[[18]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc865-18)|
|18|Yes|   |||[Message Send Protocol](https://en.wikipedia.org/wiki/Message_Send_Protocol "Message Send Protocol")[[19]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1159-19)[[20]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1312-20)|
|19|Yes|   |||[Character Generator Protocol](https://en.wikipedia.org/wiki/Character_Generator_Protocol "Character Generator Protocol") (CHARGEN)[[21]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc864-21)|
|20|Yes|Assigned|Yes[[12]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc4960-12)||[File Transfer Protocol](https://en.wikipedia.org/wiki/File_Transfer_Protocol "File Transfer Protocol") (FTP) data transfer[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|21|Yes|Assigned|Yes[[12]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc4960-12)||File Transfer Protocol (FTP) control (command)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[12]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc4960-12)[[22]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc765-22)[[23]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc959-23)|
|22|Yes|Assigned|Yes[[12]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc4960-12)||[Secure Shell](https://en.wikipedia.org/wiki/Secure_Shell "Secure Shell") (SSH),[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) secure logins, [file transfers](https://en.wikipedia.org/wiki/File_transfer "File transfer") ([scp](https://en.wikipedia.org/wiki/Secure_copy "Secure copy"), [sftp](https://en.wikipedia.org/wiki/SSH_file_transfer_protocol "SSH file transfer protocol")) and port forwarding|
|23|Yes|Assigned|||[Telnet](https://en.wikipedia.org/wiki/Telnet "Telnet") protocol—unencrypted text communications[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[24]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc854-24)|
|25|Yes|Assigned|||[Simple Mail Transfer Protocol](https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol "Simple Mail Transfer Protocol") (SMTP),[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[25]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc821-25) used for email routing between mail servers|
|27|Assigned|   |||nsw-fe (NSW User System FE)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|28|Unofficial||||Palo Alto Networks' Panorama High Availability (HA) sync encrypted port.[[26]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-PAN-OS_HALinksAndBackupLinks-26)|
|29|Assigned|   |||msg-icp (MSG ICP)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|31|Assigned|   |||msg-auth (MSG Authentication)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|33|Assigned|   |||dsp (Display Support Protocol)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|37|Yes|   |||[Time Protocol](https://en.wikipedia.org/wiki/Time_Protocol "Time Protocol")[[27]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc868-27)|
|38|Assigned|   |||rap (Route Access Protocol)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|39|Assigned|   |||rlp (Resource Location Protocol)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|41|Assigned|   |||graphics (Graphics)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|42|Assigned|Yes|||[Host Name Server Protocol](https://en.wikipedia.org/wiki/ARPA_Host_Name_Server_Protocol "ARPA Host Name Server Protocol")[[28]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ien116-28)|
|43|Yes|Assigned|||[WHOIS](https://en.wikipedia.org/wiki/WHOIS "WHOIS") protocol[[29]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc812-29)[[30]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc954-30)[[31]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc3912-31)|
|44|Assigned|   |||mpm-flags (MPM FLAGS Protocol)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|45|Assigned|   |||mpm (Message Processing Module [recv])[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|46|Assigned|   |||mpm-snd (MPM [default send])[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|47|Reserved|   ||||
|48|Assigned|   |||auditd (Digital Audit Daemon)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|49|Yes|   |||[TACACS](https://en.wikipedia.org/wiki/TACACS "TACACS") Login Host protocol.[[32]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1492-32) [TACACS+](https://en.wikipedia.org/wiki/TACACS%2B "TACACS+"), still in draft which is an improved but distinct version of TACACS, only uses TCP 49.[[33]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-33)|
|50|Assigned|   |||re-mail-ck (Remote Mail Checking Protocol)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|51|Reserved|   |||Historically used for [Interface Message Processor](https://en.wikipedia.org/wiki/Interface_Message_Processor "Interface Message Processor") logical address management,[[34]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-bbnreport5256-34) entry has been removed by IANA on 2013-05-25|
|52|Assigned|   |||[Xerox Network Systems](https://en.wikipedia.org/wiki/Xerox_Network_Systems "Xerox Network Systems") (XNS) Time Protocol. Despite this port being assigned by IANA, the service is meant to work on [SPP](https://en.wikipedia.org/wiki/Sequenced_Packet_Protocol "Sequenced Packet Protocol") (ancestor of [IPX/SPX](https://en.wikipedia.org/wiki/IPX/SPX "IPX/SPX")), instead of TCP/IP.[[35]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-xns-35)|
|53|Yes|   |||[Domain Name System](https://en.wikipedia.org/wiki/Domain_Name_System "Domain Name System") (DNS)[[36]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1035-36)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|54|Assigned|   |||Xerox Network Systems (XNS) Clearinghouse (Name Server). Despite this port being assigned by IANA, the service is meant to work on [SPP](https://en.wikipedia.org/wiki/Sequenced_Packet_Protocol "Sequenced Packet Protocol") (ancestor of [IPX/SPX](https://en.wikipedia.org/wiki/IPX/SPX "IPX/SPX")), instead of TCP/IP.[[35]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-xns-35)|
|55|Assigned|   |||isi-gl (ISI Graphics Language)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|56|Assigned|   |||Xerox Network Systems (XNS) Authentication Protocol. Despite this port being assigned by IANA, the service is meant to work on [SPP](https://en.wikipedia.org/wiki/Sequenced_Packet_Protocol "Sequenced Packet Protocol") (ancestor of [IPX/SPX](https://en.wikipedia.org/wiki/IPX/SPX "IPX/SPX")), instead of TCP/IP.[[35]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-xns-35)|
|58|Assigned|   |||Xerox Network Systems (XNS) Mail. Despite this port being assigned by IANA, the service is meant to work on [SPP](https://en.wikipedia.org/wiki/Sequenced_Packet_Protocol "Sequenced Packet Protocol") (ancestor of [IPX/SPX](https://en.wikipedia.org/wiki/IPX/SPX "IPX/SPX")), instead of TCP/IP.[[35]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-xns-35)|
|61|Reserved|   |||Historically assigned to the [NIFTP-Based Mail](https://en.wikipedia.org/w/index.php?title=NIFTP-Based_Mail&action=edit&redlink=1 "NIFTP-Based Mail (page does not exist)") protocol,[[37]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1060-37) but was never documented in the related [IEN](https://en.wikipedia.org/wiki/Internet_Experiment_Note "Internet Experiment Note").[[38]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ien169-38) The port number entry was removed from IANA's registry on 2017-05-18.[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2)|
|62|Assigned|   |||acas (ACA Services)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|63|Assigned|   |||whoispp (whois++)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|64|Assigned|   |||covia (Communications Integrator (CI))[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
| 65 | Assigned | tacacs-ds (TACACS-Database Service) | [TACACS-Database Service](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3) | | 66 | Assigned | sql-net (Oracle SQL*NET) | [Oracle SQL*NET](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3) | | 67 | Assigned | Yes | [Bootstrap Protocol (BOOTP) server; also used by DHCP](https://en.wikipedia.org/wiki/Bootstrap_Protocol#cite_note-apple-kb-HT202944-11) | | 68 | Assigned | Yes | [Bootstrap Protocol (BOOTP) client; also used by DHCP](https://en.wikipedia.org/wiki/Bootstrap_Protocol#cite_note-apple-kb-HT202944-11) |
|69|Assigned|Yes|||[Trivial File Transfer Protocol](https://en.wikipedia.org/wiki/Trivial_File_Transfer_Protocol "Trivial File Transfer Protocol") (TFTP)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[39]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ien133-39)[[40]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc783-40)[[41]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1350-41)|
|70|Yes|Assigned|||[Gopher](https://en.wikipedia.org/wiki/Gopher_(protocol) "Gopher (protocol)") protocol[[42]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1436-42)|
|71–74|Yes|   |||[NETRJS](https://en.wikipedia.org/wiki/NETRJS "NETRJS") protocol[[43]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc88-43)[[44]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc740-44)[[45]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc820-45)|
|76|Assigned|   |||deos (Distributed External Object Store)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|78|Assigned|   |||vettcp (vettcp)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|79|Yes|Assigned|||[Finger protocol](https://en.wikipedia.org/wiki/Finger_protocol "Finger protocol")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[46]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc742-46)[[47]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1288-47)|
|80|Yes|   |Yes[[12]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc4960-12)||[Hypertext Transfer Protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol "Hypertext Transfer Protocol") (HTTP)[[48]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc7230-48)[[49]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc7540-49) uses TCP in versions 1.x and 2. [HTTP/3](https://en.wikipedia.org/wiki/HTTP/3 "HTTP/3") uses [QUIC](https://en.wikipedia.org/wiki/QUIC "QUIC"),[[50]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-quic-50) a transport protocol on top of UDP.|
|81|Unofficial||||[TorPark](https://en.wikipedia.org/wiki/TorPark "TorPark") [onion routing](https://en.wikipedia.org/wiki/Onion_routing "Onion routing")[_[verification needed](https://en.wikipedia.org/wiki/Wikipedia:Verifiability "Wikipedia:Verifiability")_]|
|82|Assigned|   |||xfer (XFER Utility)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|82||Unofficial|||TorPark control[_[verification needed](https://en.wikipedia.org/wiki/Wikipedia:Verifiability "Wikipedia:Verifiability")_]|
|83|Assigned|   |||mit-ml-dev (MIT ML Device)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|84|Assigned|   |||ctf (Common Trace Facility)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|85|Assigned|   |||mit-ml-dev (MIT ML Device)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|86|Assigned|   |||mfcobol (Micro Focus Cobol)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|88|Yes|   |||[Kerberos](https://en.wikipedia.org/wiki/Kerberos_(protocol) "Kerberos (protocol)")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[51]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1510-51)[[52]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc4120-52) authentication system|
|89|Assigned|   |||su-mit-tg (SU/MIT Telnet Gateway)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|90|Assigned|   |||dnsix (DNSIX Security Attribute Token Map)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|90|Unofficial|   |||[PointCast (dotcom)](https://en.wikipedia.org/wiki/PointCast_(dotcom) "PointCast (dotcom)")[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2)|
|91|Assigned|   |||mit-dov (MIT Dover Spooler)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|92|Assigned|   |||npp (Network Printing Protocol)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|93|Assigned|   |||dcp (Device Control Protocol)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|94|Assigned|   |||objcall (Tivoli Object Dispatcher)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|95|Yes|Assigned|||SUPDUP, terminal-independent remote login[[53]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-53)|
|96|Assigned|   |||dixie (DIXIE Protocol Specification)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|97|Assigned|   |||swift-rvf (Swift Remote Virtual File Protocol)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|98|Assigned|   |||tacnews (TAC News)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|99|Assigned|   |||metagram (Metagram Relay)[[3]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6335-3)|
|101|Yes|Assigned|||[NIC](https://en.wikipedia.org/wiki/History_of_the_Internet#NIC,_InterNIC,_IANA,_and_ICANN "History of the Internet") [host name](https://en.wikipedia.org/wiki/Hostname "Hostname")[[54]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc953-54)|
|102|Yes|Assigned|||[ISO](https://en.wikipedia.org/wiki/International_Organization_for_Standardization "International Organization for Standardization") Transport Service Access Point ([TSAP](https://en.wikipedia.org/wiki/TSAP "TSAP")) Class 0 protocol;[[55]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc983-55)[[56]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1006-56)|
|104|Yes|   |||[Digital Imaging and Communications in Medicine](https://en.wikipedia.org/wiki/Digital_Imaging_and_Communications_in_Medicine "Digital Imaging and Communications in Medicine") (DICOM; also port 11112)|
|105|Yes|   |||[CCSO Nameserver](https://en.wikipedia.org/wiki/CCSO_Nameserver "CCSO Nameserver")[[57]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc2378-57)|
|106|Unofficial|No|||[macOS Server](https://en.wikipedia.org/wiki/MacOS_Server "MacOS Server"), (macOS) password server[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|107|Yes|   |||[Remote User Telnet Service](https://en.wikipedia.org/wiki/Rtelnet "Rtelnet") (RTelnet)[[58]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc818-58)|
|108|Yes|   |||IBM [Systems Network Architecture](https://en.wikipedia.org/wiki/Systems_Network_Architecture "Systems Network Architecture") (SNA) gateway access server|
|109|Yes|Assigned|||[Post Office Protocol](https://en.wikipedia.org/wiki/Post_Office_Protocol "Post Office Protocol"), version 2 (POP2)[[59]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc937-59)|
|110|Yes|Assigned|||Post Office Protocol, version 3 (POP3)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[60]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1081-60)[[61]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1939-61)|
|111|Yes|   |||[Open Network Computing Remote Procedure Call](https://en.wikipedia.org/wiki/Open_Network_Computing_Remote_Procedure_Call "Open Network Computing Remote Procedure Call") (ONC RPC, sometimes referred to as Sun RPC)|
|113|Yes|No|||[Ident](https://en.wikipedia.org/wiki/Ident_protocol "Ident protocol"), authentication service/identification protocol,[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[62]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1413-62) used by [IRC](https://en.wikipedia.org/wiki/Internet_Relay_Chat "Internet Relay Chat") servers to identify users|
|Yes|Assigned|||Authentication Service (auth), the predecessor to _identification protocol_. Used to determine a user's identity of a particular TCP connection.[[63]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc931-63)|
|115|Yes|Assigned|||[Simple File Transfer Protocol](https://en.wikipedia.org/wiki/Simple_File_Transfer_Protocol "Simple File Transfer Protocol")[[64]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc913-64)|
|117|Yes|   |||[UUCP Mapping Project](https://en.wikipedia.org/wiki/UUCP_Mapping_Project "UUCP Mapping Project") (path service)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|118|Yes|   |||Structured Query Language ([SQL](https://en.wikipedia.org/wiki/SQL "SQL")) Services[_[jargon](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style#Technical_language "Wikipedia:Manual of Style")_]|
|119|Yes|Assigned|||[Network News Transfer Protocol](https://en.wikipedia.org/wiki/Network_News_Transfer_Protocol "Network News Transfer Protocol") (NNTP),[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) retrieval of newsgroup messages[[65]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc977-65)[[66]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc3977-66)|
|123|Assigned|Yes|||[Network Time Protocol](https://en.wikipedia.org/wiki/Network_Time_Protocol "Network Time Protocol") (NTP), used for time synchronization[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|126|Yes|   |||Formerly [Unisys](https://en.wikipedia.org/wiki/Unisys "Unisys") Unitary Login, renamed by Unisys to NXEdit. Used by Unisys Programmer's Workbench for Clearpath MCP, an IDE for [Unisys MCP software development](https://en.wikipedia.org/wiki/Unisys_MCP_programming_languages "Unisys MCP programming languages")|
|135|Yes|   |||[DCE](https://en.wikipedia.org/wiki/Distributed_Computing_Environment "Distributed Computing Environment") [endpoint](https://en.wikipedia.org/wiki/Communication_endpoint "Communication endpoint") resolution|
|Yes|   |||[Microsoft](https://en.wikipedia.org/wiki/Microsoft "Microsoft") EPMAP (End Point Mapper), also known as DCE/[RPC](https://en.wikipedia.org/wiki/Remote_procedure_call "Remote procedure call") Locator service,[[67]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-67) used to remotely manage services including [DHCP server](https://en.wikipedia.org/wiki/DHCP_server "DHCP server"), [DNS](https://en.wikipedia.org/wiki/Domain_Name_System "Domain Name System") server and [WINS](https://en.wikipedia.org/wiki/Windows_Internet_Name_Service "Windows Internet Name Service"). Also used by [DCOM](https://en.wikipedia.org/wiki/Distributed_Component_Object_Model "Distributed Component Object Model")|
|137|Yes|   |||[NetBIOS](https://en.wikipedia.org/wiki/NetBIOS "NetBIOS") Name Service, used for name registration and [resolution](https://en.wikipedia.org/wiki/Name_resolution_(computer_systems) "Name resolution (computer systems)")[[68]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1001-68)[[69]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1002-69)|
|138|Assigned|Yes|||NetBIOS Datagram Service[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[68]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1001-68)[[69]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1002-69)|
|139|Yes|Assigned|||NetBIOS Session Service[[68]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1001-68)[[69]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1002-69)|
|143|Yes|Assigned|||[Internet Message Access Protocol](https://en.wikipedia.org/wiki/Internet_Message_Access_Protocol "Internet Message Access Protocol") (IMAP),[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) management of [electronic mail](https://en.wikipedia.org/wiki/Email "Email") messages on a server[[70]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc3501-70)|
|151|Assigned|   |||[HEMS](https://en.wikipedia.org/wiki/Energy_management_system "Energy management system")|
|152|Yes|   |||[Background File Transfer Program](https://en.wikipedia.org/w/index.php?title=Background_File_Transfer_Program&action=edit&redlink=1 "Background File Transfer Program (page does not exist)") (BFTP)[[71]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1068-71)[_[importance?](https://en.wikipedia.org/wiki/Wikipedia:What_Wikipedia_is_not#Encyclopedic_content "Wikipedia:What Wikipedia is not")_]|
|153|Yes|   |||[Simple Gateway Monitoring Protocol](https://en.wikipedia.org/wiki/Simple_Gateway_Monitoring_Protocol "Simple Gateway Monitoring Protocol") (SGMP), a protocol for remote inspection and alteration of gateway management information[[72]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1028-72)|
|156|Yes|   |||Structured Query Language ([SQL](https://en.wikipedia.org/wiki/SQL "SQL")) Service[_[jargon](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style#Technical_language "Wikipedia:Manual of Style")_]|
|158|Yes|   |||[Distributed Mail System Protocol](https://en.wikipedia.org/w/index.php?title=Distributed_Mail_System_Protocol&action=edit&redlink=1 "Distributed Mail System Protocol (page does not exist)") (DMSP, sometimes referred to as Pcmail)[[73]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1056-73)[_[importance?](https://en.wikipedia.org/wiki/Wikipedia:What_Wikipedia_is_not#Encyclopedic_content "Wikipedia:What Wikipedia is not")_]|
|161|Assigned|Yes|||[Simple Network Management Protocol](https://en.wikipedia.org/wiki/Simple_Network_Management_Protocol "Simple Network Management Protocol") (SNMP)[[74]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1157-74)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_][[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|162|Yes|   |||[Simple Network Management Protocol](https://en.wikipedia.org/wiki/Simple_Network_Management_Protocol "Simple Network Management Protocol") Trap (SNMPTRAP)[[74]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1157-74)[[75]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-cisco-support-7244-75)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|165|Assigned|   |||[Xerox](https://en.wikipedia.org/wiki/Xerox "Xerox")|
|169|Assigned|   |||[SEND](https://en.wikipedia.org/wiki/Secure_Neighbor_Discovery "Secure Neighbor Discovery")|
|170|Yes|   |||Network [PostScript](https://en.wikipedia.org/wiki/PostScript "PostScript") [print server](https://en.wikipedia.org/wiki/Print_server "Print server")|
|177|Yes|   |||[X Display Manager Control Protocol](https://en.wikipedia.org/wiki/X_Display_Manager_Control_Protocol "X Display Manager Control Protocol") (XDMCP), used for remote logins to an [X Display Manager](https://en.wikipedia.org/wiki/X_display_manager "X display manager") server[[76]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-X11R7.6-doc-xdmcp-76)[_[self-published source](https://en.wikipedia.org/wiki/Wikipedia:Verifiability#Self-published_sources "Wikipedia:Verifiability")_]|
|179|Yes|Assigned|Yes[[12]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc4960-12)||[Border Gateway Protocol](https://en.wikipedia.org/wiki/Border_Gateway_Protocol "Border Gateway Protocol") (BGP),[[77]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc4271-77) used to exchange routing and reachability information among [autonomous systems](https://en.wikipedia.org/wiki/Autonomous_system_(Internet) "Autonomous system (Internet)") (AS) on the [Internet](https://en.wikipedia.org/wiki/Internet "Internet")|
|180|Assigned|   |||[ris](https://en.wikipedia.org/wiki/Remote_Installation_Services "Remote Installation Services")|
|194|Yes|   |||[Internet Relay Chat](https://en.wikipedia.org/wiki/Internet_Relay_Chat "Internet Relay Chat") (IRC)[[78]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc7194-78)|
|199|Yes|   |||[SNMP](https://en.wikipedia.org/wiki/SNMP "SNMP") Unix Multiplexer (SMUX)[[79]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1227-79)|
|201|Yes|   |||[AppleTalk](https://en.wikipedia.org/wiki/AppleTalk "AppleTalk") Routing Maintenance|
|209|Yes|Assigned|||[Quick Mail Transfer Protocol](https://en.wikipedia.org/wiki/Quick_Mail_Transfer_Protocol "Quick Mail Transfer Protocol")[[80]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-qmtp.txt-80)[_[self-published source](https://en.wikipedia.org/wiki/Wikipedia:Verifiability#Self-published_sources "Wikipedia:Verifiability")_]|
|210|Yes|   |||[ANSI](https://en.wikipedia.org/wiki/ANSI "ANSI") [Z39.50](https://en.wikipedia.org/wiki/Z39.50 "Z39.50")|
|213|Yes|   |||[Internetwork Packet Exchange](https://en.wikipedia.org/wiki/Internetwork_Packet_Exchange "Internetwork Packet Exchange") (IPX)|
|218|Yes|   |||Message posting protocol (MPP)|
|220|Yes|   |||[Internet Message Access Protocol](https://en.wikipedia.org/wiki/Internet_Message_Access_Protocol "Internet Message Access Protocol") (IMAP), version 3|
|225–241|Reserved|   ||||
|249–255|Reserved|   ||||
|259|Yes|   |||Efficient Short Remote Operations (ESRO)|
|262|Yes|   |||Arcisdms|
|264|Yes|   |||[Border Gateway Multicast Protocol](https://en.wikipedia.org/wiki/Border_Gateway_Multicast_Protocol "Border Gateway Multicast Protocol") (BGMP)|
|280|Yes|   |||http-mgmt|
|300|Unofficial||||[ThinLinc](https://en.wikipedia.org/wiki/ThinLinc "ThinLinc") Web Access, Spartan protocol [[81]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-81)|
|308|Yes||||Novastor Online Backup|
|311|Yes|Assigned|||[macOS Server](https://en.wikipedia.org/wiki/MacOS_Server "MacOS Server") Admin[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) (officially [AppleShare](https://en.wikipedia.org/wiki/AppleShare "AppleShare") IP Web administration[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2))|
|312|Unofficial|No|||macOS [Xsan](https://en.wikipedia.org/wiki/Xsan "Xsan") administration[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|318|Yes|   |||PKIX [Time Stamp Protocol](https://en.wikipedia.org/wiki/Time_Stamp_Protocol "Time Stamp Protocol") (TSP)|
|319||Yes|||[Precision Time Protocol](https://en.wikipedia.org/wiki/Precision_Time_Protocol "Precision Time Protocol") (PTP) event messages|
|320||Yes|||[Precision Time Protocol](https://en.wikipedia.org/wiki/Precision_Time_Protocol "Precision Time Protocol") (PTP) general messages|
|350|Yes|   |||[Mapping of Airline Traffic over Internet Protocol](https://en.wikipedia.org/wiki/Mapping_of_Airline_Traffic_over_Internet_Protocol "Mapping of Airline Traffic over Internet Protocol") (MATIP) type A|
|351|Yes|   |||MATIP type B|
|356|Yes|   |||cloanto-net-1 (used by Cloanto Amiga Explorer and VMs)|
|366|Yes|   |||On-Demand Mail Relay (ODMR)|
|369|Yes|   |||Rpc2portmap|
|370|Yes|   |||codaauth2, Coda authentication server|
||Yes|||securecast1, outgoing packets to [NAI](https://en.wikipedia.org/wiki/McAfee "McAfee")'s SecureCast servers[[82]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-SecureCast-82)As of 2000|
|371|Yes|   |||ClearCase albd|
|376|Yes|   |||[Amiga](https://en.wikipedia.org/wiki/Amiga "Amiga") Envoy Network Inquiry Protocol|
|383|Yes|   |||HP data alarm manager|
|384|Yes|   |||A Remote Network Server System|
|387|Yes|   |||AURP ([AppleTalk](https://en.wikipedia.org/wiki/AppleTalk "AppleTalk") Update-based Routing Protocol)[[83]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-83)|
|388|Yes|Assigned|||[Unidata LDM](https://en.wikipedia.org/wiki/Local_Data_Manager "Local Data Manager") near real-time data distribution protocol[[84]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-84)[_[self-published source](https://en.wikipedia.org/wiki/Wikipedia:Verifiability#Self-published_sources "Wikipedia:Verifiability")_][[85]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-85)[_[self-published source](https://en.wikipedia.org/wiki/Wikipedia:Verifiability#Self-published_sources "Wikipedia:Verifiability")_]|
|389|Yes|Assigned|||[Lightweight Directory Access Protocol](https://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol "Lightweight Directory Access Protocol") (LDAP)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|399|Yes|   |||[Digital Equipment Corporation](https://en.wikipedia.org/wiki/Digital_Equipment_Corporation "Digital Equipment Corporation") [DECnet+](https://en.wikipedia.org/w/index.php?title=DECnet%2B&action=edit&redlink=1 "DECnet+ (page does not exist)") (Phase V) over TCP/IP (RFC1859)|
|401|Yes|   |||[Uninterruptible power supply](https://en.wikipedia.org/wiki/Uninterruptible_power_supply "Uninterruptible power supply") (UPS)|
|427|Yes|   |||[Service Location Protocol](https://en.wikipedia.org/wiki/Service_Location_Protocol "Service Location Protocol") (SLP)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|433|Yes|   |||NNTP, part of [Network News Transfer Protocol](https://en.wikipedia.org/wiki/Network_News_Transfer_Protocol "Network News Transfer Protocol")|
|434|Yes|   |||[Mobile IP](https://en.wikipedia.org/wiki/Mobile_IP "Mobile IP") Agent (RFC 5944)|
|443|Yes|   |Yes[[12]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc4960-12)||[Hypertext Transfer Protocol Secure](https://en.wikipedia.org/wiki/HTTPS "HTTPS") (HTTPS)[[48]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc7230-48)[[49]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc7540-49) uses TCP in versions 1.x and 2. [HTTP/3](https://en.wikipedia.org/wiki/HTTP/3 "HTTP/3") uses QUIC,[[50]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-quic-50) a transport protocol on top of UDP.|
|444|Yes|   |||[Simple Network Paging Protocol](https://en.wikipedia.org/wiki/Simple_Network_Paging_Protocol "Simple Network Paging Protocol") (SNPP), RFC 1568|
|445|Yes|   |||Microsoft-DS (Directory Services) [Active Directory](https://en.wikipedia.org/wiki/Active_Directory "Active Directory"),[[86]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-msft-tn-dd772723-86) Windows shares|
|Yes|Assigned|||Microsoft-DS (Directory Services) [SMB](https://en.wikipedia.org/wiki/Server_Message_Block "Server Message Block")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) file sharing|
|464|Yes|   |||[Kerberos](https://en.wikipedia.org/wiki/Kerberos_(protocol) "Kerberos (protocol)") Change/Set password|
|465[[note 1]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-tcp465-87)|Yes|No|||SMTP over implicit SSL _(obsolete)_[[87]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-88)|
|Yes|No|||URL Rendezvous Directory for Cisco SSM _(primary usage assignment)_[[88]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-89)|
|Yes|No|||Authenticated [SMTP](https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol "Simple Mail Transfer Protocol")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) over [TLS/SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") ([SMTPS](https://en.wikipedia.org/wiki/SMTPS "SMTPS")) _(alternative usage assignment)_[[89]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-theregister-2018-02-01-rfc8314-90)|
|475|Yes|   |||tcpnethaspsrv, [Aladdin Knowledge Systems](https://en.wikipedia.org/wiki/Aladdin_Knowledge_Systems "Aladdin Knowledge Systems") Hasp services|
|476–490|Unofficial|   |||[Centro Software ERP](https://www.centrosoftware.com/) ports|
|491|Unofficial||||[GO-Global remote access and application publishing software](https://en.wikipedia.org/wiki/GO-Global "GO-Global")|
|497|Yes|   |||[Retrospect](https://en.wikipedia.org/wiki/Retrospect_(software) "Retrospect (software)")|
|500|Assigned|Yes|||[Internet Security Association and Key Management Protocol](https://en.wikipedia.org/wiki/Internet_Security_Association_and_Key_Management_Protocol "Internet Security Association and Key Management Protocol") (ISAKMP) / [Internet Key Exchange](https://en.wikipedia.org/wiki/Internet_Key_Exchange "Internet Key Exchange") (IKE)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|502|Yes|   |||[Modbus](https://en.wikipedia.org/wiki/Modbus "Modbus") Protocol|
|504|Yes|   |||[Citadel](https://en.wikipedia.org/wiki/Citadel/UX "Citadel/UX"), multiservice protocol for dedicated clients for the Citadel groupware system|
|510|Yes|   |||FirstClass Protocol (FCP), used by [FirstClass](https://en.wikipedia.org/wiki/FirstClass "FirstClass") client/server groupware system|
|512|Yes||||[Rexec](https://en.wikipedia.org/wiki/Remote_Process_Execution "Remote Process Execution"), Remote Process Execution|
||Yes|||comsat, together with [biff](https://en.wikipedia.org/wiki/Biff_(Unix) "Biff (Unix)")|
|513|Yes||||[rlogin](https://en.wikipedia.org/wiki/Rlogin "Rlogin")|
||Yes|||Who[[90]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1340-91)|
|514|Unofficial||||[Remote Shell](https://en.wikipedia.org/wiki/Remote_Shell "Remote Shell"), used to execute non-interactive commands on a remote system (Remote Shell, rsh, remsh)|
|No|Yes|||[Syslog](https://en.wikipedia.org/wiki/Syslog "Syslog"),[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) used for system logging|
|515|Yes|Assigned|||[Line Printer Daemon](https://en.wikipedia.org/wiki/Line_Printer_Daemon_protocol "Line Printer Daemon protocol") (LPD),[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) print service|
|517||Yes|||[Talk](https://en.wikipedia.org/wiki/Talk_(software) "Talk (software)")|
|518||Yes|||NTalk|
|520|Yes||||efs, extended file name server|
||Yes|||[Routing Information Protocol](https://en.wikipedia.org/wiki/Routing_Information_Protocol "Routing Information Protocol") (RIP)|
|521||Yes|||[Routing Information Protocol Next Generation](https://en.wikipedia.org/wiki/RIPng "RIPng") (RIPng)|
|524|Yes|   |||[NetWare Core Protocol](https://en.wikipedia.org/wiki/NetWare_Core_Protocol "NetWare Core Protocol") (NCP) is used for a variety things such as access to primary NetWare server resources, Time Synchronization, etc.|
|525||Yes|||Timed, [Timeserver](https://en.wikipedia.org/wiki/Timeserver "Timeserver")|
|530|Yes|   |||[Remote procedure call](https://en.wikipedia.org/wiki/Remote_procedure_call "Remote procedure call") (RPC)|
|532|Yes|Assigned|||netnews[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|533||Yes|||netwall, for emergency broadcasts|
|540|Yes||||Unix-to-Unix Copy Protocol ([UUCP](https://en.wikipedia.org/wiki/UUCP "UUCP"))|
|542|Yes|   |||[commerce](https://en.wikipedia.org/wiki/Commerce "Commerce") (Commerce Applications)|
|543|Yes||||klogin, [Kerberos](https://en.wikipedia.org/wiki/Kerberos_(protocol) "Kerberos (protocol)") login|
|544|Yes||||kshell, Kerberos Remote shell|
|546|Yes|   |||[DHCPv6](https://en.wikipedia.org/wiki/DHCPv6 "DHCPv6") client|
|547|Yes|   |||DHCPv6 server|
|548|Yes|Assigned|||[Apple Filing Protocol](https://en.wikipedia.org/wiki/Apple_Filing_Protocol "Apple Filing Protocol") (AFP) over [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol "Transmission Control Protocol")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|550|Yes|   |||new-rwho, new-who[[90]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1340-91)|
|554|Yes|   |||[Real Time Streaming Protocol](https://en.wikipedia.org/wiki/Real_Time_Streaming_Protocol "Real Time Streaming Protocol") (RTSP)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|556|Yes||||Remotefs, [RFS](https://en.wikipedia.org/wiki/Remote_File_System "Remote File System"), rfs_server|
|560||Yes|||rmonitor, Remote Monitor|
|561||Yes|||monitor|
|563|Yes|   |||[NNTP](https://en.wikipedia.org/wiki/NNTP "NNTP") over [TLS/SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") (NNTPS)|
|564|Unofficial||||[9P](https://en.wikipedia.org/wiki/9P_(protocol) "9P (protocol)") ([Plan 9](https://en.wikipedia.org/wiki/Plan_9_from_Bell_Labs "Plan 9 from Bell Labs"))|
|585|No|   |||Previously assigned for use of [Internet Message Access Protocol](https://en.wikipedia.org/wiki/Internet_Message_Access_Protocol "Internet Message Access Protocol") over [TLS/SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") (IMAPS), now deregistered in favour of port 993.[[91]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-oreilly-fire-2ndEd-92)|
|587|Yes|Assigned|||[email message submission](https://en.wikipedia.org/wiki/Mail_submission_agent "Mail submission agent")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[92]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-93) ([SMTP](https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol "Simple Mail Transfer Protocol"))|
|591|Yes||||[FileMaker](https://en.wikipedia.org/wiki/FileMaker "FileMaker") 6.0 (and later) Web Sharing (HTTP Alternate, also see port 80)|
|593|Yes|   |||HTTP RPC Ep Map, [Remote procedure call](https://en.wikipedia.org/wiki/Remote_procedure_call "Remote procedure call") over [Hypertext Transfer Protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol "Hypertext Transfer Protocol"), often used by [Distributed Component Object Model](https://en.wikipedia.org/wiki/Distributed_Component_Object_Model "Distributed Component Object Model") services and [Microsoft Exchange Server](https://en.wikipedia.org/wiki/Microsoft_Exchange_Server "Microsoft Exchange Server")|
|601|Yes||||Reliable [Syslog](https://en.wikipedia.org/wiki/Syslog "Syslog") Service — used for system logging|
|604|Yes||||TUNNEL profile,[[93]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-94) a protocol for [BEEP](https://en.wikipedia.org/wiki/BEEP "BEEP") [peers](https://en.wikipedia.org/wiki/Peer-to-peer "Peer-to-peer") to form an [application layer](https://en.wikipedia.org/wiki/Application_layer "Application layer") [tunnel](https://en.wikipedia.org/wiki/Tunneling_protocol "Tunneling protocol")|
|623||Yes|||ASF Remote Management and Control Protocol (ASF-[RMCP](https://en.wikipedia.org/wiki/Intelligent_Platform_Management_Interface#RMCP "Intelligent Platform Management Interface")) & IPMI Remote Management Protocol|
|625|Unofficial|No|||Open Directory Proxy (ODProxy)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|631|Yes|   |||[Internet Printing Protocol](https://en.wikipedia.org/wiki/Internet_Printing_Protocol "Internet Printing Protocol") (IPP)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|Unofficial|   |||[Common Unix Printing System](https://en.wikipedia.org/wiki/Common_Unix_Printing_System "Common Unix Printing System") (CUPS) administration console (extension to IPP)|
|635|Yes|   |||RLZ DBase|
|636|Yes|Assigned|||[Lightweight Directory Access Protocol](https://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol "Lightweight Directory Access Protocol") over [TLS/SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") (LDAPS)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|639|Yes|   |||[Multicast Source Discovery Protocol](https://en.wikipedia.org/wiki/Multicast_Source_Discovery_Protocol "Multicast Source Discovery Protocol"), MSDP|
|641|Yes|   |||SupportSoft Nexus Remote Command (control/listening), a proxy gateway connecting remote control traffic|
|643|Yes|   |||SANity|
|646|Yes|   |||[Label Distribution Protocol](https://en.wikipedia.org/wiki/Label_Distribution_Protocol "Label Distribution Protocol") (LDP), a routing protocol used in [MPLS](https://en.wikipedia.org/wiki/Multiprotocol_Label_Switching "Multiprotocol Label Switching") networks|
|647|Yes||||[DHCP Failover](https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol#Reliability "Dynamic Host Configuration Protocol") protocol[[94]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-95)|
|648|Yes||||Registry Registrar Protocol (RRP)[[95]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-96)|
|651|Yes|   |||IEEE-MMS|
|653|Yes|   |||SupportSoft Nexus Remote Command (data), a proxy gateway connecting remote control traffic|
|654|Yes||||Media Management System (MMS) Media Management Protocol (MMP)[[96]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-97)|
|655|Yes|   |||[Tinc](https://en.wikipedia.org/wiki/Tinc_(protocol) "Tinc (protocol)") VPN daemon|
|657|Yes|   |||[IBM](https://en.wikipedia.org/wiki/IBM "IBM") RMC (Remote monitoring and Control) protocol, used by [System p5](https://en.wikipedia.org/wiki/IBM_System_p "IBM System p") [AIX](https://en.wikipedia.org/wiki/IBM_AIX "IBM AIX") Integrated Virtualization Manager (IVM)[[97]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-98) and [Hardware Management Console](https://en.wikipedia.org/wiki/IBM_Hardware_Management_Console "IBM Hardware Management Console") to connect managed [logical partitions (LPAR)](https://en.wikipedia.org/wiki/LPAR "LPAR") to enable dynamic partition reconfiguration|
|660|Yes|Assigned|||[macOS Server](https://en.wikipedia.org/wiki/MacOS_Server "MacOS Server") administration,[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2) version 10.4 and earlier[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|[666](https://en.wikipedia.org/wiki/Number_of_the_beast "Number of the beast")|Yes|   |||_[Doom](https://en.wikipedia.org/wiki/Doom_(1993_video_game) "Doom (1993 video game)")_, the first online [first-person shooter](https://en.wikipedia.org/wiki/First-person_shooter "First-person shooter")|
|Unofficial||||[airserv-ng](http://www.aircrack-ng.org/doku.php?id=airserv-ng), [aircrack-ng](https://en.wikipedia.org/wiki/Aircrack-ng "Aircrack-ng")'s server for remote-controlling wireless devices|
|674|Yes||||[Application Configuration Access Protocol](https://en.wikipedia.org/wiki/Application_Configuration_Access_Protocol "Application Configuration Access Protocol") (ACAP)|
|684|Yes|   |||CORBA IIOP SSL[[98]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-99)|
|688|Yes|   |||REALM-RUSD (ApplianceWare Server Appliance Management Protocol)|
|690|Yes|   |||Velneo Application Transfer Protocol (VATP)|
|691|Yes||||[MS](https://en.wikipedia.org/wiki/Microsoft "Microsoft") [Exchange](https://en.wikipedia.org/wiki/Microsoft_Exchange_Server "Microsoft Exchange Server") Routing|
|694|Yes|   |||[Linux-HA](https://en.wikipedia.org/wiki/Linux-HA "Linux-HA") high-availability heartbeat|
|695|Yes||||[IEEE](https://en.wikipedia.org/wiki/IEEE "IEEE") Media Management System over [SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") (IEEE-MMS-SSL)[[99]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-100)|
|698||Yes|||[Optimized Link State Routing](https://en.wikipedia.org/wiki/Optimized_Link_State_Routing_protocol "Optimized Link State Routing protocol") (OLSR)|
|700|Yes||||[Extensible Provisioning Protocol](https://en.wikipedia.org/wiki/Extensible_Provisioning_Protocol "Extensible Provisioning Protocol") (EPP), a protocol for communication between [domain name registries](https://en.wikipedia.org/wiki/Domain_name_registry "Domain name registry") and [registrars](https://en.wikipedia.org/wiki/Domain_name_registrar "Domain name registrar") (RFC 5734)|
|701|Yes||||Link Management Protocol (LMP),[[100]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-101) a protocol that runs between a pair of [nodes](https://en.wikipedia.org/wiki/Node_(networking) "Node (networking)") and is used to manage [traffic engineering](https://en.wikipedia.org/wiki/Teletraffic_engineering "Teletraffic engineering") (TE) [links](https://en.wikipedia.org/wiki/Telecommunications_link "Telecommunications link")|
|702|Yes||||IRIS[[101]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-102)[[102]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-103) (Internet Registry Information Service) over [BEEP](https://en.wikipedia.org/wiki/BEEP "BEEP") (Blocks Extensible Exchange Protocol)[[103]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-104) (RFC 3983)|
|706|Yes||||[Secure Internet Live Conferencing](https://en.wikipedia.org/wiki/SILC_(protocol) "SILC (protocol)") (SILC)|
|711|Yes||||[Cisco](https://en.wikipedia.org/wiki/Cisco "Cisco") Tag Distribution Protocol[[104]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-105)[[105]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-106)[[106]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-107)—being replaced by the MPLS [Label Distribution Protocol](https://en.wikipedia.org/wiki/Label_Distribution_Protocol "Label Distribution Protocol")[[107]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-108)|
|712|Yes||||[Topology Broadcast based on Reverse-Path Forwarding routing protocol](https://en.wikipedia.org/wiki/Topology_Broadcast_based_on_Reverse-Path_Forwarding_routing_protocol "Topology Broadcast based on Reverse-Path Forwarding routing protocol") (TBRPF; RFC 3684)|
|749|Yes|   |||Kerberos administration[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|750||Yes|||kerberos-iv, [Kerberos](https://en.wikipedia.org/wiki/Kerberos_(protocol) "Kerberos (protocol)") version IV|
|751|Unofficial|   |||kerberos_master, Kerberos authentication|
|752||Unofficial|||passwd_server, Kerberos password (kpasswd) server|
|753|Yes|   |||Reverse Routing Header (RRH)[[108]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-109)|
||Unofficial|||userreg_server, Kerberos userreg server|
|754|Yes|   |||tell send|
|Unofficial||||krb5_prop, Kerberos v5 slave propagation|
|760|Unofficial|   |||krbupdate [kreg], Kerberos registration|
|782|Unofficial||||[Conserver](https://en.wikipedia.org/wiki/Conserver "Conserver") serial-console management server|
|783|Unofficial||||[SpamAssassin](https://en.wikipedia.org/wiki/SpamAssassin "SpamAssassin") spamd daemon|
|800|Yes|   |||mdbs-daemon|
|802|Yes|   |||[MODBUS](https://en.wikipedia.org/wiki/Modbus "Modbus")/TCP Security[[109]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-mbap-s-110)|
|808|Unofficial||||Microsoft Net.TCP Port Sharing Service|
|829|Yes|Assigned|||[Certificate Management Protocol](https://en.wikipedia.org/wiki/Certificate_Management_Protocol "Certificate Management Protocol")[[110]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc4210-111)|
|830|Yes|   |||[NETCONF](https://en.wikipedia.org/wiki/NETCONF "NETCONF") over [SSH](https://en.wikipedia.org/wiki/Secure_Shell "Secure Shell")|
|831|Yes|   |||NETCONF over [BEEP](https://en.wikipedia.org/wiki/BEEP "BEEP")|
|832|Yes|   |||NETCONF for [SOAP](https://en.wikipedia.org/wiki/SOAP "SOAP") over HTTPS|
|833|Yes|   |||NETCONF for SOAP over BEEP|
|843|Unofficial||||[Adobe Flash](https://en.wikipedia.org/wiki/Adobe_Flash "Adobe Flash")[[111]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-112)|
|847|Yes||||[DHCP Failover](https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol#Reliability "Dynamic Host Configuration Protocol") protocol|
|848|Yes|   |||Group Domain Of Interpretation (GDOI) protocol|
|853|Yes||||[DNS over TLS](https://en.wikipedia.org/wiki/DNS_over_TLS "DNS over TLS") (RFC 7858)|
||Yes|||DNS over QUIC or DNS over DTLS[[112]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-113)|
|860|Yes||||[iSCSI](https://en.wikipedia.org/wiki/ISCSI "ISCSI") (RFC 3720)|
|861|Yes|   |||OWAMP control (RFC 4656)|
|862|Yes|   |||TWAMP control (RFC 5357)|
|873|Yes||||[rsync](https://en.wikipedia.org/wiki/Rsync "Rsync") file synchronization protocol|
|888|Unofficial||||cddbp, [CD DataBase](https://en.wikipedia.org/wiki/CD_database "CD database") ([CDDB](https://en.wikipedia.org/wiki/CDDB "CDDB")) protocol (CDDBP)|
|Unofficial||||IBM Endpoint Manager Remote Control|
|897|Unofficial|   |||[Brocade](https://en.wikipedia.org/wiki/Brocade_Communications_Systems "Brocade Communications Systems") SMI-S RPC|
|898|Unofficial|   |||Brocade SMI-S RPC SSL|
|902|Unofficial|   |||[VMware ESXi](https://en.wikipedia.org/wiki/VMware_ESXi "VMware ESXi")[[113]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-vmware-kb-1022256-114)[[114]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-vmware-kb-1005189-115)|
|903|Unofficial||||VMware ESXi[[113]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-vmware-kb-1022256-114)[[114]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-vmware-kb-1005189-115)|
|953|Yes|Reserved|||[BIND](https://en.wikipedia.org/wiki/BIND "BIND") remote name daemon control (RNDC)[[115]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-centos-5-deployment-rndc-116)[[116]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-man-rndc.8-117)|
|981|Unofficial||||Remote HTTPS management for firewall devices running embedded [Check Point VPN-1](https://en.wikipedia.org/wiki/Check_Point_VPN-1 "Check Point VPN-1") software[[117]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-fw-1-ports-ng-118)|
|987||Unofficial|||Sony PlayStation Wake On Lan|
|Unofficial||||[Microsoft Remote Web Workplace](https://en.wikipedia.org/wiki/Microsoft_Remote_Web_Workplace "Microsoft Remote Web Workplace"), a feature of [Windows Small Business Server](https://en.wikipedia.org/wiki/Windows_Small_Business_Server "Windows Small Business Server")[[118]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-msft-tn-cc52751-119)|
|988|Unofficial||||[Lustre (file system)](https://en.wikipedia.org/wiki/Lustre_(file_system) "Lustre (file system)")[[119]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-120) Protocol (data).|
|989|Yes|   |||[FTPS](https://en.wikipedia.org/wiki/FTPS "FTPS") Protocol (data), [FTP](https://en.wikipedia.org/wiki/FTP "FTP") over [TLS/SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security")|
|990|Yes|   |||FTPS Protocol (control), FTP over TLS/SSL|
|991|Yes|   |||[Netnews](https://en.wikipedia.org/wiki/Netnews "Netnews") Administration System (NAS)[[120]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-121)|
|992|Yes|   |||[Telnet](https://en.wikipedia.org/wiki/Telnet "Telnet") protocol over TLS/SSL|
|993|Yes|Assigned|||[Internet Message Access Protocol](https://en.wikipedia.org/wiki/Internet_Message_Access_Protocol "Internet Message Access Protocol") over [TLS/SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") (IMAPS)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|994|Reserved|   |||Previously assigned to [Internet Relay Chat](https://en.wikipedia.org/wiki/Internet_Relay_Chat "Internet Relay Chat") over [TLS/SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") (IRCS), but was not used in common practice.|
|995|Yes|   |||[Post Office Protocol](https://en.wikipedia.org/wiki/Post_Office_Protocol "Post Office Protocol") 3 over [TLS/SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") (POP3S)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|1010|Unofficial||||[ThinLinc](https://en.wikipedia.org/wiki/ThinLinc "ThinLinc") web-based administration interface[[121]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-cendio-docs-tag-tcp-ports-122)|
|1011–1020|Reserved|   ||||
|1023|Reserved|   |||[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2)|
|Unofficial|   |||[z/OS](https://en.wikipedia.org/wiki/Z/OS "Z/OS") Network File System (NFS) (potentially ports 991–1023)[[78]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc7194-78)[[79]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc1227-79)[[122]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ibm-zos-surpp-123)|

## Registered ports

This is a [dynamic list](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_Lists#Dynamic_lists "Wikipedia:WikiProject Lists") and may never be able to satisfy particular standards for completeness. You can help by [adding missing items](https://en.wikipedia.org/wiki/Special:EditPage/List_of_TCP_and_UDP_port_numbers "Special:EditPage/List of TCP and UDP port numbers") with [reliable sources](https://en.wikipedia.org/wiki/Wikipedia:Reliable_sources "Wikipedia:Reliable sources").

The range of port numbers from 1024 to 49151 (210 to 214 + 215 − 1) are the [registered ports](https://en.wikipedia.org/wiki/Registered_port "Registered port"). They are assigned by [IANA](https://en.wikipedia.org/wiki/Internet_Assigned_Numbers_Authority "Internet Assigned Numbers Authority") for specific service upon application by a requesting entity.[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2) On most systems, registered ports can be used without superuser privileges.

Registered ports

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|Port|TCP|UDP|SCTP|DCCP|Description|
|1024|Reserved|   |||Reserved|
|1025|Yes|   |||[Teradata](https://en.wikipedia.org/wiki/Teradata "Teradata") [database management system](https://en.wikipedia.org/wiki/Database_management_system "Database management system") (Teradata) server|
|1027|Reserved||||Reserved|
||Yes|||Native IPv6 behind IPv4-to-IPv4 NAT Customer Premises Equipment (6a44)[[123]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6751-124)|
|1028|Reserved[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2)|   |   |   ||
|1029|Unofficial|   |||Microsoft [DCOM](https://en.wikipedia.org/wiki/Distributed_Component_Object_Model "Distributed Component Object Model") services|
|1058|Yes|   |||nim, [IBM](https://en.wikipedia.org/wiki/IBM "IBM") [AIX](https://en.wikipedia.org/wiki/IBM_AIX "IBM AIX") [Network Installation Manager](https://en.wikipedia.org/wiki/Network_Installation_Manager "Network Installation Manager") (NIM)|
|1059|Yes|   |||nimreg, IBM AIX Network Installation Manager (NIM)|
|1080|Yes|   |||[SOCKS](https://en.wikipedia.org/wiki/SOCKS "SOCKS") proxy|
|1085|Yes|   |||[WebObjects](https://en.wikipedia.org/wiki/WebObjects "WebObjects")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|1098|Yes|   |||rmiactivation, [Java remote method invocation](https://en.wikipedia.org/wiki/Java_remote_method_invocation "Java remote method invocation") (RMI) activation|
|1099|Yes|Assigned|||rmiregistry, Java remote method invocation (RMI) registry|
|1109|Reserved|   |||Reserved|
|1112|Unofficial||||[ESET](https://en.wikipedia.org/wiki/ESET "ESET") virus updates[[124]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-eset_user_guide_5_2-125)|
|1113|Assigned  <br>[[note 2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-126)[[125]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-127)|Yes[[126]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-128)|||[Licklider Transmission Protocol](https://en.wikipedia.org/wiki/Licklider_Transmission_Protocol "Licklider Transmission Protocol") (LTP) delay tolerant networking protocol|
|1119|Yes|   |||[Battle.net](https://en.wikipedia.org/wiki/Battle.net "Battle.net") chat/game protocol, used by [Blizzard](https://en.wikipedia.org/wiki/Blizzard_Entertainment "Blizzard Entertainment")'s games[[127]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-blizzard-129)|
|1167|Yes|Yes|Yes||Cisco [IP SLA](https://en.wikipedia.org/wiki/IP_SLA "IP SLA") (Service Assurance Agent)|
|1194|Yes|   |||[OpenVPN](https://en.wikipedia.org/wiki/OpenVPN#Networking "OpenVPN")|
|1198|Yes|   |||The [cajo project](https://en.wikipedia.org/wiki/Cajo_project "Cajo project") Free dynamic transparent distributed computing in Java|
|1212|Unofficial|   |||Equalsocial [Fediverse](https://en.wikipedia.org/wiki/Fediverse "Fediverse") protocol|
|1214|Yes|   |||[Kazaa](https://en.wikipedia.org/wiki/Kazaa "Kazaa")|
|1220|Yes|Assigned|||[QuickTime Streaming Server](https://en.wikipedia.org/wiki/QuickTime_Streaming_Server "QuickTime Streaming Server") administration[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|1234|Yes|   |||[Infoseek](https://en.wikipedia.org/wiki/Infoseek "Infoseek") search agent|
||Unofficial|||[VLC media player](https://en.wikipedia.org/wiki/VLC_media_player "VLC media player") default port for UDP/RTP stream|
|1241|Unofficial|   |||[Nessus Security Scanner](https://en.wikipedia.org/wiki/Nessus_(software) "Nessus (software)")|
|1270|Yes|   |||Microsoft [System Center Operations Manager](https://en.wikipedia.org/wiki/System_Center_Operations_Manager "System Center Operations Manager") (SCOM) (formerly Microsoft Operations Manager (MOM)) agent|
|1293|Yes|   |||Internet Protocol Security ([IPSec](https://en.wikipedia.org/wiki/IPSec "IPSec"))|
|1311|Yes|   |||Windows `RxMon.exe`|
|Unofficial||||Dell [OpenManage](https://en.wikipedia.org/wiki/OpenManage "OpenManage") HTTPS[[128]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-dell-opnmang-srvr-admin-130)|
|1314|Unofficial|   |||[Festival Speech Synthesis System](https://en.wikipedia.org/wiki/Festival_Speech_Synthesis_System "Festival Speech Synthesis System") server[[129]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-festival_7-131)|
|1319|Yes|   |||AMX ICSP (Protocol for communications with AMX control systems devices)|
|[1337](https://en.wikipedia.org/wiki/Leet "Leet")|Yes|   |||[Men&Mice DNS](https://en.wikipedia.org/w/index.php?title=Men%26Mice_DNS&action=edit&redlink=1 "Men&Mice DNS (page does not exist)")[[130]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-132)|
|Unofficial||||[Strapi](https://en.wikipedia.org/w/index.php?title=Strapi&action=edit&redlink=1 "Strapi (page does not exist)")[[131]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-133)|
|Unofficial||||[Sails.js](https://en.wikipedia.org/wiki/Sails.js "Sails.js") default port[[132]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-134)|
|1341|Yes|   |||Qubes ([Manufacturing Execution System](https://en.wikipedia.org/wiki/Manufacturing_Execution_System "Manufacturing Execution System"))|
|1344|Yes|   |||[Internet Content Adaptation Protocol](https://en.wikipedia.org/wiki/Internet_Content_Adaptation_Protocol "Internet Content Adaptation Protocol")|
|1352|Yes|   |||IBM [Lotus Notes](https://en.wikipedia.org/wiki/Lotus_Notes "Lotus Notes")/[Domino](https://en.wikipedia.org/wiki/IBM_Lotus_Domino "IBM Lotus Domino") [(RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call "Remote procedure call") protocol|
|1360|Yes|   |||[Mimer SQL](https://en.wikipedia.org/wiki/Mimer_SQL "Mimer SQL")|
|1414|Yes|   |||[IBM](https://en.wikipedia.org/wiki/IBM "IBM") [WebSphere MQ](https://en.wikipedia.org/wiki/WebSphere_MQ "WebSphere MQ") (formerly known as [MQSeries](https://en.wikipedia.org/wiki/MQSeries "MQSeries"))|
|1417|Yes|   |||[Timbuktu](https://en.wikipedia.org/wiki/Timbuktu_(software) "Timbuktu (software)") Service 1 Port|
|1418|Yes|   |||Timbuktu Service 2 Port|
|1419|Yes|   |||Timbuktu Service 3 Port|
|1420|Yes|   |||Timbuktu Service 4 Port|
|1431|Yes||||[Reverse Gossip Transport Protocol](https://en.wikipedia.org/w/index.php?title=Reverse_Gossip_Transport_Protocol&action=edit&redlink=1 "Reverse Gossip Transport Protocol (page does not exist)") (RGTP), used to access a General-purpose Reverse-Ordered Gossip Gathering System (GROGGS) [bulletin board](https://en.wikipedia.org/wiki/Bulletin_board_system "Bulletin board system"), such as that implemented on the [Cambridge University](https://en.wikipedia.org/wiki/University_of_Cambridge "University of Cambridge")'s [Phoenix system](https://en.wikipedia.org/wiki/Phoenix_(computer) "Phoenix (computer)")|
|1433|Yes|   |||[Microsoft SQL Server](https://en.wikipedia.org/wiki/Microsoft_SQL_Server "Microsoft SQL Server") [database management system](https://en.wikipedia.org/wiki/Database_management_system "Database management system") (MSSQL) server|
|1434|Yes|   |||Microsoft SQL Server database management system (MSSQL) monitor|
|1476|Yes|   |||WiFi Pineapple Hak5.|
|1481|Yes|   |||AIRS data interchange.|
|1492|Unofficial||||_[Sid Meier's CivNet](https://en.wikipedia.org/wiki/Sid_Meier%27s_CivNet "Sid Meier's CivNet")_, a multiplayer remake of the original _Sid Meier's Civilization_ game[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|1494|Unofficial|   |||Citrix [Independent Computing Architecture](https://en.wikipedia.org/wiki/Independent_Computing_Architecture "Independent Computing Architecture") (ICA)[[133]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-citrixblogger-135)|
|1500|Unofficial||||[IBM Tivoli Storage Manager](https://en.wikipedia.org/wiki/IBM_Tivoli_Storage_Manager "IBM Tivoli Storage Manager") server[[134]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ibm-support-swg21625297-136)|
|1501|Unofficial||||IBM Tivoli Storage Manager client scheduler[[134]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ibm-support-swg21625297-136)|
|1503|Unofficial|   |||[Windows Live Messenger](https://en.wikipedia.org/wiki/Windows_Live_Messenger "Windows Live Messenger") (Whiteboard and Application Sharing)[[135]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-msft-kb-927847-137)|
|1512|Yes|   |||Microsoft's [Windows Internet Name Service](https://en.wikipedia.org/wiki/Windows_Internet_Name_Service "Windows Internet Name Service") (WINS)|
|1513|Unofficial|   |||[Garena](https://en.wikipedia.org/wiki/Garena "Garena") game client[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|1521|Yes|   |||[nCUBE](https://en.wikipedia.org/wiki/NCUBE "NCUBE") License Manager|
|Unofficial||||[Oracle database](https://en.wikipedia.org/wiki/Oracle_database "Oracle database") default listener, in future releases[_[when?](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style/Dates_and_numbers#Chronological_items "Wikipedia:Manual of Style/Dates and numbers")_][[136]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-138) official port 2483 (TCP/IP) and 2484 (TCP/IP with SSL)|
| 1524 | Yes | Ingres | [Ingres (database)](https://en.wikipedia.org/wiki/Ingres_(database)) | | 1527 | Yes | Oracle Net Services (formerly SQL*Net) | [Oracle Net Services](https://en.wikipedia.org/wiki/Oracle_Net_Services) | | | | | (formerly known as SQL*Net)[[137]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-toadworld-1635-139) | | | Unofficial| Apache Derby Network Server | [Apache Derby Network Server](https://en.wikipedia.org/wiki/Apache_Derby#Derby_Network_Server) | | 1533 | Yes | IBM Sametime Virtual Places Chat | [IBM Sametime](https://en.wikipedia.org/wiki/IBM_Sametime) Virtual Places Chat |
|1534|No|Unofficial|||Eclipse Target Communication Framework[[139]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Eclipse_Foundation-141)|
|1540|Unofficial|   |||[1C:Enterprise](https://en.wikipedia.org/wiki/1C:Enterprise "1C:Enterprise") server agent (ragent)[[140]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-enterprise1c-ports-142)[[141]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-enterprise1c-admin-guide-143)|
|1541|Unofficial|   |||1C:Enterprise master cluster manager (rmngr)[[140]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-enterprise1c-ports-142)|
|1542|Unofficial|   |||1C:Enterprise configuration repository server[[140]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-enterprise1c-ports-142)|
|1545|Unofficial|   |||1C:Enterprise cluster administration server (RAS)[[140]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-enterprise1c-ports-142)|
|1547|Yes|   |||[Laplink](https://en.wikipedia.org/wiki/Laplink "Laplink")|
|1550|Unofficial|   |||1C:Enterprise debug server[[140]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-enterprise1c-ports-142)|
|Unofficial||||[Gadu-Gadu](https://en.wikipedia.org/wiki/Gadu-Gadu "Gadu-Gadu") (direct client-to-client)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|1560–1590|Unofficial|   |||1C:Enterprise cluster working processes[[140]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-enterprise1c-ports-142)|
|1581|Yes|   |||[MIL STD 2045-47001 VMF](https://en.wikipedia.org/wiki/Combat-net_radio "Combat-net radio")|
|Unofficial||||[IBM Tivoli Storage Manager](https://en.wikipedia.org/wiki/IBM_Tivoli_Storage_Manager "IBM Tivoli Storage Manager") web client[[134]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ibm-support-swg21625297-136)|
|1582–1583|Unofficial||||IBM Tivoli Storage Manager server web interface[[134]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ibm-support-swg21625297-136)|
|1583|Unofficial|   |||[Pervasive PSQL](https://en.wikipedia.org/wiki/Pervasive_PSQL "Pervasive PSQL")[[142]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-PSQLVx_SP3_readme-144)|
|1589|Yes|   |||Cisco VLAN Query Protocol ([VQP](https://en.wikipedia.org/wiki/VQP "VQP"))|
|1604|Unofficial|   |||[DarkComet](https://en.wikipedia.org/wiki/DarkComet "DarkComet") remote administration tool (RAT)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|1626|Unofficial||||[iSketch](https://en.wikipedia.org/wiki/ISketch "ISketch")[[143]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-isketch-help-145)|
|1627|Unofficial||||iSketch[[143]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-isketch-help-145)|
|1628|Yes|   |||[LonTalk](https://en.wikipedia.org/wiki/LonTalk "LonTalk") normal|
|1629|Yes|   |||LonTalk urgent|
|1645|No|Unofficial|||Early deployment of [RADIUS](https://en.wikipedia.org/wiki/RADIUS "RADIUS") before RFC standardization was done using UDP port number 1645. Enabled for compatibility reasons by default on [Cisco](https://en.wikipedia.org/wiki/Cisco "Cisco")[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_] and [Juniper Networks](https://en.wikipedia.org/wiki/Juniper_Networks "Juniper Networks") RADIUS servers.[[144]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-juniper-radius-overview-146) Official port is 1812. TCP port 1645 **MUST NOT** be used.[[145]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6613-147)|
|1646|No|Unofficial|||Old `radacct` port,[_[when?](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style/Dates_and_numbers#Chronological_items "Wikipedia:Manual of Style/Dates and numbers")_] RADIUS accounting protocol. Enabled for compatibility reasons by default on Cisco[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_] and [Juniper Networks](https://en.wikipedia.org/wiki/Juniper_Networks "Juniper Networks") RADIUS servers.[[144]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-juniper-radius-overview-146) Official port is 1813. TCP port 1646 **MUST NOT** be used.[[145]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6613-147)|
|1666|Unofficial||||[Perforce](https://en.wikipedia.org/wiki/Perforce "Perforce")[[146]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-perforce-cmdref-p4port-148)|
|1677|Yes|   |||[Novell GroupWise](https://en.wikipedia.org/wiki/Novell_GroupWise "Novell GroupWise") clients in client/server access mode|
|1688|Unofficial||||Microsoft [Key Management Service](https://en.wikipedia.org/wiki/Key_Management_Service "Key Management Service") (KMS) for Windows Activation[[147]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-msft-tn-ee939272-149)|
|1701|Yes|   |||[Layer 2 Forwarding Protocol](https://en.wikipedia.org/wiki/Layer_2_Forwarding_Protocol "Layer 2 Forwarding Protocol") (L2F)|
|Assigned|Yes|||[Layer 2 Tunneling Protocol](https://en.wikipedia.org/wiki/Layer_2_Tunneling_Protocol "Layer 2 Tunneling Protocol") (L2TP)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|1707|Yes|   |||[Windward Studios](https://en.wikipedia.org/wiki/Windward_Studios "Windward Studios") games (vdmplay)|
||Unofficial|||L2TP/IPsec, for establish an initial connection[[148]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc3193-150)|
|1714–1764|Unofficial|   |||[KDE Connect](https://en.wikipedia.org/wiki/KDE_Connect "KDE Connect")[[149]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-151)|
|1716||Unofficial|||[America's Army](https://en.wikipedia.org/wiki/America%27s_Army "America's Army"), a [massively multiplayer online game](https://en.wikipedia.org/wiki/Massively_multiplayer_online_game "Massively multiplayer online game") (MMO)[[150]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-aa-manual-ls-152)|
|1719|Yes|   |||[H.323](https://en.wikipedia.org/wiki/H.323 "H.323") registration and alternate communication|
|1720|Yes|   |||[H.323](https://en.wikipedia.org/wiki/H.323 "H.323") call signaling|
|1723|Yes|Assigned|||[Point-to-Point Tunneling Protocol](https://en.wikipedia.org/wiki/Point-to-Point_Tunneling_Protocol "Point-to-Point Tunneling Protocol") (PPTP)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|1755|Yes|   |||[Microsoft Media Services](https://en.wikipedia.org/wiki/Microsoft_Media_Services "Microsoft Media Services") (MMS, `ms-streaming`)|
|1761|Unofficial|   |||[Novell ZENworks](https://en.wikipedia.org/wiki/Novell_ZENworks "Novell ZENworks")[[151]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-novell-kb-3880659-153)[[152]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-novell-zen11-b18151xi-154)|
|1776|Yes|   |||[Emergency management information system](https://en.wikipedia.org/wiki/Emergency_management_information_system "Emergency management information system")|
|1783|Reserved|   |   |   |"Decomissioned [_[sic](https://en.wikipedia.org/wiki/Sic "Sic")_] Port 04/14/00, ms"[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2)|
|1801|Yes|   |||[Microsoft Message Queuing](https://en.wikipedia.org/wiki/Microsoft_Message_Queuing "Microsoft Message Queuing")|
|1812|Yes|   |||[RADIUS](https://en.wikipedia.org/wiki/RADIUS "RADIUS") authentication protocol, `radius`|
|1813|Yes|   |||[RADIUS](https://en.wikipedia.org/wiki/RADIUS "RADIUS") accounting protocol, `radius-acct`|
|1863|Yes|   |||[Microsoft Notification Protocol](https://en.wikipedia.org/wiki/Microsoft_Notification_Protocol "Microsoft Notification Protocol") (MSNP), used by the [Microsoft Messenger service](https://en.wikipedia.org/wiki/Microsoft_Messenger_service "Microsoft Messenger service") and a number of instant messaging [Messenger clients](https://en.wikipedia.org/wiki/Microsoft_Messenger_service#Official_clients "Microsoft Messenger service")|
|1880|Unofficial|   |||[Node-RED](https://en.wikipedia.org/wiki/Node-RED "Node-RED")[[153]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-nodered-docs-config-155)|
|1883|Yes|   |||[MQTT](https://en.wikipedia.org/wiki/MQTT "MQTT") (formerly MQ Telemetry Transport)|
|1900|Assigned|Yes|||[Simple Service Discovery Protocol](https://en.wikipedia.org/wiki/Simple_Service_Discovery_Protocol "Simple Service Discovery Protocol") (SSDP),[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) discovery of [UPnP](https://en.wikipedia.org/wiki/Universal_Plug_and_Play "Universal Plug and Play") devices|
|1935|Yes|   |||[Macromedia Flash](https://en.wikipedia.org/wiki/Adobe_Flash "Adobe Flash") Communications [Server MX](https://en.wikipedia.org/wiki/Macromedia_Studio_MX "Macromedia Studio MX"), the precursor to [Adobe Flash Media Server](https://en.wikipedia.org/wiki/Adobe_Flash_Media_Server "Adobe Flash Media Server") before [Macromedia](https://en.wikipedia.org/wiki/Macromedia "Macromedia")'s acquisition by [Adobe](https://en.wikipedia.org/wiki/Adobe_Inc "Adobe Inc") on December 3, 2005|
|Unofficial|   |||[Real Time Messaging Protocol](https://en.wikipedia.org/wiki/Real_Time_Messaging_Protocol "Real Time Messaging Protocol") (RTMP)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_], primarily used in [Adobe Flash](https://en.wikipedia.org/wiki/Adobe_Flash "Adobe Flash")[[154]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-adobe-helpx-ports-firewalls-156)|
|1965|Unofficial|No|||[Gemini](https://en.wikipedia.org/wiki/Gemini_(protocol) "Gemini (protocol)"), a lightweight, collaboratively designed protocol, striving to fill the gap between Gopher and HTTP[[155]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-gemini-specification-157)|
|1967||Unofficial|||Cisco IOS IP Service Level Agreements ([IP SLAs](https://en.wikipedia.org/wiki/IP_SLA "IP SLA")) Control Protocol[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|1972|Yes|   |||[InterSystems Caché](https://en.wikipedia.org/wiki/InterSystems_Cach%C3%A9 "InterSystems Caché"), and [InterSystems](https://en.wikipedia.org/wiki/InterSystems "InterSystems") IRIS versions 2020.3 and later|
|1984|Yes|   |||[Big Brother](https://en.wikipedia.org/wiki/Big_Brother_(software) "Big Brother (software)")|
|Unofficial||||Arweave mining node[[156]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-arweave-mining-guide-158)|
|1985|Assigned|Yes|||Cisco [Hot Standby Router Protocol](https://en.wikipedia.org/wiki/Hot_Standby_Router_Protocol "Hot Standby Router Protocol") (HSRP)[[157]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-cisco-support-hsrp-faq-159)[_[self-published source](https://en.wikipedia.org/wiki/Wikipedia:Verifiability#Self-published_sources "Wikipedia:Verifiability")_]|
|1998|Yes|   |||Cisco X.25 over TCP ([XOT](https://en.wikipedia.org/wiki/XOT "XOT")) service|
|2000|Yes|   |||Cisco [Skinny Client Control Protocol](https://en.wikipedia.org/wiki/Skinny_Client_Control_Protocol "Skinny Client Control Protocol") (SCCP)|
|2009|yes|yes|||only for Jasper|
|2010|Unofficial|   |||[Artemis: Spaceship Bridge Simulator](https://en.wikipedia.org/wiki/Artemis:_Spaceship_Bridge_Simulator "Artemis: Spaceship Bridge Simulator")[[158]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-160)|
|2033|Unofficial|   |||[Civilization IV](https://en.wikipedia.org/wiki/Civilization_IV "Civilization IV") multiplayer[[159]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-2k-support-201333253-161)|
|2049|Yes|Yes|Yes||[Network File System](https://en.wikipedia.org/wiki/Network_File_System "Network File System") (NFS)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|2056|Unofficial|   |||Civilization IV multiplayer[[159]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-2k-support-201333253-161)|
|2080|Yes|   |||[Autodesk](https://en.wikipedia.org/wiki/Autodesk "Autodesk") NLM ([FLEXlm](https://en.wikipedia.org/wiki/FLEXlm "FLEXlm"))|
|2082|Unofficial||||[cPanel](https://en.wikipedia.org/wiki/CPanel "CPanel") default[[160]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-cpanel-ckb-login-162)|
|2083|Yes|   |||Secure [RADIUS](https://en.wikipedia.org/wiki/RADIUS "RADIUS") Service (radsec)|
|Unofficial||||cPanel default [SSL](https://en.wikipedia.org/wiki/Secure_Sockets_Layer "Secure Sockets Layer")[[160]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-cpanel-ckb-login-162)|
|2086|Yes|   |||[GNUnet](https://en.wikipedia.org/wiki/GNUnet "GNUnet")|
|Unofficial||||[WebHost Manager](https://en.wikipedia.org/wiki/WHM "WHM") default[[160]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-cpanel-ckb-login-162)|
|2087|Unofficial||||WebHost Manager default [SSL](https://en.wikipedia.org/wiki/Secure_Sockets_Layer "Secure Sockets Layer")[[160]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-cpanel-ckb-login-162)|
|2095|Yes||||cPanel default web mail[[160]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-cpanel-ckb-login-162)|
|2096|Unofficial||||cPanel default [SSL](https://en.wikipedia.org/wiki/Secure_Sockets_Layer "Secure Sockets Layer") web mail[[160]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-cpanel-ckb-login-162)|
|2100|Unofficial||||[Warzone 2100](https://en.wikipedia.org/wiki/Warzone_2100 "Warzone 2100") multiplayer[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|2101|Unofficial||||[Networked Transport of RTCM via Internet Protocol](https://en.wikipedia.org/wiki/Networked_Transport_of_RTCM_via_Internet_Protocol "Networked Transport of RTCM via Internet Protocol") (NTRIP)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|2102|Yes|   |||[Zephyr Notification Service](https://en.wikipedia.org/wiki/Zephyr_(protocol) "Zephyr (protocol)") server|
|2103|Yes|   |||Zephyr Notification Service `serv-hm` connection|
|2104|Yes|   |||Zephyr Notification Service hostmanager|
|2123|Yes|   |||[GTP](https://en.wikipedia.org/wiki/GPRS_Tunnelling_Protocol "GPRS Tunnelling Protocol") control messages (GTP-C)|
|2142|Yes|   |||[TDMoIP](https://en.wikipedia.org/wiki/TDMoIP "TDMoIP") (TDM over IP)|
|2152|Yes|   |||[GTP](https://en.wikipedia.org/wiki/GPRS_Tunnelling_Protocol "GPRS Tunnelling Protocol") user data messages (GTP-U)|
|2159|Yes|   |||[GDB remote debug port](https://en.wikipedia.org/wiki/Gdbserver "Gdbserver")|
|2181|Yes|   |||EForward-document transport system|
|Unofficial||||[Apache ZooKeeper](https://en.wikipedia.org/wiki/Apache_ZooKeeper "Apache ZooKeeper") default client port[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|2195|Unofficial||||[Apple Push Notification Service](https://en.wikipedia.org/wiki/Apple_Push_Notification_Service "Apple Push Notification Service"), binary, gateway.[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[161]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT203609-163) Deprecated March 2021.[[162]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-dev-news-2020-10-09-164)|
|2196|Unofficial||||[Apple Push Notification Service](https://en.wikipedia.org/wiki/Apple_Push_Notification_Service "Apple Push Notification Service"), binary, feedback.[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[161]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT203609-163) Deprecated March 2021.[[162]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-dev-news-2020-10-09-164)|
|2197|Unofficial||||[Apple Push Notification Service](https://en.wikipedia.org/wiki/Apple_Push_Notification_Service "Apple Push Notification Service"), [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2 "HTTP/2"), [JSON](https://en.wikipedia.org/wiki/JSON "JSON")-based [API](https://en.wikipedia.org/wiki/API "API").|
|2210|Yes|   |||[NOAAPORT](https://en.wikipedia.org/wiki/National_Weather_Service "National Weather Service") Broadcast Network|
|2211|Yes|   |||[EMWIN](https://en.wikipedia.org/wiki/EMWIN "EMWIN")|
|2221|Unofficial||||[ESET](https://en.wikipedia.org/wiki/ESET "ESET") anti-virus updates[[124]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-eset_user_guide_5_2-125)|
|2222|Yes|   |||[EtherNet/IP](https://en.wikipedia.org/wiki/EtherNet/IP "EtherNet/IP") implicit messaging for IO data|
|Unofficial|   |||[DirectAdmin](https://en.wikipedia.org/wiki/DirectAdmin "DirectAdmin") Access[[163]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-directadmin-help-71-165)|
|2222–2226|Yes||||ESET Remote administrator[[124]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-eset_user_guide_5_2-125)|
|2240|Yes|   |||[General Dynamics](https://en.wikipedia.org/wiki/General_Dynamics "General Dynamics") Remote Encryptor Configuration Information Protocol (RECIPe)|
|2261|Yes|   |||[CoMotion](https://en.wikipedia.org/wiki/CoMotion "CoMotion") master|
|2262|Yes|   |||CoMotion backup|
|2302||Unofficial|||[ArmA](https://en.wikipedia.org/wiki/ArmA "ArmA") multiplayer[[164]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-:0-166)|
||Unofficial|||[Halo: Combat Evolved](https://en.wikipedia.org/wiki/Halo:_Combat_Evolved "Halo: Combat Evolved") multiplayer host[[165]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-msft-kb-829469-167)|
|2303||Unofficial|||ArmA multiplayer _(default port for game +1)_[[164]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-:0-166)[[166]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-168)|
||Unofficial|||Halo: Combat Evolved multiplayer listener[[165]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-msft-kb-829469-167)|
|2305||Unofficial|||ArmA multiplayer _(default port for game +3)_[[164]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-:0-166)|
|2351|Unofficial||||[AIM](https://en.wikipedia.org/wiki/AOL_Instant_Messenger "AOL Instant Messenger") game LAN network port[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|2368|Unofficial||||[Ghost (blogging platform)](https://en.wikipedia.org/wiki/Ghost_(blogging_platform) "Ghost (blogging platform)")[[167]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-gfb-config-169)|
|2369|Unofficial||||Default for [BMC Control-M/Server](https://en.wikipedia.org/wiki/BMC_Control-M "BMC Control-M") Configuration Agent|
|2370|Unofficial||||Default for BMC Control-M/Server, to allow the Control-M/Enterprise Manager to connect to the Control-M/Server|
|2372|Unofficial||||Default for [K9 Web Protection](https://en.wikipedia.org/wiki/K9_Web_Protection "K9 Web Protection")/parental controls, content filtering agent[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|2375|Yes|Reserved|||[Docker](https://en.wikipedia.org/wiki/Docker_(software) "Docker (software)") REST API (plain)|
|2376|Yes|Reserved|||Docker REST API (SSL)|
|2377|Yes|Reserved|||Docker Swarm cluster management communications[[168]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-docker-swarm-tutorial-170)[_[self-published source](https://en.wikipedia.org/wiki/Wikipedia:Verifiability#Self-published_sources "Wikipedia:Verifiability")_]|
|2379|Yes|Reserved|||CoreOS [etcd](https://en.wikipedia.org/wiki/Etcd "Etcd") client communication|
|Unofficial||||[KGS Go Server](https://en.wikipedia.org/wiki/KGS_Go_Server "KGS Go Server")[[169]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-gokgs-prefs-171)|
|2380|Yes|Reserved|||CoreOS etcd server communication|
|2389|Assigned|   |||OpenView Session Mgr|
|2399|Yes|   |||[FileMaker](https://en.wikipedia.org/wiki/FileMaker "FileMaker") Data Access Layer (ODBC/JDBC)|
|2401|Yes|   |||[CVS](https://en.wikipedia.org/wiki/Concurrent_Versions_System "Concurrent Versions System") version control system password-based server|
|2404|Yes|   |||[IEC 60870-5-104](https://en.wikipedia.org/wiki/IEC_60870-5-104 "IEC 60870-5-104"), used to send electric power telecontrol messages between two systems via directly connected [data circuits](https://en.wikipedia.org/w/index.php?title=Data_circuit&action=edit&redlink=1 "Data circuit (page does not exist)")|
|2424|Unofficial||||[OrientDB](https://en.wikipedia.org/wiki/OrientDB "OrientDB") database listening for binary client connections[[170]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-orientdb-docs-dbserver-172)|
|2427|Yes|   |||[Media Gateway Control Protocol](https://en.wikipedia.org/wiki/Media_Gateway_Control_Protocol "Media Gateway Control Protocol") (MGCP) media gateway|
|2447|Yes|   |||ovwdb—[OpenView](https://en.wikipedia.org/wiki/OpenView "OpenView") [Network Node Manager](https://en.wikipedia.org/wiki/Network_Node_Manager "Network Node Manager") (NNM) daemon|
|2456|Unofficial|   |||[Valheim](https://en.wikipedia.org/wiki/Valheim "Valheim")|
|2459|Yes|   |||[XRPL](https://en.wikipedia.org/wiki/Xrp "Xrp")|
|2480|Unofficial||||[OrientDB](https://en.wikipedia.org/wiki/OrientDB "OrientDB") database listening for HTTP client connections[[170]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-orientdb-docs-dbserver-172)|
|2483|Yes|   |||[Oracle database](https://en.wikipedia.org/wiki/Oracle_database "Oracle database") listening for insecure client connections to the listener, replaces port 1521[_[when?](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style/Dates_and_numbers#Chronological_items "Wikipedia:Manual of Style/Dates and numbers")_]|
|2484|Yes|   |||Oracle database listening for [SSL](https://en.wikipedia.org/wiki/Secure_Sockets_Layer "Secure Sockets Layer") client connections to the listener|
|2500|Unofficial|   |||NetFS communication[[171]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-173)|
|2501||Unofficial|||NetFS probe|
|2535|Yes|   |||[Multicast Address Dynamic Client Allocation Protocol](https://en.wikipedia.org/wiki/Multicast_Address_Dynamic_Client_Allocation_Protocol "Multicast Address Dynamic Client Allocation Protocol") (MADCAP).[[172]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc2730-port-174) All standard messages are UDP datagrams.[[173]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc2730-udp-175)|
|2541|Yes|   |||[LonTalk](https://en.wikipedia.org/wiki/LonTalk "LonTalk")/IP|
|2546–2548|Yes|   |||[EVault](https://en.wikipedia.org/wiki/EVault "EVault") data protection services|
|2593|Unofficial|   |||_[Ultima Online](https://en.wikipedia.org/wiki/Ultima_Online "Ultima Online")_ servers[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|2598|Unofficial||||Citrix [Independent Computing Architecture](https://en.wikipedia.org/wiki/Independent_Computing_Architecture "Independent Computing Architecture") (ICA) with Session Reliability; port 1494 without session reliability[[133]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-citrixblogger-135)|
|2599|Unofficial|   |||_Ultima Online_ servers[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|2628|Yes|   |||[DICT](https://en.wikipedia.org/wiki/DICT "DICT")[[174]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-176)|
|2638|Yes|   |||[SQL Anywhere](https://en.wikipedia.org/wiki/SQL_Anywhere "SQL Anywhere") database server[[175]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-177)[[176]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-178)|
|2710|Unofficial|   |||XBT Tracker.[[177]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-sf-xbtt-port-179) UDP tracker extension is considered experimental.[[178]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-sf-xbtt-udp-180)|
|2727|Yes|   |||[Media Gateway Control Protocol](https://en.wikipedia.org/wiki/Media_Gateway_Control_Protocol "Media Gateway Control Protocol") (MGCP) media gateway controller (call agent)|
|2775|Yes|   |||[Short Message Peer-to-Peer](https://en.wikipedia.org/wiki/Short_Message_Peer-to-Peer "Short Message Peer-to-Peer") (SMPP)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|2809|Yes|   |||corbaloc:iiop URL, per the [CORBA](https://en.wikipedia.org/wiki/CORBA "CORBA") 3.0.3 specification|
|2811|Yes|   |||gsi ftp, per the [GridFTP](https://en.wikipedia.org/wiki/GridFTP "GridFTP") specification|
|2827|Unofficial||||[I2P](https://en.wikipedia.org/wiki/I2P "I2P") BOB Bridge[[179]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-geti2p-ports-181)|
|2944|Yes|   |||[Megaco](https://en.wikipedia.org/wiki/Megaco "Megaco") text H.248|
|2945|Yes|   |||Megaco binary (ASN.1) H.248|
|2947|Yes|   |||[gpsd](https://en.wikipedia.org/wiki/Gpsd "Gpsd"), GPS daemon|
|2948–2949|Yes|   |||[WAP](https://en.wikipedia.org/wiki/Wireless_Application_Protocol "Wireless Application Protocol") push [Multimedia Messaging Service](https://en.wikipedia.org/wiki/Multimedia_Messaging_Service "Multimedia Messaging Service") (MMS)|
|2967|Yes|   |||[Symantec System Center](https://en.wikipedia.org/wiki/Symantec_AntiVirus "Symantec AntiVirus") agent (SSC-AGENT)|
|2989|Yes|   |||Zarkov Intelligent Agent Communication[[180]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-182)|
|3000|Unofficial||||[Ruby on Rails](https://en.wikipedia.org/wiki/Ruby_on_Rails "Ruby on Rails") development default[[181]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-183)|
|Unofficial||||[Meteor](https://en.wikipedia.org/wiki/Meteor_(web_framework) "Meteor (web framework)") development default[[182]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-184)[_[failed verification](https://en.wikipedia.org/wiki/Wikipedia:Verifiability "Wikipedia:Verifiability")_]|
|Unofficial|   |||[Resilio Sync](https://en.wikipedia.org/wiki/Resilio_Sync "Resilio Sync"),[[183]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-getsync-kb-204754759-185) spun from BitTorrent Sync.|
|Unofficial||||Create React App, script to create single-page [React](https://en.wikipedia.org/wiki/React_(JavaScript_library) "React (JavaScript library)") applications[[184]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-186)|
|Unofficial||||Gogs (self-hosted GIT service) [[185]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-187)|
|Unofficial||||[Grafana](https://en.wikipedia.org/wiki/Grafana "Grafana")[[186]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-188)|
|3001|Yes|No|||Honeywell Prowatch[[187]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-189)|
|3004|Unofficial||||[iSync](https://en.wikipedia.org/wiki/ISync "ISync")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|3010|Yes|   |||KWS Connector|
|3020|Yes|   |||[Common Internet File System](https://en.wikipedia.org/wiki/Common_Internet_File_System "Common Internet File System") (CIFS). See also port 445 for [Server Message Block](https://en.wikipedia.org/wiki/Server_Message_Block "Server Message Block") (SMB), a dialect of CIFS.|
|3050|Yes|   |||gds-db ([Interbase](https://en.wikipedia.org/wiki/Interbase "Interbase")/[Firebird](https://en.wikipedia.org/wiki/Firebird_(database_server) "Firebird (database server)") databases)|
|3052|Yes|   |||[APC](https://en.wikipedia.org/wiki/APC_by_Schneider_Electric "APC by Schneider Electric") [PowerChute Network](https://en.wikipedia.org/wiki/PowerChute "PowerChute")|
|3074|Yes|   |||Xbox LIVE and [Games for Windows – Live](https://en.wikipedia.org/wiki/Games_for_Windows_%E2%80%93_Live "Games for Windows – Live")|
|3101|Unofficial||||[BlackBerry Enterprise Server](https://en.wikipedia.org/wiki/BlackBerry_Enterprise_Server "BlackBerry Enterprise Server") communication protocol[[188]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-blkbr-kb-3735-190)|
|3128|Unofficial|No|||[Squid](https://en.wikipedia.org/wiki/Squid_(software) "Squid (software)") caching web proxy[[189]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-squid-doc-http_port-191)|
|3225|Yes|   |||[Fibre Channel over IP](https://en.wikipedia.org/wiki/Fibre_Channel_over_IP "Fibre Channel over IP") (FCIP)|
|3233|Yes|   |||[WhiskerControl](https://en.wikipedia.org/wiki/WhiskerControl "WhiskerControl") research control protocol|
|3260|Yes|   |||[iSCSI](https://en.wikipedia.org/wiki/ISCSI "ISCSI")|
|3268|Yes|   |||msft-gc, Microsoft Global Catalog ([LDAP](https://en.wikipedia.org/wiki/LDAP "LDAP") service which contains data from [Active Directory](https://en.wikipedia.org/wiki/Active_Directory "Active Directory") forests)|
|3269|Yes|   |||msft-gc-ssl, Microsoft Global Catalog over [SSL](https://en.wikipedia.org/wiki/Secure_Sockets_Layer "Secure Sockets Layer") (similar to port 3268, [LDAP](https://en.wikipedia.org/wiki/LDAP "LDAP") over [SSL](https://en.wikipedia.org/wiki/Secure_Sockets_Layer "Secure Sockets Layer"))|
|3283|Yes|   |||_Net Assistant_,[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) a predecessor to _Apple Remote Desktop_|
|Unofficial|   |||[Apple Remote Desktop](https://en.wikipedia.org/wiki/Apple_Remote_Desktop "Apple Remote Desktop") 2.0 or later[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|3290||Unofficial|||[Virtual Air Traffic Simulation](https://en.wikipedia.org/wiki/VATSIM "VATSIM") (VATSIM) network voice communication[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|3305|Yes|   |||[Odette File Transfer Protocol](https://en.wikipedia.org/wiki/OFTP "OFTP") (OFTP)|
|3306|Yes|Assigned|||[MySQL](https://en.wikipedia.org/wiki/MySQL "MySQL") database system[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|3323|Unofficial|   |||[DECE](https://en.wikipedia.org/wiki/DECE "DECE") GEODI Server|
|3332||Unofficial|||Thundercloud DataPath Overlay Control|
|3333|Unofficial||||[Eggdrop](https://en.wikipedia.org/wiki/Eggdrop "Eggdrop"), an IRC bot default port[[190]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-192)|
|Unofficial||||[Network Caller ID](https://en.wikipedia.org/wiki/Network_Caller_ID "Network Caller ID") server|
|Unofficial||||[CruiseControl.rb](https://en.wikipedia.org/wiki/CruiseControl.rb "CruiseControl.rb")[[191]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-193)|
|Unofficial||||OpenOCD ([gdbserver](https://en.wikipedia.org/wiki/Gdbserver "Gdbserver"))[[192]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-openocd-194)|
|3344|Unofficial|   |||Repetier-Server|
|3351|Unofficial|   |||[Pervasive PSQL](https://en.wikipedia.org/wiki/Pervasive_PSQL "Pervasive PSQL")[[142]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-PSQLVx_SP3_readme-144)|
|3386|Yes|   |||[GTP'](https://en.wikipedia.org/wiki/GTP%27 "GTP'") [3GPP](https://en.wikipedia.org/wiki/3GPP "3GPP") [GSM](https://en.wikipedia.org/wiki/GSM "GSM")/[UMTS](https://en.wikipedia.org/wiki/UMTS "UMTS") [CDR](https://en.wikipedia.org/wiki/Call_detail_record "Call detail record") logging protocol|
|3389|Yes|   |||[Microsoft Terminal Server](https://en.wikipedia.org/wiki/Microsoft_Terminal_Server "Microsoft Terminal Server") ([RDP](https://en.wikipedia.org/wiki/Remote_Desktop_Protocol "Remote Desktop Protocol")) officially registered as Windows Based Terminal (WBT)[[193]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-195)|
|3396|Yes|   |||[Novell](https://en.wikipedia.org/wiki/Novell "Novell") NDPS Printer Agent|
|3412|Yes|   |||xmlBlaster|
|3423|Yes||||Xware xTrm Communication Protocol|
|3424|Yes||||Xware xTrm Communication Protocol over SSL|
|3435|Yes|   |||Pacom Security User Port|
|3455|Yes|   |||[Resource Reservation Protocol](https://en.wikipedia.org/wiki/Resource_Reservation_Protocol "Resource Reservation Protocol") (RSVP)|
|3478|Yes|   |||[STUN](https://en.wikipedia.org/wiki/STUN "STUN"), a protocol for NAT traversal[[194]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-STUN-196)|
|Yes|   |||[TURN](https://en.wikipedia.org/wiki/Traversal_Using_Relay_NAT "Traversal Using Relay NAT"), a protocol for NAT traversal[[195]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-TURN-197) (extension to STUN)|
|Yes|   |||STUN Behavior Discovery.[[196]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc5780-198) See also port 5349.|
|3478-3481||Unofficial|||[Microsoft Teams](https://en.wikipedia.org/wiki/Microsoft_Teams "Microsoft Teams")[[197]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-199)|
|3479|Unofficial|   |||[PlayStation Network](https://en.wikipedia.org/wiki/PlayStation_Network "PlayStation Network")[[198]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-playstation-manual-ps4-nw_test-200)|
|3480|Unofficial|   |||PlayStation Network[[198]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-playstation-manual-ps4-nw_test-200)|
|3483||Yes|||[Slim Devices](https://en.wikipedia.org/wiki/Slim_Devices "Slim Devices") discovery protocol|
|Yes||||[Slim Devices](https://en.wikipedia.org/wiki/Slim_Devices "Slim Devices") SlimProto protocol|
|3493|Yes|   |||[Network UPS Tools](https://en.wikipedia.org/wiki/Network_UPS_Tools "Network UPS Tools") (NUT)|
|3503|Yes|   |||MPLS LSP-echo Port|
|3516|Yes|   |||Smartcard Port|
|3527||Yes|||[Microsoft Message Queuing](https://en.wikipedia.org/wiki/Microsoft_Message_Queuing "Microsoft Message Queuing")|
|3535|Unofficial||||[SMTP](https://en.wikipedia.org/wiki/SMTP "SMTP") alternate[[199]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-201)|
|3544||Yes|||[Teredo tunneling](https://en.wikipedia.org/wiki/Teredo_tunneling "Teredo tunneling")|
|3551|Yes|   |||Apcupsd Information Port [[200]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-202)|
|3601|Yes||||[SAP](https://en.wikipedia.org/wiki/SAP "SAP") Message Server Port[[201]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-203)|
|3632|Yes|Assigned|||[Distcc](https://en.wikipedia.org/wiki/Distcc "Distcc"), distributed compiler[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|3645|Yes|   |||[Cyc](https://en.wikipedia.org/wiki/Cyc "Cyc")|
|3655|Yes|   |||[Advanced Systems Concepts, Inc.](https://en.wikipedia.org/wiki/Advanced_Systems_Concepts,_Inc. "Advanced Systems Concepts, Inc.") ActiveBatch Exec Agent[[202]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-iana.org-204)|
|3659|Yes|   |||Apple [SASL](https://en.wikipedia.org/wiki/Simple_Authentication_and_Security_Layer "Simple Authentication and Security Layer"), used by [macOS Server](https://en.wikipedia.org/wiki/MacOS_Server "MacOS Server") Password Server[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
||Unofficial|||Battlefield 4|
|3667|Yes|   |||Information Exchange|
|3671|Yes|   |||KNXnet/IP(EIBnet/IP)|
|3689|Yes|Assigned|||[Digital Audio Access Protocol](https://en.wikipedia.org/wiki/Digital_Audio_Access_Protocol "Digital Audio Access Protocol") (DAAP), used by [Apple's](https://en.wikipedia.org/wiki/Apple_Inc. "Apple Inc.") [iTunes](https://en.wikipedia.org/wiki/ITunes "ITunes") and [AirPlay](https://en.wikipedia.org/wiki/AirPlay "AirPlay")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|3690|Yes|   |||[Subversion (SVN)](https://en.wikipedia.org/wiki/Subversion_(software) "Subversion (software)")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) version control system|
|3702|Yes|   |||[Web Services Dynamic Discovery](https://en.wikipedia.org/wiki/Web_Services_Dynamic_Discovery "Web Services Dynamic Discovery") (WS-Discovery), used by various components of [Windows Vista](https://en.wikipedia.org/wiki/Windows_Vista "Windows Vista") and later|
|3721|Unofficial||||[ES File Explorer](https://en.wikipedia.org/wiki/ES_File_Explorer "ES File Explorer") FTP server|
|3724|Yes|   |||Some [Blizzard](https://en.wikipedia.org/wiki/Blizzard_Entertainment "Blizzard Entertainment") games[[127]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-blizzard-129)|
|Unofficial||||[Club Penguin](https://en.wikipedia.org/wiki/Club_Penguin "Club Penguin") Disney online game for kids|
|3725|Yes|   |||Netia NA-ER Port|
|3749|Yes|   |||[CimTrak](https://www.cimcor.com/cimtrak/) registered port|
|3768|Yes|   |||RBLcheckd server daemon|
|3784||Yes|||Bidirectional Forwarding Detection (BFD)for IPv4 and IPv6 (Single Hop) (RFC 5881)|
|3785||Unofficial|||VoIP program used by [Ventrilo](https://en.wikipedia.org/wiki/Ventrilo "Ventrilo")|
|3799||Yes|||[RADIUS](https://en.wikipedia.org/wiki/RADIUS "RADIUS") change of authorization|
|3804|Yes|   |||Harman Professional [HiQnet](https://en.wikipedia.org/w/index.php?title=HiQnet&action=edit&redlink=1 "HiQnet (page does not exist)") protocol|
|3825|Unofficial||||RedSeal Networks client/server connection[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|3826|Yes|   |||WarMUX game server|
|Unofficial||||RedSeal Networks client/server connection[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|3835|Unofficial||||RedSeal Networks client/server connection[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|3830|Yes|   |||System Management Agent, developed and used by Cerner to monitor and manage solutions|
|3856|Unofficial|   |||ERP Server Application used by F10 Software|
|3880|Yes|   |||IGRS|
|3868|Yes||Yes||[Diameter](https://en.wikipedia.org/wiki/Diameter_(protocol) "Diameter (protocol)") base protocol (RFC 3588)|
|3872|Yes||||[Oracle Enterprise Manager](https://en.wikipedia.org/wiki/Oracle_Enterprise_Manager "Oracle Enterprise Manager") Remote Agent|
|3900|Yes||||udt_os, [IBM UniData](https://en.wikipedia.org/wiki/IBM_U2 "IBM U2") UDT OS[[203]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-205)|
|3960||Unofficial|||_[Warframe](https://en.wikipedia.org/wiki/Warframe "Warframe")_ online interaction[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|3962||Unofficial|||_Warframe_ online interaction[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|3978|Unofficial|   |||_[OpenTTD](https://en.wikipedia.org/wiki/OpenTTD "OpenTTD")_ game (masterserver and content service)|
|3978|Unofficial||||Palo Alto Networks' Panorama management of firewalls and log collectors & pre-PAN-OS 8.0 Panorama-to-managed devices software updates.[[204]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-EDU-120_10-206)|
|3979|Unofficial|   |||_OpenTTD_ game|
|3999|Yes|   |||Norman distributed scanning service|
|4000|Unofficial|   |||_[Diablo II](https://en.wikipedia.org/wiki/Diablo_II "Diablo II")_ game|
|4001|Unofficial||||_[Microsoft Ants](https://en.wikipedia.org/wiki/Microsoft_Ants "Microsoft Ants")_ game|
|Unofficial||||CoreOS [etcd](https://en.wikipedia.org/wiki/Etcd "Etcd") client communication|
|4018|Yes|   |||Protocol information and warnings[_[clarification needed](https://en.wikipedia.org/wiki/Wikipedia:Please_clarify "Wikipedia:Please clarify")_]|
|4035|Unofficial||||[IBM](https://en.wikipedia.org/wiki/IBM "IBM") Rational Developer for System z Remote System Explorer Daemon|
|4045|Unofficial|   |||[Solaris](https://en.wikipedia.org/wiki/Solaris_(operating_system) "Solaris (operating system)") lockd NFS lock daemon/manager|
|4050|Unofficial||||Mud Master Chat protocol (MMCP) - Peer-to-peer communications between [MUD](https://en.wikipedia.org/wiki/Multi-user_dungeon "Multi-user dungeon") clients.[[205]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-207)|
|4069||Yes|||[Minger Email Address Verification Protocol](https://en.wikipedia.org/wiki/Minger_Email_Address_Verification_Protocol "Minger Email Address Verification Protocol")[[206]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-208)|
|4070|Unofficial|   |||[Amazon Echo](https://en.wikipedia.org/wiki/Amazon_Echo "Amazon Echo") Dot ([Amazon Alexa](https://en.wikipedia.org/wiki/Amazon_Alexa "Amazon Alexa")) streaming connection with [Spotify](https://en.wikipedia.org/wiki/Spotify "Spotify")[[207]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-209)|
|4089|Yes|   |||OpenCORE Remote Control Service|
|4090|Yes|   |||[Kerio](https://en.wikipedia.org/wiki/Kerio_Technologies "Kerio Technologies")|
|4093|Yes|   |||PxPlus Client server interface [ProvideX](https://en.wikipedia.org/wiki/ProvideX "ProvideX")|
|4096|Yes|   |||[Ascom Timeplex](https://en.wikipedia.org/wiki/Ascom_(company) "Ascom (company)") Bridge Relay Element (BRE)|
|4105|Yes|   |||Shofar (ShofarNexus)|
|4111|Yes|Assigned|||[Xgrid](https://en.wikipedia.org/wiki/Xgrid "Xgrid")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|4116|Yes|   |||Smartcard-TLS|
|4123|Assigned|Yes|||Z-Wave Protocol[[208]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-210)|
|4125|Unofficial||||[Microsoft Remote Web Workplace](https://en.wikipedia.org/wiki/Microsoft_Remote_Web_Workplace "Microsoft Remote Web Workplace") administration|
|4172|Yes|   |||[Teradici](https://en.wikipedia.org/wiki/Teradici "Teradici") [PCoIP](https://en.wikipedia.org/wiki/PCoIP "PCoIP")|
|4190|Yes||||ManageSieve[[209]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-211)|
|4195|Yes|   |   |   |[AWS](https://en.wikipedia.org/wiki/AWS "AWS") protocol for cloud remoting solution|
|4197|Yes|   |||Harman International's HControl protocol for control and monitoring of Audio, Video, Lighting and Control equipment|
|4198|Unofficial|   |||Couch Potato Android app[[210]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-212)|
|4200|Unofficial||||[Angular](https://en.wikipedia.org/wiki/Angular_(web_framework) "Angular (web framework)") app|
|4201|Unofficial||||[TinyMUD](https://en.wikipedia.org/wiki/TinyMUD "TinyMUD") and various derivatives|
|4222|Unofficial||||NATS server default port[[211]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-213)|
|4226|Unofficial|   |||[Aleph One](https://en.wikipedia.org/wiki/Aleph_One_(computer_game) "Aleph One (computer game)"), a computer game|
|4242|Unofficial||||[Orthanc](https://en.wikipedia.org/wiki/Orthanc_(software) "Orthanc (software)") – [DICOM](https://en.wikipedia.org/wiki/DICOM "DICOM") server[[212]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-orthanc-book-configuration-214)|
|Unofficial||||[Quassel](https://en.wikipedia.org/wiki/Quassel "Quassel") distributed IRC client|
|4243|Unofficial||||[Docker](https://en.wikipedia.org/wiki/Docker_(software) "Docker (software)") implementations, redistributions, and setups default[[213]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-215)[_[needs update?](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style/Dates_and_numbers#Chronological_items "Wikipedia:Manual of Style/Dates and numbers")_]|
|Unofficial||||[CrashPlan](https://en.wikipedia.org/wiki/CrashPlan "CrashPlan")|
|4244|Unofficial|   |||[Viber](https://en.wikipedia.org/wiki/Viber "Viber")[[214]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-viber-216)|
|4303|Yes|   |||Simple Railroad Command Protocol (SRCP)|
|4307|Yes||||TrueConf Client - TrueConf Server media data exchange[[215]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-217)|
|4321|Yes||||[Referral Whois (RWhois) Protocol](https://en.wikipedia.org/wiki/RWhois "RWhois")[[216]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-218)|
|4444|Unofficial|   |||[Oracle](https://en.wikipedia.org/wiki/Oracle_Corporation "Oracle Corporation") WebCenter Content: Content Server—Intradoc Socket port. (formerly known as Oracle [Universal Content Management](https://en.wikipedia.org/wiki/Universal_Content_Management "Universal Content Management")).|
|Unofficial|   |||[Metasploit](https://en.wikipedia.org/wiki/Metasploit "Metasploit")'s default listener port[[217]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-219)|
|Unofficial|   |||[Xvfb](https://en.wikipedia.org/wiki/Xvfb "Xvfb") X server virtual frame buffer service|
|Unofficial||||OpenOCD ([Telnet](https://en.wikipedia.org/wiki/Telnet "Telnet"))[[192]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-openocd-194)|
|4444–4445|Unofficial||||[I2P](https://en.wikipedia.org/wiki/I2P "I2P") HTTP/S proxy|
|4486|Yes|   |||Integrated Client Message Service (ICMS)|
|4488|Yes|Assigned|||Apple Wide Area Connectivity Service, used by [Back to My Mac](https://en.wikipedia.org/wiki/Back_to_My_Mac "Back to My Mac")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|4500|Assigned|Yes|||[IPSec NAT Traversal](https://en.wikipedia.org/wiki/IPsec_Passthrough "IPsec Passthrough")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) (RFC 3947, RFC 4306)|
|4502–4534|Yes||||Microsoft Silverlight connectable ports under non-elevated trust|
|4505–4506|Unofficial||||[Salt](https://en.wikipedia.org/wiki/Salt_(software) "Salt (software)") master|
|4534||Unofficial|||[Armagetron Advanced](https://en.wikipedia.org/wiki/Armagetron_Advanced "Armagetron Advanced") server default|
|4560|Unofficial||||default [Log4j](https://en.wikipedia.org/wiki/Log4j "Log4j") socketappender port|
|4567|Unofficial||||[Sinatra](https://en.wikipedia.org/wiki/Sinatra_(software) "Sinatra (software)") default server port in development mode (HTTP)|
|4569||Yes|||[Inter-Asterisk eXchange](https://en.wikipedia.org/wiki/Inter-Asterisk_eXchange "Inter-Asterisk eXchange") (IAX2)|
|4604|Yes||||[Identity Registration Protocol](https://en.wikipedia.org/wiki/Identity_Registration_Protocol "Identity Registration Protocol")|
|4605|Yes||||[Direct End to End Secure Chat Protocol](https://en.wikipedia.org/wiki/Direct_End_to_End_Secure_Chat_Protocol "Direct End to End Secure Chat Protocol")|
|4610–4640|Unofficial||||[QualiSystems](https://en.wikipedia.org/wiki/QualiSystems "QualiSystems") TestShell Suite Services|
|4662|Yes|   |||OrbitNet Message Service|
|Unofficial||||Default for older versions of [eMule](https://en.wikipedia.org/wiki/EMule "EMule")[[218]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-eMule-220)|
|4664|Unofficial||||[Google Desktop Search](https://en.wikipedia.org/wiki/Google_Desktop "Google Desktop")|
|4672||Unofficial|||Default for older versions of [eMule](https://en.wikipedia.org/wiki/EMule "EMule")[[218]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-eMule-220)|
|4711|Unofficial||||[eMule](https://en.wikipedia.org/wiki/EMule "EMule") optional web interface[[218]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-eMule-220)|
|4713|Unofficial||||[PulseAudio](https://en.wikipedia.org/wiki/PulseAudio "PulseAudio") sound server|
|4723|Unofficial||||[Appium](https://en.wikipedia.org/wiki/Appium "Appium") open source automation tool|
|4724|Unofficial||||Default bootstrap port to use on device to talk to [Appium](https://en.wikipedia.org/wiki/Appium "Appium")|
|4728|Yes||||Computer Associates Desktop and Server Management (DMP)/Port Multiplexer[[219]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-SANS-221)|
|4730|Yes|   |||[Gearman](https://en.wikipedia.org/wiki/Gearman "Gearman")'s job server|
|4739|Yes|   |||[IP Flow Information Export](https://en.wikipedia.org/wiki/IP_Flow_Information_Export "IP Flow Information Export")|
|4747|Unofficial||||[Apprentice](https://en.wikipedia.org/wiki/Apprentice_(software) "Apprentice (software)")|
|4753|Yes|   |||SIMON (service and discovery)|
|4757|Unofficial|   |||[Select Studios](https://www.select-studios.com/) Official Servers|
|4789||Yes|||Virtual eXtensible Local Area Network ([VXLAN](https://en.wikipedia.org/wiki/Virtual_Extensible_LAN "Virtual Extensible LAN"))|
|4791||Yes|||[IP Routable RocE](https://en.wikipedia.org/wiki/RDMA_over_Converged_Ethernet "RDMA over Converged Ethernet") (RoCEv2)|
|4840|Yes|   |||OPC UA Connection Protocol (TCP) and OPC UA Multicast Datagram Protocol (UDP) for [OPC Unified Architecture](https://en.wikipedia.org/wiki/OPC_Unified_Architecture "OPC Unified Architecture") from [OPC Foundation](https://en.wikipedia.org/wiki/OPC_Foundation "OPC Foundation")|
|4843|Yes|   |||OPC UA TCP Protocol over TLS/SSL for [OPC Unified Architecture](https://en.wikipedia.org/wiki/OPC_Unified_Architecture "OPC Unified Architecture") from [OPC Foundation](https://en.wikipedia.org/wiki/OPC_Foundation "OPC Foundation")|
|4847|Yes|   |||Web Fresh Communication, Quadrion Software & Odorless Entertainment|
|4848|Unofficial||||Java, Glassfish Application Server administration default|
|4894|Yes|   |||[LysKOM](https://en.wikipedia.org/wiki/LysKOM "LysKOM") Protocol A[[220]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-222)|
|4944|No|Unofficial|||[DrayTek](https://en.wikipedia.org/wiki/DrayTek "DrayTek") DSL Status Monitoring[[221]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-draytek-support-5365-223)|
|4949|Yes||||Munin Resource Monitoring Tool|
|4950|Yes|   |||Cylon Controls UC32 Communications Port|
|5000|Unofficial||||[UPnP](https://en.wikipedia.org/wiki/Universal_Plug_and_Play "Universal Plug and Play")—Windows network device interoperability|
|Unofficial|   |||[VTun](https://en.wikipedia.org/wiki/VTun "VTun"), [VPN](https://en.wikipedia.org/wiki/VPN "VPN") Software|
|Unofficial||||[ASP.NET Core](https://en.wikipedia.org/wiki/ASP.NET_Core "ASP.NET Core") — Development Webserver|
||Unofficial|||[FlightGear](https://en.wikipedia.org/wiki/FlightGear "FlightGear") multiplayer[[222]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-auto-224)|
|Unofficial||||[Synology Inc.](https://en.wikipedia.org/wiki/Synology_Inc. "Synology Inc.") Management Console, File Station, Audio Station|
|Unofficial||||[Flask](https://en.wikipedia.org/wiki/Flask_(web_framework) "Flask (web framework)") Development Webserver|
|Unofficial||||[Heroku](https://en.wikipedia.org/wiki/Heroku "Heroku") console access|
|Unofficial|   |||[Docker](https://en.wikipedia.org/wiki/Docker_(software) "Docker (software)") Registry[[223]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-225)|
|Unofficial||||[AT&T U-verse](https://en.wikipedia.org/wiki/AT%26T_U-verse "AT&T U-verse") [public, educational, and government access](https://en.wikipedia.org/wiki/Public,_educational,_and_government_access "Public, educational, and government access") (PEG) streaming over [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol "Hypertext Transfer Protocol")[[224]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-226)|
|Unofficial|   |||[High-Speed SECS Message Services](https://en.wikipedia.org/wiki/High-Speed_SECS_Message_Services "High-Speed SECS Message Services")[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|Unofficial||||[3CX Phone System](https://en.wikipedia.org/wiki/3CX_Phone_System "3CX Phone System") Management Console/Web Client (HTTP)|
|Unofficial||||RidgeRun GStreamer Daemon (GSTD) [[225]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-227)|
|Unofficial||||[Apple's](https://en.wikipedia.org/wiki/Apple_Inc. "Apple Inc.") [AirPlay](https://en.wikipedia.org/wiki/AirPlay "AirPlay") Receiver[[226]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-228)|
|5000–5500|No|Unofficial|||_[League of Legends](https://en.wikipedia.org/wiki/League_of_Legends "League of Legends")_, a [multiplayer online battle arena](https://en.wikipedia.org/wiki/Multiplayer_online_battle_arena "Multiplayer online battle arena") video game[[227]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-riotgames-kb-201752664-229)|
|5001|Unofficial||||[Slingbox](https://en.wikipedia.org/wiki/Slingbox "Slingbox") and Slingplayer|
|Unofficial|   |||[Iperf](https://en.wikipedia.org/wiki/Iperf "Iperf") (Tool for measuring TCP and UDP bandwidth performance)|
|Unofficial||||[Synology Inc.](https://en.wikipedia.org/wiki/Synology_Inc. "Synology Inc.") Secured Management Console, File Station, Audio Station|
|Unofficial||||[3CX Phone System](https://en.wikipedia.org/wiki/3CX_Phone_System "3CX Phone System") Management Console/Web Client (HTTPS)|
|5002|Unofficial||||ASSA ARX access control system[[228]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-230)|
|5003|Yes|Assigned|||[FileMaker](https://en.wikipedia.org/wiki/FileMaker "FileMaker") – name binding and transport[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|5004|Yes|   ||Yes|[Real-time Transport Protocol](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol "Real-time Transport Protocol") media data (RTP) (RFC 3551, RFC 4571)|
|5005|Yes|   ||Yes|[Real-time Transport Protocol control protocol](https://en.wikipedia.org/wiki/RTP_Control_Protocol "RTP Control Protocol") (RTCP) (RFC 3551, RFC 4571)|
|5007|Unofficial||||Palo Alto Networks - User-ID agent|
|5010|Yes|   |||Registered to: TelePath (the IBM FlowMark [workflow-management system](https://en.wikipedia.org/wiki/Workflow-management_system "Workflow-management system") messaging platform)[[229]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Hill-231)  <br>The TCP port is now used for: IBM [WebSphere MQ](https://en.wikipedia.org/wiki/WebSphere_MQ "WebSphere MQ") Workflow|
|5011|Yes|   |||TelePath (the IBM FlowMark [workflow-management system](https://en.wikipedia.org/wiki/Workflow-management_system "Workflow-management system") messaging platform)[[229]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Hill-231)|
|5022|Unofficial||||MSSQL Server Replication and Database mirroring endpoints[[230]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Microsoft-232)|
|5025|Yes|   |||scpi-raw [Standard Commands for Programmable Instruments](https://en.wikipedia.org/wiki/Standard_Commands_for_Programmable_Instruments "Standard Commands for Programmable Instruments")|
|5029||Unofficial|||[Sonic Robo Blast 2](https://en.wikipedia.org/wiki/Sonic_Robo_Blast_2 "Sonic Robo Blast 2") and Sonic Robo Blast 2 Kart servers|
|5031|Unofficial|   |||AVM CAPI-over-TCP ([ISDN](https://en.wikipedia.org/wiki/ISDN "ISDN") over [Ethernet](https://en.wikipedia.org/wiki/Ethernet "Ethernet") tunneling)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|5037|Unofficial||||Android ADB server|
|5044|Yes||||Standard port in Filebeats/Logstash implementation of Lumberjack protocol.|
|5048|Yes||||Texai Message Service|
|5050|Unofficial||||[Yahoo! Messenger](https://en.wikipedia.org/wiki/Yahoo!_Messenger "Yahoo! Messenger")|
|5051|Yes||||ita-agent [Symantec](https://en.wikipedia.org/wiki/NortonLifeLock "NortonLifeLock") Intruder Alert[[231]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-233)|
|5060|Yes|   |||[Session Initiation Protocol](https://en.wikipedia.org/wiki/Session_Initiation_Protocol "Session Initiation Protocol") (SIP)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|5061|Yes[[232]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-234)||||[Session Initiation Protocol](https://en.wikipedia.org/wiki/Session_Initiation_Protocol "Session Initiation Protocol") (SIP) over [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security")|
|5062|Yes|   |||Localisation access|
|5064|Yes|   |||[EPICS](https://en.wikipedia.org/wiki/EPICS "EPICS") Channel Access server[[233]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-epics-r3.14-reference-manual-235)|
|5065|Assigned|Yes|||EPICS Channel Access repeater beacon[[233]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-epics-r3.14-reference-manual-235)|
|5070|Unofficial|No|||[Binary Floor Control Protocol](https://en.wikipedia.org/w/index.php?title=Binary_Floor_Control_Protocol&action=edit&redlink=1 "Binary Floor Control Protocol (page does not exist)") (BFCP)[[234]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc4582-236)|
|5080|Unofficial|   |||[List of telephone switches#NEC](https://en.wikipedia.org/wiki/List_of_telephone_switches#NEC "List of telephone switches")[NEC Phone System] NEC SV8100 and SV9100 MLC Phones Default iSIP Port|
|5084|Yes|   |||[EPCglobal](https://en.wikipedia.org/wiki/EPCglobal "EPCglobal") Low Level Reader Protocol ([LLRP](https://en.wikipedia.org/wiki/LLRP "LLRP"))|
|5085|Yes|   |||EPCglobal Low Level Reader Protocol ([LLRP](https://en.wikipedia.org/wiki/LLRP "LLRP")) over [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security")|
|5090|Unofficial|   |||[3CX Phone System](https://en.wikipedia.org/wiki/3CX_Phone_System "3CX Phone System") 3CX Tunnel Protocol, 3CX App API, 3CX Session Border Controller|
|5093||Yes|||[SafeNet, Inc](https://en.wikipedia.org/wiki/SafeNet "SafeNet") Sentinel LM, Sentinel RMS, License Manager, client-to-server|
|5099|Yes|   |||SafeNet, Inc Sentinel LM, Sentinel RMS, License Manager, server-to-server|
|5104|Unofficial||||[IBM](https://en.wikipedia.org/wiki/IBM "IBM") [Tivoli Framework](https://en.wikipedia.org/w/index.php?title=IBM_Tivoli_Framework&action=edit&redlink=1 "IBM Tivoli Framework (page does not exist)") NetCOOL/Impact[[235]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-237) [HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP") Service|
|5121|Unofficial||||[Neverwinter Nights](https://en.wikipedia.org/wiki/Neverwinter_Nights_(2002_video_game) "Neverwinter Nights (2002 video game)")|
|5124|Unofficial|   |||TorgaNET ([Micronational](https://en.wikipedia.org/wiki/Micronation "Micronation") [Darknet](https://en.wikipedia.org/wiki/Darknet "Darknet"))|
|5125|Unofficial|   |||TorgaNET ([Micronational](https://en.wikipedia.org/wiki/Micronation "Micronation") Intelligence [Darknet](https://en.wikipedia.org/wiki/Darknet "Darknet"))|
|5150|Yes|   |||ATMP Ascend Tunnel Management Protocol[[236]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-238)|
|5151|Yes||||[ESRI](https://en.wikipedia.org/wiki/Environmental_Systems_Research_Institute "Environmental Systems Research Institute") SDE Instance|
||Yes|||ESRI SDE Remote Start|
|5154|Yes|   |||[BZFlag](https://en.wikipedia.org/wiki/BZFlag "BZFlag")|
|5172|Yes||||PC over IP Endpoint Management[[237]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-239)|
|5173|Unofficial||||[Vite](https://vitejs.dev/)|
|5190|Yes|   |||[AOL Instant Messenger](https://en.wikipedia.org/wiki/AOL_Instant_Messenger "AOL Instant Messenger") protocol.[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) The chat app is defunct as of 15 December 2017.[[238]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-vice-rip-aim-240)|
|5198||Unofficial|||[EchoLink](https://en.wikipedia.org/wiki/Echolink "Echolink") VoIP Amateur Radio Software (Voice)|
|5199||Unofficial|||EchoLink VoIP Amateur Radio Software (Voice)|
|5200|Unofficial||||EchoLink VoIP Amateur Radio Software (Information)|
|5201|Unofficial|   |||[Iperf3](https://en.wikipedia.org/wiki/Iperf3 "Iperf3") (Tool for measuring TCP and UDP bandwidth performance)|
|5222|Yes|Reserved|||[Extensible Messaging and Presence Protocol](https://en.wikipedia.org/wiki/Extensible_Messaging_and_Presence_Protocol "Extensible Messaging and Presence Protocol") (XMPP) client connection[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[239]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc3920-241)[[240]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6120-242)|
|5223|Unofficial||||[Apple Push Notification Service](https://en.wikipedia.org/wiki/Apple_Push_Notification_Service "Apple Push Notification Service")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[161]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT203609-163)|
|Unofficial||||Extensible Messaging and Presence Protocol (XMPP) client connection over [SSL](https://en.wikipedia.org/wiki/Secure_Sockets_Layer "Secure Sockets Layer")|
|5228|Yes||||HP Virtual Room Service|
|Unofficial||||[Google Play](https://en.wikipedia.org/wiki/Google_Play "Google Play"), [Android Cloud to Device Messaging Service](https://en.wikipedia.org/wiki/Android_Cloud_to_Device_Messaging_Service "Android Cloud to Device Messaging Service"), [Google Cloud Messaging](https://en.wikipedia.org/wiki/Google_Cloud_Messaging "Google Cloud Messaging")|
|5235-5236|Unofficial||||[Firebase Cloud Messaging](https://en.wikipedia.org/wiki/Firebase_Cloud_Messaging "Firebase Cloud Messaging")[[241]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-243)|
|5242|Unofficial|   |||[Viber](https://en.wikipedia.org/wiki/Viber "Viber")[[214]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-viber-216)|
|5243|Unofficial|   |||Viber[[214]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-viber-216)|
|5246||Yes|||Control And Provisioning of Wireless Access Points ([CAPWAP](https://en.wikipedia.org/wiki/CAPWAP "CAPWAP")) CAPWAP control[[242]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc5415-244)|
|5247||Yes|||Control And Provisioning of Wireless Access Points (CAPWAP) CAPWAP data[[242]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc5415-244)|
|5269|Yes||||Extensible Messaging and Presence Protocol (XMPP) server-to-server connection[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[239]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc3920-241)[[240]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6120-242)|
|5280|Yes||||Extensible Messaging and Presence Protocol (XMPP)[[243]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-245)|
|5281|Unofficial||||Extensible Messaging and Presence Protocol (XMPP)[[244]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-246)|
|5298|Yes|   |||Extensible Messaging and Presence Protocol (XMPP)[[245]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-247)|
|5310|Assigned|Yes|||_[Outlaws](https://en.wikipedia.org/wiki/Outlaws_(1997_video_game) "Outlaws (1997 video game)")_, a 1997 first-person shooter video game[[246]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-248)|
|5318|Yes|Reserved|||[Certificate Management over CMS](https://en.wikipedia.org/wiki/Certificate_Management_over_CMS "Certificate Management over CMS")[[247]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc6402-249)|
|5349|Yes|   |||[STUN](https://en.wikipedia.org/wiki/STUN "STUN") over [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security")/[DTLS](https://en.wikipedia.org/wiki/Datagram_Transport_Layer_Security "Datagram Transport Layer Security"), a protocol for [NAT traversal](https://en.wikipedia.org/wiki/NAT_traversal "NAT traversal")[[194]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-STUN-196)|
|Yes|   |||[TURN](https://en.wikipedia.org/wiki/Traversal_Using_Relay_NAT "Traversal Using Relay NAT") over TLS/DTLS, a protocol for NAT traversal[[195]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-TURN-197)|
|Yes|Reserved|||STUN Behavior Discovery over TLS.[[196]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc5780-198) See also port 3478.|
|5351|Reserved|Yes|||[NAT Port Mapping Protocol](https://en.wikipedia.org/wiki/NAT_Port_Mapping_Protocol "NAT Port Mapping Protocol") and [Port Control Protocol](https://en.wikipedia.org/wiki/Port_Control_Protocol "Port Control Protocol")—client-requested configuration for connections through [network address translators](https://en.wikipedia.org/wiki/Network_Address_Translation "Network Address Translation") and [firewalls](https://en.wikipedia.org/wiki/Firewall_(computing) "Firewall (computing)")|
|5353|Assigned|Yes|||[Multicast DNS](https://en.wikipedia.org/wiki/Multicast_DNS "Multicast DNS") (mDNS)[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|5355|Yes|   |||[Link-Local Multicast Name Resolution](https://en.wikipedia.org/wiki/LLMNR "LLMNR") (LLMNR), allows [hosts](https://en.wikipedia.org/wiki/Host_(network) "Host (network)") to perform [name resolution](https://en.wikipedia.org/wiki/Hostname_resolution "Hostname resolution") for hosts on the same [local link](https://en.wikipedia.org/wiki/Local_area_network "Local area network") (only provided by [Windows Vista](https://en.wikipedia.org/wiki/Windows_Vista "Windows Vista") and [Server 2008](https://en.wikipedia.org/wiki/Server_2008 "Server 2008"))|
|5357|Unofficial|   |||[Web Services for Devices](https://en.wikipedia.org/wiki/Web_Services_for_Devices "Web Services for Devices") (WSDAPI) (only provided by Windows Vista, Windows 7 and Server 2008)|
|5358|Unofficial|   |||[WSDAPI](https://en.wikipedia.org/wiki/Web_Services_for_Devices "Web Services for Devices") Applications to Use a Secure Channel (only provided by Windows Vista, Windows 7 and Server 2008)|
|5394||Unofficial|||Kega Fusion, a Sega multi-console emulator[[248]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Niobium-250)[[249]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-251)|
|5402|Yes|   |||[Multicast File Transfer Protocol](https://en.wikipedia.org/w/index.php?title=Multicast_File_Transfer_Protocol&action=edit&redlink=1 "Multicast File Transfer Protocol (page does not exist)") (MFTP)[[250]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-draft-miller-mftp-spec-03-252)[_[importance?](https://en.wikipedia.org/wiki/Wikipedia:What_Wikipedia_is_not#Encyclopedic_content "Wikipedia:What Wikipedia is not")_]|
|5405|Yes|   |||[NetSupport Manager](https://en.wikipedia.org/wiki/NetSupport_Manager "NetSupport Manager")|
|5412|Yes|   |||[IBM](https://en.wikipedia.org/wiki/IBM "IBM") Rational Synergy ([Telelogic Synergy](https://en.wikipedia.org/wiki/Telelogic_Synergy "Telelogic Synergy")) (Continuus CM) Message Router|
|5413|Yes|   |||[Wonderware](https://en.wikipedia.org/wiki/Wonderware "Wonderware") SuiteLink service|
|5417|Yes|   |||SNS Agent|
|5421|Yes|   |||[NetSupport Manager](https://en.wikipedia.org/wiki/NetSupport_Manager "NetSupport Manager")|
|5432|Yes|Assigned|||[PostgreSQL](https://en.wikipedia.org/wiki/PostgreSQL "PostgreSQL")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11) database system|
|5433|Unofficial||||Bouwsoft file/webserver[[251]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-253)|
|5445||Unofficial|||Cisco Unified Video Advantage[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|5450|Unofficial|   |||[OSIsoft](https://en.wikipedia.org/wiki/OSIsoft "OSIsoft") PI Server Client Access [[252]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-254)|
|5457|Unofficial||||[OSIsoft](https://en.wikipedia.org/wiki/OSIsoft "OSIsoft") PI Asset Framework Client Access [[253]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-255)|
|5458|Unofficial||||[OSIsoft](https://en.wikipedia.org/wiki/OSIsoft "OSIsoft") PI Notifications Client Access [[254]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-256)|
|5480|Unofficial||||[VMware](https://en.wikipedia.org/wiki/VMware "VMware") VAMI (Virtual Appliance Management Infrastructure)—used for initial setup of various administration settings on Virtual Appliances designed using the VAMI architecture.|
|5481|Unofficial||||[Schneider Electric](https://en.wikipedia.org/wiki/Schneider_Electric "Schneider Electric")'s ClearSCADA ([SCADA](https://en.wikipedia.org/wiki/SCADA "SCADA") implementation for Windows) — used for client-to-server communication.[[255]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-257)|
|5495|Unofficial||||[IBM Cognos TM1](https://en.wikipedia.org/wiki/TM1 "TM1") Admin server|
|5498|Unofficial||||[Hotline](https://en.wikipedia.org/wiki/Hotline_Communications "Hotline Communications") tracker server connection|
|5499||Unofficial|||Hotline tracker server discovery|
|5500|Unofficial||||Hotline control connection|
|Unofficial||||[VNC](https://en.wikipedia.org/wiki/Virtual_Network_Computing "Virtual Network Computing") Remote Frame Buffer [RFB protocol](https://en.wikipedia.org/wiki/RFB_protocol "RFB protocol")—for incoming listening viewer|
|5501|Unofficial||||Hotline file transfer connection|
|5517|Unofficial||||[Setiqueue](https://en.wikipedia.org/wiki/SETI@home#Software "SETI@home") Proxy server client for [SETI@Home](https://en.wikipedia.org/wiki/SETI@Home "SETI@Home") project|
|5550|Unofficial||||[Hewlett-Packard](https://en.wikipedia.org/wiki/Hewlett-Packard "Hewlett-Packard") Data Protector[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|5554|Unofficial|   |||[Fastboot](https://en.wikipedia.org/wiki/Fastboot "Fastboot") default wireless port|
|5555|Unofficial|   |||[Oracle](https://en.wikipedia.org/wiki/Oracle_Corporation "Oracle Corporation") WebCenter Content: Inbound Refinery—Intradoc Socket port. (formerly known as Oracle [Universal Content Management](https://en.wikipedia.org/wiki/Universal_Content_Management "Universal Content Management")). Port though often changed during installation|
|Unofficial||||[Freeciv](https://en.wikipedia.org/wiki/Freeciv "Freeciv") versions up to 2.0, [Hewlett-Packard](https://en.wikipedia.org/wiki/Hewlett-Packard "Hewlett-Packard") Data Protector, [McAfee EndPoint Encryption](https://en.wikipedia.org/wiki/Comparison_of_disk_encryption_software "Comparison of disk encryption software") Database Server, [SAP](https://en.wikipedia.org/wiki/Session_Announcement_Protocol "Session Announcement Protocol"), Default for Microsoft Dynamics CRM 4.0, Softether VPN default port|
|Unofficial||||Wireless [adb](https://en.wikipedia.org/wiki/Android_Debug_Bridge "Android Debug Bridge") (Android Debug Bridge) control of an [Android](https://en.wikipedia.org/wiki/Android_(operating_system) "Android (operating system)") device over the network.|
|5556|Yes|   |||[Freeciv](https://en.wikipedia.org/wiki/Freeciv "Freeciv"), Oracle WebLogic Server Node Manager[[256]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-258)|
|5568|Yes|   |||Session Data Transport (SDT), a part of [Architecture for Control Networks](https://en.wikipedia.org/wiki/Architecture_for_Control_Networks "Architecture for Control Networks") (ACN)[[257]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ANSI_E1.17-2010-259)[_[full citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citing_sources#What_information_to_include "Wikipedia:Citing sources")_]|
|5601|Unofficial||||[Kibana](https://en.wikipedia.org/wiki/Kibana "Kibana")[[258]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-260)|
|5631|Yes||||pcANYWHEREdata, [Symantec](https://en.wikipedia.org/wiki/NortonLifeLock "NortonLifeLock") [pcAnywhere](https://en.wikipedia.org/wiki/Pcanywhere "Pcanywhere") (version 7.52 and later[[259]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-261))[[260]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-262) data|
|5632||Yes|||pcANYWHEREstat, Symantec pcAnywhere (version 7.52 and later) status|
|5656|Unofficial||||[IBM Lotus Sametime](https://en.wikipedia.org/wiki/IBM_Lotus_Sametime "IBM Lotus Sametime") p2p file transfer|
|5666|Unofficial||||[NRPE](https://en.wikipedia.org/wiki/NRPE "NRPE") ([Nagios](https://en.wikipedia.org/wiki/Nagios "Nagios"))|
|5667|Unofficial||||NSCA (Nagios)|
|5670|Yes||||[FILEMQ](https://en.wikipedia.org/w/index.php?title=FILEMQ&action=edit&redlink=1 "FILEMQ (page does not exist)") ZeroMQ File Message Queuing Protocol|
||Yes|||[ZRE-DISC](https://en.wikipedia.org/w/index.php?title=ZRE-DISC&action=edit&redlink=1 "ZRE-DISC (page does not exist)") ZeroMQ Realtime Exchange Protocol (Discovery)|
|5671|Yes|Assigned|||[Advanced Message Queuing Protocol](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol "Advanced Message Queuing Protocol") (AMQP)[[261]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ampq-263) over [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security")|
|5672|Yes|Assigned|Yes||Advanced Message Queuing Protocol (AMQP)[[261]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ampq-263)|
|5678|Unofficial|No|||[n8n](https://en.wikipedia.org/w/index.php?title=N8n&action=edit&redlink=1 "N8n (page does not exist)")[[262]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-264)|
|5683|Yes|   |||[Constrained Application Protocol](https://en.wikipedia.org/wiki/Constrained_Application_Protocol "Constrained Application Protocol") (CoAP)|
|5684|Yes|   |||Constrained Application Protocol Secure (CoAPs)|
|5693|Unofficial||||[Nagios](https://en.wikipedia.org/wiki/Nagios "Nagios") Cross Platform Agent (NCPA)[[263]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-265)|
|5701|Unofficial||||[Hazelcast](https://en.wikipedia.org/wiki/Hazelcast "Hazelcast") default communication port[[264]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-266)|
|5718|Unofficial||||Microsoft DPM Data Channel (with the agent coordinator)|
|5719|Unofficial||||Microsoft DPM Data Channel (with the protection agent)|
|5722|Yes|   |||Microsoft RPC, DFSR (SYSVOL) Replication Service[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|5723|Unofficial||||[System Center Operations Manager](https://en.wikipedia.org/wiki/System_Center_Operations_Manager "System Center Operations Manager")[[265]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-267)|
|5724|Unofficial||||Operations Manager Console|
|5741|Yes|   |||IDA Discover Port 1|
|5742|Yes|   |||IDA Discover Port 2|
|5800|Unofficial||||[VNC](https://en.wikipedia.org/wiki/Virtual_Network_Computing "Virtual Network Computing") Remote Frame Buffer [RFB protocol](https://en.wikipedia.org/wiki/RFB_protocol "RFB protocol") over [HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP")|
|Unofficial||||[ProjectWise Server](https://en.wikipedia.org/wiki/ProjectWise "ProjectWise")[[266]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-268)|
|5900|Yes|   |||[Remote Frame Buffer protocol](https://en.wikipedia.org/wiki/RFB_protocol "RFB protocol") (RFB)|
|Unofficial||||[Virtual Network Computing](https://en.wikipedia.org/wiki/Virtual_Network_Computing "Virtual Network Computing") (VNC) Remote Frame Buffer [RFB protocol](https://en.wikipedia.org/wiki/RFB_protocol "RFB protocol")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)[[267]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-269)|
|5905|Unofficial||||Windows service "C:\Program Files\Intel\Intel(R) Online Connect Access\IntelTechnologyAccessService.exe" that listens on 127.0.0.1|
|5931|Yes|   |||[AMMYY](https://en.wikipedia.org/wiki/AMMYY "AMMYY") admin Remote Control|
|5938|Unofficial|   |||[TeamViewer](https://en.wikipedia.org/wiki/TeamViewer "TeamViewer") remote desktop protocol[[268]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-270)|
|5984|Yes|   |||[CouchDB](https://en.wikipedia.org/wiki/CouchDB "CouchDB") database server|
|5985|Yes||||[Windows PowerShell](https://en.wikipedia.org/wiki/Windows_PowerShell "Windows PowerShell") Default psSession Port[[269]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Enter-PSSession-271) [Windows Remote Management Service](https://en.wikipedia.org/wiki/WS-Management "WS-Management") (WinRM-HTTP)[[270]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-microsoft1-272)|
|5986|Yes||||Windows PowerShell Default psSession Port[[269]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Enter-PSSession-271) [Windows Remote Management Service](https://en.wikipedia.org/wiki/WS-Management "WS-Management") (WinRM-HTTPS)[[270]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-microsoft1-272)|
|5988–5989|Yes||||[CIM](https://en.wikipedia.org/wiki/Common_Information_Model_(computing) "Common Information Model (computing)")-XML (DMTF Protocol)[[271]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-273)|
|6000–6063|Yes|   |||[X11](https://en.wikipedia.org/wiki/X_Window_System "X Window System")—used between an X client and server over the network|
|6005|Unofficial||||Default for [BMC Software](https://en.wikipedia.org/wiki/BMC_Software "BMC Software") [Control-M/Server](https://en.wikipedia.org/wiki/BMC_Control-M "BMC Control-M")—Socket used for communication between Control-M processes—though often changed during installation|
|Unofficial||||Default for [Camfrog](https://en.wikipedia.org/wiki/Camfrog "Camfrog") chat & cam client|
|6009|Unofficial||||[JD Edwards EnterpriseOne](https://en.wikipedia.org/wiki/JD_Edwards_EnterpriseOne "JD Edwards EnterpriseOne") ERP system JDENet messaging client listener|
|6050|Unofficial||||[Arcserve](https://en.wikipedia.org/wiki/Arcserve "Arcserve") backup|
|6051|Unofficial||||Arcserve backup|
|6086|Yes||||[Peer Distributed Transfer Protocol](https://en.wikipedia.org/wiki/Peer_Distributed_Transfer_Protocol "Peer Distributed Transfer Protocol") (PDTP), FTP like file server in a P2P network|
|6100|Unofficial||||[Vizrt](https://en.wikipedia.org/wiki/Vizrt "Vizrt") System|
|Unofficial||||[Ventrilo](https://en.wikipedia.org/wiki/Ventrilo "Ventrilo") authentication for version 3|
|6101|Unofficial||||Backup Exec Agent Browser[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|6110|Yes|   |||softcm, [HP](https://en.wikipedia.org/wiki/Hewlett-Packard "Hewlett-Packard") [Softbench](https://en.wikipedia.org/wiki/Softbench "Softbench") CM|
|6111|Yes|   |||spc, [HP](https://en.wikipedia.org/wiki/Hewlett-Packard "Hewlett-Packard") [Softbench](https://en.wikipedia.org/wiki/Softbench "Softbench") Sub-Process Control|
|6112|Yes|   |||dtspcd, execute commands and launch applications remotely|
|Unofficial|   |||[Blizzard](https://en.wikipedia.org/wiki/Blizzard_Entertainment "Blizzard Entertainment")'s [Battle.net](https://en.wikipedia.org/wiki/Battle.net "Battle.net") gaming service and some games,[[127]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-blizzard-129) [ArenaNet](https://en.wikipedia.org/wiki/ArenaNet "ArenaNet") gaming service, [Relic](https://en.wikipedia.org/wiki/Relic_Entertainment "Relic Entertainment") gaming service|
|Unofficial||||[Club Penguin](https://en.wikipedia.org/wiki/Club_Penguin "Club Penguin") Disney online game for kids|
|6113|Unofficial||||[Club Penguin](https://en.wikipedia.org/wiki/Club_Penguin "Club Penguin") Disney online game for kids, Used by some [Blizzard](https://en.wikipedia.org/wiki/Blizzard_Entertainment "Blizzard Entertainment") games[[127]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-blizzard-129)|
|6136|Unofficial||||[ObjectDB](https://en.wikipedia.org/wiki/ObjectDB "ObjectDB") database server[[272]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-objectdb-jpa-setting-server-274)|
|6159|Yes||||[ARINC](https://en.wikipedia.org/wiki/ARINC "ARINC") 840 [EFB](https://en.wikipedia.org/wiki/Electronic_flight_bag "Electronic flight bag") Application Control Interface|
|6160|Unofficial||||[Veeam](https://en.wikipedia.org/wiki/Veeam "Veeam") Installer Service|
|6161|Unofficial||||[Veeam](https://en.wikipedia.org/wiki/Veeam "Veeam") vPower NFS Service|
|6162|Unofficial||||[Veeam](https://en.wikipedia.org/wiki/Veeam "Veeam") Data Mover|
|6163|Unofficial||||[Veeam](https://en.wikipedia.org/wiki/Veeam "Veeam") Hyper-V Integration Service|
|6164|Unofficial||||[Veeam](https://en.wikipedia.org/wiki/Veeam "Veeam") WAN Accelerator|
|6165|Unofficial||||[Veeam](https://en.wikipedia.org/wiki/Veeam "Veeam") WAN Accelerator Data Transfer|
|6167|Unofficial||||[Veeam](https://en.wikipedia.org/wiki/Veeam "Veeam") Log Shipping Service|
|6170|Unofficial||||[Veeam](https://en.wikipedia.org/wiki/Veeam "Veeam") Mount Server|
|6200|Unofficial||||[Oracle WebCenter](https://en.wikipedia.org/wiki/Oracle_WebCenter "Oracle WebCenter") Content Portable: Content Server (With Native UI) and Inbound Refinery|
|6201|Assigned|   |||Thermo-Calc Software AB: Management of service nodes in a processing grid for thermodynamic calculations|
|Unofficial||||Oracle WebCenter Content Portable: Admin|
|6225|Unofficial||||Oracle WebCenter Content Portable: Content Server Web UI|
|6227|Unofficial||||Oracle WebCenter Content Portable: JavaDB|
|6240|Unofficial||||Oracle WebCenter Content Portable: Capture|
|6244|Unofficial|   |||Oracle WebCenter Content Portable: Content Server—Intradoc Socket port|
|6255|Unofficial|   |||Oracle WebCenter Content Portable: Inbound Refinery—Intradoc Socket port|
|6257||Unofficial|||[WinMX](https://en.wikipedia.org/wiki/WinMX "WinMX") (see also 6699)|
|6260|Unofficial|   |||planet M.U.L.E.|
|6262|Unofficial||||Sybase [Advantage Database Server](https://en.wikipedia.org/wiki/Advantage_Database_Server "Advantage Database Server")|
|6343||Yes|||[SFlow](https://en.wikipedia.org/wiki/SFlow "SFlow"), sFlow traffic monitoring|
|6346|Yes|   |||[gnutella-svc](https://en.wikipedia.org/wiki/Gnutella "Gnutella"), gnutella ([FrostWire](https://en.wikipedia.org/wiki/FrostWire "FrostWire"), [Limewire](https://en.wikipedia.org/wiki/Limewire "Limewire"), [Shareaza](https://en.wikipedia.org/wiki/Shareaza "Shareaza"), etc.)|
|6347|Yes|   |||gnutella-rtr, Gnutella alternate|
|6350|Yes|   |||App Discovery and Access Protocol|
|6379|Yes||||[Redis](https://en.wikipedia.org/wiki/Redis "Redis") key-value data store|
|6389|Unofficial||||[EMC](https://en.wikipedia.org/wiki/EMC_Corporation "EMC Corporation") [CLARiiON](https://en.wikipedia.org/wiki/CLARiiON "CLARiiON")|
|6432|Yes||||PgBouncer—A connection pooler for PostgreSQL|
|6436|Unofficial||||[Leap Motion](https://en.wikipedia.org/wiki/Leap_Motion "Leap Motion") Websocket Server TLS|
|6437|Unofficial||||Leap Motion Websocket Server|
|6443|Yes||||[Kubernetes](https://en.wikipedia.org/wiki/Kubernetes "Kubernetes") API server [[273]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-275)|
|6444|Yes|   |||[Sun Grid Engine](https://en.wikipedia.org/wiki/Sun_Grid_Engine "Sun Grid Engine") Qmaster Service|
|6445|Yes|   |||Sun Grid Engine Execution Service|
|6454||Unofficial|||[Art-Net](https://en.wikipedia.org/wiki/Art-Net "Art-Net") protocol|
|6463–6472|Unofficial||||[Discord](https://en.wikipedia.org/wiki/Discord_(software) "Discord (software)") RPC[[274]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-276)|
|6464|Yes|   |||Port assignment for medical device communication in accordance to [IEEE 11073-20701](https://en.wikipedia.org/wiki/ISO/IEEE_11073 "ISO/IEEE 11073")|
|6513|Yes||||[NETCONF](https://en.wikipedia.org/wiki/NETCONF "NETCONF") over [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security")|
|6514|Yes||||Syslog over TLS[[275]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-277)|
|6515|Yes|   |||[Elipse](https://en.wikipedia.org/wiki/Elipse_Software "Elipse Software") RPC Protocol (REC)|
|6516|Unofficial|   |||[Windows Admin Center](https://en.wikipedia.org/wiki/Windows_Admin_Center "Windows Admin Center")|
|6543|Unofficial||||[Pylons project#Pyramid](https://en.wikipedia.org/wiki/Pylons_project#Pyramid "Pylons project") Default Pylons Pyramid web service port|
|6556|Unofficial||||[Check MK](https://en.wikipedia.org/wiki/Check_MK "Check MK") Agent|
|6566|Yes||||[SANE](https://en.wikipedia.org/wiki/Scanner_Access_Now_Easy "Scanner Access Now Easy") (Scanner Access Now Easy)—SANE network scanner daemon[[276]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-278)|
|6560–6561|Unofficial||||[Speech-Dispatcher](https://en.wikipedia.org/w/index.php?title=Speech-Dispatcher&action=edit&redlink=1 "Speech-Dispatcher (page does not exist)") daemon[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|6571|Unofficial|   |||[Windows Live FolderShare](https://en.wikipedia.org/wiki/Windows_Live_FolderShare "Windows Live FolderShare") client|
|6600|Yes||||Microsoft [Hyper-V](https://en.wikipedia.org/wiki/Hyper-V "Hyper-V") Live|
|Unofficial||||[Music Player Daemon](https://en.wikipedia.org/wiki/Music_Player_Daemon "Music Player Daemon") (MPD)|
|6601|Yes||||[Microsoft Forefront Threat Management Gateway](https://en.wikipedia.org/wiki/Microsoft_Forefront_Threat_Management_Gateway "Microsoft Forefront Threat Management Gateway")|
|6602|Yes||||Microsoft Windows WSS Communication|
|6619|Yes|   |||odette-ftps, [Odette File Transfer Protocol](https://en.wikipedia.org/wiki/OFTP "OFTP") ([OFTP](https://en.wikipedia.org/wiki/OFTP "OFTP")) over [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security")/[SSL](https://en.wikipedia.org/wiki/Secure_Sockets_Layer "Secure Sockets Layer")|
|6622|Yes|   |||Multicast FTP|
|6626|Yes|   |||Semaphore Messenger|
|6653|Yes|Assigned|||[OpenFlow](https://en.wikipedia.org/wiki/OpenFlow "OpenFlow")[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|6660–6664|Unofficial||||[Internet Relay Chat](https://en.wikipedia.org/wiki/Internet_Relay_Chat "Internet Relay Chat") (IRC)|
|6665–6669|Yes||||Internet Relay Chat (IRC)|
|6679|Yes|   |||Osorno Automation Protocol (OSAUT)|
|Unofficial||||Internet Relay Chat (IRC) [SSL](https://en.wikipedia.org/wiki/Secure_Sockets_Layer "Secure Sockets Layer") (Secure Internet Relay Chat)—often used|
|6690|Unofficial||||Synology Cloud station|
|6697|Yes||||IRC SSL (Secure Internet Relay Chat)—often used|
|6699|Unofficial||||[WinMX](https://en.wikipedia.org/wiki/WinMX "WinMX") (see also 6257)|
|6715|Unofficial||||AberMUD and derivatives default port|
|6771||Unofficial|||BitTorrent [Local Peer Discovery](https://en.wikipedia.org/wiki/Local_Peer_Discovery "Local Peer Discovery")|
|6783–6785|Unofficial||||[Splashtop Remote](https://en.wikipedia.org/wiki/Splashtop_Remote "Splashtop Remote") server broadcast|
|6801|Yes|   |||ACNET Control System Protocol|
|6881–6887|Unofficial|   |||[BitTorrent](https://en.wikipedia.org/wiki/BitTorrent "BitTorrent") beginning of range of ports used most often|
|6888|Yes|   |||MUSE|
|Unofficial|   |||BitTorrent continuation of range of ports used most often|
|6889–6890|Unofficial|   |||BitTorrent continuation of range of ports used most often|
|6891–6900|Unofficial|   |||BitTorrent continuation of range of ports used most often|
|6891–6900|Unofficial|   |||[Windows Live Messenger](https://en.wikipedia.org/wiki/Windows_Live_Messenger "Windows Live Messenger") (File transfer)|
|6901|Unofficial|   |||Windows Live Messenger (Voice)|
|Unofficial|   |||BitTorrent continuation of range of ports used most often|
|6902–6968|Unofficial|   |||BitTorrent continuation of range of ports used most often|
|6924|Yes|   |||split-ping, ping with RX/TX latency/loss split|
|6935|Yes|   |||EthoScan Service|
|6936|Yes|   |||XenSource Management Service|
|6969|Yes|   |||acmsoda|
|Unofficial||||[BitTorrent tracker](https://en.wikipedia.org/wiki/BitTorrent_tracker "BitTorrent tracker")|
|6970–6999|Unofficial|   |||BitTorrent end of range of ports used most often|
||Unofficial|||[QuickTime Streaming Server](https://en.wikipedia.org/wiki/QuickTime_Streaming_Server "QuickTime Streaming Server")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|6980||Unofficial|||[Voicemeeter](https://en.wikipedia.org/wiki/Voicemeeter "Voicemeeter") VBAN network audio protocol[[277]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-279)|
|7000|Unofficial||||Default for [Vuze](https://en.wikipedia.org/wiki/Vuze "Vuze")'s built-in [HTTPS](https://en.wikipedia.org/wiki/HTTPS "HTTPS") Bittorrent tracker|
|Unofficial||||[Avira](https://en.wikipedia.org/wiki/Avira "Avira") Server Management Console|
|7001|Unofficial||||Avira Server Management Console|
|Unofficial||||Default for [BEA](https://en.wikipedia.org/wiki/BEA_Systems "BEA Systems") [WebLogic Server](https://en.wikipedia.org/wiki/WebLogic "WebLogic")'s [HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP") server, though often changed during installation|
|7002|Unofficial||||Default for BEA WebLogic Server's HTTPS server, though often changed during installation|
|7005|Unofficial||||Default for [BMC Software](https://en.wikipedia.org/wiki/BMC_Software "BMC Software") [Control-M/Server](https://en.wikipedia.org/wiki/BMC_Control-M "BMC Control-M") and Control-M/Agent for Agent-to-Server, though often changed during installation|
|7006|Unofficial||||Default for BMC Software Control-M/Server and Control-M/Agent for Server-to-Agent, though often changed during installation|
|7010|Unofficial||||Default for Cisco AON AMC (AON Management Console)[[278]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-280)|
|7022|Unofficial||||Database mirroring endpoints[[230]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Microsoft-232)|
|7023||Yes|||Bryan Wilcutt T2-NMCS Protocol for SatCom Modems|
|7025|Unofficial||||Zimbra [LMTP](https://en.wikipedia.org/wiki/Local_Mail_Transfer_Protocol "Local Mail Transfer Protocol") [mailbox]—local mail delivery|
|7047|Unofficial||||[Zimbra](https://en.wikipedia.org/wiki/Zimbra "Zimbra") conversion server|
|7070|Unofficial|   |||[Real Time Streaming Protocol](https://en.wikipedia.org/wiki/Real_Time_Streaming_Protocol "Real Time Streaming Protocol") (RTSP), used by [QuickTime Streaming Server](https://en.wikipedia.org/wiki/QuickTime_Streaming_Server "QuickTime Streaming Server"). TCP is used by default, UDP is used as an alternate.[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|7077|Yes|   |||Development-Network Authentification-Protocol|
|7133|Unofficial||||[Enemy Territory: Quake Wars](https://en.wikipedia.org/wiki/Enemy_Territory:_Quake_Wars "Enemy Territory: Quake Wars")|
|7144|Unofficial||||Peercast[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|7145|Unofficial||||Peercast[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|7171|Unofficial||||[Tibia](https://en.wikipedia.org/wiki/Tibia_(computer_game) "Tibia (computer game)")|
|7262|Yes|   |||CNAP (Calypso Network Access Protocol)|
|7272|Yes|   |||WatchMe - WatchMe Monitoring|
|7306|Unofficial||||Zimbra mysql [mailbox][_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|7307|Unofficial||||Zimbra mysql [logger][_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|7312||Unofficial|||[Sibelius](https://en.wikipedia.org/wiki/Sibelius_notation_program "Sibelius notation program") License Server|
|7396|Unofficial||||Web control interface for [Folding@home v7.3.6](https://en.wikipedia.org/wiki/Folding@home#V7 "Folding@home") and later[[279]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-281)|
|7400|Yes|   |||RTPS (Real Time Publish Subscribe) [DDS](https://en.wikipedia.org/wiki/Data_Distribution_Service "Data Distribution Service") Discovery|
|7401|Yes|   |||RTPS (Real Time Publish Subscribe) [DDS](https://en.wikipedia.org/wiki/Data_Distribution_Service "Data Distribution Service") User-Traffic|
|7402|Yes|   |||RTPS (Real Time Publish Subscribe) [DDS](https://en.wikipedia.org/wiki/Data_Distribution_Service "Data Distribution Service") Meta-Traffic|
|7471|Unofficial||||Stateless Transport Tunneling (STT)|
|7473|Yes||||[Rise: The Vieneo Province](https://en.wikipedia.org/wiki/Rise:_The_Vieneo_Province "Rise: The Vieneo Province")|
|7474|Yes||||Neo4J Server webadmin[[280]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-282)|
|7478|Yes||||Default port used by [Open iT](https://en.wikipedia.org/wiki/Open_iT "Open iT") Server.[[281]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-283)|
|7542|Yes|   |||_Saratoga_ file transfer protocol[[282]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-draft-wood-tsvwg-saratoga-284)[[283]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-10.1109/IWSSC.2007.4409410-285)|
|7547|Yes|   |||CPE WAN Management Protocol (CWMP) [Technical Report 069](https://en.wikipedia.org/wiki/TR-069 "TR-069")|
|7575||Unofficial|||[Populous: The Beginning](https://en.wikipedia.org/wiki/Populous:_The_Beginning "Populous: The Beginning") server|
|7624|Yes|   |||[Instrument Neutral Distributed Interface](https://en.wikipedia.org/wiki/Instrument_Neutral_Distributed_Interface "Instrument Neutral Distributed Interface")|
|7631|Yes||||ERLPhase|
|7634|Unofficial||||hddtemp—Utility to monitor hard drive temperature|
|7652–7654|Unofficial||||[I2P](https://en.wikipedia.org/wiki/I2P "I2P") anonymizing overlay network|
|7655||Unofficial|||I2P SAM Bridge Socket API|
|7656–7660|Unofficial||||I2P anonymizing overlay network|
|7659|Unofficial|   |||[Polypheny](https://en.wikipedia.org/w/index.php?title=Polypheny&action=edit&redlink=1 "Polypheny (page does not exist)") User Interface (database system)|
|7670|Unofficial||||[BrettspielWelt](https://en.wikipedia.org/wiki/BrettspielWelt "BrettspielWelt") BSW Boardgame Portal|
|7680|Unofficial||||Delivery Optimization for [Windows 10](https://en.wikipedia.org/wiki/Windows_10 "Windows 10")[[284]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ms-win10-delivery-optimization-286)|
|7687|Yes||||[Bolt](https://en.wikipedia.org/wiki/Bolt_(network_protocol) "Bolt (network protocol)") database connection|
|7707–7708||Unofficial|||_[Killing Floor](https://en.wikipedia.org/wiki/Killing_Floor_(2009_video_game) "Killing Floor (2009 video game)")_|
|7717||Unofficial|||_Killing Floor_|
|7777|Unofficial||||[iChat](https://en.wikipedia.org/wiki/IChat "IChat") server file transfer proxy[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|Unofficial||||Oracle Cluster File System 2[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|Unofficial||||Windows backdoor program tini.exe default[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|Unofficial||||_Just Cause 2: Multiplayer Mod_ Server[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|Unofficial||||_[Terraria](https://en.wikipedia.org/wiki/Terraria "Terraria")_ default server|
||Unofficial|||_San Andreas Multiplayer_ (SA-MP) default port server|
||Unofficial|||_SCP: Secret Laboratory_ Multiplayer Server|
|7777-7788||Yes|||Common default Steam game server ports(Ark, L4D2, ect)|
|7777–7788|Unofficial|   |||_Unreal Tournament_ series default server[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|7831|Unofficial||||Default used by Smartlaunch Internet Cafe Administration[[285]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-287) software|
|7880|Unofficial|   |||PowerSchool Gradebook Server[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|7890|Unofficial||||Default that will be used by the iControl Internet Cafe Suite Administration software|
|7915|Unofficial||||Default for YSFlight server[[286]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Midnight_Rambler-288)|
|7935|Unofficial||||Fixed port used for Adobe Flash Debug Player to communicate with a debugger (Flash IDE, Flex Builder or fdb).[[287]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-289)|
|7946|Unofficial|   |||Docker Swarm communication among nodes[[168]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-docker-swarm-tutorial-170)|
|7979||Unofficial|||Used by SilverBluff Studios for communication between servers and clients.[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|7990|Unofficial||||Atlassian [Bitbucket](https://en.wikipedia.org/wiki/Bitbucket "Bitbucket") (default port)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|8000|Unofficial||||Commonly used for Internet radio streams such as [SHOUTcast](https://en.wikipedia.org/wiki/SHOUTcast "SHOUTcast")[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_], [Icecast](https://en.wikipedia.org/wiki/Icecast "Icecast")[[288]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-290) and [iTunes Radio](https://en.wikipedia.org/wiki/ITunes_Radio "ITunes Radio")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|Unofficial|   |||[DynamoDB](https://en.wikipedia.org/wiki/DynamoDB "DynamoDB") Local[[289]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-aws-docs-dynamodb-developer-local-291)|
|Unofficial|   |||[Django](https://en.wikipedia.org/wiki/Django_(web_framework) "Django (web framework)") Development Webserver[[290]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-django-docs-1.10-tutorial01-292)|
|Unofficial|   |||[Python 3](https://en.wikipedia.org/wiki/Python_3 "Python 3") http.server[[291]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-293)|
|8005|Unofficial||||[Tomcat](https://en.wikipedia.org/wiki/Apache_Tomcat "Apache Tomcat") remote shutdown[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|Unofficial||||[PLATO](https://en.wikipedia.org/wiki/PLATO_(computer_system) "PLATO (computer system)") ASCII protocol (RFC 600)|
|Unofficial||||Windows SCCM HTTP listener service[[292]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-294)|
|8006|Unofficial||||[Quest AppAssure](https://en.wikipedia.org/wiki/Quest_AppAssure "Quest AppAssure") 5 API[[293]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-appassure-kb-firewall-port-295)|
|Unofficial|No|||[Proxmox Virtual Environment](https://en.wikipedia.org/wiki/Proxmox_Virtual_Environment "Proxmox Virtual Environment") admin web interface[[294]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-296)|
|8007|Unofficial||||Quest AppAssure 5 Engine[[293]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-appassure-kb-firewall-port-295)|
|8007|Yes||||[Proxmox Backup Server](https://en.wikipedia.org/wiki/Proxmox_Backup_Server "Proxmox Backup Server") admin web interface|
|8008|Unofficial|   |||Alternative port for [HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP"). See also ports 80 and 8080.|
|Unofficial||||[IBM HTTP Server](https://en.wikipedia.org/wiki/IBM_HTTP_Server "IBM HTTP Server") administration default[_[importance?](https://en.wikipedia.org/wiki/Wikipedia:What_Wikipedia_is_not#Encyclopedic_content "Wikipedia:What Wikipedia is not")_]|
|Unofficial||||[iCal](https://en.wikipedia.org/wiki/ICal "ICal"), a calendar application by [Apple](https://en.wikipedia.org/wiki/Apple,_Inc. "Apple, Inc.")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|Unofficial|No|||[Matrix](https://en.wikipedia.org/wiki/Matrix_(protocol) "Matrix (protocol)") homeserver federation over HTTP[[295]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-matrix-homeserver-297)|
|8009|Unofficial||||[Apache JServ Protocol](https://en.wikipedia.org/wiki/Apache_JServ_Protocol "Apache JServ Protocol") (`ajp13`)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|8010|Unofficial|No|||[Buildbot](https://en.wikipedia.org/wiki/Buildbot "Buildbot") web status page[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|8042|Unofficial|   |||[Orthanc](https://en.wikipedia.org/wiki/Orthanc_(software) "Orthanc (software)") – REST API over HTTP[[212]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-orthanc-book-configuration-214)|
|8061|Yes|Reserved|||Nikatron Device Protocol (nikatron-dev)|
|8069|Unofficial||||[OpenERP](https://en.wikipedia.org/wiki/OpenERP "OpenERP") 5.0 XML-RPC protocol[[296]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-odoo-doc-5.0-install-linux-web-298)|
|8070|Unofficial||||OpenERP 5.0 NET-RPC protocol[[296]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-odoo-doc-5.0-install-linux-web-298)|
|8074|Yes|   |||[Gadu-Gadu](https://en.wikipedia.org/wiki/Gadu-Gadu "Gadu-Gadu")|
|8075|Unofficial||||_Killing Floor_ web administration interface[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|8080|Yes|   |||Alternative port for [HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP"). See also ports 80 and 8008.|
|Unofficial||||[Apache Tomcat](https://en.wikipedia.org/wiki/Apache_Tomcat "Apache Tomcat")[[297]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-299)|
|Unofficial||||[Atlassian JIRA](https://en.wikipedia.org/wiki/Jira_(software) "Jira (software)") applications[[298]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-atlassian-jira-071-tcp-ports-300)|
|8081|Yes|   |||Sun Proxy Admin Service[[299]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-301)|
|8088|Unofficial||||[Asterisk](https://en.wikipedia.org/wiki/Asterisk_(PBX) "Asterisk (PBX)") management access via HTTP[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|Unofficial||||[YARN](https://en.wikipedia.org/wiki/Apache_Hadoop "Apache Hadoop") ResourceManager Web UI[[300]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-302)|
|8089|Unofficial|No|||[Splunk](https://en.wikipedia.org/wiki/Splunk "Splunk") daemon management[[301]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-303)|
|Unofficial||||[Fritz!Box](https://en.wikipedia.org/wiki/Fritz!Box "Fritz!Box") automatic [TR-069](https://en.wikipedia.org/wiki/TR-069 "TR-069") configuration[[302]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-avm-fritzbox-7490-port-8089-304)|
|8090|Unofficial|   |||[Atlassian Confluence](https://en.wikipedia.org/wiki/Atlassian_Confluence "Atlassian Confluence")[[303]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-atlassian-confluence-6.0-doc-listen-port-305)|
|Unofficial||||Coral Content Distribution Network (legacy; 80 and 8080 now supported)[[304]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-coralcdn-wiki-faq-306)|
|Unofficial|   |||Matrix identity server[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|8091|Unofficial|   |||[CouchBase](https://en.wikipedia.org/wiki/CouchBase "CouchBase") web administration[[305]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-couchbase-dev-doc-server-ports-307)|
|8092|Unofficial|   |||CouchBase API[[305]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-couchbase-dev-doc-server-ports-307)|
|8096|Unofficial||||[Emby](https://en.wikipedia.org/wiki/Emby "Emby") and [Jellyfin](https://en.wikipedia.org/wiki/Jellyfin "Jellyfin") HTTP port[[306]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-:1-308)|
|8111|Unofficial||||[JOSM](https://en.wikipedia.org/wiki/JOSM "JOSM") Remote Control|
|8112|Unofficial||||PAC Pacifica Coin|
|8116||Unofficial|||[Check Point](https://en.wikipedia.org/wiki/Check_Point "Check Point") Cluster Control Protocol|
|8118|Yes||||[Privoxy](https://en.wikipedia.org/wiki/Privoxy "Privoxy")—advertisement-filtering Web proxy|
|8123|Unofficial||||[Polipo](https://en.wikipedia.org/wiki/Polipo "Polipo") Web proxy|
|Unofficial||||[Home Assistant](https://en.wikipedia.org/wiki/Home_Assistant "Home Assistant") Home automation|
|Unofficial||||BURST P2P[[307]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-BURST-309)|
|8124|Unofficial||||Standard BURST Mining Pool Software Port|
|8125|Unofficial||||BURST Web Interface|
|8139|Unofficial||||[Puppet (software)](https://en.wikipedia.org/wiki/Puppet_(software) "Puppet (software)") Client agent|
|8140|Yes||||Puppet (software) Master server|
|8172|Unofficial||||[Microsoft](https://en.wikipedia.org/wiki/Microsoft "Microsoft") Remote Administration for IIS Manager[[308]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-310)|
|8184|Unofficial||||[NCSA Brown Dog](https://en.wikipedia.org/wiki/NCSA_Brown_Dog "NCSA Brown Dog") Data Access Proxy|
|8194–8195|Yes|   |||[Bloomberg Terminal](https://en.wikipedia.org/wiki/Bloomberg_Terminal "Bloomberg Terminal")[[309]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Bloomberg_TS-311)|
|8200|Unofficial||||[GoToMyPC](https://en.wikipedia.org/wiki/GoToMyPC "GoToMyPC")|
|Unofficial||||MiniDLNA media server Web Interface|
|8222|Unofficial|   |||[VMware](https://en.wikipedia.org/wiki/VMware "VMware") VI Web Access via HTTP[[310]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-vmware-server-2.0-rc2-releasenotes-312)|
|8236|Unofficial|   |||jRCS listener for [Rocket Software](https://en.wikipedia.org/wiki/Rocket_Software "Rocket Software") jBASE Remote Connectivity Server[[311]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Rocket_Software_jBASE-313)|
|8243|Yes|   |||[HTTPS](https://en.wikipedia.org/wiki/HTTPS "HTTPS") listener for [Apache Synapse](https://en.wikipedia.org/wiki/Apache_Synapse "Apache Synapse")[[312]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Apache_Synapse-314)|
|8245|Unofficial||||[Dynamic DNS](https://en.wikipedia.org/wiki/Dynamic_DNS "Dynamic DNS") for at least [No-IP](https://en.wikipedia.org/wiki/No-IP "No-IP") and DynDNS[[313]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-DynDNS_API-315)|
|8280|Yes|   |||[HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP") listener for [Apache Synapse](https://en.wikipedia.org/wiki/Apache_Synapse "Apache Synapse")[[312]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Apache_Synapse-314)|
|8281|Unofficial||||HTTP Listener for Gatecraft Plugin|
|8291|Unofficial||||Winbox—Default on a MikroTik RouterOS for a Windows application used to administer MikroTik RouterOS[[314]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-316)|
|8303||Unofficial|||[Teeworlds](https://en.wikipedia.org/wiki/Teeworlds "Teeworlds") Server|
|8332|Unofficial||||[Bitcoin](https://en.wikipedia.org/wiki/Bitcoin "Bitcoin") [JSON-RPC](https://en.wikipedia.org/wiki/JSON-RPC "JSON-RPC") server[[315]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-317)|
|8333|Unofficial||||[Bitcoin](https://en.wikipedia.org/wiki/Bitcoin "Bitcoin")[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|Unofficial|   |||[VMware](https://en.wikipedia.org/wiki/VMware "VMware") VI Web Access via HTTPS[[310]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-vmware-server-2.0-rc2-releasenotes-312)|
|8334|Unofficial||||[Filestash](https://en.wikipedia.org/w/index.php?title=Filestash&action=edit&redlink=1 "Filestash (page does not exist)") server (default) [[316]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-318)|
|8337|Unofficial||||VisualSVN Distributed File System Service (VDFS)[[317]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-319)|
|8384|Unofficial||||[Syncthing](https://en.wikipedia.org/wiki/Syncthing "Syncthing") web GUI|
|8388|Unofficial||||[Shadowsocks](https://en.wikipedia.org/wiki/Shadowsocks "Shadowsocks") proxy server[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|8400|Yes||||[Commvault Communications Service](https://documentation.commvault.com/commvault/v11/article?p=8572.htm) (GxCVD, found in all client computers)|
|8401|Yes||||Commvault Server Event Manager (GxEvMgrS, available in CommServe)|
|8403|Yes||||Commvault Firewall (GxFWD, tunnel port for HTTP/HTTPS)|
|8443|Unofficial||||[SW Soft Plesk](https://en.wikipedia.org/wiki/SW_Soft_Plesk "SW Soft Plesk") Control Panel|
|Unofficial||||[Apache Tomcat](https://en.wikipedia.org/wiki/Apache_Tomcat "Apache Tomcat") SSL|
|Unofficial||||Promise WebPAM SSL|
|Unofficial||||[iCal](https://en.wikipedia.org/wiki/ICal "ICal") over [SSL](https://en.wikipedia.org/wiki/Secure_Sockets_Layer "Secure Sockets Layer")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|Unofficial||||[MineOs](https://en.wikipedia.org/w/index.php?title=MineOs&action=edit&redlink=1 "MineOs (page does not exist)") WebUi|
|8444|Unofficial||||[Bitmessage](https://en.wikipedia.org/wiki/Bitmessage "Bitmessage")|
|Unofficial||||[Chia](https://en.wikipedia.org/wiki/Chia_(cryptocurrency) "Chia (cryptocurrency)")[[318]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-320)|
|8448|Yes|   |||Matrix homeserver federation over HTTPS[[295]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-matrix-homeserver-297)|
|8484|Unofficial||||[MapleStory](https://en.wikipedia.org/wiki/MapleStory "MapleStory") Login Server|
|8500|Unofficial||||[Adobe ColdFusion](https://en.wikipedia.org/wiki/Adobe_ColdFusion "Adobe ColdFusion") built-in web server[[319]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-adobe-help-cf10-admin-321)|
|8530|Unofficial|   |||[Windows Server Update Services](https://en.wikipedia.org/wiki/Windows_Server_Update_Services "Windows Server Update Services") over [HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP"), when using the default role installation settings in Windows Server 2012 and later versions.[[320]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-msft-tn-bb693717-322)[[321]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-msft-tn-hh852346-323)|
|8531|Unofficial|   |||[Windows Server Update Services](https://en.wikipedia.org/wiki/Windows_Server_Update_Services "Windows Server Update Services") over [HTTPS](https://en.wikipedia.org/wiki/HTTPS "HTTPS"), when using the default role installation settings in Windows Server 2012 and later versions.[[320]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-msft-tn-bb693717-322)[[321]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-msft-tn-hh852346-323)|
|8555|Unofficial||||Symantec DLP OCR Engine [[322]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-SymantecDLP_OCREngine-324)|
|Unofficial||||[Chia](https://en.wikipedia.org/wiki/Chia_(cryptocurrency) "Chia (cryptocurrency)") [JSON-RPC](https://en.wikipedia.org/wiki/JSON-RPC "JSON-RPC") server[[323]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-325)|
|8580|Unofficial|   |||[Freegate](https://en.wikipedia.org/wiki/Freegate "Freegate"), an Internet [anonymizer](https://en.wikipedia.org/wiki/Anonymizer "Anonymizer") and proxy tool[[324]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-flossmanuals-bypasscensor-freegate-326)|
|8611-8614|Yes|   |||[Canon](https://en.wikipedia.org/wiki/Canon_Inc. "Canon Inc.") BubbleJet Network Protocol [[325]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-327)|
|8629|Unofficial||||Tibero database[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|8642|Unofficial||||[Lotus Notes Traveler](https://en.wikipedia.org/wiki/IBM_Lotus_Notes_Traveler "IBM Lotus Notes Traveler") auto synchronization for Windows Mobile and Nokia devices[[326]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ibm-support-lnt851-planning-net-328)|
|8691|Unofficial||||[Ultra Fractal](https://en.wikipedia.org/wiki/Ultra_Fractal "Ultra Fractal"), a [fractal](https://en.wikipedia.org/wiki/Fractal "Fractal") generation and rendering [software application](https://en.wikipedia.org/wiki/Graphic_art_software "Graphic art software") – distributed calculations over networked computers[[327]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ultrafractal-329)[[328]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ultrafractal-help-network-servers-330)|
|8765|Unofficial|No|||Default port of a local GUN relay peer that the [Internet Archive](https://en.wikipedia.org/wiki/Internet_Archive "Internet Archive")[[329]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-331) and others use as a decentralized mirror for censorship resistance.[[330]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-332)|
|8767||Unofficial|||Voice channel of [TeamSpeak 2](https://en.wikipedia.org/wiki/TeamSpeak_2 "TeamSpeak 2"),[[331]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-tsusa-kb-ts2-ports-333) a proprietary [Voice over IP](https://en.wikipedia.org/wiki/Voice_over_IP "Voice over IP") protocol targeted at [gamers](https://en.wikipedia.org/wiki/Gamer "Gamer")[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|8834|Unofficial|   |||[Nessus](https://en.wikipedia.org/wiki/Nessus_(software) "Nessus (software)"), a [vulnerability scanner](https://en.wikipedia.org/wiki/Vulnerability_scanner "Vulnerability scanner") – remote [XML-RPC](https://en.wikipedia.org/wiki/XML-RPC "XML-RPC") web server[[332]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-tenable-docs-nessus68-usermanual-334)[_[third-party source needed](https://en.wikipedia.org/wiki/Wikipedia:Independent_sources "Wikipedia:Independent sources")_]|
|8840|Unofficial|   |||[Opera Unite](https://en.wikipedia.org/w/index.php?title=Opera_Unite&action=edit&redlink=1 "Opera Unite (page does not exist)"), an extensible [framework](https://en.wikipedia.org/wiki/Software_framework "Software framework") for web applications[[333]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-computerworld-article-2525727-335)[[334]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-lifehacker-5472050-336)|
|8880|Yes||||Alternate port of [CDDB](https://en.wikipedia.org/wiki/CDDB "CDDB") (Compact Disc Database) protocol, used to look up audio CD ([compact disc](https://en.wikipedia.org/wiki/Compact_disc "Compact disc")) information over the [Internet](https://en.wikipedia.org/wiki/Internet "Internet").[[335]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ccdb-howto.txt-337) See also port 888.|
|Unofficial|   |||[IBM WebSphere Application Server](https://en.wikipedia.org/wiki/IBM_WebSphere_Application_Server "IBM WebSphere Application Server") [SOAP](https://en.wikipedia.org/wiki/SOAP "SOAP") connector[[336]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ibm-support-websphere-express8-portnumber-338)[_[jargon](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style#Technical_language "Wikipedia:Manual of Style")_]|
|8883|Yes|   |||Secure [MQTT](https://en.wikipedia.org/wiki/MQTT "MQTT") (MQTT over TLS)[[337]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-mqtt-faq-339)[[338]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-oasisopen-docs-mqtt-v3.1.1-spec-340)|
|8887|Unofficial|   |||HyperVM over HTTP[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|8888|Unofficial|   |||HyperVM over [HTTPS](https://en.wikipedia.org/wiki/HTTPS "HTTPS")[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|Unofficial|No|||[Freenet](https://en.wikipedia.org/wiki/Freenet "Freenet") web UI (localhost only)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|Unofficial|   |||Default for [IPython](https://en.wikipedia.org/wiki/IPython "IPython")[[339]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ipython-doc-3-notebook-server-341) / [Jupyter](https://en.wikipedia.org/wiki/Jupyter "Jupyter")[[340]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-jyputer-docs-running-notebook-342) notebook dashboards|
|Unofficial|   |||[MAMP](https://en.wikipedia.org/wiki/MAMP "MAMP")[[341]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-osxdaily-mamp-343)|
|8889|Unofficial|   |||MAMP[[341]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-osxdaily-mamp-343)|
|8920|Unofficial|   |||[Jellyfin](https://en.wikipedia.org/wiki/Jellyfin "Jellyfin") HTTPS port[[306]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-:1-308)|
|8983|Unofficial|   |||[Apache Solr](https://en.wikipedia.org/wiki/Apache_Solr "Apache Solr")[[342]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apache-solr-6_6-running-solr-344)|
|8997|Unofficial|   |||Alternate port for [I2P](https://en.wikipedia.org/wiki/I2P "I2P") Monotone Proxy[[179]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-geti2p-ports-181)[_[jargon](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style#Technical_language "Wikipedia:Manual of Style")_]|
|8998|Unofficial|   |||I2P Monotone Proxy[[179]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-geti2p-ports-181)[_[jargon](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style#Technical_language "Wikipedia:Manual of Style")_]|
|8999|Unofficial|   |||Alternate port for I2P Monotone Proxy[[179]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-geti2p-ports-181)[_[jargon](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style#Technical_language "Wikipedia:Manual of Style")_]|
|9000|Unofficial||||[SonarQube](https://en.wikipedia.org/wiki/SonarQube "SonarQube") Web Server[[343]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-345)|
|Unofficial||||[ClickHouse](https://en.wikipedia.org/wiki/ClickHouse "ClickHouse") default port|
|Unofficial||||[DBGp](https://en.wikipedia.org/wiki/DBGp "DBGp")|
|Unofficial||||[SqueezeCenter](https://en.wikipedia.org/wiki/SqueezeCenter "SqueezeCenter") web server & streaming|
||Unofficial|||[UDPCast](https://en.wikipedia.org/wiki/UDPCast "UDPCast")|
|Unofficial||||[Play Framework](https://en.wikipedia.org/wiki/Play_Framework "Play Framework") web server[[344]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-playframeworkdocumentation-346)|
|Unofficial||||[Hadoop](https://en.wikipedia.org/wiki/Hadoop_Distributed_File_System "Hadoop Distributed File System") NameNode default port|
|Unofficial||||[PHP-FPM](https://en.wikipedia.org/wiki/PHP-FPM "PHP-FPM") default port|
|Unofficial||||[QBittorrent](https://en.wikipedia.org/wiki/QBittorrent "QBittorrent")'s embedded torrent tracker default port[[345]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-347)|
|9001|Yes|   |||ETL Service Manager[[346]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-348)|
|Unofficial|   |||[Microsoft SharePoint](https://en.wikipedia.org/wiki/Microsoft_SharePoint "Microsoft SharePoint") authoring environment|
|Unofficial|   |||cisco-xremote router configuration[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|Unofficial|   |||[Tor](https://en.wikipedia.org/wiki/Tor_(anonymity_network) "Tor (anonymity network)") network default|
|Unofficial||||[DBGp](https://en.wikipedia.org/wiki/DBGp "DBGp") Proxy|
|Unofficial||||[HSQLDB](https://en.wikipedia.org/wiki/HSQLDB "HSQLDB") default port|
|9002|Unofficial|   |||Newforma Server comms|
|9003|Unofficial|   |||[Xdebug](https://en.wikipedia.org/wiki/Xdebug "Xdebug") default client port[[347]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-xdebugclient-349)|
|9006|Reserved[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2)|   |   |   ||
|Unofficial||||[Tomcat](https://en.wikipedia.org/wiki/Apache_Tomcat "Apache Tomcat") in standalone mode[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|9030|Unofficial||||[Tor](https://en.wikipedia.org/wiki/Tor_(anonymity_network) "Tor (anonymity network)") often used|
|9042|Unofficial||||[Apache Cassandra](https://en.wikipedia.org/wiki/Apache_Cassandra "Apache Cassandra") native protocol clients|
|9043|Unofficial||||[WebSphere Application Server](https://en.wikipedia.org/wiki/WebSphere_Application_Server "WebSphere Application Server") Administration Console secure|
|9050–9051|Unofficial||||[Tor](https://en.wikipedia.org/wiki/Tor_(anonymity_network) "Tor (anonymity network)") (SOCKS-5 proxy client)|
|9060|Unofficial||||[WebSphere Application Server](https://en.wikipedia.org/wiki/WebSphere_Application_Server "WebSphere Application Server") Administration Console|
|9080|Yes|   |||glrpc, [Groove](https://en.wikipedia.org/wiki/Microsoft_Groove "Microsoft Groove") [Collaboration software](https://en.wikipedia.org/wiki/Collaboration_software "Collaboration software") GLRPC|
|Unofficial||||[WebSphere Application Server](https://en.wikipedia.org/wiki/WebSphere_Application_Server "WebSphere Application Server") [HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP") Transport (port 1) [default](https://en.wikipedia.org/wiki/Default_(computer_science) "Default (computer science)")|
|Unofficial||||Remote Potato by FatAttitude, Windows Media Center addon|
|Unofficial||||ServerWMC, Windows Media Center addon|
|9081|Unofficial||||[Zerto](https://en.wikipedia.org/wiki/Zerto "Zerto") ZVM to ZVM communication|
|9090|Unofficial||||[Prometheus](https://en.wikipedia.org/wiki/Prometheus_(software) "Prometheus (software)") metrics server|
|Unofficial||||[Openfire](https://en.wikipedia.org/wiki/Openfire "Openfire") Administration Console|
|Unofficial||||[SqueezeCenter](https://en.wikipedia.org/wiki/SqueezeCenter "SqueezeCenter") control (CLI)|
|Unofficial||||[Cherokee](https://en.wikipedia.org/wiki/Cherokee_(web_server) "Cherokee (web server)") Admin Panel|
|9091|Unofficial||||[Openfire](https://en.wikipedia.org/wiki/Openfire "Openfire") Administration Console (SSL Secured)|
|Unofficial||||[Transmission (BitTorrent client)](https://en.wikipedia.org/wiki/Transmission_(BitTorrent_client) "Transmission (BitTorrent client)") Web Interface|
|9092|Unofficial||||[H2 (DBMS)](https://en.wikipedia.org/wiki/H2_(DBMS) "H2 (DBMS)") Database Server|
|Unofficial||||[Apache Kafka](https://en.wikipedia.org/wiki/Apache_Kafka "Apache Kafka") A Distributed Streaming Platform[[348]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-350)|
|9100|Yes|Assigned|||[PDL](https://en.wikipedia.org/wiki/Page_description_language "Page description language") Data Stream, used for printing to certain network printers[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|9101|Yes|   |||[Bacula](https://en.wikipedia.org/wiki/Bacula "Bacula") Director|
|9102|Yes|   |||[Bacula](https://en.wikipedia.org/wiki/Bacula "Bacula") File Daemon|
|9103|Yes|   |||[Bacula](https://en.wikipedia.org/wiki/Bacula "Bacula") Storage Daemon|
|9119|Yes|   |||[MXit](https://en.wikipedia.org/wiki/MXit "MXit") Instant Messenger|
|9150|Unofficial||||[Tor](https://en.wikipedia.org/wiki/Tor_(anonymity_network) "Tor (anonymity network)") Browser|
|9191|Unofficial||||Sierra Wireless Airlink|
|9199|Unofficial||||Avtex LLC—qStats|
|9200|Unofficial||||Elasticsearch[[349]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-351)—default Elasticsearch port|
|9217|Unofficial||||iPass Platform Service|
|9293|Unofficial||||Sony PlayStation RemotePlay[[350]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-352)|
|9295|Unofficial|   |||Sony PlayStation Remote Play Session creation communication port|
|9296||Unofficial|||Sony PlayStation Remote Play|
|9897||Unofficial|||Sony PlayStation Remote Play Video stream|
|9300|Unofficial||||[IBM Cognos BI](https://en.wikipedia.org/wiki/IBM_Cognos_Business_Intelligence "IBM Cognos Business Intelligence")[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|9303||Unofficial|||[D-Link Shareport](https://en.wikipedia.org/w/index.php?title=D-Link_Shareport&action=edit&redlink=1 "D-Link Shareport (page does not exist)") Share storage and MFP printers[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|9306|Yes||||[Sphinx](https://en.wikipedia.org/wiki/Sphinx_(search_engine) "Sphinx (search engine)") Native API|
|9309|Unofficial|   |||Sony PlayStation Vita Host Collaboration WiFi Data Transfer[[351]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-353)|
|9312|Yes||||[Sphinx](https://en.wikipedia.org/wiki/Sphinx_(search_engine) "Sphinx (search engine)") SphinxQL|
|9332|Unofficial||||[Litecoin](https://en.wikipedia.org/wiki/Litecoin "Litecoin") [JSON-RPC](https://en.wikipedia.org/wiki/JSON-RPC "JSON-RPC") server|
|9333|Unofficial||||[Litecoin](https://en.wikipedia.org/wiki/Litecoin "Litecoin")|
|9339|Unofficial||||Used by all Supercell games such as Brawl Stars and Clash of Clans, mobile freemium strategy video games|
|9389|Yes|   |||adws, [Microsoft](https://en.wikipedia.org/wiki/Microsoft "Microsoft") [AD DS](https://en.wikipedia.org/wiki/AD_DS "AD DS") Web Services, [Powershell](https://en.wikipedia.org/wiki/Powershell "Powershell") uses this port|
|9392|Unofficial|No|||OpenVAS Greenbone Security Assistant web interface|
|9418|Yes|   |||git, [Git](https://en.wikipedia.org/wiki/Git_(software) "Git (software)") pack transfer service|
|9419|Unofficial||||[MooseFS](https://en.wikipedia.org/wiki/Moose_File_System "Moose File System") distributed file system – master control port[[352]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-mfs-manual3.0-ports-354)|
|9420|Unofficial||||MooseFS distributed file system – master command port[[352]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-mfs-manual3.0-ports-354)|
|9421|Unofficial||||MooseFS distributed file system – master client port[[352]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-mfs-manual3.0-ports-354)|
|9422|Unofficial||||MooseFS distributed file system – Chunkservers[[352]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-mfs-manual3.0-ports-354)|
|9425|Unofficial||||MooseFS distributed file system – CGI server[[352]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-mfs-manual3.0-ports-354)|
|9443|Unofficial||||[VMware](https://en.wikipedia.org/wiki/VMware "VMware") Websense Triton console (HTTPS port used for accessing and administrating a vCenter Server via the Web Management Interface)|
|Unofficial||||[NCSA Brown Dog](https://en.wikipedia.org/wiki/NCSA_Brown_Dog "NCSA Brown Dog") Data Tilling Service|
|9535|Yes|   |||mngsuite, [LANDesk](https://en.wikipedia.org/wiki/Landesk "Landesk") Management Suite Remote Control|
|9536|Yes|   |||laes-bf, IP Fabrics Surveillance buffering function|
|9600|No|Unofficial|||[Factory Interface Network Service](https://en.wikipedia.org/wiki/Factory_Interface_Network_Service "Factory Interface Network Service") (FINS), a network protocol used by [Omron](https://en.wikipedia.org/wiki/Omron "Omron") [programmable logic controllers](https://en.wikipedia.org/wiki/Programmable_logic_controller "Programmable logic controller")[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|9669|Unofficial|No|||VGG Image Search Engine [VISE](https://www.robots.ox.ac.uk/~vgg/software/vise/)|
|9675|Unofficial|   |||[Spiceworks](https://en.wikipedia.org/wiki/Spiceworks "Spiceworks") Desktop, IT Helpdesk Software|
|9676|Unofficial|   |||[Spiceworks](https://en.wikipedia.org/wiki/Spiceworks "Spiceworks") Desktop, IT Helpdesk Software|
|9695|Yes|   |||[Content centric networking](https://en.wikipedia.org/wiki/Content_centric_networking "Content centric networking") (CCN, CCNx)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|9735|Unofficial||||[Bitcoin](https://en.wikipedia.org/wiki/Bitcoin "Bitcoin") [Lightning Network](https://en.wikipedia.org/wiki/Lightning_Network "Lightning Network")[[353]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-355)|
|9785|Unofficial|   |||[Viber](https://en.wikipedia.org/wiki/Viber "Viber")[[214]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-viber-216)|
|9800|Yes|   |||[WebDAV](https://en.wikipedia.org/wiki/WebDAV "WebDAV") Source|
|Unofficial|   |||[WebCT](https://en.wikipedia.org/wiki/WebCT "WebCT") e-learning portal|
|9875|Unofficial||||[Club Penguin](https://en.wikipedia.org/wiki/Club_Penguin "Club Penguin") Disney online game for kids|
|9898|Unofficial||||[Tripwire](https://en.wikipedia.org/wiki/Tripwire_(software) "Tripwire (software)")—File Integrity Monitoring Software[[354]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-356)|
|9899||Yes|||[SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol "Stream Control Transmission Protocol") tunneling (port number used in SCTP packets encapsulated in UDP, RFC 6951)|
|9901|Unofficial||||Banana for Apache Solr|
|9981|Unofficial||||[Tvheadend](https://en.wikipedia.org/wiki/Tvheadend "Tvheadend") HTTP server (web interface)[[355]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-tvh-wiki-install-initial-setup-357)|
|9982|Unofficial||||[Tvheadend](https://en.wikipedia.org/wiki/Tvheadend "Tvheadend") HTSP server (Streaming protocol)[[355]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-tvh-wiki-install-initial-setup-357)|
|9987|Unofficial|No|||[TeamSpeak](https://en.wikipedia.org/wiki/TeamSpeak "TeamSpeak") 3 server default (voice) port (for the conflicting service see the IANA list)[[356]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-hub.docker.com-358)|
|9993||Unofficial|||[ZeroTier](https://en.wikipedia.org/wiki/ZeroTier "ZeroTier") Default port for ZeroTier|
|9997|Unofficial||||[Splunk](https://en.wikipedia.org/wiki/Splunk "Splunk") port for communication between the forwarders and indexers|
|9999|Unofficial|   |||[Urchin](https://en.wikipedia.org/wiki/Urchin_Software_Corporation "Urchin Software Corporation") Web Analytics[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|9999|Unofficial||||[Dash (cryptocurrency)](https://en.wikipedia.org/wiki/Dash_(cryptocurrency) "Dash (cryptocurrency)")[[357]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-359)|
|10000|Yes|   |||Network Data Management Protocol ([NDMP](https://en.wikipedia.org/wiki/NDMP "NDMP")) Control stream for network backup and restore.|
|Unofficial|   |||[BackupExec](https://en.wikipedia.org/wiki/BackupExec "BackupExec")|
|Unofficial|   |||[Webmin](https://en.wikipedia.org/wiki/Webmin "Webmin"), Web-based Unix/Linux system administration tool (default port)|
|10000–20000|No|Unofficial|||Used on [VoIP](https://en.wikipedia.org/wiki/Voice_over_IP "Voice over IP") networks for receiving and transmitting voice telephony traffic which includes [Google Voice](https://en.wikipedia.org/wiki/Google_Voice "Google Voice") via the [OBiTalk](https://en.wikipedia.org/wiki/Obihai_Technology "Obihai Technology") [ATA](https://en.wikipedia.org/wiki/Analog_telephone_adapter "Analog telephone adapter") devices as well as on the [MagicJack](https://en.wikipedia.org/wiki/MagicJack "MagicJack") and [Vonage](https://en.wikipedia.org/wiki/Vonage "Vonage") ATA network devices.[[358]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-support.vonage.com-360)|
|10001||Unofficial|||Ubiquiti UniFi access points broadcast to 255.255.255.255:10001 (UDP) to locate the controller(s)|
|10009|Unofficial|   |||_[Crossfire](https://en.wikipedia.org/wiki/Crossfire_(2007_video_game) "Crossfire (2007 video game)")_, a multiplayer online First Person Shooter[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|10011|Unofficial|No|||[TeamSpeak](https://en.wikipedia.org/wiki/TeamSpeak "TeamSpeak") 3 ServerQuery[[356]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-hub.docker.com-358)|
|10022|Unofficial|No|||[TeamSpeak](https://en.wikipedia.org/wiki/TeamSpeak "TeamSpeak") 3 ServerQuery over SSH|
|10024|Unofficial||||Zimbra smtp [mta]—to amavis from postfix[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|10025|Unofficial||||Zimbra smtp [mta]—back to postfix from amavis[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|10042|Unofficial||||[Mathoid](https://www.mediawiki.org/wiki/Mathoid "mw:Mathoid") server [[359]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-361)|
|10050|Yes|   |||[Zabbix](https://en.wikipedia.org/wiki/Zabbix "Zabbix") agent|
|10051|Yes|   |||[Zabbix](https://en.wikipedia.org/wiki/Zabbix "Zabbix") trapper|
|10110|Yes|   |||NMEA 0183 Navigational Data. Transport of NMEA 0183 sentences over TCP or UDP|
|10172|Unofficial||||Intuit [Quickbooks](https://en.wikipedia.org/wiki/Quickbooks "Quickbooks") client|
|10200|Unofficial||||[FRISK Software International](https://en.wikipedia.org/wiki/FRISK_Software_International "FRISK Software International")'s _fpscand_ virus scanning daemon for Unix platforms[[360]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-362)|
|Unofficial||||FRISK Software International's _f-protd_ virus scanning daemon for Unix platforms[[361]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-autogenerated2-363)|
|10201–10204|Unofficial||||FRISK Software International's _f-protd_ virus scanning daemon for Unix platforms[[361]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-autogenerated2-363)|
|10212|Yes||||GE Intelligent Platforms Proficy HMI/SCADA – CIMPLICITY WebView[[362]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-364)|
|10308|Unofficial|   |||_[Digital Combat Simulator](https://en.wikipedia.org/wiki/Digital_Combat_Simulator "Digital Combat Simulator")_ Dedicated Server [[363]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-365)|
|10346|No||||TEKWorx Limited - interfaceIT board protocol|
|10468||Unofficial|||Flyer - discovery protocol[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|10480|Unofficial|   |||_[SWAT 4](https://en.wikipedia.org/wiki/SWAT_4 "SWAT 4")_ Dedicated Server[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|10505||Unofficial|||BlueStacks (android simulator) broadcast[[364]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-366)|
|10514|Unofficial|   |||TLS-enabled Rsyslog (default by convention)|
|10578|Unofficial|No|||Skyrim Together multiplayer server for [The Elder Scrolls V: Skyrim](https://en.wikipedia.org/wiki/The_Elder_Scrolls_V:_Skyrim "The Elder Scrolls V: Skyrim") mod.|
|10800|Unofficial||||[Touhou](https://en.wikipedia.org/wiki/Touhou "Touhou") fight games ([Immaterial and Missing Power](https://en.wikipedia.org/wiki/Immaterial_and_Missing_Power "Immaterial and Missing Power"), [Scarlet Weather Rhapsody](https://en.wikipedia.org/wiki/Scarlet_Weather_Rhapsody "Scarlet Weather Rhapsody"), [Hisoutensoku](https://en.wikipedia.org/wiki/Touhou_His%C5%8Dtensoku "Touhou Hisōtensoku"), [Hopeless Masquerade](https://en.wikipedia.org/wiki/Hopeless_Masquerade "Hopeless Masquerade") and [Urban Legend in Limbo](https://en.wikipedia.org/wiki/Urban_Legend_in_Limbo "Urban Legend in Limbo"))|
|10823||Unofficial|||_[Farming Simulator 2011](https://en.wikipedia.org/wiki/Farming_Simulator_2011 "Farming Simulator 2011")_[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|10836|Unofficial||||configurable-world-domination-game multiplayer server[[365]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-367)|
|10891|Unofficial||||Jungle Disk (this port is opened by the Jungle Disk Monitor service on the localhost)[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|10933|Yes|No|||Octopus Deploy Tentacle deployment agent[[366]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-368)|
|11001|||||metasys ( Johnson Controls Metasys java AC control environment )|
|11100|No|Unofficial|||[Risk of Rain](https://en.wikipedia.org/wiki/Risk_of_Rain "Risk of Rain") multiplayer server|
|11111|Unofficial||||RiCcI, Remote Configuration Interface (Redhat Linux)|
|Yes|   |||random code|
|11112|Yes|   |||[ACR](https://en.wikipedia.org/wiki/American_College_of_Radiology "American College of Radiology")/[NEMA](https://en.wikipedia.org/wiki/National_Electrical_Manufacturers_Association "National Electrical Manufacturers Association") [Digital Imaging and Communications in Medicine](https://en.wikipedia.org/wiki/Digital_Imaging_and_Communications_in_Medicine "Digital Imaging and Communications in Medicine") (DICOM)|
|11211|Unofficial|   |||[memcached](https://en.wikipedia.org/wiki/Memcached "Memcached")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|11214|Unofficial|   |||memcached incoming SSL proxy|
|11215|Unofficial|   |||memcached internal outgoing SSL proxy|
|11235|Yes|   |   ||[XCOMPUTE](https://en.wikipedia.org/w/index.php?title=XCOMPUTE&action=edit&redlink=1 "XCOMPUTE (page does not exist)") numerical systems messaging (Xplicit Computing)[[367]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-xcompute-iana-record-369)|
|11311|Unofficial|   |||[Robot Operating System](https://en.wikipedia.org/wiki/Robot_Operating_System "Robot Operating System") master|
|11371|Yes|   |||[OpenPGP](https://en.wikipedia.org/wiki/OpenPGP "OpenPGP") HTTP [key server](https://en.wikipedia.org/wiki/Key_server_(cryptographic) "Key server (cryptographic)")|
|11753|Unofficial||||[OpenRCT2](https://en.wikipedia.org/wiki/OpenRCT2 "OpenRCT2") multiplayer[[368]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-openrct2-docs-multiplayer-370)|
|12000|Unofficial|   |||[CubeForm](https://en.wikipedia.org/w/index.php?title=CubeForm&action=edit&redlink=1 "CubeForm (page does not exist)"), Multiplayer SandBox Game|
|12012||Unofficial|||[Audition Online Dance Battle](https://en.wikipedia.org/wiki/Audition_Online_Dance_Battle "Audition Online Dance Battle"), Korea Server—Status/Version Check|
|12013|Unofficial|   |||Audition Online Dance Battle, Korea Server|
|12035||Unofficial|||_[Second Life](https://en.wikipedia.org/wiki/Second_Life "Second Life")_, used for server UDP in-bound[[369]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-http://wiki.secondlife.com/wiki/Authentication_Flow@step_4-371)|
|12043|Unofficial||||_Second Life_, used for LSL HTTPS in-bound[[370]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-wiki.secondlife.com/wiki/LSL_HTTP_server@Functions-372)|
|12046|Unofficial||||_Second Life_, used for LSL HTTP in-bound[[370]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-wiki.secondlife.com/wiki/LSL_HTTP_server@Functions-372)|
|12201|Unofficial|   |||Graylog Extended Log Format (GELF)[[371]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-373)[_[importance?](https://en.wikipedia.org/wiki/Wikipedia:What_Wikipedia_is_not#Encyclopedic_content "Wikipedia:What Wikipedia is not")_]|
|12222||Yes|||Light Weight Access Point Protocol ([LWAPP](https://en.wikipedia.org/wiki/LWAPP "LWAPP")) LWAPP data (RFC 5412)|
|12223||Yes|||Light Weight Access Point Protocol ([LWAPP](https://en.wikipedia.org/wiki/LWAPP "LWAPP")) LWAPP control (RFC 5412)|
|12307||Unofficial|||Makerbot UDP Broadcast (client to printer) (JSON-RPC)[[372]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-https://support.makerbot.com/learn/makerbot-desktop-software/using-makerbot-desktop/network-connectivity-for-enterprise-private-networks-fifth-generation-makerbot-3d-printers_1190-374)|
|12308||Unofficial|||Makerbot UDP Broadcast (printer to client) (JSON-RPC)[[372]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-https://support.makerbot.com/learn/makerbot-desktop-software/using-makerbot-desktop/network-connectivity-for-enterprise-private-networks-fifth-generation-makerbot-3d-printers_1190-374)|
|12345|Unofficial|   |||_[Cube World](https://en.wikipedia.org/wiki/Cube_World "Cube World")_[[373]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-375)|
|Unofficial||||_[Little Fighter 2](https://en.wikipedia.org/wiki/Little_Fighter_2 "Little Fighter 2")_|
|Unofficial|   |||[NetBus](https://en.wikipedia.org/wiki/NetBus "NetBus") remote administration tool (often [Trojan horse](https://en.wikipedia.org/wiki/Trojan_horse_(computing) "Trojan horse (computing)")).|
|12443|Unofficial||||[IBM HMC](https://en.wikipedia.org/wiki/IBM_Hardware_Management_Console "IBM Hardware Management Console") web browser management access over [HTTPS](https://en.wikipedia.org/wiki/HTTPS "HTTPS") instead of default port 443[[374]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-376)|
|12489|Unofficial||||NSClient/NSClient++/NC_Net (Nagios)|
|12975|Unofficial||||[LogMeIn](https://en.wikipedia.org/wiki/LogMeIn "LogMeIn") [Hamachi](https://en.wikipedia.org/wiki/Hamachi_(software) "Hamachi (software)") (VPN tunnel software; also port 32976)—used to connect to Mediation Server (bibi.hamachi.cc); will attempt to use [SSL](https://en.wikipedia.org/wiki/Secure_Sockets_Layer "Secure Sockets Layer") (TCP port 443) if both 12975 & 32976 fail to connect|
|13000–13050||Unofficial|||_[Second Life](https://en.wikipedia.org/wiki/Second_Life "Second Life")_, used for server UDP in-bound[[375]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-377)|
|13008|Unofficial|   |||_[Crossfire](https://en.wikipedia.org/wiki/Crossfire_(2007_video_game) "Crossfire (2007 video game)")_, a multiplayer online First Person Shooter[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|13075|Yes||||Default[[376]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-378) for [BMC Software](https://en.wikipedia.org/wiki/BMC_Software "BMC Software") [Control-M/Enterprise Manager](https://en.wikipedia.org/wiki/BMC_Control-M "BMC Control-M") Corba communication, though often changed during installation|
|13400|Yes|   |||ISO 13400 Road vehicles — Diagnostic communication over Internet Protocol(DoIP)|
|13698|Unofficial||||[File-Transferer](https://github.com/UltraQbik/File-Transferer)|
|13720|Yes|   |||[Symantec](https://en.wikipedia.org/wiki/NortonLifeLock "NortonLifeLock") [NetBackup](https://en.wikipedia.org/w/index.php?title=NetBackup&action=edit&redlink=1 "NetBackup (page does not exist)")—bprd (formerly [VERITAS](https://en.wikipedia.org/wiki/Veritas_Software "Veritas Software"))|
|13721|Yes|   |||Symantec NetBackup—bpdbm (formerly VERITAS)|
|13724|Yes|   |||Symantec Network Utility—vnetd (formerly VERITAS)|
|13782|Yes|   |||Symantec NetBackup—bpcd (formerly VERITAS)|
|13783|Yes|   |||Symantec VOPIED protocol (formerly VERITAS)|
|13785|Yes|   |||Symantec NetBackup Database—nbdb (formerly VERITAS)|
|13786|Yes|   |||Symantec nomdb (formerly VERITAS)|
|14550||Unofficial|||[MAVLink](https://en.wikipedia.org/wiki/MAVLink "MAVLink") Ground Station Port|
|14567||Unofficial|||[Battlefield 1942](https://en.wikipedia.org/wiki/Battlefield_1942 "Battlefield 1942") and mods|
|14652|Unofficial||||Repgen DoxBox reporting tool|
|14800|Unofficial||||[Age of Wonders III](https://en.wikipedia.org/wiki/Age_of_Wonders_III "Age of Wonders III") p2p port[[377]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-379)|
|15000|Unofficial||||[psyBNC](https://en.wikipedia.org/wiki/PsyBNC "PsyBNC")|
|Unofficial||||[Wesnoth](https://en.wikipedia.org/wiki/Wesnoth "Wesnoth")|
|Unofficial||||Kaspersky Network Agent[[378]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-380)|
||Unofficial|||Teltonika networks remote management system (RMS)|
|15009|Unofficial|   |||Teltonika networks remote management system (RMS)|
|15010|Unofficial|   |||Teltonika networks remote management system (RMS)|
|15441|Unofficial|   |||[ZeroNet](https://en.wikipedia.org/wiki/ZeroNet "ZeroNet") fileserver[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|15567||Unofficial|||_[Battlefield Vietnam](https://en.wikipedia.org/wiki/Battlefield_Vietnam "Battlefield Vietnam")_ and mods|
|15345|Yes|   |||_[XPilot](https://en.wikipedia.org/wiki/XPilot "XPilot")_ Contact|
|15672|Unofficial|No|||[RabbitMQ](https://en.wikipedia.org/wiki/RabbitMQ "RabbitMQ") management plugin[[379]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rabbitmq-management-381)|
|16000|Unofficial||||[Oracle WebCenter](https://en.wikipedia.org/wiki/Oracle_WebCenter "Oracle WebCenter") Content: Imaging (formerly known as Oracle [Universal Content Management](https://en.wikipedia.org/wiki/Universal_Content_Management "Universal Content Management")). Port though often changed during installation|
|Unofficial||||[shroudBNC](https://en.wikipedia.org/wiki/ShroudBNC "ShroudBNC")|
|16080|Unofficial||||[macOS Server](https://en.wikipedia.org/wiki/MacOS_Server "MacOS Server") Web (HTTP) service with performance cache[[380]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-382)|
|16200|Unofficial||||Oracle WebCenter Content: Content Server (formerly known as Oracle [Universal Content Management](https://en.wikipedia.org/wiki/Universal_Content_Management "Universal Content Management")). Port though often changed during installation|
|16225|Unofficial||||Oracle WebCenter Content: Content Server Web UI. Port though often changed during installation|
|16250|Unofficial||||Oracle WebCenter Content: Inbound Refinery (formerly known as Oracle [Universal Content Management](https://en.wikipedia.org/wiki/Universal_Content_Management "Universal Content Management")). Port though often changed during installation|
|16261|Unofficial|   |||_[Project Zomboid](https://en.wikipedia.org/wiki/Project_Zomboid "Project Zomboid")_ multiplayer. Additional sequential ports used for each player connecting to server.[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|16300|Unofficial||||Oracle WebCenter Content: Records Management (formerly known as Oracle [Universal Records Management](https://en.wikipedia.org/w/index.php?title=Universal_Records_Management&action=edit&redlink=1 "Universal Records Management (page does not exist)")). Port though often changed during installation|
|16384||Unofficial|||CISCO Default RTP MIN|
|16384–16403||Unofficial|||[Real-time Transport Protocol](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol "Real-time Transport Protocol") (RTP), [RTP Control Protocol](https://en.wikipedia.org/wiki/RTP_Control_Protocol "RTP Control Protocol") (RTCP), used by [Apple](https://en.wikipedia.org/wiki/Apple_Inc. "Apple Inc.")'s [iChat](https://en.wikipedia.org/wiki/IChat "IChat") for audio and video[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|16384–16387||Unofficial|||Real-time Transport Protocol (RTP), RTP Control Protocol (RTCP), used by Apple's [FaceTime](https://en.wikipedia.org/wiki/FaceTime "FaceTime") and [Game Center](https://en.wikipedia.org/wiki/Game_Center "Game Center")[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|16393–16402||Unofficial|||Real-time Transport Protocol (RTP), RTP Control Protocol (RTCP), used by Apple's FaceTime and Game Center[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|16403–16472||Unofficial|||Real-time Transport Protocol (RTP), RTP Control Protocol (RTCP), used by Apple's Game Center[[11]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-apple-kb-HT202944-11)|
|16400|Unofficial||||Oracle WebCenter Content: Capture (formerly known as Oracle Document Capture). Port though often changed during installation|
|16567||Unofficial|||[Battlefield 2](https://en.wikipedia.org/wiki/Battlefield_2 "Battlefield 2") and mods|
|16666|Unofficial|   |||SITC Port for mobile web traffic|
|16677|Unofficial|   |||SITC Port for mobile web traffic|
|17000||Unofficial|||M17 - Digital RF voice and data protocol with Internet (UDP) gateways (reflectors).[[381]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-383)|
|17011|Unofficial||||[Worms](https://en.wikipedia.org/wiki/Worms_(series) "Worms (series)") multiplayer|
|17224|Yes|   |||Train Realtime Data Protocol (TRDP) Process Data, network protocol used in train communication.[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2)[[382]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-port_17224,_IANA,_2019-384)|
|17225|Yes|   |||Train Realtime Data Protocol (TRDP) Message Data, network protocol used in train communication.[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2)[[383]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-port_17225,_IANA,_2019-385)|
|17333|Unofficial||||CS Server (CSMS), default binary protocol port|
|17472|Yes||||Tanium Communication Port|
|17474||Unofficial|||DMXControl 3 Network Discovery|
|17475|Unofficial|   |||DMXControl 3 Network Broker|
|17500|Yes|   |||[Dropbox](https://en.wikipedia.org/wiki/Dropbox_(storage_provider) "Dropbox (storage provider)") LanSync Protocol (db-lsp); used to synchronize file catalogs between Dropbox clients on a local network.|
|17777|Unofficial|   |||SITC Port for mobile web traffic|
|18080|Unofficial|No|||[Monero](https://en.wikipedia.org/wiki/Monero_(cryptocurrency) "Monero (cryptocurrency)") P2P network communications[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|18081|Unofficial|No|||Monero incoming RPC calls[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|18091|Unofficial|   |||[memcached](https://en.wikipedia.org/wiki/Memcached "Memcached") Internal REST HTTPS for SSL|
|18092|Unofficial|   |||memcached Internal CAPI HTTPS for SSL|
|18104|Yes||||RAD PDF Service|
|18200|Unofficial|   |||[Audition Online Dance Battle](https://en.wikipedia.org/wiki/Audition_Online_Dance_Battle "Audition Online Dance Battle"), AsiaSoft Thailand Server status/version check|
|18201|Unofficial|   |||Audition Online Dance Battle, AsiaSoft Thailand Server|
|18206|Unofficial|   |||Audition Online Dance Battle, AsiaSoft Thailand Server FAM database|
|18300|Unofficial|   |||Audition Online Dance Battle, AsiaSoft SEA Server status/version check|
|18301|Unofficial|   |||Audition Online Dance Battle, AsiaSoft SEA Server|
|18306|Unofficial|   |||Audition Online Dance Battle, AsiaSoft SEA Server FAM database|
|18333|Unofficial||||[Bitcoin](https://en.wikipedia.org/wiki/Bitcoin "Bitcoin") testnet[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|18400|Unofficial|   |||Audition Online Dance Battle, KAIZEN Brazil Server status/version check|
|18401|Unofficial|   |||Audition Online Dance Battle, KAIZEN Brazil Server|
|18505|Unofficial|   |||Audition Online Dance Battle R4p3 Server, Nexon Server status/version check|
|18506|Unofficial|   |||Audition Online Dance Battle, Nexon Server|
|18605|Unofficial|   |||[X-BEAT](https://en.wikipedia.org/wiki/X-BEAT "X-BEAT") status/version check|
|18606|Unofficial|   |||[X-BEAT](https://en.wikipedia.org/wiki/X-BEAT "X-BEAT")|
|18676|Unofficial|   |||YouView|
|19000|Unofficial|   |||Audition Online Dance Battle, G10/alaplaya Server status/version check|
||Unofficial|||[JACK](https://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit "JACK Audio Connection Kit") sound server|
|19001|Unofficial|   |||Audition Online Dance Battle, G10/alaplaya Server|
|19132||Unofficial|||_[Minecraft: Bedrock Edition](https://en.wikipedia.org/wiki/Minecraft:_Bedrock_Edition "Minecraft: Bedrock Edition")_ multiplayer server[[384]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-minecraft_wiki-386)|
|19133||Unofficial|||_Minecraft: Bedrock Edition_ IPv6 multiplayer server[[384]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-minecraft_wiki-386)|
|19150|Unofficial|   |||[Gkrellm](https://en.wikipedia.org/wiki/Gkrellm "Gkrellm") Server|
|19226|Unofficial||||[Panda Software](https://en.wikipedia.org/wiki/Panda_Security "Panda Security") AdminSecure Communication Agent|
|19294|Unofficial||||[Google Talk](https://en.wikipedia.org/wiki/Google_Talk "Google Talk") Voice and Video connections[[385]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-gtalk_voice-387)|
|19295||Unofficial|||Google Talk Voice and Video connections[[385]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-gtalk_voice-387)|
|19302||Unofficial|||Google Talk Voice and Video connections[[385]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-gtalk_voice-387)|
|19531|Unofficial|No|||[systemd](https://en.wikipedia.org/wiki/Systemd "Systemd")-journal-gatewayd[[386]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-388)|
|19532|Unofficial|No|||[systemd](https://en.wikipedia.org/wiki/Systemd "Systemd")-journal-remote[[387]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-389)|
|19788|No|Yes|||Mesh Link Establishment protocol for IEEE 802.15.4 radio mesh networks[[388]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-MLE-390)|
|19812|Yes|No|||4D database SQL Communication[[389]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-4D_ports-391)|
|19813|Yes|   |||4D database Client Server Communication[[389]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-4D_ports-391)|
|19814|Yes||||4D database DB4D Communication[[389]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-4D_ports-391)|
|19999|Yes|   |||Distributed Network Protocol—Secure ([DNP](https://en.wikipedia.org/wiki/DNP3 "DNP3")—Secure), a secure version of the protocol used in [SCADA](https://en.wikipedia.org/wiki/SCADA "SCADA") systems between communicating [RTU](https://en.wiktionary.org/wiki/RTU "wikt:RTU")'s and [IED](https://en.wiktionary.org/wiki/IED "wikt:IED")'s|
|20000|Yes|   |||Distributed Network Protocol ([DNP](https://en.wikipedia.org/wiki/DNP3 "DNP3")), a protocol used in [SCADA](https://en.wikipedia.org/wiki/SCADA "SCADA") systems between communicating [RTU](https://en.wikipedia.org/wiki/Remote_Terminal_Unit "Remote Terminal Unit")'s and [IED](https://en.wikipedia.org/wiki/Intelligent_electronic_device "Intelligent electronic device")'s|
|Yes|   |||[OpenWebNet](https://en.wikipedia.org/wiki/OpenWebNet "OpenWebNet"), communications protocol used in [Bticino](https://en.wikipedia.org/wiki/Bticino "Bticino") products|
|Unofficial|   |||[Usermin](https://en.wikipedia.org/wiki/Usermin "Usermin"), Web-based Unix/Linux user administration tool (default port)|
|Unofficial|   |||Used on [VoIP](https://en.wikipedia.org/wiki/Voice_over_IP "Voice over IP") networks for receiving and transmitting voice telephony traffic which includes [Google Voice](https://en.wikipedia.org/wiki/Google_Voice "Google Voice") via the [OBiTalk](https://en.wikipedia.org/wiki/Obihai_Technology "Obihai Technology") [ATA](https://en.wikipedia.org/wiki/Analog_telephone_adapter "Analog telephone adapter") devices as well as on the [MagicJack](https://en.wikipedia.org/wiki/MagicJack "MagicJack") and [Vonage](https://en.wikipedia.org/wiki/Vonage "Vonage") ATA network devices.[[358]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-support.vonage.com-360)|
|20560|Unofficial|   |||_[Killing Floor](https://en.wikipedia.org/wiki/Killing_Floor_(2009_video_game) "Killing Floor (2009 video game)")_|
|20582||Unofficial|||HW Development IoT comms|
|20583||Unofficial|||HW Development IoT comms|
|20595||Unofficial|||_[0 A.D. Empires Ascendant](https://en.wikipedia.org/wiki/0_A.D._(video_game) "0 A.D. (video game)")_|
|20808||Unofficial|||Ableton Link|
|21025|Unofficial||||Starbound Server (default), [Starbound](http://playstarbound.com/)|
|21064|Unofficial||||Default Ingres DBMS server|
|22000|Unofficial||||[Syncthing](https://en.wikipedia.org/wiki/Syncthing "Syncthing") (default)|
|22136|Unofficial||||[FLIR Systems](http://www.flir.com/) Camera Resource Protocol|
|22222|Unofficial||||Davis Instruments, [WeatherLink IP](http://davisnet.com/weather/products/weather_product.asp?pnum=06555)|
|23073|Unofficial|   |||[Soldat](https://en.wikipedia.org/wiki/Soldat_(video_game) "Soldat (video game)") Dedicated Server|
|23399|Unofficial|   |||[Skype](https://en.wikipedia.org/wiki/Skype "Skype") default protocol|
|23513|Unofficial|   |||[_Duke Nukem 3D_ source ports](https://en.wikipedia.org/wiki/Duke_Nukem_3D#Source_ports "Duke Nukem 3D")|
|24441|Unofficial|   |||Pyzor spam detection network|
|24444|Unofficial|   |||[NetBeans](https://en.wikipedia.org/wiki/NetBeans "NetBeans") integrated development environment|
|24465|Yes|   |||[Tonido Directory Server](https://en.wikipedia.org/wiki/Tonido "Tonido") for [Tonido](http://www.tonido.com/) which is a Personal Web App and P2P platform|
|24554|Yes|   |||[BINKP](https://en.wikipedia.org/wiki/Binkp "Binkp"), [Fidonet](https://en.wikipedia.org/wiki/Fidonet "Fidonet") mail transfers over [TCP/IP](https://en.wikipedia.org/wiki/TCP/IP "TCP/IP")|
|24800|Unofficial|   |||[Synergy](https://en.wikipedia.org/wiki/Synergy_(software) "Synergy (software)"): keyboard/mouse sharing software|
|24842|Unofficial|   |||_[StepMania: Online](https://en.wikipedia.org/wiki/StepMania "StepMania")_: _[Dance Dance Revolution](https://en.wikipedia.org/wiki/Dance_Dance_Revolution "Dance Dance Revolution")_ Simulator|
|25565|Unofficial||||_[Minecraft](https://en.wikipedia.org/wiki/Minecraft "Minecraft")_ (Java Edition) multiplayer server[[390]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-392)[[391]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Protocol_-_wiki.vg-393)|
||Unofficial|||_Minecraft (Java Edition)_ multiplayer server query[[392]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-394)|
|25575||Unofficial|||_Minecraft_ (Java Edition) multiplayer server RCON[[393]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-395)|
|25600-25700|Unofficial|   |||SamsidParty Operational Ports|
|25734-25735|Unofficial|   |||SOLIDWORKS SolidNetworkLicense Manager[[394]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-396)|
|25826||Unofficial|||[collectd](https://en.wikipedia.org/wiki/Collectd "Collectd") default port[[395]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-397)|
|26000|Yes|   |||[id Software](https://en.wikipedia.org/wiki/Id_Software "Id Software")'s _[Quake](https://en.wikipedia.org/wiki/Quake_(video_game) "Quake (video game)")_ server|
|Unofficial||||_[EVE Online](https://en.wikipedia.org/wiki/EVE_Online "EVE Online")_|
||Unofficial|||_[Xonotic](https://en.wikipedia.org/wiki/Xonotic "Xonotic")_, an [open-source](https://en.wikipedia.org/wiki/Open-source_software "Open-source software") [arena shooter](https://en.wikipedia.org/wiki/Arena_shooter "Arena shooter")|
|26822||Unofficial|||_MSI MysticLight_|
|26900–26901|Unofficial||||_EVE Online_|
|26909–26911|Unofficial||||_Action Tanks Online_|
|27000|Unofficial||||[PowerBuilder](https://en.wikipedia.org/wiki/PowerBuilder "PowerBuilder") _[SySAM](https://en.wikipedia.org/w/index.php?title=SySAM&action=edit&redlink=1 "SySAM (page does not exist)")_ license server|
|27000–27006||Unofficial|||[id Software](https://en.wikipedia.org/wiki/Id_Software "Id Software")'s _[QuakeWorld](https://en.wikipedia.org/wiki/QuakeWorld "QuakeWorld")_ master server|
|27000–27009|Yes|   |||[FlexNet Publisher](https://en.wikipedia.org/wiki/FlexNet_Publisher "FlexNet Publisher")'s License server (from the range of default ports)|
|27000–27015|No|Unofficial|||[Steam](https://en.wikipedia.org/wiki/Steam_(service) "Steam (service)") (game client traffic)[[396]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-steam-support-8571-GLVN-8711-398)|
|27015|No|Unofficial|||[GoldSrc](https://en.wikipedia.org/wiki/GoldSrc "GoldSrc") and [Source engine](https://en.wikipedia.org/wiki/Source_engine "Source engine") dedicated server port[[396]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-steam-support-8571-GLVN-8711-398)|
|27015–27018||Unofficial|||_[Unturned](https://en.wikipedia.org/wiki/Unturned "Unturned")_, a survival game|
|27015–27030|No|Unofficial|||Steam (matchmaking and HLTV)[[396]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-steam-support-8571-GLVN-8711-398)|
|Unofficial|   |||Steam (downloads)[[396]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-steam-support-8571-GLVN-8711-398)|
|27016|Unofficial|   |||_[Magicka](https://en.wikipedia.org/wiki/Magicka "Magicka")_ and [Space Engineers](https://en.wikipedia.org/wiki/Space_Engineers "Space Engineers") server port|
|27017|Unofficial|No|||[MongoDB](https://en.wikipedia.org/wiki/MongoDB "MongoDB") daemon process (`mongod`) and routing service (`mongos`)[[397]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-mongodb-docs-reference-default-mongodb-port-399)|
|27031–27035|No|Unofficial|||Steam (In-Home Streaming)[[396]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-steam-support-8571-GLVN-8711-398)|
|27036|Unofficial|   |||Steam (In-Home Streaming)[[396]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-steam-support-8571-GLVN-8711-398)|
|27374|Unofficial|   |||[Sub7](https://en.wikipedia.org/wiki/Sub7 "Sub7") default.|
|27500–27900||Unofficial|||[id Software](https://en.wikipedia.org/wiki/Id_Software "Id Software")'s _[QuakeWorld](https://en.wikipedia.org/wiki/QuakeWorld "QuakeWorld")_|
|27888||Unofficial|||[Kaillera](https://en.wikipedia.org/wiki/Kaillera "Kaillera") server|
|27901–27910||Unofficial|||[id Software](https://en.wikipedia.org/wiki/Id_Software "Id Software")'s _[Quake II](https://en.wikipedia.org/wiki/Quake_II "Quake II")_ master server|
|27950||Unofficial|||_[OpenArena](https://en.wikipedia.org/wiki/OpenArena "OpenArena")_ outgoing|
|27960–27969||Unofficial|||[Activision](https://en.wikipedia.org/wiki/Activision "Activision")'s _[Enemy Territory](https://en.wikipedia.org/wiki/Wolfenstein:_Enemy_Territory "Wolfenstein: Enemy Territory")_ and [id Software](https://en.wikipedia.org/wiki/Id_Software "Id Software")'s _[Quake III Arena](https://en.wikipedia.org/wiki/Quake_III_Arena "Quake III Arena")_, _Quake III_ and _[Quake Live](https://en.wikipedia.org/wiki/Quake_Live "Quake Live")_ and some ioquake3 derived games, such as _Urban Terror_ (_OpenArena_ incoming)|
|28000|Yes|   |||[Siemens Digital Industries Software](https://en.wikipedia.org/wiki/Siemens_Digital_Industries_Software "Siemens Digital Industries Software") license server[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2)|
|28001|Unofficial|   |||_[Starsiege: Tribes](https://en.wikipedia.org/wiki/Starsiege:_Tribes "Starsiege: Tribes")_[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|28015||Unofficial|||[_Rust_ (video game)](https://en.wikipedia.org/wiki/Rust_(video_game) "Rust (video game)")[[398]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-400)|
|28016||Unofficial|||_Rust_ (video game) RCON[[399]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-401)|
|28200|Assigned|   |||[VoxelStorm](https://en.wikipedia.org/wiki/VoxelStorm "VoxelStorm") game server|
|28260|Unofficial||||Palo Alto Networks' Panorama HA-1 backup unencrypted sync port.[[26]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-PAN-OS_HALinksAndBackupLinks-26)|
|28443|Unofficial||||Palo Alto Networks' Panorama-to-managed devices software updates, PAN-OS 8.0 and later.[[204]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-EDU-120_10-206)|
|28769|Unofficial||||Palo Alto Networks' Panorama HA unencrypted sync port.[[26]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-PAN-OS_HALinksAndBackupLinks-26)|
|28770|Unofficial||||Palo Alto Networks' Panorama HA-1 backup sync port.[[26]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-PAN-OS_HALinksAndBackupLinks-26)|
|28770–28771||Unofficial|||_[AssaultCube Reloaded](https://en.wikipedia.org/w/index.php?title=AssaultCube_Reloaded&action=edit&redlink=1 "AssaultCube Reloaded (page does not exist)")_, a video game based upon a modification of _[AssaultCube](https://en.wikipedia.org/wiki/AssaultCube "AssaultCube")_[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|28785–28786||Unofficial|||_[Cube 2: Sauerbraten](https://en.wikipedia.org/wiki/Cube_2:_Sauerbraten "Cube 2: Sauerbraten")_[[400]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Cube2Sauerbraten-402)|
|28852|Unofficial|   |||_[Killing Floor](https://en.wikipedia.org/wiki/Killing_Floor_(2009_video_game) "Killing Floor (2009 video game)")_[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|28910|Unofficial|   |||[Nintendo Wi-Fi Connection](https://en.wikipedia.org/wiki/Nintendo_Wi-Fi_Connection "Nintendo Wi-Fi Connection")[[401]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-nintendo-wfc-instruction-booklet-403)|
|28960|Unofficial|   |||_[Call of Duty](https://en.wikipedia.org/wiki/Call_of_Duty "Call of Duty")_; _[Call of Duty: United Offensive](https://en.wikipedia.org/wiki/Call_of_Duty:_United_Offensive "Call of Duty: United Offensive")_; _[Call of Duty 2](https://en.wikipedia.org/wiki/Call_of_Duty_2 "Call of Duty 2")_; _[Call of Duty 4: Modern Warfare](https://en.wikipedia.org/wiki/Call_of_Duty_4:_Modern_Warfare "Call of Duty 4: Modern Warfare")_[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_] _[Call of Duty: World at War](https://en.wikipedia.org/wiki/Call_of_Duty:_World_at_War "Call of Duty: World at War")_ (PC platform)[[402]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-activision-kb-cod-game-ports-404)|
|29000|Yes|   |||[Siemens Digital Industries Software](https://en.wikipedia.org/wiki/Siemens_Digital_Industries_Software "Siemens Digital Industries Software") license server[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2)|
|29070|Unofficial|   |||_[Jedi Knight: Jedi Academy](https://en.wikipedia.org/wiki/Jedi_Knight:_Jedi_Academy "Jedi Knight: Jedi Academy")_ by [Ravensoft](https://en.wikipedia.org/wiki/Ravensoft "Ravensoft")[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|29900–29901|Unofficial|   |||Nintendo Wi-Fi Connection[[401]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-nintendo-wfc-instruction-booklet-403)|
|29920|Unofficial|   |||Nintendo Wi-Fi Connection[[401]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-nintendo-wfc-instruction-booklet-403)|
|30000||Unofficial|||[XLink Kai P2P](https://en.wikipedia.org/wiki/XLink_Kai "XLink Kai")|
||Unofficial|||[Minetest](https://en.wikipedia.org/wiki/Minetest "Minetest") server default port[[403]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-minetest-setting-up-a-server-405)|
||Unofficial|||Foundry Virtual Tabletop server default port[[404]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Foundry_VTT_Application_Configuration-406)|
|30003|Yes|Yes|||Amicon FPSU-IP Remote Administration|
|30004|Yes|Yes|||Amicon FPSU-IP VPN|
|30033|Unofficial|No|||[TeamSpeak](https://en.wikipedia.org/wiki/TeamSpeak "TeamSpeak") 3 File Transfer[[356]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-hub.docker.com-358)|
|30120|Unofficial|   |||_[Fivem](https://en.wikipedia.org/w/index.php?title=Fivem&action=edit&redlink=1 "Fivem (page does not exist)")_ (Default Port) GTA V multiplayer[[405]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-407)[[391]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-Protocol_-_wiki.vg-393)|
|30564|Unofficial||||[Multiplicity](https://en.wikipedia.org/wiki/Multiplicity_(software) "Multiplicity (software)"): keyboard/mouse/clipboard sharing software[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|[31337](https://en.wikipedia.org/wiki/Leet "Leet")|Unofficial||||[Back Orifice](https://en.wikipedia.org/wiki/Back_Orifice "Back Orifice") and [Back Orifice 2000](https://en.wikipedia.org/wiki/Back_Orifice_2000 "Back Orifice 2000") remote administration tools[[406]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-408)[[407]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-409)|
|Unofficial|   |||[ncat](https://en.wikipedia.org/wiki/Nmap "Nmap"), a [netcat](https://en.wikipedia.org/wiki/Netcat "Netcat") alternative[[408]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-410)|
|31416|Unofficial|   |||[BOINC](https://en.wikipedia.org/wiki/BOINC "BOINC") [RPC](https://en.wikipedia.org/wiki/Remote_procedure_call "Remote procedure call")[[409]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-man-1-boinc-die.net-411)|
|31438|Unofficial||||[Rocket U2](https://en.wikipedia.org/wiki/Rocket_U2 "Rocket U2")[[410]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rocket-universe-installguide-v1123-412)|
|31457|Yes||||_[TetriNET](https://en.wikipedia.org/wiki/TetriNET "TetriNET")_|
|32137|Unofficial|   |||[Immunet Protect](https://en.wikipedia.org/wiki/Immunet "Immunet") (UDP in version 2.0,[[411]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-immunet-support-tiki-4-413) TCP since version 3.0[[412]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-414))|
|32400|Yes||||[Plex Media Server](https://en.wikipedia.org/wiki/Plex_Media_Server "Plex Media Server")[[413]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-plex-kb-201543147-415)|
|32764|Unofficial||||A [backdoor](https://en.wikipedia.org/wiki/Backdoor_(computing) "Backdoor (computing)") found on certain Linksys, Netgear and other wireless DSL modems/combination routers[[414]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-ars-security-2014-01-backdoor-dsl-416)|
|32887|Unofficial||||_[Ace of Spades](https://en.wikipedia.org/wiki/Ace_of_Spades_(video_game) "Ace of Spades (video game)")_, a multiplayer [FPS](https://en.wikipedia.org/wiki/First-person_shooter "First-person shooter") video game[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|32976|Unofficial||||[LogMeIn Hamachi](https://en.wikipedia.org/wiki/LogMeIn_Hamachi "LogMeIn Hamachi"), a [VPN](https://en.wikipedia.org/wiki/Virtual_private_network "Virtual private network") application; also TCP port 12975 and [SSL](https://en.wikipedia.org/wiki/Secure_Sockets_Layer "Secure Sockets Layer") (TCP 443).[[415]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-logmein-kb-ports-protocols-417)|
|33434|Yes|   |||[traceroute](https://en.wikipedia.org/wiki/Traceroute "Traceroute")|
|33848||Unofficial|||[Jenkins](https://en.wikipedia.org/wiki/Jenkins_(software) "Jenkins (software)"), a [continuous integration](https://en.wikipedia.org/wiki/Continuous_integration "Continuous integration") (CI) tool[[416]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-jenkins-wiki-remote-api-418)[[417]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-jenkins-wiki-auto-discovering-419)|
|34000||Unofficial|||_[Infestation: Survivor Stories](https://en.wikipedia.org/wiki/Infestation:_Survivor_Stories "Infestation: Survivor Stories")_ (formerly known as _The War Z_), a multiplayer zombie video game[_[verification needed](https://en.wikipedia.org/wiki/Wikipedia:Verifiability "Wikipedia:Verifiability")_]|
|34197|No|Unofficial|||_[Factorio](https://en.wikipedia.org/wiki/Factorio "Factorio")_, a multiplayer survival and factory-building game[[418]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-420)|
|35357|Yes||||[OpenStack Identity](https://en.wikipedia.org/wiki/OpenStack#Identity_(Keystone) "OpenStack") (Keystone) administration[[419]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-openstack-docs-config-appendix-b-421)[_[self-published source?](https://en.wikipedia.org/wiki/Wikipedia:Verifiability#Self-published_sources "Wikipedia:Verifiability")_]|
|36330|Unofficial||||[Folding@home](https://en.wikipedia.org/wiki/Folding@home "Folding@home") Control Port|
|37008||Unofficial|||[TZSP](https://en.wikipedia.org/wiki/TZSP "TZSP") intrusion detection[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|40000|Yes|   |||[SafetyNET p](https://en.wikipedia.org/wiki/SafetyNET_p "SafetyNET p") – a real-time [Industrial Ethernet](https://en.wikipedia.org/wiki/Industrial_Ethernet "Industrial Ethernet") protocol|
|41121|Yes|   |||Tentacle Server[[420]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA_41121-422) - [Pandora FMS](https://en.wikipedia.org/wiki/Pandora_FMS "Pandora FMS")|
|41230|Assigned|Yes|||Z-Wave Protocol over DTLS[[421]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-423)|
|41794|Yes|   |||Crestron Control Port[[422]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA_41794-424) - [Crestron Electronics](https://en.wikipedia.org/wiki/Crestron_Electronics "Crestron Electronics")|
|41795|Yes|   |||Crestron Terminal Port[[423]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA_41795-425) - [Crestron Electronics](https://en.wikipedia.org/wiki/Crestron_Electronics "Crestron Electronics")|
|41796|Yes|No|||Crestron Secure Control Port[[424]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA_41796-426) - [Crestron Electronics](https://en.wikipedia.org/wiki/Crestron_Electronics "Crestron Electronics")|
|41797|Yes|No|||Crestron Secure Terminal Port[[425]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA_41797-427) - [Crestron Electronics](https://en.wikipedia.org/wiki/Crestron_Electronics "Crestron Electronics")|
|42081-42090|Yes|   |||Zippin - [Zippin Stores](https://getzippin.com/)|
|42590-42595|Yes|   |||Glue - [MakePro X](https://makepro-x.com/)|
|42999|Yes||||[Curiosity](https://curiosity.ai/) [[426]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA_42999-428)|
|43110|Unofficial||||[ZeroNet](https://en.wikipedia.org/wiki/ZeroNet "ZeroNet") web UI default port [[427]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-429)|
|43594–43595|Unofficial|   |||_[RuneScape](https://en.wikipedia.org/wiki/RuneScape "RuneScape")_[[428]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rs-support-205845152-430)|
|44123|Assigned|Unofficial|||Z-Wave Secure Tunnel[[429]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-431)|
|44405|Unofficial||||_[Mu Online](https://en.wikipedia.org/wiki/Mu_Online "Mu Online")_ Connect Server[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|44818|Yes|   |||[EtherNet/IP](https://en.wikipedia.org/wiki/EtherNet/IP "EtherNet/IP") explicit messaging|
|47808–47823|Yes|   |||[BACnet](https://en.wikipedia.org/wiki/BACnet "BACnet") Building Automation and Control Networks (4780810 = BAC016 to 4782310 = BACF16)|
|48556|Yes|   |||[drive.web](https://en.wikipedia.org/w/index.php?title=Drive.web&action=edit&redlink=1 "Drive.web (page does not exist)") AC/DC Drive Automation and Control Networks [[430]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-432)|
|48656|Unofficial||||[Brainy LAB](https://brainy-lab.com/) Control Server|
|48657||Unofficial|||[Brainy LAB](https://brainy-lab.com/) Control Server|
|49151|Reserved|   |||Reserved[[2]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-IANA-2)|

## Dynamic, private or ephemeral ports

See also: [Ephemeral port](https://en.wikipedia.org/wiki/Ephemeral_port "Ephemeral port")

The range 49152–65535 (215 + 214 to 216 − 1) contains dynamic or private ports that cannot be registered with IANA.[[431]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-433) This range is used for private or customized services, for temporary purposes, and for automatic allocation of [ephemeral ports](https://en.wikipedia.org/wiki/Ephemeral_port "Ephemeral port").

Dynamic, private or ephemeral ports

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|Port|TCP|UDP|SCTP|DCCP|Description|
|49152–65535|Unofficial|No|||[Certificate Management over CMS](https://en.wikipedia.org/wiki/Certificate_Management_over_CMS "Certificate Management over CMS")[[432]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-rfc5273-434)|
|49160|Unofficial||||Palo Alto Networks' Panorama.[[204]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-EDU-120_10-206)|
|51820|No|Unofficial|||[WireGuard](https://en.wikipedia.org/wiki/WireGuard "WireGuard") protocol[[433]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-435)|
|55555|No||||Used by mac OS 11 Big Sur and later.[[434]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-436)|
|60000–61000|No|Unofficial|||Range from which [Mosh](https://en.wikipedia.org/wiki/Mosh_(software) "Mosh (software)") – a remote-terminal application similar to [SSH](https://en.wikipedia.org/wiki/Secure_shell "Secure shell") – typically assigns ports for ongoing sessions between Mosh servers and Mosh clients.[[435]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-437)|
|64738|Unofficial|   |||[Mumble](https://en.wikipedia.org/wiki/Mumble_(software) "Mumble (software)")[[436]](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_note-murmurconfig73a0b2f-438)|

## Note

1. **[^](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_ref-tcp465_87-0)** TCP port 465 was originally assigned to allow the use of [SMTP](https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol "Simple Mail Transfer Protocol") over [SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") ([SMTPS](https://en.wikipedia.org/wiki/SMTPS "SMTPS")), but practical concerns meant that it was left unused and according to the registration rules at that time was subsequently revoked and eventually re-assigned for use by [Cisco](https://en.wikipedia.org/wiki/Cisco "Cisco")'s URD protocol. Subsequently, port 587 was assigned as the SMTP submission port, but was initially in [plaintext](https://en.wikipedia.org/wiki/Plaintext "Plaintext"), with encryption eventually provided years later by the [STARTTLS](https://en.wikipedia.org/wiki/STARTTLS "STARTTLS") extension. At the same time, the subsequent adoption of the usage of 465 as an SSL-enabled SMTP submission port, even though that the original registration did not envision that usage and despite the fact that it was registered to another service has endured. Subsequently, RFC 8314, in a special exemption to the normal assignment process as defined by RFC 6335, has acknowledged the _de-facto_ situation and has designated SMTP over TLS as an 'alternate usage assignment'.
2. **[^](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_ref-126)** Deployment typically occurs only directly over UDP, but other underlying protocol layers which meet the requirements described in the specification are possible.