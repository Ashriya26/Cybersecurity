Protocols

-Its a set of rules and messages that form an Internet standard
- Eg : ARP-> resolves IP to MAC mappings
- This has ARP request and Response-> these was a need to design how these request and response is, this is done by RFC 826
- RFC 826: An Ethernet Address Resolution protocol: this protocol allows dynamic dist. of info needed to build tables to translate an address in protocol p's address space into a 48 bit ethernet address

1. FTP( file transfer protocol)
   - allows client and server to send and receive files from wach other
   <img width="283" height="132" alt="image" src="https://github.com/user-attachments/assets/1f33a128-f68f-4813-951c-f7b0d2d76a79" />

2. SMTP (Simple mail transfer protocol)
   - email servers use to exchange emails
     <img width="290" height="135" alt="image" src="https://github.com/user-attachments/assets/fef76312-f78e-4843-896d-261d8d29a5a3" />

3. HTTP ( Hyper Text Transfer Protocol)
   - used while communicating between the websites, ( exchnaging the HTML pages)
   <img width="299" height="62" alt="image" src="https://github.com/user-attachments/assets/e11af174-5d3d-42be-abfc-c5d1ca795bdf" />

4. SSL ( Secure Sockets Layer)
5. TLS ( Transport Layer Security)
  - These 2 help build a secure tunnel between the client and the server, and then they can do the http communication within the tunnel
6. HTTPS( HTTP secured with SSL/TLS)
  - allow http to run within the secure tunnel created by SSL or TLS
<img width="295" height="52" alt="image" src="https://github.com/user-attachments/assets/353449d8-47a8-49de-a698-6f71bc59f70b" />

- For a host to communication with another host, it must have an IP address
- If its an FTP server, it has an IP address, so it can communicate with it directly
- But what abt SMPT(where its email) and http and https(where its a site's address)(domain names)?

7. DNS - Domain Naming System : converts Domain names to IP address
   - The Host asks for IP address for a particular site from DNS server and the server responds to it. This IP address can be sent to the Web server and continue the communication
   - Not just the Domain name, DNS also resolves the email address to an IP address and then passes it back to the host, where it can then communicate with the SMTP server directly( send mail) using this IP address

---> every Host needs 4 items for internet connectivity:
i. IP address ( 9.1.1.11)- host's identity on a network
ii. Subnet mask (/24,/16,/8)(255.255.255.0)- size of host's network
iii. Default Gateway(9.1.1.1) - Router's IP address
iv. DNS server IP (8.8.8.8) - translate domain names to IP address

- u basically dont have to do all these stuff manually bcz all these things are happening as a part of another protocol automatically (DHCP protocol)

8. DHCP ( Dynamic Host Configuration Protocol)
   - provides IP/SM/DG/DNS for clients
   - Whenever u try to connect to a wi-fi or non wi-fi network, the host first sends a DHCP discover message, and in response, the DHCP server will offer these 4 things
   
     <img width="434" height="184" alt="image" src="https://github.com/user-attachments/assets/b19e6883-9ccb-4241-bce0-e5d2b0c100a3" />



IPv4 (Internet Protocol version 4)

- communication in network layer is host to host
- The host in 1 network would want to communicate with another host in some other network and at some other part of the world, in such situation, the 2 hosts communicate over the internet using logical addresses called IP address
- IP addresses can be 32 bit( 2^32 addresses-> IPv4) and 128 bit(2^128 addresses-> IPv6)
- IPv6 provides much more flexibility in address allocation in a packet switched computer network
- The data packets in the network layer is called a datagram ( 2 types-> IPv4 and IPv6 datagrams)
  <img width="297" height="231" alt="image" src="https://github.com/user-attachments/assets/3642fb96-56e5-402e-bab2-bac92f612e0b" />


i. Ver ( version number)
- 4 bit
- specifies if the datagram is of version 4 or version 6
- based on the version, there are different ways in which the datagram is processed bcz different versions use different datagram formats
- This will tell the IP software present in the system how to process the datagram

ii. HLen(headder length)
- 4 bytes
- it gives the length of the header fields, with 4 bytes/word
- If HLen is 5, it means header is 5 words*4 bytes=> 20 bytes in length

iii. Option
- Variable in length
- If option field is empty, i.e the HLen is of 5 bytes(0101). Therefore total length-> 5*4=20
- If option field is filled, the Hlen would be of 15(1111). Therefore total length-> 15*4=60 bytes
- Therefore the length of the header field of a data gram varies from 20-60 bytes

  <img width="381" height="225" alt="image" src="https://github.com/user-attachments/assets/addbdfc2-b09a-4485-a52f-d88631ce29a8" />

iv. Data(payload)
- The length of the header determines where the data would be present in a datagram
- The data of the datagram is called a segment of the transport layer

v. DS(differentiated services)
- 8 bits in length
- divided into 2 parts( first 6 bits-> Differentiated services code points(DSCP) and the next 2 are called ECN( Explicit congestion notification)
- since code points are 6 bit in length, there can be 2^6-> 64 diff bit combinations
- These bit combinations help classify the IP addresses and prioritize 1 IP over other( for eg, Network Management IP address is of higher priority than that of
Audio, video IP address)

vi. Datagram length:
- gives the entire length of the datagram ( data+header)
- its normally of 16 bits-> 2^16-1=> 65535 bytes
- This is rarely > 1500 bytes which allows the IP datagram to fit in the payload section of the Ethernet frame
- The size of the payload in the ethernet frame varies from 46-1500 bytes


----> IP Fragmentation:
- Suppose a datagram is of 4000 bytes, the header is of 20 bytes, so the data would be of 4000-20=3980 bytes.
- But the thernet frame max length is only 1500 bytes
- For this reason we will ahve to break down the Larget IP address to smaller fragments(1400+1400+1180)


vii. Identifier:
- The fragmented IP packets are identified by Identifier field
- When the IP datagram is created it will be given a certain value
- This value keeps incrementing for every new IP datagram
- If a datagram is given a value of X, then all its fragments created too will have an Identifier of X  (not X+1, X+1 is for another IP datagram)

viii. Flag:
- 3 bits( only 2 bits are used
- "D"-> Do not fragment: 1-> IP datagram SHOULD NOT be fragmented, 0-> CAN be fragmented
- "M"-> More fragments: 1->indicates that the datagram is not the last fragment, 0-> either the last fragment/the only fragment

ix. Fragmentation offset:
- 13 bit
- Now these fragmented offsets are identified to which datagram they belong to,
and also have their flag, but how do we decide which order should these datagrams be combined so as to give the correct resultant datagram-> this is done by Fragmentation offset
- It gives the relative position of the fragment WRT the whole datagram
- this way it will find the correct order to create the original datagram
  <img width="430" height="235" alt="image" src="https://github.com/user-attachments/assets/18773b85-be35-43d8-a793-6fb3a5f5a17b" />

NOTE: 
IPv6 DOES NOT allow IP fragmentation


x. Time-to-live
-limit the time of an IP datagram as it travels through the host to the internet
- At the beginning, the host sets a value on the datagram and on every hop (from to host to another router or to another host or anything), it will decrease the value by 1.
- If this value becomes 0, the router discards this IP datagram
- This prevents the router table corruption due to the circulation of datagrams for a longer time among the routers


xi. Protocol:
- when the data reaches it destination, the value in the protocol determines to which transport layer protocol the data of the IP datagram must be passed
- Eg : 6-> passed to TCP, 17-> UDP, 1-> ICMP, 2-> IGMP, 89->OSPF

xii. Header checksum:
- 16 bit
- helps in detecting bit errors in the IP datagram headers

xiii. Source and dest IP address:
- represent the IPv4 address of the source and the destination host resp.


--> While the host A sends an IP datagram to Host b, the IP address contains Host IP+ dest IP and the data is the segments of the transport layer which would also contain the ICMP message



IPv6 (Internet Protocol version 6):



- Most recent verion of IP protocol ( developed by IETF( internet engineering task force)
- it was intended to replace IPv4
- 128 bit address
- Why IPv6?--> IPv4 was created in early 80s and support limited access and time
           - as time passed the internet usage surged leading to teh creation of IPv6
           - This increases the limit upto  abt 3.6 * 10^38 addresses


Representation:
- 128 bits in length(hex format for address)
- acc to RFC4291: IPv6 format is as below
           X   :  X  :  X  :  X  :  X  :  X  :  X  :  X
           |
       16 bits ( 4 HEX digits)
- to make it more readable: it uses 8 sets of 4 HEX digits separated by ":"
  <img width="311" height="36" alt="image" src="https://github.com/user-attachments/assets/ecf8dcaa-2493-4e3e-a340-f8358476c7a6" />


Abbreviation of IPv6 addresses:

IPv6 address can be quite long, so they can be shortened 

<img width="356" height="78" alt="image" src="https://github.com/user-attachments/assets/7dd83a64-55f4-4a13-9f3a-79fd2f4a1b2f" />
<img width="258" height="166" alt="image" src="https://github.com/user-attachments/assets/091ce170-44dd-4768-941a-2bec2632a407" />

Features:
- larger address space ( 3.4 * 10^38 combinantion of addresses)
- SImplified header
<img width="261" height="166" alt="image" src="https://github.com/user-attachments/assets/6c9b0359-c3ae-41dc-bb4a-d4206e0cb7d3" />
- end-to-end connectivity: No Network Adress Translatio (NAT) required
- Auto-configuration: allows both stateless and stateful auto-config of its host devices, this way the absence of DHCP server dosnt put a halt on the inter segment communication
  <img width="216" height="127" alt="image" src="https://github.com/user-attachments/assets/8f59c5ef-fb9a-4c78-a9e6-59ea022c6911" />
-Faster Forwarding/Routing: the simplified header put all the unnecessary details towards the end with only the necessary info on the top, the routers can process this data faster and thus transport it effectively
-IPSec : It was previously decided that IPSec must be present in IPv6 making it more secure than IPv4( now its been made optional)
-No broadcast: uses multicast communication to connect to multiple hosts
<img width="193" height="172" alt="image" src="https://github.com/user-attachments/assets/8336af25-871c-4599-b2a9-d4a584f7202a" />
-AnyCast support: router while routing send it to the nearest destination(different from multicast and broadcast)
-Mobility: allows host to move around the globe and still be connected with the same IP address. makes use of auto IP config and extension header
-enhanced priority support: traffic classes and Flow labels tells the user how to efficiently access the packet and route it
- Smooth transition: large IP scheme, Globally unique IP address, NAT not req., header is less loaded, Forward them as quickly as they arrive
- Extensibility: We can add more info in the option part this is present between the header and the data segment
  <img width="333" height="186" alt="image" src="https://github.com/user-attachments/assets/03741e82-9784-417d-8cea-3e8c280bd165" />



Public Vs Private IP addresses:

Public IP:
- its uniques
- assigned to the device by the Internet service provider
- This is the address that the entire internet service uses to connect to u
- Its the 1 address that the world sees
- If ur hosting a website or a gaming server, this is the address that other ppl use to connect with u directly
- they r directly exposed to the internet making it vulnerable to attacks

Private IPs:
- Only used within ur local network
- It is assigned by ur router using DHCP and is not visible to the internet
- Since they r isolated, they add an extra layer of security
- Hackers cannot access ur network without first breaching ur router ( acts as gatekeeper)


----> y do we need 2 types:
- if everything had its own IP like TV, mobile etc, we would run out of IP addresses
- Private IPs helps us to conserve those limited public IPs using NAT( network address trnaslation)
- the router uses this to convert private IP to public IP

  

 Subnetting:

- Subnetting is the process of breaking down larger network into smaller, more manageable subnetworks or subnets
- By breaking down the network, it helps efficienty allocate IP addresses
- Improve performace by reducing network congestion
- Improves security by isolating different parts of the network
- It also allows administrators to better manage and contrale access within different areas of a network making it easier to troubleshoot and maintain
- Each subnet works independently, but still remains a part of the larger network thus enabling efficient communication between the networks

 
IP addresses and sub net masks:

-It is a unique number assigned to every device
This allows to identify amd locate teh evice within a network or across the internet
- IPv4 and IPv6

Subnet masks:

- they r a crutial companion of IP addresses
- they determine how addresses are split btw the network and host portion
- Its normally written in the similar pattern of IP address
- It shows how much of the IP address belongs to the network and how much of it belongs to the device

IP address classes:

- categorizing the IP address based on their intended use and range inordeer to provide a structured method to allocating address within the network
- class A- (1.0.0.0 - 126.0.0.0) Very large networks- 16 million hosts- major org and ISPs
- class B- (128.0.0.0-191.255.255.255) medium size entworks- 65 thousand hosts-universities and larger businesses
- class C-(192.0.0.0-223.255.255.255) smaller size networks- 254 hosts- smaller org and houses
- class D- (224.0.0.0-239.255.255.255) multicast groups-allows single packet to be sent to multiple hosts-useful in streaming media and conference apps
- Class E- (240.0.0.0 - 255.255.255.255) reserved for R&D for advance networking protocols
- Loopback addreses -(126.0.0.0-128.0.0.0) - this allows to devices to communicate with the host without requiring an external network- most commonly used in this range is -> 127.0.0.1( refered to as local host)

- This is useful for efficient design and management and lao allows the admin to allocate the IP addresses acoording to the specific needs of their networks)


SUbnetting calculations:

NOTE: the number of 0's in the subnet mask determines the number of possible hosts
- possible addresses: 2^n ( where n is the number of 0s)
- usable addresses : 2^n-2 ( 1st one is reserved for network ID which helps identify teh subnet and the last is reserved for broadcast addresses used to send datat to all devices in the subnet
- the more the 0s, the more number of hosts that can be supposed in that subnet
- more no. 1s=> more subnets and less hosts
- more no. of 0s=> more hosts and less subnets
- To calc no. of subnets: 2^m (m-> no. of bits borrowed to from the host portion to create subnets)-> if u broow from the host bits, it will reduce the number of hosts but increase the number of subnets allowing for a more structured layout
<img width="457" height="198" alt="image" src="https://github.com/user-attachments/assets/17a5b4ef-483a-420d-bab8-392b074cb356" />


Reading and interpretting subnetting:

-includes classifying Network, and broadcast addresses and address range
- common way is CIDR ( classless Inter-domain Routing) notation-> combines the IP address with suffix which will indicate the number of network bits in a subnet msak
<img width="263" height="100" alt="image" src="https://github.com/user-attachments/assets/13d14fb7-2eb3-4a19-b182-2170dcf4df87" />
- helps us understand how network is segmented inorder to organize and allocate IP addresses efficiently
<img width="451" height="201" alt="image" src="https://github.com/user-attachments/assets/02f4bd97-25b4-4b59-ab6a-e7abbb7cd048" />


Common Subnetting scenerios:

- breaking down larger network into smaller ones inorder to maintain, increate security and reduce traffic
- Eg : Internet is divided for the Engineers, admins and Guests to prevent leekage of confidential datat into the internet
- Partition based on geographical locations enabling remote office to communicate efficiently while maintaining separation from the main corporate network
- to accomodate growth: as no. of devices increases, they can easily craete new subnets without inturupting the entire network structure
- The Internet Service Providers (ISPs) breakthem into subnets to manage their IP address space more effectively, distributing ranges to customers while maintaining optimal utilization and preventiong network wastage
  

Classful Vs Classless subnetting:

Classful:
- they r divided into classes(A-E)
- they have predefined subnet mask and address range
- limits flexibility and allocating address spaces
- This rigit structure allowed efficeint use of IP addresses specially by smaller networks that didint need the the large no. of addresses assigned by the class system

Classless:
- CIDR
- more flexibity by allowing u to chosse the no. of bits for the network portion of an IP address, rather than fixing it to a particular range
- This allows efficient allocation of IP address, minimized waste and increase scalability by allowing org. to create subnets according to their needs
- CIDR->Increases the router efficiency by reducing the size of the routing tables, making it more useful in modern networks


Pitfalls and Best practices to increase network efficiency:

- must maintain clear docs abt the assigned IP addresses, subnet masks and the purpose of each subnet
- Networks must be designed with scalability in mind so that u dont alster the entire network structure as no. of devices increases
- regurlary revieving teh address allocations prevents conflicts and allows efficient utilization of IP address space
- By this network admins can reduce errors, make it managable and flexible and also increase performace

<img width="212" height="308" alt="image" src="https://github.com/user-attachments/assets/05eb2c00-35d7-486d-8f62-51626c782b48" />
<img width="202" height="288" alt="image" src="https://github.com/user-attachments/assets/8579c142-b90a-4a14-befa-744531bd26fe" />


CIDR ( Class Inter Domain Routing):

-if ending with /24-> u can create 256 IP addresses
- 11.0.0.0/16 -> /16-> 65.536 IP addresses
- 11.0.0.0/8-? /8=> 16.777.216 IP addresses
- As the number decreases, no.of possible IP addresses increases
  <img width="122" height="65" alt="image" src="https://github.com/user-attachments/assets/db07a2df-2a7d-453d-beeb-82317f1c35f1" />
  <img width="68" height="131" alt="image" src="https://github.com/user-attachments/assets/d809790e-6ab4-47ba-baa5-fc76ca06364e" />
  
--> 16 possibilities of IP addresses
<img width="307" height="19" alt="image" src="https://github.com/user-attachments/assets/2a68ad68-b34b-4c87-87dd-4c4bf13d6bbc" />


How to create VPC and subnets:
- A VPC can contain multiple private and public subnets within it, here for illustration, 1 private and 1 public is used( depends on business requirement)
- VPC has higher no. of IP addresses compared to subnets( cannot be grater than VPC)
  <img width="317" height="190" alt="image" src="https://github.com/user-attachments/assets/e52d7e3c-a00f-4071-9ac6-548e7aa9741e" />

Diff btw hub/switch/router
<img width="459" height="229" alt="image" src="https://github.com/user-attachments/assets/aa2dea74-4ff0-4148-bc14-be1eb2d1d09b" />

Gateway:
- connects 2 networks using different protocols together
- Also connects t different networks( acts as a gate between 2 networks)
- --> router, firewall or other devices enable traffic to flow into and out of the network

<img width="438" height="250" alt="image" src="https://github.com/user-attachments/assets/a63a295f-29ed-442c-bc1e-46a4bed9c0b1" />
-here is acting as a gateway that will allow the network to flow into and out of the server

<img width="459" height="252" alt="image" src="https://github.com/user-attachments/assets/dbd9744a-e7ca-4a07-a262-7ed81f239f92" />
here, router is acting like a gateway


Use of Gateway in a network:
- Router can communicate with 2 different networks using the same protocols
- The gateway is a network node that connects 2 networks using different protocols
- The gateway is also called a protocol converter
<img width="393" height="200" alt="image" src="https://github.com/user-attachments/assets/3bc0bed4-396b-4150-bc4f-91b8c7d3a918" />


NAT ( Network Address Translation):
- used in outers
- translate a set of IP addresses to another set of IP addresses
- Help preserve the limited amt of IPv4 public IP addresses
- When Engineers created IPv4 they didnt realize that the Internet would boom in the future, so they developed private IP addresses and NAT
-  2 types of IPv4 addresses: Public and private
-  Public: (66.94.234.13)-publicly registered on the internet and must have public IP to access the Internet
-  Private: ( 10.0.0.1) - not publicly registered, only used internally and cannot access the internet directly using private IP
-  Eg: In our house we have multiple devices that need internet access. For each of these devices, we could ask the ISP to provide Public IP address to access the common network, but this would be unnecessary, more expensive and leads to wastage of IP addresses.
-  Instead, the ISP will assign a public IP to the router. The the router can assign Private IPs to the devices in our home and when it wants to access the network, these private IPs would be passed to the router where the NAT in the router will convert this private IP to that public IP of the router and then access the internet
---> NAT translates a set of IP addresses to another set of IP addresses
-NAT translates : private to public and vice versa
----> In the future, we wouldn't want NAT or private IP addresses bcz of IPv6, bcz of which each device will have its own public IP address, so no need of IP translation


MAC(Media Access Control) Address:(physical/hardware addresses)
- its an identifier that every network device uses to uniquely identify itself in the network
- no 2 devices will have the same IP address
- made of 6 byte hexadecimal number burned into every NIC(Network Interface Card)
- divided into 2 parts
- <img width="396" height="124" alt="image" src="https://github.com/user-attachments/assets/71d65f57-3f73-447c-8e60-8e0a9c3fb52c" />
- Representation:
  <img width="379" height="130" alt="image" src="https://github.com/user-attachments/assets/a0d978f5-d3f5-4395-a16e-0c3e5d0a77fa" />
- Purpose: network devices can communicate with each other
- If Mac address is used for communication, whats the use of IP addresses? even they help in communication. But the private and public IPs can change periodically, but an NSP/ISP can change this address unlike MAC which is permananent
- A networking device needs both mac and Ip address. the IP address is used to locate a device( like address of a house ) and a mac address is used to identify a device( name of the people in the house)
- ARP
- DNS
- If the networks r not the same, it will end the data to the default gateway(router) and that will continue its work
<img width="439" height="179" alt="image" src="https://github.com/user-attachments/assets/2a3c3e9e-adc9-4478-ae23-3c02c2eb27a6" />

- to check an mac address in windows-> ipconfig /all (in mac and linux-> ifconfig)
- a device can have multiple MAC addresses, it depends on how many network interfaces it has
  <img width="442" height="260" alt="image" src="https://github.com/user-attachments/assets/7936b80d-51e4-4ad2-a959-9db747707293" />



