OSI Model

- Purpose of Networking: Allows 2 hosts to share data with each other
- This sharing of data has a set of rules and this is done by the OSI model
- The OSI model divides the rules of networking into 7 layers where each layer serves a specific function
- if all layers are functioning fine, then the hosts can share the data


1. Layer 1- Physical layer ( Transports Bits)
   - the data in the computer is stored in the form of bits and this layer helps transport this data between the hosts
   - Eg : Cables( ethernet, Coaxial, Fiber), Repeaters, hubs, Wifi

2. Layer 2- Data Link Layer (Hop to Hop)
   - This layer directly interacts with the physical layer(wires)
   - transports bits from 1 host to the other 
   - Each host has a NIC (network Interface Card) / Wifi-Access card whereever the wire connects to the PC
   - The addressing schema is MAC Address
         - 48 bits, represented as 12 hex digits
         - 94-65-9C-3B-8A-E5 or 94:65:9C:3B:8A:E5 or 9465.9C3B.8AE5
         -every NIC has a unique MAC address
   -Technologies : NICs , switches
   -Often communication between hosts require multiple hops

3. Layer 3- Network Layer (End to end)
   - Address scheme: IP Address
   - Technologies : Routers, Hosts, (or anything with an IP address)
   - This IP address allows the data to be transferred from the source host to the destination host
  

NOTE:
-----> Layer 3: IP Address
-----> Layer 2: MAC Address
--> both of these serve different functions, but they both collectively work to transport data across the internet

Every host has its own IP address, so the data will flow from 1 host to the other. But In between it would encounter routers. SO the MAC address comparison by NICs between the host and the router helps the data to move forward in the wire and then between the routers too which ultimately leads to reaching the destination Host
   <img width="434" height="132" alt="image" src="https://github.com/user-attachments/assets/d431b73d-e853-4544-bdc7-259645ba12e4" />
- ARP(address Resolution Protocol)-> links layer 3 address to layer 2 address


4. Layer 4-Transport layer(Service to Service)
   - Imagine ur running multiple tasks in ur computer, like playing games, chatting and also searching something online, how does it know which data must be passed to which task, this is done by the transport layer
   - Distinguishing data streams
   - Addressing Scheme : Ports
       -TCP-> favors reliability (0-65535)
       -UDP-> favors efficiency (0-65535)

  <img width="819" height="243" alt="image" src="https://github.com/user-attachments/assets/af7286cf-5a41-49b8-9fcb-78bb3e46dc57" />

  - Server listens for requests to pre-defined prots
  - Client selects a random port for each connection
  - The server responds to this request using this port
  - The client can also do multiple connections to the same server
<img width="436" height="107" alt="image" src="https://github.com/user-attachments/assets/0174033e-86de-445c-95fa-bf3b004bb605" />

<img width="445" height="133" alt="image" src="https://github.com/user-attachments/assets/b243d535-b486-46ea-85ce-f70ba89a8723" />

5. Layer 5,6,7 - session, presentation, Application
   - the distinction between these layers is somewhat vague
   - Other networking models just combine these 3 layers into a single layer

<img width="279" height="137" alt="image" src="https://github.com/user-attachments/assets/68caf864-62b5-41ee-94ad-f6f16876d71c" />

  - L1- L4-> imp to understand how data flows


Entire flow:

- The data sent from the hosts is encapsulated ( sending) and is passed through layers 7->6-> 5
- When it reaches layer 4, the data is bound with Port(TCP/UDP) to form a segment ( data+port)
- then it goes down to layer 3 (network layer) where the segment is combined with IP address to form a packet(data+Port+IP)
- Then it goes to layer 2(data link) where the packet is combined with the MAC address ( data+port+IP+MAC) to form a frame
- Then through the physical layer, it passes through the wires and reaches the destination host
- Here, it undergoes de-encapsulation ( recieving)
- The frame Mac in the frame is identified, and then discarded forming packet
- It then moves to the network layer where it checks the IP to analyze was this the actual host to which the data was sent, then discards the IP to form Segment
- Then moves to the Transport layer, where the Port is identified and the Port is removed from the segment to give only the data.
- This remaining data will move further in the application and reach the Destination host

<img width="481" height="145" alt="image" src="https://github.com/user-attachments/assets/64ba0615-dece-4640-99df-44071b2ee821" />

<img width="480" height="113" alt="image" src="https://github.com/user-attachments/assets/1bac297e-1cf5-4a7d-b85f-310b552f7485" />

----> Network devices and protocols operate at specific layers. Neither of them are strict rules
----> OSI model is simply a model which helps us understand how the data flows through the internet



TCP-IP Model


  
   



