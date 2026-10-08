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
-Switches maintain a map address table which maps a post to its particular MAC address
- Switch perform only 3 actions:
        - Learn
        -Flood
        -Forward



