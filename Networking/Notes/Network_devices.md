Network devices

1. Hosts : 

-any device that send or recieve traffic
-Eg : Computer, laptop, phones, printers, servers, cloud servers, lights,       refrigerators, speakers, TV, thermometers etc
- 2 types:
  i. clients : initiate requests
  ii. servers : responds to requests : they r simply computers with software installed which responds to specific requests
  - Client-server is relative to specific communication

2. IP address:

   -identity of each host
   - required to send information over the internet (packets over a network)
  Eg : a computer would ask for information from the server. 
      - while doing so, the computer would send a packet consisting of 2 IP addresses, 1 of source and one of the destination, in the similar manner, when the server send the reply through a packet, it would again contain 2 IP addresses, one of source and other of destination.
     - IP addresses are 32 bits
     - represented as 4 octets ( smallest number obtained from the octet is
       '0' -0000 0000 and the largest is '255'-1111 1111)
     -represented as 0000 0000.0000 0000.0000 0000.0000 0000
                      [0-255]   [0-255]   [0-255]   [0-255]
 - Its hierarchically assigned      
 <img width="335" height="190" alt="Screenshot 2026-10-06 204008" src="https://github.com/user-attachments/assets/92470726-9d63-4e92-91bc-46fe189fe031" />

3. Network:

   - transports traffic between hosts
   - Anytime 2 hosts are connected, u have a network
   - before networks: transferring data btw hosts required portable media (disks, thumb drives etc)
   - logical grouping of hosts which required similar connectivity
     Eg: ur home laptop, TV etc are connected to ur home Wi-fi
   - Networks can contain other networks (Sub-Networks or Subnet)
     Eg : A school as a whole would have its own network, and each classroom  within it would have different networks to which the hosts are connected to
   - Network connect to other networks -> Internet


4. Repeater:

   -data passing through the wires end up decaying as it travells and this would cause a problem when it has to travel longer distances
   - In this case, the repeaters become handy, where its main purpose is to regenerate signals and allow spanning over grater distances



   ----> If there are multiple host, then each host must be connected to every other host over the network to facilitate communication between them. For this, instead of this way, we can connect all these hosts to a common device, so that if any extra device is added to that network, it can simply be added just to that device rather than connecting to all the other devices. These r the Hubs, bridges and switches.

5. Hub

   - its a multi-port repeater
   - Eg; If any 2  hosts want to communicate, the host would send a packet and the hub would duplicate it and communicate it to all the other hosts over the network
   - facilitates scaling communication between additional hosts
   - everyone receives everyone else's data
   - <img width="311" height="93" alt="Screenshot 2026-10-06 210849" src="https://github.com/user-attachments/assets/da5dc11a-0414-477c-a272-5f60ff31c888" />

  
6. Bridges

   -there would be 2 sets of hosts interconnected with the hubs
   -the bridges sit between the hub-connected hosts
   -bridges have only 2 ports
   -bridges learn which host is on which side
   -it helps contain packets only to its relative networks
   -if 2 hosts within the same port want to communicate, then the bridge will not let the signal leak into the other port.
   -likewise, if a host from 1 post wants to communicate with the host of another port, the bridge recognizes it and allows communication.

<img width="316" height="129" alt="Screenshot 2026-10-06 210839" src="https://github.com/user-attachments/assets/07070a77-5adb-4342-ae9c-fbe046883f9c" />

7. Switches:

   - Facilitate communication within a NETWORK
   -its a combination of hubs and bridges
   -has multiple ports
   -learns which host is connected on each port
   -(bridge and hubs are kind of broadcasting models, but switch is confined, it allows communication only between 2 specific hosts and dosnt leak the data to other hosts)
   -hosts on a network share the same IP address space
  - Switching is the process of moving data within networks

<img width="353" height="159" alt="Screenshot 2026-10-06 210825" src="https://github.com/user-attachments/assets/e15e15d9-6562-42e6-a114-3e6c2427c1e5" />

8. Router

<img width="334" height="183" alt="Screenshot 2026-10-06 211200" src="https://github.com/user-attachments/assets/447755e5-9ebb-43e6-adbc-bfb5078912fb" />

   -Handles communication between networks
   - provide traffic control point(security, filtering, redirecting)
   - routers learns which networks they are attached to
   - These r routes and they r stored in a routing table( all the networks a router knows abt)
   - every router has an IP address in the network they r attached to.
   - This acts as a GATEWAY ( a hosts way out of its local network)
   - Routing is a process of moving data between networks
   - Router is a device whose primary purpose is routing
  <img width="341" height="171" alt="Screenshot 2026-10-06 211711" src="https://github.com/user-attachments/assets/2527937f-e65b-4ccc-a646-653d6d59f9aa" />

   -they create Hierarchy in networks and entire Internet
   <img width="345" height="199" alt="Screenshot 2026-10-06 211843" src="https://github.com/user-attachments/assets/03eb8037-a83c-4f3b-ba8c-8f0d61a9da1e" />


NOTE:

-Layers: hubs and repeaters work at Layer 1 (bits and signals), bridges and switches at Layer 2 using MAC addresses, and routers at Layer 3 using IP addresses. Switches and bridges learn MAC addresses, which are stored in a MAC address table.
-Domains: a hub puts everything in one collision domain. A switch gives each port its own collision domain. A router separates broadcast domains.
-Security link: hubs let anyone on the network sniff everyone's traffic, which is part of why switches replaced them.




**Everything a host does to speak on the internet:**

2 scenerios:

Case 1: Hosts connected directly to each other
- on the same network
- Its irrespective of if there are hubs or switches between the hosts
- both have NIC Therefor have MAC address
- Both have IP address and a subnet mask (SUBNET MASK-> identifies the size of the IP network)
- Host A has some data and also knows the IP address of host b(mayne by typing : ping 10.1.1.33)
- Host b knows the IP address of host A(maybe it acquired it from DNS( DNS converts a domain name to IP address)(eg: www.abcd.com----> 192.249.124.38)
- Host A also knows its very own IP network
- Host A creates a L3 header 
- host A doesn't know the Mac Address of host b, so it uses ARP
- The host A will shoot a message saying..if anyone has IP address of 10.1.1.33, send me ur mac address, my IP/MAC is 10.1.1.22/a2a2 --> this would have a L2 header but it wouldn't have the destination mac address----> sent as a BROADCAST
- Broadcast: sent to everyone on the network
- ARP mappings that r got are stored in ARP cache
- the host 2 maps the IP address and the MAC address got from host A and send a packet containing host B's IP and MAC address to host A(UNICAST-> response sent directly to host A)
- Then host A populates its ARP cache with the Host B IP and MAC address
- Now as host A has all the details required, the data passed on to L2 would be sent to HOST B
- Host B now has all the necessary information, so it send the data faster to the Host A
  <img width="448" height="111" alt="image" src="https://github.com/user-attachments/assets/28d8b6fb-2d72-461d-ac6e-4c0d9af9c1e6" />

  <img width="451" height="100" alt="image" src="https://github.com/user-attachments/assets/41ebf017-f8a8-46fb-a8d2-eed088e507c5" />



Case 2: Hosts connected through a router
- in a foreign network
- Both have MAC and IP address(/24 is a subnet mask-255.255.255.0)
- Anything with an IP address would have an ARP cache
- Host A knows IP address of host B(provided by the user or the application)
- Host A also knows that the Host b is on the foreign network as it just compared its own IP address with the Host B's IP address
- Host A will create a L3 header
- Host A will broadcast the ARP message and the router will receive it
- But, how will Host A know the IP address of the router? it will use the ARP to resolve the MAC address of router's IP---> routers IP is configured as a default Gateway
- By this Host A will shoot an ARP request to Router, and the the router will send back a response consisting the MAC address
- Now the Host A has the complete data
- This is then sent to the router
- The router will add the L3 and L2 levels as required and then it would send it the same way to the Host B
- ARP mapping can be used for ANY host in foreign network

<img width="446" height="148" alt="image" src="https://github.com/user-attachments/assets/9e77222f-cdb2-4178-b7dc-eff1188d545b" />

Summary:

The first step of sending the data is always the same
-Determine if the Target IP is in local/foreign network
- If local: ARP for target IP
- If foreign : ARP for default Gateway IP


**Everything Switches do to facilitate communication**

-switching: process of moving data within networks
-Switches are devices whose primary purpose is switching
These communicating devices belong to the same IP
- Switches look only into the Layer 2 headers, and it donst look ino layer 3 header
- So u dont need anything related to IP
-Switches maintain a MAC address table which maps a port to its particular MAC address
- Switch perform only 3 actions:
        - Learn : Update MAC address table with mapping of Switch Port to Source MAC
Meaning: the host A will send out the data consisting of source and destination, the switch will update the MAC Address table with the Port of this host and its corresponding MAC address
        -Flood :Duplicate and send Frame out to all switch ports(except the recieving port)
Meaning: Now the switch has the data. But it dosnt know which dest. host has that particular MAC address. so it will broadcast it out to all the hosts. The hosts look at the dest. mac address, and if it not their mac address, they just discard it, and it would be kept only by that Host of the intended MAC address.
        -Forward: Use MAC Addess Table to deliver frame to appropriate switch port.
Meaning: The Host B, which was intended to receive the message, then forwards the reply to the source. As the MAC Address table now has the MAC address of the  source port, it will just send the reply to the source

<img width="320" height="117" alt="image" src="https://github.com/user-attachments/assets/d0776b5a-a936-4c75-bd78-d95c8dc9e48e" />

<img width="360" height="87" alt="image" src="https://github.com/user-attachments/assets/3819912c-5d8b-4902-83a7-d46163a5aed2" />
So anymore if host A and B have to send any kind of data to each other, they can send it directly, without doing the flooding action
- the process would be identical if Host D was a router connected to the internet
- If u want to send/recieve data to the switch, then the switch must have a MAC and an IP address and the switch would act as a host
- If ur sending it through a switch, then the MAC and IP address for the switch is not required

-> Unicast frame : Destination MAC is another host( 1 to 1 communication)-floods only when the dest. MAC address is not known
-> Broadcast Frame: Destination MAC address of FFFF.FFFF.FFFF( specially reserved mac address which shows that this data must be delivered to all hosts on the local network)-They r always flooded

NOTE:
-swicth dosnt broadcast anything
- Broadcast is a type of frame
- flood is a switch action
- switch will only send broadcasts if traffic is going to and from the switch. If its through the switch, then it dosnt Broadcast, it floods

-> VLANs(virtual Local Area Network)
- divides switch ports into isolated groups
- divides switches into multiple "Mini-switches"
- switches do all 3 individual actions within each VLAN
  <img width="227" height="88" alt="image" src="https://github.com/user-attachments/assets/be254492-0f78-4293-94b8-ee9249d0a33c" />

-> Multiple switches:

<img width="361" height="83" alt="image" src="https://github.com/user-attachments/assets/c2ae478a-2f51-44c8-8ab8-93ce4c1949e4" />

- There can be multiple switches for this action.
- here, both these switches have their own MAC address and also perform tasks independently
- Now Host A will send a Frame to the switch
- The switch will learn the Host MAC and save it in the table but it dosnt know the dest. MAC , so it will flood it, which as a result will go to the 2nd switch.
- This switch, will now have the source and again, this switch too dosnt know the dest. so it will flood the frame to all hosts, thereby reaching the intended host.
(in this process, when switch A floods, it will send it to host C too, but it will ignore it as host C MAC addres != desc MAC address, and the same happens when the switch 2 sends the data to host D and host B, Host D ignores it)
-Now the response is sent from the host B to Host A by the forwarding action and no need of flooding as it already has the data in its MAC Address table.

<img width="375" height="90" alt="image" src="https://github.com/user-attachments/assets/da33e806-0886-441b-9434-5ef7852d4370" />



**Everything Routers do to facilitate communication**

-Routers have an IP address and a MAC address
--> difference between hosts and routers
    It comes from the IPv6 RFC(request for comments)-docs that defines internet standards
    RFC 2460: Internet Protocol Version 6(IPv6) specification:
    -Node : a device that implements IPv6
    -router : a node that forwards IPv6 packets not explicitely addressed to itself
    -Host: any node that is not a router
    Router must have an IP and MAC address on each network(it cantmaintain a single IP/MAC for all networks)
- routers maintain a map of all the networks they know abt : Routing table

<img width="431" height="96" alt="image" src="https://github.com/user-attachments/assets/adf9b271-0bee-472a-846e-29899320a3eb" />

Routers can be populated by 3 methods:
i. Directly connected: routes for the networks which r attached
  - Here, the router is directly connected to the networks
  - The routers will maintain a routing table for the either side of the network
  - for the left, router will add the IP of the left side of the router and vice versa
  - In this img, there r 2 routers and each of them have their own routing tables
  - When Host A send a packet, the router will first check for the destination IP, and if that IP is present in its table, it will just forward it to the designated host
  - But if Host A sends a packet, and the destination is not repesent in the routing table of the particular router, it just DISCARDS it

<img width="431" height="146" alt="image" src="https://github.com/user-attachments/assets/64f69013-e28a-4fe2-a25e-c93199f44140" />

ii. Static routes: routes manually provided by an administrator
  - This helps resolve the issue of, if the mapping is not present in the routing table, it will be discarded.
  - for this, u can log into router 1, and adding the details of the router and the IP to which the packet must be pushed to(addede manually)
  - Bcz of this, even if the value is not present in the routing table, it would be added by the admin manually, so the packet would move to its intended dest without any issues
  - even during the reply from the Host 2, u can insert the routing values in the R!s routing tbl regarding the Router IP and also the destination IP from that router. This will allow the packet to be delivered without any issues
    
  <img width="427" height="141" alt="image" src="https://github.com/user-attachments/assets/bfab7f9d-a4a7-4b78-be6d-e2ffa837f7f2" />

iii. Dynamic routes: routers learned automatically from other routers
    - The routers communicate with each other inorder to reach their designated destination
    - The R1 would tell R2 that it knows abt 10.0.55 and 10.0.44, and the R2 would tell R1 that it knows abt 10.0.66 and 10.0.55 but not abt 10.0.44
    - so it will add it to the R2s table. So anything thats to be sent to R1s related host, R2 will directly send to R1 and then R1 will send it to designated host and same vice versa
    - The only difference between static and dynamic is the way in which its learnt
    - The exact methods that the routers use to communicate with each other is governed by different Routing Protocols -> RIP, OSFP, BGP, EIGRP, IS-IS

<img width="422" height="141" alt="image" src="https://github.com/user-attachments/assets/343df70b-8a60-4957-b3b7-0edade9ffd2e" />

- routers also have ARP tables ( mapping of L3(IP) and L2(MAC) address)
- ARP tables are initially empty and would be populated as needed with the network traffic
- But Router table must be populated ahead of time
  
<img width="455" height="114" alt="image" src="https://github.com/user-attachments/assets/98de1ccf-8a60-4add-a328-a91c538e4f79" />

Working:

Part 1: Host A to Host C:

- host A has the data to be sent to host C
- L3 header is added to this data, and it would have its own IP address and also the IP Address of the dest. Host
- Now, comparing its own IP address and the IP address of teh dest. it knows that the network is present in a different network so it would need to send the packet to the default Gateway(which is R1)
- Now, Host A dosnt have the MAC address to pass the packet-> cannot construct L2 header-> no ARP entry for Gateway's IP Address(R1)
- The Host A will now send an ARP request requesting for the MAC address, by proving its very own IP and MAC addresses-10.0.44.1.
- This then reaches the R1, bcz of which the R1 now has the values required of the source IP and MAC, so it will add it in its ARP table-populates with entry for 10.0.44.9.
- The router will respond to this message with its own IP and MAC addresses.
- so Host A will populate the ARP table with entry for 10.0.44.1
- Host A will send this entire packet and all data to the router
- R1 receives this packet and discards the L2 header
- R1 looks up the destination IP in routing table-> packet's next hop is to 10.0.55.2
- Since there is no MAC address available, it will send the ARP requiest and awaits for the response
- R2 populates its arp table with entry for 10.0.55.1 and sends a response
- R1 will populate its ARP table with entry for 10.0.55.2
- Now the packets r sent from R1 to R2 and L2 header is discarded
- The R1 finds the appropriate IP address in the routing table(r2), but no MAC address. SO it will send out an ARP request.
- Then the Host will respond with its MAC address( 10.0.66.7-> c7c7)
- The router now has the MAC and IP address so it will send the required data to the host
- The host C will discard the L2 header, L3 header and then it processes the data
<img width="450" height="117" alt="image" src="https://github.com/user-attachments/assets/04cf4278-3149-4678-8c6c-2bc6e997439d" />

  PART 2 : response from Host C to Host A

-faster bcz the values r already populated in the ARP table
- Host C has the data and creates the L3 header and as it already has the data required in the ARP table, it will directly add the L2 header inorder to send the data and send it to the default gateway(R2)
- The data is delivered from Host C to Router 2, in the table, it has the info of the next IP address and the MAC address of that corresponding IP address-> so it will just send it directly after creating L2 header
- The same path is followed from R1 to its destination Host A-> it will discard L3 and L2 and process the data


- Events btw R2 and R1 would repeat for any amt of routers in the path
- Every time these steps r followed:
  1. Look up the dest IP in routing tbl to determine the next hop IP
  2. Adds a L2 header with dest MAC next Router's MAC
  3. Performs ARP as necessary


-Routers typically connected in hierarchy
- easier to scale- more consistent connectivity
- Here, its helpful bcz if any router goes down, it will not affect the other routers
  <img width="451" height="108" alt="image" src="https://github.com/user-attachments/assets/544575f4-2183-4f9a-8e3e-3c08e4302834" />
- Hierarcy allows for route summarization
- u might have observed "/24" -> used to match the first 3 octets( bits in the octets) in subnetting-> which means when the router is mapping the IP, it will look into the first 3 octets and map it to the corresponding IP(either host/router) and no need to checking all the 4 octets
- If u want to match only the first 16 bits (2 octets) then u can give /16 instead of /24
- U can reduce the number of routes in routing table
- U can further simplify it further to /8, like if u want to send the data from R8 to R5( same network) or some router in New york
- In case ur routing table has /24, /16 and /8, it will check for the value thats more specific(i.e /24 bcz it has more octets)
- Default route: ultimate route summary( eg, R8 has to go to R5 irrespective of if its passing the data within Tokyo network or its been passed to new york network. In such cases u can give the default route like 0.0.0.0 /0(every IPv4 address)-->this means every single IP address is matched by this particular route
This basically means that, For everything else, go to route 5



Encapsulation: ( using TCP/IP model)
- process of formatting data
- adds a overhead at each layer, and this over head is called a header
- segment header, Packet header, frame header-> PDU ( protocol data unit)
<img width="272" height="176" alt="image" src="https://github.com/user-attachments/assets/6a105a19-e436-4e0f-98c7-1ec46b7baade" />
- the Data link and the Physical later is collectively called the Network access layer
- The data from the client/host goes through the application layer
- It then goes to the Transport layer where the segment header(PDU for transport layer ) is added to the data
- Then it goes to the Network layer where the packet header(PDU for Network later) is added to the segment
- Then is goes down to the Data link layer, where the frame header is added to the packet
- This then passes to the physical layer where its just bits and then is transported to the recipient.
- All these layers are independent of each other and all of them perform their specific functions
- The data is never altered during the course of this event.

Decapsulation:

<img width="331" height="193" alt="image" src="https://github.com/user-attachments/assets/01e55d8a-69c0-458f-8649-e4c424a57d1a" />

- its the opposite of encapsulation
- here the encapsulated data reaches the destination machine at the physical layer and it consists of only bits
- This is then passed to the data link layer where it reads the Frame header and the frame trailer, and once it gets the required info from it, it will discard the frame header.
- Packet then moves to the Network layer where it reads the info in the Physical header and discards it, remaining only with data and segment layer
- This segment is further passed to the Transport layer where it would read out the segment data and then discard it.
- The data that remains is then sent to the application layer which then finally reaches the destination Host.



LAN Vs WAN:

4 important types of network:

i. LAN- local area network
  - small network coverage
  - easy to manage
  - low cost
  - high speed internet
  - Used in homes, schools, offices, labs
  - fast bcz these devices r close to each other
  - LAN is one of the most commonly used networks
    
ii. MAN- Metropolitan Area Network
  - more area coverage than LAN
  - More expensive than LAN
  - medium speed
  - connects multiple LANs
  - Used for city wise internet access
  - Multiple office branches connected by a common network
  - Its larger than LAN but smaller than WAN
    
iii. WAN- Wide Area Network
  - Connects larger areas
  - used to connect the entire country / even the entire world
  - Bcz it has to cover such a large distance, it basically slower
  - WAN connects many smaller networks together
  - Best example is Internet
  - Uses public communication systems ( Eg: Internet)
    
iv. WLAN- Wireless Local Area Network
  - similar to LAN but dosnt use cables, it transmits wirelessly
  -  uses wifi instead of cables
  -  WLAN gives more flexibility bcz devices can move more freely
  -  Wireless connection
  -  Wifi technology
  -  no need for cables
  -  easy to connect devices

NOTE:
WAN connects networks, while a LAN connects devices within a local area


# LAN vs WAN vs MAN vs WLAN

| Type     | Full Form                   | Coverage                  | Typical Use                                                | Example               |
| -------- | --------------------------- | ------------------------- | ---------------------------------------------------------- | --------------------- |
| **LAN**  | Local Area Network          | Small geographical area   | Connect devices within a home, office, building, or campus | Office network        |
| **WAN**  | Wide Area Network           | Large geographical area   | Connect networks across cities, countries, or continents   | Internet              |
| **MAN**  | Metropolitan Area Network   | City or metropolitan area | Connect multiple LANs within a city                        | City-wide network     |
| **WLAN** | Wireless Local Area Network | Small geographical area   | Connect devices wirelessly within a LAN                    | Wi-Fi network at home |

## Key Differences

### LAN

* Covers a **small geographical area**.
* Usually owned and managed by a single organization or individual.
* Uses technologies such as **Ethernet** and sometimes Wi-Fi.
* Example: Computers, printers, and servers connected within an office.

### WAN

* Covers a **large geographical area**.
* Connects multiple LANs or other networks.
* Often uses leased lines, fiber, cellular networks, VPNs, or other carrier infrastructure.
* Example: A company connecting offices in Bengaluru, London, and New York.
* The **Internet is the largest example of a WAN**.

### MAN

* Covers an area larger than a LAN but smaller than a WAN, typically a **city or metropolitan region**.
* Can connect multiple LANs across the city.
* Example: A university or organization connecting multiple campuses across a city.

### WLAN

* A **wireless form of LAN**.
* Uses wireless communication, primarily **Wi-Fi (IEEE 802.11)**, instead of physical Ethernet cables for local connectivity.
* Example: Devices connected to your home Wi-Fi network.

## Easy Way to Remember

```text
LAN  → Building / Small area
MAN  → City
WAN  → Country / Continent / World
WLAN → Wireless LAN
```

> **Important:** WLAN is different from LAN mainly in how devices connect. A WLAN is still a LAN, but it uses wireless communication.



VLANs:( Virtual LAN)
- instead of physical partitioning ,we do the logical partitioning of the switch and then assign each part to 1 LAN
- once a switch is divided then you can connect hosts, based on the number of ports that are ressent in VLAN
- the devices of 1 VLAN cannot communicate with hosts of other VLAN, but can communicate within the VLAN.
- If u want inter VLAN communication, then u need a router, and this router is connected to the trunk port and this is called the trunk line
<img width="401" height="218" alt="image" src="https://github.com/user-attachments/assets/dc3c8086-1541-4b14-8e89-7edef597e69f" />

- This is the logical partitioning of layer 2 network
- multiple partitions can be created allowing multiple hosts to be connected, if not partitioned, then they become a part of the default VLAN
- Each VLAN is a broadcast domain , usually with its own IP address
- VLANs are Mutually Isolated and Packets can pass between them via the router
- the partitioning of L2 happens inside a L2 device like a switch, and the hosts are unaware of the VLANs existance

Benifits:
- security: broadcast of 1 VLAN wont be sent to others
- Cost reduction( only 1 switch is used)
- Better performance ( max utilization of the switch)
- Shrink broadcast domains
- Improves IT staff efficiency
- simpler project and application management

Types:
- data VLAN
- Default VLAN
- Native VLAN
- Management VLAN
- Voice VLAN

VLAN frame Tagging:
<img width="326" height="208" alt="image" src="https://github.com/user-attachments/assets/299c8f56-9bc5-4c84-bc35-0394682e1d07" />

- its the process of adding the VLAN identification header to the fremae
- It is used to properly transmit multiple VLAN frames through a trunk link
- Switches tag frames to identify the VLAN to that they belong to. Diff tagging protocols exists: IEEE 802.1Q is a very popular one
- it defines the structure of the tagging header added to the frame
- switches add VLAN tags to the frames before placing them into the trunk links and remove the tags before forwarding them through the non trunk ports
- When properly tagged, the frames can traverse any number of swicthes via trunk links and still be forwarded withinthe correct VLAN at the destination


Firewall:
- Its a system that is used to prevent unauthorized access from entering a private network
- creates a safety barrier between a private network and public internet
- Its specially important to large organizations
- It has a set of rules and present in an access control list
- They are controlled by the admin
<img width="385" height="70" alt="image" src="https://github.com/user-attachments/assets/5891132b-c675-4d1d-a3aa-58df7e4a655a" />
- Firewall rules are based on:
    - IP addreses
    - Domain names
    - Protocols
    - Programs
    - prots
    - key words
- Eg: using port numbers, data form some ports are allowed while of other ports are denied

Types:
- Host-Based Firewall : its a software installed on a computer and it protects that computer only
    - Eg: Microsoft windows Firewall, Zone alarm( 3rd party)
    - lot of antivirus programs come with a host based firewall
- Network based Firewall:
    - Combination of hardware and software
    - placed between the public inter net and private network
    - This protects the entire network based on the management rules applied
    - stand-alone: Used by large organizations
    - Routers have built-in firewall
    - Could firewall
- most organizations have both network and host based firewall because if any traffic is missed from the network firewall, it can be stopped in the host based firewall


Proxies:
- proxy server is a server that retrieves data out on the internet on behalf of the user
- Eg: when a computer wants to view a webpage, u will insert the name of the webpage and retrieve the webpage from its web server
- Proxy server acts a middleman between u and the webserver, so when u send a request for a webpage, it will retrieve it from the webserver on ur behalf and then give it to u
- Benifits:
    - Privacy: allows u to access the internet anonymously and ur IP address becomes invisible, only the IP of the proxy server would be seen viewing the webpage
    - Speed: when the proxy server requests for a webpage from the webserver, it will store a copy of it in its Central DB, so that next time someone else queries for the same website, it can give it from the cache directly, instead of querying the web server
    - saves bandwidth: as it saves the copy of whatever it has retrieved, it will reduce the time of going to the internet always and fetching the data
    - activity logging: in many companies, it can keep track of the websites that the employees are logging into and also block the use of certain websites
- Proxy servers cannot encrypt the data- so the data can be intercepted by hackers, ISP or the government, so this is where a VPN comes in
- A VPN( Virtual private network)- not only hides the IP address, but also encrypts the data thats being passed from ur system to the internet
- It provides a dedicated secured tunnel between 2 points

Proxy and Reverse Proxy:
- Proxy : someone or something that has the authority to do something for the another person or a thing
- A proxy is a server
- Proxy server is a middleman btw private network and public internet
- Forward Proxy:
  <img width="402" height="191" alt="image" src="https://github.com/user-attachments/assets/86786fce-f3e3-4c6a-b485-530c1c2c18bd" />
    - when multiple devices want to access the internet, it would pass through the server and and then would be sent to the cloud
    - helps prevents harmful websites and hides IP address of the hosts
    - Logs user activity
    - can bypass restricted consent and increases speed
- Reverse Proxy:
    - regulates traffic coming into a network
  <img width="424" height="206" alt="image" src="https://github.com/user-attachments/assets/c8f56856-beef-47ab-9889-a26c168586a3" />
    - The private network will have its own servers. Now clients on the internet might want to communicate or get some data from these private servers. But at the same time, some malicious users too might be present and would corrupt the private servers. So for this we use a Reverse proxy that would filter the queries from a computer on the internet and then send it to the private network with servers and computers
    - Benefits: Increases security, Hides IP address, blocks malicious traffic-> DDOS attack( an attack by a bunch of computer on the internet attacking a particular server on the internet)
    - load balancing: evenly dist. traffic between multiple servers


VPN:( Virtual Private Nwtwork)
- establishes a secure and reliable network connection over an unsecure network connection as the internet
- protects ur internt activity and disguises ur identity on the internet
- When the ISP creates a connection in ur device, it could be sent to the government and the advertisements and whatever ur browsing is no longer private inorder to prevent this, we use VPN that would Bypass the ISP server and keeps ur browsing history private
- Benifits:
    - disguise ur identity by hiding ur IP address( they only see VPNs IP)
    - encrypts and protects data: when the data passes through ur sytem to the internet, it is broken down into smaller packets and these packets are accessible by the ISPs, so VPNs prevents this by encapsulating the data with an extra layer of protection and sent it over the internet-> this is called tunneling and the data would pass through a virtual tunnel
    - U can access internet content thats restricted in certain geographical networks-> for this u can use the VPN of that particular geographical location of which you want to gain access to and retrieve the data from restricted wbsites
    - provides secure connection for remote workers-> done using a leased line.If there is an employee working remotely, they would have to access the files thats present in the office server-> this is done using a leased line(private line)-> directly connect the 2 host together using a secure channel and helps communication between them. But this can be expensive is the distance is too much and this must be renewed on monthly basis, so instead they can use a VPN
- Who needs VPN: anyone who wants extra layer of protection( specially if ur using free wi-fi connections)-> VPNs can be there in ur Laptops, desktops, smartphone or the tablets


IDS Vs IPS Vs Firewall:
IDS : Intrusion detection system
- passive monitering tech. for detecting cybersecurity attacks
- If a problem is detected, it will alert the admin so that necessary actions would be taken
- Types:
    - based on deployment place:
        - Network based: Network IDS : monitors traffic moving into and outside the network
        - host based : Host IDS: monitors traffic of only that specific computer and also track the activity of clients on that particular system( eh: it might alert the admin if a video game is accessing private files
    - threat identification:
        - signature- based: it will identify the threat based on the signatures of the known number of threats and works similar to antivirus software
        - Anomaly-based: It will create a record of normal activities of a system and if there is any activity outside this it will alert the admin ( THEY ARE BETTER THAN SIGNATIRE BASED AS THEY CAN IDENTIFY ANY NEW THREATS THAN THE NORMAL ONES)
        - Hybrid-system: uses both methods to identify potential threats
          
IPS : Intrusion prevention system
- Its an active monitoring system that protects the company's network from malicious attacks
- They not only raise alter but also prevent the threats from happening by taking an action
- when IPS detects a danger, it will place it a separate place
- Types:
    - Threat detection methods:
        - Signature-based
        - Anomaly based
        - Bybrid
    - based on deployment place:
        - host-based
        - network-based
        - wireless-based
        - network-behavious
- IDS and IPS can be integrated together into a single unit too: NGFW and UTM


## Difference Between Firewall, IDS, and IPS

| Feature | Firewall | IDS (Intrusion Detection System) | IPS (Intrusion Prevention System) |
|---|---|---|---|
| Full Form | Firewall | Intrusion Detection System | Intrusion Prevention System |
| Main Purpose | Controls network traffic based on security rules | Detects suspicious or malicious activity | Detects and blocks suspicious or malicious activity |
| Primary Function | Filters incoming and outgoing traffic | Monitors traffic and identifies potential threats | Monitors traffic and actively prevents threats |
| Action Taken | Allows or blocks traffic based on predefined rules | Generates alerts when suspicious activity is detected | Automatically blocks or drops malicious traffic |
| Response | Preventive (based on configured rules) | Detective (identifies and reports threats) | Preventive (actively stops detected threats) |
| Placement | Usually placed at the boundary between networks or on individual devices | Can monitor network traffic passively or analyze host activity | Usually placed inline in the network traffic path |
| Traffic Handling | Filters traffic according to rules such as IP addresses, ports, and protocols | Observes or analyzes activity without directly blocking traffic | Inspects traffic and can block it before it reaches its destination |
| Example | Blocks incoming connections to an unauthorized port | Detects repeated login attempts that may indicate a brute-force attack | Detects a known attack pattern and drops the malicious packets |
| Limitation | May not detect every attack hidden within permitted traffic | Cannot directly stop an attack unless integrated with a blocking mechanism | May accidentally block legitimate traffic if incorrectly configured |

### Easy Way to Remember

- **Firewall:** Decides what traffic is allowed or denied.
- **IDS:** Detects suspicious activity and alerts the administrator.
- **IPS:** Detects suspicious activity and takes action to stop it.

## Difference Between VPN and Proxy Server

| Feature | VPN (Virtual Private Network) | Proxy Server |
|---|---|---|
| Main Purpose | Creates an encrypted connection between your device and a VPN server | Acts as an intermediary between your device and the destination server |
| How It Works | Routes your network traffic through a VPN server and encrypts it through the VPN tunnel | Forwards requests to the destination server on your behalf |
| Encryption | Usually encrypts traffic between your device and the VPN server | Does not necessarily encrypt traffic |
| IP Address | Replaces your public IP address with the VPN server's IP address for routed traffic | The destination server generally sees the proxy's IP address instead of your IP |
| Scope | Usually protects traffic from multiple applications on your device, depending on configuration | Often works only for a specific application, browser, or configured connection |
| Security | Helps protect data in transit, especially on untrusted networks | Primarily forwards requests; security depends on the proxy type and configuration |
| Privacy | Helps hide your traffic from your local network operator, but the VPN provider may see metadata or unencrypted traffic | Can hide your IP address from the destination, but the proxy provider may see your requests |
| Speed | Encryption and routing may add overhead, depending on the VPN server and connection | May have less overhead, but speed depends on the proxy server and network |
| Common Uses | Securing public Wi-Fi connections, remote access to company networks, and protecting traffic in transit | Accessing content through another server, caching web content, and filtering web requests |
| Example | An employee connects securely to their company's internal network from home | A browser sends a website request through a proxy server |
| Limitation | Does not guarantee complete anonymity or protect against every type of threat | May not encrypt traffic or protect applications that are not configured to use it |

### Easy Way to Remember

- **VPN:** Creates an encrypted tunnel for network traffic.
- **Proxy:** Acts as an intermediary between the client and the destination server.

### Example

Suppose you are using public Wi-Fi at a coffee shop:

- **Without a VPN:** Your traffic may be exposed to local network monitoring if it is not otherwise encrypted.
- **With a VPN:** Your traffic is encrypted between your device and the VPN server, helping protect it from local network monitoring.
- **With a proxy:** Your requests pass through the proxy server, which can hide your IP address from the destination, but the connection is not necessarily encrypted.


DMZ ( Demilitarized zone):
- basically means an are where firewall protection is forbidden and there is a way that we can configure devices into DMZ
- used to improve the security of an org's network by segregating the devices, such as computers and servers on the opposite sides of a firewall
<img width="375" height="204" alt="image" src="https://github.com/user-attachments/assets/ff19f745-746a-4393-b829-328f659c2487" />
- There would be servers that r present behind the Company's firewall and inside the private network
- and these servers might be given access to the clients on the internet
- This will allow the unauthorized clients( anyone on the internet) to access the servers of a company present inside the company's private network
- If this happens, there is a chance that malicious users can access the server and could cause havoc they have already got past the firewall bcz the company allows it.
- This would also allow the attackers to access the other devices and DB present inside the same network and inject viruses( this is a security network)
- So instead we could place the servers infront of the firewall so that the other users dont have access inside the company's data behind the firewall and only the servers would be exposed on the internet-> these servers are no in a DMZ
  <img width="370" height="116" alt="image" src="https://github.com/user-attachments/assets/05e856a9-7d98-4a7f-88ff-b9eaea96074a" />
- this could also act as a screened network to detect any malicious activity before it can get into the other side of the firewall
- DMZ divides a network into 2 parts by taking the devices from inside the firewall and placing them outside the firewall
- for extra protection, a firewall could be added infront of the servers, so that when hackers try to break a firewall, they would have to break into another firewall too, inorder to get into the company's data
- There's also a DMZ that u can configure in ur home
- a home router DMZ setup designates a device as a DMZ host and will forward all the ports to that device
- Like adding a gaming console and configuring it as  a DMZ host, bcz most of these games are played online and gamers dont want any kind of interference while gaming from a firewall
- for this, u could just go into the DMZ configuration page of the router and give the IP of the gaming console as the DMZ
- NOTE: the device in the DMZ must be configured with a static IP and not dynamic IP
<img width="364" height="142" alt="image" src="https://github.com/user-attachments/assets/d323ff24-c825-4560-b21f-39ad815b7e1a" />
- here, the home router will act as a firewall, so as the computers are on the other side of the router(which is a firewall) it is safe, but the gaming console is given as a DMZ and is directly exposed to the internet
