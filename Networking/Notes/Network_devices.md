Network devices

1. Hosts : 

-any device that send or recieve traffic
-Eg : Computer, laptop, phones, printers, servers, cloud servers, lights,       refrigerators, speakers, TV, thermometers etc
- 2 types:
  i. clients : initiate requests
  ii. servers : responds to requests : they r simply computers with software installed which responds to specific requests
  - this is relative to specific communication

2. IP address:

   -identity of each host
   - required to send information over the internet (packets over a network)
  Eg : a computer would ask for information from the server. 
      - while doing so, the computer would send a packet consisting of 2 IP addresses, 1 of source and one of the destination, in the similar manner, when the server send the reply through a packet, it would again contain 2 IP addresses, one of source and other of destination.
     - IP addresses are 32 bits
     - represented as 4 octets ( smallest number obtained from the octet is
       '0' -0000 0000 and the largest is '255'-1111 11111)
     -represented as 0000 0000.0000 0000.0000 0000.0000 0000
                      [0-255]   [0-255]   [0-255]   [0-255]
 - Its hierarchically assigned      
 <img width="335" height="190" alt="Screenshot 2026-10-06 204008" src="https://github.com/user-attachments/assets/92470726-9d63-4e92-91bc-46fe189fe031" />

3. Network:

   - transports traffic between hosts
   - Anytime 2 hosts are connected, u have a network
   - before networks: transferring data btw hosys required postable media (disks, thumb drives etc)
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
  
6. Bridges

   -there would be 2 sets of hosts interconnected with the hubs
   -the bridges sit between the hub-connected hosts
   -bridges have only 2 ports
   -bridges learn which host is on which side
   -it helps contain packets only to its relative networks
   -if 2 hosts within the same port want to communicate, then the bridge will not let the signal leak into the other port.
   -likewise, if a host from 1 post wants to communicate with the host of another port, the bridge recognizes it and allows communication.

7. Switches:

   - Facilitate communication within a NETWORK
   -its a combination of hubs and bridges
   -has multiple ports
   -learns which host is connected on each port
   -(bridge and hubs are kind of broadcasting models, but switch is confined, it allows communication only between 2 specific hosts and dosnt leak the data to other hosts)
   -hosts on a network share the same IP address space
  - Switching is the process of moving data within networks

8. Router

   -Handles communication between networks
   - provide traffic control point(security, filtering, redirecting)
   - routers learns which networks they are attached to
   - These r routes and they r stored in a routing table( all the networks a router knows abt)
   - every router has an IP address in the network they r attached to.
   - This acts as a GATEWAY ( a hosts way out of its local network)
   - Routing is a process of moving data between networks
   - Router is a device whose primary purpose is routing
  
   -they create Hierarchy in networks and entire Internet
   
