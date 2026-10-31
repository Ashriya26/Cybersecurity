Peer-to-peer(P2P) Architecture:
- the nodes act as both the host and the server
- The osts directly connect with each other and share the resources and dont require a centralized server to do the task.
- A popular example of Peer-to-Peer (P2P) architecture is torrenting, as seen with applications like BitTorrent. In this system, anyone who has the file, referred to as a seeder, can upload it, allowing others to download it from multiple sources simultaneously.
- Advantages:
    - scalability: adding more nodes increases resources
    - resilience: If 1 node goes gown, others can continue working
    - Cost distribution: the resources and the cost is distributed among the peers so that making it more cost-efficient
- Disadvantages:
    - Management complexity:	Harder to control and manage updates/security policies across all nodes
    - Potential reliability issues:	If too many peers leave, resources could be unavailable.
    - Security challenges:	Each node is exposed to potential vulnerabilities.
<img width="965" height="655" alt="image" src="https://github.com/user-attachments/assets/e041153d-2a9b-414f-9142-ce1f2b3bdefe" />

 
Client-Server Architecture:
- Most widely used architecture over the internet
- Client: send requests
- Server: receives, process and replies to the request
- Eg: we want to check the weather forecast on our phone, the the client will query the website name, this is then sent to the server after the DNS lookup. The server will find this IP address, and then send this request to the respective hosting server of this website. This servre will then respond to the client which will be displayed on our screen as weather forecast.
<img width="958" height="482" alt="image" src="https://github.com/user-attachments/assets/7ceeb7eb-9fe3-46a3-b419-aa51941f6a49" />

Types:
- single-tier:
  - client, server, DB all r in the same machine
  - rarely used in largescale due to scalability and security issues
- two-tier:
  - The client and server are in different machines
  - the user can access the UI present in his system and when he queries or if a request is sent, it will go to the server( DB server) and queries for the required data
  -  normally, the client dosnt directly communicate with the web server, but instead, it would query the web server, and the web server would query the DB if required
- Three-tier:
  - there r 3 layers, te client is in the presentation laer, the application layer is present ebtween the client and the DB server layer
  - The application layer would handle all the business logic
  - provides added flexibility and ascalability
- N tier:
  - There r multiple application layers between the client and server and each of these handle individual activity like data, business logic etc
  - this makes the system highly robust and scalable
  - N-tier architectures are highly scalable and allow for distributed deployment, making them ideal for web applications and services that demand robust, flexible solutions.
 
Advantages and disadvantages of client-server architecture:
Advantage	
- Centralized control:	Easier to manage and update.
- Security:	Central security policies can be applied.
- Performance:	Dedicated servers can be optimized for their tasks.
Disadvantage	
- Single point of failure:	If the central server goes down, clients lose access.
- High Cost and Maintenance:	Setting up and sustaining a client-server architecture is expensive, requiring constant operation and expert management , making it costly to maintain.
- Network Congestion:	High traffic on the network can lead to congestion, slowing down or even disrupting connections when too many clients access the server simultaneously.


Hybrid architecture:
- this is a combination of both the peer-to-peer and client-server models
- The central servers are used only for coordination and authentication tasks and the actual communication happens directly between the clients
- Eg: In a video conference, initially the server will check the credentials of the user login to check if its an authentic user. One the user credentials are validated, the user/clients in the meeting would directly communicate wit each other without the requirement of a central server
<img width="1021" height="575" alt="image" src="https://github.com/user-attachments/assets/d3a4a6c2-cb39-4f3d-b534-50e3b21637cc" />

Advantages and disadvantages of hybrid architecture:

Advantage	
- Efficiency:	Relieves workload from servers by letting peers share data.
- Control:	Central server can still manage user authentication, directory services, or indexing.
Disadvantage	
- Complex Implementation:	Requires more sophisticated design to handle both centralized and distributed components.
- Potential Single Point of Failure:	If the central coordinating server fails, peer discovery might stop.

Cloud architecture:
- The third party hosts and manages this infrastructure like google cloud, AWS etc
- These parties provide all the necessary services like storage, sercurity etc
- It provides in-demand access to resources like server, storage and application without the requirement of controlling the underlying hardware
- Characteristics of cloud services (SaaS):
   1. On-demand self-service	Automatically set up and manage the services without human help.
   2. Broad network access	Access services from any internet-connected device.
   3. Resource pooling	Share and allocate service resources dynamically among multiple users.
   4. Rapid elasticity	Quickly scale services up or down based on demand.
   5. Measured service	Only pay for the resources you use, tracked with precision.
<img width="1022" height="707" alt="image" src="https://github.com/user-attachments/assets/6d58adc2-51f0-4136-9fd9-94ffcff85b30" />

Advantages and disadvantages:
Advantage	
- Scalability:	Easily add or remove computing resources as needed.
- Reduced cost & maintenance:	Hardware managed by the cloud provider.
- Flexibility:	Access services from anywhere with Internet connectivity.
Disadvantage	
- Vendor lock-in:	Migrating from one cloud provider to another can be complex.
- Security/Compliance:	Relying on a third party for data hosting can introduce concerns about data privacy.
- Connectivity:	Requires stable Internet access.

Software-Defined Architecture(SDN):
- it defines how the data is being accessed
- the networking approach generally has 2 planes,
  - Control plane : this makes decisions of where to move the traffic
  - data plane: actually moves the traffic
- In SDN, the control plane is located inside the software-based controller
- this configuration allows the networking devices to directly execute the instructions they receive from the computer
  <img width="767" height="713" alt="image" src="https://github.com/user-attachments/assets/0b4649d4-c6dd-45c7-8ac3-741a9ec64341" />

Advantages and disadvantages:

Advantage	
- Centralized control:	Simplifies network management.
- Programmability & Automation:	Network configurations can be changed quickly through software instead of manually configuring each device.
- Scalability & Efficiency:	Can optimize traffic flows dynamically, leading to better resource utilization.
Disadvantage	
- Controller Vulnerability:	If the central controller goes down, the network might be adversely affected.
- Complex Implementation:	Requires new skill sets and specialized software/hardware.

<img width="818" height="442" alt="image" src="https://github.com/user-attachments/assets/71863a01-5a91-4402-ac2c-3e4b6f65926f" />
