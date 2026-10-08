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




Everything a host does to speak on the internet:

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


Everything Switches do to facilitate communication

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



Everything Routers do to facilitate communication

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





