WEP/WPA2/WPA3:
- wireless security methods
- A wifi network always usually has a password. But there would be some open wifi hat would allow u to connect to it without the need for a password
- WEP( wired equivalent Privacy):
  - earliest security protocol used for wireless network
  - the 40 bit encryption key it used was easily vulnarable and easy to hack
- WPA ( Wifi protected access) :
  - dev. to solve problems of WEP
  - uses strong encryption thats done through TKIP( Temporal key integrity protocol)
  - This was more secure as it would change the TKIP key after every use, but it still had some vulnerabilities so its still outdated
- WPA 2:
  - stronger than WPA
  - uses AES ( Advanced Encryption tsandard)
  - uses symmetric encryption algo. that makes it strong enough to resist Brute-force attack
  - Its adopted by the US federal govt.
- in ur wifi security page, if u go into wifi sec. section , ull find diff seurity protocols that could be used to secure ur network
- some routers would have a mixed option of of WPA and aWPA2 bcz some older versions ( prior to 2006) wouldnt have WPA2 option ( AES compatibility)
- even though u feel that mixed one is the best and would provide better security, tahts wrong, bcz the WPA uses TKIP and thats vulnerable, so if ur device is compatible with WPA2, just go for it and not WPA
- WPA3:
  - introduced in 2018
  - provides cutting-edge security protocols to the mrket
  - adds new features to simplify wifi security and enable more robust authentication
  - receive increased protection from password guessing attempts
- WPS ( Wifi protected set-up)
  - here u dont have to type in a password
  - designed for ppl who dont know much abt wireless networks
  - uses a push button method( a physical WPS button)
  - If u want to connect a wifi connected printer to a router, u just press the WPS button on the router and then within a few mins, u also press the WPS button on the printer
  - this will connect teh printer to the router within just few seconds
  - or u could also use WPS pin number
- Access control:
  - allow or block devices from joining ur network using the devices mac address
  - when a device is blocked, it would only get the IP address of the router, and it would be able to connect to the internet-> this is only for wired devices

Network segmentation:
- normally, u would have ur switch, to which u connect a printer. Now this switch is connected to a router and the router is connected to the internet
- In this scenario, theres network segmentation happening to some extent by the router with CPE on the left of the router connecting to the switch and ISP to the right of the router connected to the WAN
- Now if u want to connect multiple other internet connected devices like IOT device, fridge, home assistant then how would u do it
- U want these devices conencte to the  network but not on the same network bcz some of these might have a vulnarability and would also affect the otehr devices that r connected to the same network
- One way of doing this is using the router as a router firewall security hybrid, where u would have a router connected to 2 different switches and also connected to the WAN, one of the switch would have connection to the IOT devices, fridge, Camera, thermostat etc , the other switch woudld be connected to ur PC, server etc
- Now anyone who connects to these devices would also be able to connect to the main network, so for this, we must use strong usernames and passwords so that even though this device is exposed, the network as a whole would be protected
- At some point of time, u would also need to connect the PC to the home assistant which are both on different switches, so for this u need to explicitly connect these 2 devices, through the router
- In small enterprises: u might have a router connected to a switch with multiple IOT devices and PCs and on the other end, connected to the WAN
- So u could use Virtual segmentation ( VLAN): so u can configure multiple networks using VLANs and thats how switches support network segmentation
- High-bandwidth performace
- users shouldnt talk directly to the DB servers, and the only applications in the core are SQL and SSH
- Mandated segmentation ( PCI Compliance) makes change control much easier
- ACLs and Access allow list/deny list


ACL( Access COntrol List)
- its a set of rules used to control network traffic and reduce network attacks
- Filters the incoming and outgoing traffic based on certain rules
- Its in layer 3
- also called packet filtering firewalls
- ACL is a set of rules, so whenever the traffic travels through the router, it will check each of these packets against those set of rules if it should be allow or deny it
- U can either block 1 specific IP, host or u can also block an entire network too
- File system ACL:
    - Filters access to Files and directories
    - It tells the OS which user is allowed to access the system and what r the privileges offerred
- Networking ACL:
    - Filters access to the entire network
    - It tell which kind of traffic can access the network
    - what each device or user can do once its inside
    - they can further be categorized based on traffic identification
- Standard ACL:
    - developed only using the source IP to protect the network
    - they allow/block the entire protocol suite
    - they dont differentiate between any IP traffic( for eg, if u block the source IP of TCP/IP suite, then none of those traffic would pass through the router) 
    - It would allow all the traffic to pass, including the malicious ones
    - Its the most basic type and can  be used for simple deployments
    - But it dosnt provide strong security
- Extended ACL:
    - filters traffic based on protocol info
    - widely used as it can different btw diff, protocols like TCP, UDP, ICMP etc
    - it uses source and dest IP address and port numbers
    - uses numbers from 100-199,2000-2699
    - using ACL, u can block the source/dest. for a single host/ the entire network 

- help organize traffic
- improve network efficiency
- give admin high level control over users and computer systems
- keeps out malicious traffic

Load balancer:
- its a piece of h/w or s/w thats used to evenly distribute the data activity across the network
- so that so single server/computer becomes overwhelmed bcz of the amt of traffic
- Imagine theres a small company and it adds its website directly to teh server. Now when the user accesses it, it will access directly from the server. This is ok until its min no.of users, but when the number of users increases, there would be a load on the server. Adding more servers would help, but theres a possibility that the user would still use the same server to retrieve the website info, so for this reason, load balancers play an imp. role, where it evenly distributes the traffic coming from the users across all the servers evenly.
<img width="1320" height="891" alt="image" src="https://github.com/user-attachments/assets/4f8b2717-d299-4cab-a1ee-bc22dba7b502" />
For example:
1. A user opens a website.
2. The request reaches the load balancer.
3. The load balancer chooses a suitable backend server.
4. That server processes the request and sends a response back.
Instead of one server handling all requests, several servers share the work.
Why do we need load balancers?
- Performance: Prevents one server from becoming overloaded.
- Availability: Traffic can be sent to healthy servers if another server fails.
- Scalability: More servers can be added as traffic increases.
- Reliability: Helps a website continue operating during some server failures.
- Security: Can hide backend server addresses and sometimes provide TLS termination, filtering, or integration with a web application firewall (WAF).

Important: A load balancer does not automatically protect an application from cyberattacks. Its security depends on its configuration and the other controls around it.

Types of load balancers:
1. Layer 4 load balancer (Transport layer):
Distributes traffic using network information such as IP addresses, TCP/UDP ports, and connection information.
2. Layer 7 load balancer (Application layer):
Understands application protocols such as HTTP and HTTPS. It can route traffic based on the hostname, URL path, or other HTTP information.

Common load-balancing algorithms
Algorithm	How it works
- Round Robin	Sends requests to servers in a repeating order.
- Weighted Round Robin	Sends more requests to servers assigned higher weights.
- Least Connections	Prefers the server handling the fewest active connections.
- IP Hash	Uses a hash of the client's IP address to select a server.
- Random	Selects a server randomly.

Health checks and failover
A load balancer can periodically check whether backend servers are healthy.
- If Server A responds successfully, it can continue receiving traffic.
- If Server B fails its health check, the load balancer can stop sending it new requests.
- When Server B becomes healthy again, it may receive traffic again.
This is called health-based routing or failover, depending on the setup.

One limitation: if the load balancer itself is a single point of failure, it can still bring the service down. Production systems often use redundant load balancers or managed services.
Load balancers: security concepts you should know
- TLS termination: The load balancer handles the HTTPS/TLS connection from the client. It may forward traffic to backend servers over a separate encrypted or unencrypted connection, depending on configuration.
- Session persistence (sticky sessions): Tries to direct a client's requests to the same backend server. This can help applications that store session information locally, but it isn't always necessary.
- Single point of failure: One load balancer without redundancy can become a point where the entire service fails.
- DDoS protection: Load balancers can help distribute traffic, but they cannot necessarily stop a large distributed denial-of-service attack by themselves.
- Reverse proxy: Many application load balancers also act as reverse proxies, accepting client requests and forwarding them to backend servers.

1. Static vs. dynamic load-balancing algorithms
A load-balancing algorithm decides which backend server should receive an incoming request or connection.
Static load balancing
- Predefined rules
- Uses a predefined distribution rule and generally does not adapt its decisions to the servers' current workload.
- Example: Send requests to Server A, then B, then C, and repeat.
- A. Round Robin (RR)
    - Requests are distributed in a repeating sequence across the available servers.
    - Advantages: Simple, easy to implement, distributes requests evenly by count.
    - Disadvantages: Does not consider differences in server capacity or how much work each request requires.
    - Best for: Similar servers receiving requests with roughly similar processing costs.
- B. Weighted Round Robin (WRR)
    - Each server is assigned a weight based on its capacity or intended share of traffic. A server with a higher weight receives a larger share.
    - Advantages: Accounts for different server capacities.
    - Disadvantages: Fixed weights may not reflect changing workloads; exact request order depends on the implementation.
    - Best for: Server pools with known, relatively stable capacity differences.
- C. IP Hash
    - The load balancer calculates a hash from the client's IP address and uses it to choose a backend server.
    - Advantages: The same client IP will often map to the same server when the server pool and hashing configuration remain unchanged.
    - Disadvantages: Many users behind one NAT or proxy can appear to share an IP. Traffic can become uneven, and changing the server pool may change mappings.
    - Best for: Situations where consistent routing based on client IP is useful.
    - IP Hash does not guarantee that every user has a unique server or that all of a user's sessions are preserved.
- D. Random Selection
    - The load balancer randomly selects a backend server for each new request or connection.
    - Advantages: Simple and can work well when multiple load balancers independently distribute traffic.
    - Disadvantages: Random distribution can be uneven, especially with fewer requests.
    - Best for: Certain distributed environments where a random choice is useful.
    - Random selection is sometimes classified separately rather than as a core static algorithm. Its exact behavior depends on the implementation. 
- E. Hash-Based Routing
    - A hash function converts a selected value, such as a client IP address, URL, or request key, into a value used to select a server.
    - Two important forms are:
      - IP Hash: Uses the client's IP address as the routing key.
      - Consistent Hashing: Arranges servers and keys in a hash space to reduce how many keys must be reassigned when servers are added or removed.
Why does consistent hashing matter? Imagine a cache-based application with three servers. If a fourth server is added, a simple hash-modulo-server-count approach may remap many keys. Consistent hashing is designed to limit that remapping.
    - Advantages: Can provide predictable routing and improve cache reuse.
    - Disadvantages: Traffic can be uneven, and client identity does not necessarily correspond to workload. Consistent hashing also depends on its configuration and hash distribution.
    - Best for: Caching, distributed systems, and applications where keeping related requests on the same backend is useful.
      
Dynamic load balancing
- Responds to current conditions
- Uses changing information, such as active connections, response times, or server load, to make routing decisions.
- Example: Send the next connection to the server with the fewest active connections.

- A. Least Connections (LC)
    - The load balancer selects the server with the fewest active connections.
    - Advantages: Adapts to changing numbers of active connections.
    - Disadvantages: A connection can be idle or require much more processing than another connection.
    - Best for: Applications with long-lived connections or varying connection durations.
- B. Weighted Least Connections (WLC)
    - This is Least Connections with server capacity taken into account.
    - The load balancer considers both the number of active connections and the assigned weight of each server.
    - For example, Server A may support many more connections than Server B because it has greater capacity. A higher weight allows the algorithm to account for this difference.
    - Advantages: Considers both current connections and different server capacities.
    - Disadvantages: Depends on sensible weights and may not reflect the actual cost of each connection.
    - Best for: Backend servers with different capacities.
    - A common conceptual rule is to compare the active-connection count relative to the server's weight. The exact formula and tie-breaking behavior vary by implementation. 
- C. Least Response Time (LRT)
    - The load balancer chooses a server based on measured response times, often combined with another metric such as active connections.
    - For example:
      - Server A responds in 100 ms.
      - Server B responds in 35 ms.
      - Server C responds in 70 ms.
    -If the measurements are comparable and other conditions are equal, Server B may be preferred.
    - Advantages: Can favor servers that are responding faster.
    - Disadvantages: Response times fluctuate, measurements can be noisy, and the fastest server is not necessarily the least loaded for the next request.
    - Best for: Applications where responsiveness is important.
    - Some implementations use average latency, time to first byte, time to receive the full response, or a combination of response time and connections. These are not all identical algorithms. 
- D. Resource-Based Load Balancing
  - The load balancer selects servers based on current resource availability.
  - It may consider:
    - CPU utilization
    - Memory usage
    - Available processing capacity
    - Queue length
    - Application-specific health or workload metrics
  - Example: Server A is using 95% of its CPU, Server B is using 40%, and Server C is using 60%. If CPU utilization is a reliable indicator for this application, the load balancer may prefer Server B.
  - Advantages: Can respond to actual resource pressure.
  - Disadvantages: Requires reliable metrics, monitoring agents or telemetry, and sometimes additional communication.
  - Best for: Workloads with significant variation in CPU, memory, or other resource requirements.
  - The algorithm must use relevant metrics: a server with free CPU may still be slow because of database, disk, or network bottlenecks. 
- E. Weighted Response Time
    - This approach considers response-time measurements and may also account for server weights or active connections.
    - The aim is to direct more traffic toward servers that can respond quickly while still considering their capacity.
    - Advantages: Can combine responsiveness with server-capacity information.
    - Disadvantages: More complex than simple Round Robin, and stale or noisy measurements can lead to poor choices.
    - Best for: Applications where backend performance differs and response time is a key concern.
    - The exact calculation differs between load balancers; "weighted response time" is not a single universal formula. 
- F. Least Bandwidth / Least Traffic
    - Some network load balancers can choose a server or link based on the amount of traffic it is currently handling.
    - For example, a server currently transmitting less data may be preferred over one handling heavy transfers.
    - Advantages: Useful when network traffic volume is a meaningful measure of load.
    - Disadvantages: Low bandwidth usage does not necessarily mean a server has spare CPU or can process a new request quickly.
    - Best for: Network-heavy services where traffic volume is relevant.
    - This is a vendor- or system-dependent option rather than a feature available in every load balancer.
- G. Adaptive Load Balancing
    - An adaptive algorithm changes its routing behavior based on changing measurements, feedback, or health information.
    - For example, if Server A becomes consistently slow, the load balancer may reduce its traffic share or adjust its effective weight.
    - Advantages: Can adapt to changing workloads and server performance.
    - Disadvantages: Requires accurate feedback; delayed or unstable measurements can cause traffic to shift too aggressively.
    - Best for: Systems where workload and server performance change over time.
    - Adaptive load balancing is a broad approach, not one universally defined algorithm. It can be implemented by adjusting weights, using response-time measurements, or applying other dynamic techniques.
 

## Comparison of Major Load-Balancing Algorithms

| Algorithm | Category (Typical) | Main Decision Factor |
|---|---|---|
| Round Robin | Static | Fixed rotation |
| Weighted Round Robin | Static | Configured server weights |
| IP Hash | Static / Hash-Based | Client IP address |
| Generic Hash | Static / Hash-Based | A chosen key, such as a URL or request value |
| Random | Often Static | Random selection |
| Consistent Hashing | Hash-Based | Stable key-to-server mapping |
| Least Connections | Dynamic | Active connection count |
| Weighted Least Connections | Dynamic | Connections relative to server capacity |
| Least Response Time | Dynamic | Measured response time, sometimes combined with connection count |
| Resource-Based | Dynamic | CPU, memory, queue length, or other resource metrics |
| Least Bandwidth | Dynamic | Current network traffic |
| Adaptive | Dynamic Approach | Feedback from changing conditions |

**Note:** These classifications are common teaching conventions, not a universal standard. Vendors may classify, combine, or implement these algorithms differently.

## Which Load-Balancing Algorithm Should You Choose?

| Situation | Suitable Starting Point |
|---|---|
| Servers have similar capacities and workloads | Round Robin |
| Servers have different known capacities | Weighted Round Robin |
| Connections last for different lengths of time | Least Connections |
| Servers have different capacities and connection loads | Weighted Least Connections |
| Response speed is the main concern | Least Response Time |
| CPU or memory pressure is a reliable indicator of load | Resource-Based |
| Requests should map consistently to backends | IP Hash or Consistent Hashing |
| Multiple independent load balancers share the same backends | Random may be suitable in certain implementations |


Important distinctions to remember
- Load-balancing algorithm vs. health check: The algorithm selects a backend; health checks help determine which backends are eligible.
- Load balancing vs. failover: Load balancing distributes traffic; failover switches away from a failed component.
- Load balancing vs. autoscaling: Load balancing distributes existing traffic, while autoscaling adds or removes computing resources.
- Load balancing vs. session persistence: An algorithm selects a backend; session persistence tries to keep a client associated with a particular backend.
- DNS round robin vs. proxy load balancing: DNS can return different server addresses, but clients and DNS caches may continue using a previously returned address. A reverse proxy or network load balancer can make a new backend selection for incoming traffic according to its own algorithm.


## 2. Zero Trust

### What is Zero Trust?

Zero Trust is a security approach in which users, devices, and connections are not automatically trusted simply because they are inside an organization's network.

Access is granted according to identity, permissions, device status, context, and security policies.

**Core idea: Never grant implicit trust. Verify access explicitly and limit permissions.**

### Why Is Zero Trust Needed?

In a traditional network, an attacker who gains access to one device may try to reach other internal systems.

Zero Trust helps reduce this risk by verifying access to resources, limiting permissions, and restricting movement between systems.
<img width="1532" height="895" alt="image" src="https://github.com/user-attachments/assets/c308d2a2-c5a6-4b6b-af8d-424a8f3aa571" />

### Core Principles of Zero Trust

#### 1. Verify Explicitly

Verify identity and relevant context before granting access.

Checks may include:
- User identity
- Multi-factor authentication (MFA)
- Device health
- Sign-in risk
- Requested resource

#### 2. Use Least Privilege

Give each user or system only the permissions necessary for its tasks.

Example: An employee who only needs to read reports should not automatically receive administrator access.

#### 3. Assume Breach

Operate as though an attacker may already have gained access.

This means:
- Monitor suspicious activity.
- Restrict unnecessary access between systems.
- Limit permissions and potential damage.
- Prepare to detect and contain incidents.

### Important Zero Trust Concepts

| Concept | Simple Explanation |
|---|---|
| Authentication | Verifies who you are. |
| Authorization | Determines what you are allowed to do. |
| MFA | Requires two or more different authentication factors. |
| Least Privilege | Grants only the permissions needed. |
| Microsegmentation | Divides an environment into smaller security zones to limit access and lateral movement. |
| Device Posture | Checks whether a device meets security requirements. |
| Conditional Access | Applies access rules based on identity, device, context, or risk. |
| Continuous Evaluation | Reassesses access when relevant conditions change. |
| Logging and Monitoring | Records and analyzes activity to identify suspicious behavior. |

### Authentication vs. Authorization

- **Authentication:** Are you really who you claim to be?
- **Authorization:** Are you allowed to access this resource or perform this action?

Example:

An employee signs in using a password and MFA.

Authentication verifies the employee's identity. Authorization determines whether the employee can view a report, edit records, or access administrator functions.

### How Zero Trust Works

1. A user requests access to a resource.
2. The system evaluates identity and relevant context.
3. It checks permissions and applicable security policies.
4. Access is granted, denied, or subjected to additional verification.
5. Activity is monitored, and access may be reevaluated if risk changes.

Zero Trust does not mean asking users to log in repeatedly for every action. Existing secure sessions and tokens can be used under appropriate policies.

### Traditional Security vs. Zero Trust

| Traditional Perimeter-Based Security | Zero Trust |
|---|---|
| Places significant trust in the internal network. | Does not automatically trust users or devices because they are inside the network. |
| Focuses heavily on the network boundary. | Protects individual resources as well as the network. |
| May grant broad access after a user connects. | Uses explicit access policies and least privilege. |
| Can allow attackers to move between internal systems. | Uses segmentation and access restrictions to limit lateral movement. |
| Often relies heavily on network location. | Considers identity, device health, resource, and risk. |

Traditional controls such as firewalls are still useful in a Zero Trust environment.

### Zero Trust Example

An employee wants to access a company's confidential database.

1. The employee requests access.
2. The system verifies the employee's identity.
3. It checks MFA, device health, and relevant risk signals.
4. It verifies that the employee has permission to access the database.
5. Access is granted only if the required policies are satisfied.
6. Suspicious activity can trigger additional checks or access restrictions.

### Important Points to Remember

- Being inside the office network does not automatically make a user trustworthy.
- Authentication and authorization are different.
- MFA strengthens authentication but does not replace authorization.
- Least privilege reduces the potential damage caused by compromised accounts.
- Microsegmentation helps limit lateral movement.
- Zero Trust is an overall security strategy, not a single product.
- Firewalls, endpoint protection, identity management, and monitoring can all support Zero Trust.

---

## 3. Load Balancers vs. Zero Trust

| Load Balancer | Zero Trust |
|---|---|
| Primarily distributes traffic across servers. | Controls and evaluates access to resources. |
| Helps improve performance and availability. | Helps reduce unauthorized access and limit the impact of compromised accounts or devices. |
| Uses routing algorithms and health checks. | Uses identity, permissions, context, and security policies. |
| Can provide security features such as TLS termination. | Is a broader security approach involving multiple controls. |
| Example: Distributing requests across three web servers. | Example: Allowing only an authorized, compliant device to access a database. |

### Final Summary

- **Load balancer:** Distributes traffic across servers.
- **Zero Trust:** Verifies access instead of automatically trusting users or devices.
- **Authentication:** Verifies identity.
- **Authorization:** Determines permissions.
- **Least privilege:** Gives only the access needed.
- **Microsegmentation:** Limits movement between systems.
- **Health checks:** Identify unavailable backend servers.
- **Failover:** Redirects service to an available system.
