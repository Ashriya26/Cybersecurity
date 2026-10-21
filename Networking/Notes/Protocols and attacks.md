ICMP( Internet control message protocol):
- error reports protocol used by routers, hosts and other networking devices to communicate error info/updates to other routers, hosts and networking devices
- ICMP messages are sent in a variety of error reporting contexts
    - when the source send a message to the recipient, if the message is too large, the recipient will drop that message and will send an ICMP message back to the source
    - when the gateway finds a shorter route for the message to travel on, when this happens, the router will send an ICMP message to the source and then the source will redirect its message to pass through the router
- ICMP is commonly associated to traceroute and ping( they r common network diagnostic tools that use ICMP messages
- Traceroute: allows admins to locate the source of a network delay
- Ping: used to collect info abt the latency
- NOTE: ICMP can also be exploited:
    - In DOS attack  the attacker can flood the server will multiple requests, bcz of which the server cannot provide services to its intended users
        - Ping sweep
        - ping flood
        - smurf attack
     - Bcz of these things the admins normally block the ICMP, and TCP/IP can work even with the network blocked
     - bcz of which, diagnostics, reliability and network performace can be negatively impacted

SSH(Secure shell):
- protects data from being attacked/stolen
- was developed to provide secured and reliable service over unsecure networks
- Its a go to things for remote works and secure file transfers
<img width="240" height="163" alt="image" src="https://github.com/user-attachments/assets/4a3609dc-cff7-49f2-bc2a-a6de12b7c39f" />
Working:
- First establish TCP connection
- Then teh client and server start version negotiation(which SSH version is used)
- Then is algorithm negotiation: which cryptographic algos would be used
<img width="415" height="173" alt="image" src="https://github.com/user-attachments/assets/c0f2a016-50f4-4eb8-ae53-198f50250825" />
- Then comes key exchnage
- then is the end of key exchnage
- the client will then a request a login into the server and the server will look into the authorized key stored and then try to encrypt the data with the matching key found
- if the login by the server is successful, the server will then send an encrypted random number back to the client: this shows that the server has the correct public key and the server has the correct corresponding private key
- The client will decrypt the data using its private key and send it back to the server, by which the server will understand that its a legitimate host
- Then it will start the session request and response
- the client then would send encrypted commands, which the server decrypts using its public key
- Then it will send the encrypted result to the client which it will decrypt
- This encryption and decryption will continue until the end of each session
  <img width="381" height="244" alt="image" src="https://github.com/user-attachments/assets/d4e6ab8c-7d9d-4583-ac01-02425f217fb9" />


FTP Vs SFTP:
- FTP:
    - used for transferring files over a computer network
    - it opens a control channel and a data channel to transfer data over a network
      <img width="386" height="156" alt="image" src="https://github.com/user-attachments/assets/845c88f2-6ef4-49cd-8e1c-c064327d82e3" />
- Reasons for using:
    - best for uploading and downloading extremely large files
    - fastest file transfer from 1 remote loc. to another
    - user friendly for daily business op. between stakeholders
    - ideal for backup of large amt of business data
    - web devs trust FTP to move their code to server hosting
- SFTP ( SSH File transfer protocol):
    - the function is almost the same
    - But it needs authentication
  <img width="406" height="166" alt="image" src="https://github.com/user-attachments/assets/f7f1c66f-7763-4037-8575-aea29c518639" />
- Reasons for using:
    - for sensitive data that needs encryption
    - widely used for compliance with federal regulations
    - businesses that need firewall friendly file transfer choose SFTP
    - popular with business that rely on Linux/Unix
    - Delivers more detailed metadata with ur files

TelNet:( Teletype network)
- a terminal emulation program that is used to access remote servers
- its a cmd line tool that runs on ur computer and thats used to communicate with the servers and send cmds to it remotely
- u can use this for: run programs, create folders, delete files, create files, transfer files, browse directories, start/stop sevices
- its also used to configure switches and routers and also check if the ports are open/closed on a server
- its a CMD line tool
- no GUI
- its fast, bcz it sends only cmds
- no encryption, so hackers might be able to see this
- bcz of this, its outdated and shouldnt be used, but if they r working with older servers or any older equipment, then there is no option
- alternate is SSH
- It will secure the data by encrypting it
- it also provides password and public key authentication


SMTP/ IMAP/ POP3:
- POP( post office protocol version 3):
  - Its an email program running on ur computer uses to communicate with the email sever to download the email( Eg : Thunderbird)
  - email is downloaded
- IMPA(Internet Message Access Protocol):
  - its a program that runs on ur device to access ur email o the email services servers
  - It assumes that the email server holds the master copy of ur email server and IMAP leaves the master copy of ur email on the email server, so the IMAP kind of gives u a window on the master copy so that u can access ur emails from any device
  - by this, if u had done any changer to any email on 1 device it would reflect in other devices too as ur doing the changes to the master copy
- SMTP ( Simple Mail Transfer Protocol):
  - its used to send the email
  - its the workhorse of email, its the protocol thats used to send the email from server to server
- Webmail:
    - it works differently
    - like gmail, ur accessing the master copy of the email, but u dont know how they are configuring stuff
    - some email services will allow u to fetch email from another account to ur account using POP3

SMB( server message block):
- this allows ur device to communicate with remote desktops and servers
- This helps u to transfer files
- For eg: imagine u have ur laptop, and there's a printer that's connected to the company computer. When u end a printer request, ur laptop will communicate or send a request to the company computer using SMB and then the printer would be sending a response like weather the file is being printed or not
- Versions:
    - SMB version 1: released by IBM, modified by : Microsoft
    - SMB version 2: improved performance
    - SMB version 3: increased security
    - The Infumus wannacry ransomware was an exploit of the vulnarability of SMB1
- If u have a very old laptop, update this to the most recent SMP so that u get better protection


RDP ( Remote desktop computer):
- this is a proprietary tool of ur desktop which allows u to control another control another computer using ur computer

working:
- RDP works by configuring the remote desktop. And it works over the TCP connections over the port **3389** by default
- u can also move the port from 3389 to 6895, this wouldnt make the port more secure, but would prevent anyone from assuming the obvious port
- the clinet is the one tht connects to the remote desktop and then takes over its control
- 1st step: TCP handshake btw client and server: SYN, SYN/ACK, ACK
- 2nd step: connection initiation: once the tcp is done, the RDP must find a way to communicate with the remote desktops, mouse, keyboard, GUI etc, for this it uses the port X.224 ( This is a single port which is further divided into individual conversation for different things like mouse, keyboard GUI etc)
- 3rd step: basic setting exchange and channel connection: the X.224 sits on top of TCP, but it dosnt handle the actual communication. The actual communication is handled by multi channel communication(MSC) which allows the server to successfully connect and communicate with the different devices between the sytems
- 4th step: RDP security component: securing the connection and encrypting the data before sending it using session keys
- There might be a possibility where the server can refuse the encryption and the data would be openly available
- 5th step: Secure settings exchange: communication between the client and the server
- 5th step: disconnection : the client send a disconnection request and the server sends a disconnection response, the data would still be available on either side, so this will be handled by the specified protocols to prevent any corruption or data loss and also the resources that were allocated on either sides must be deallocated


## ICMP, SSH, FTP, SFTP, Telnet, SMTP, IMAP, POP3, SMB and RDP

| Protocol | Full Form | Default Port | Purpose | Secure or Insecure? | Why? |
|---|---|---|---|---|---|
| ICMP | Internet Control Message Protocol | No TCP/UDP port | Used for network diagnostics and error reporting (e.g., ping). | Depends on usage | ICMP does not provide encryption or authentication. Attackers may abuse it for reconnaissance, network mapping, or certain denial-of-service attacks. |
| SSH | Secure Shell | TCP 22 | Secure remote login and command execution on another computer. | Secure when configured properly | Encrypts communication and supports authentication. Weak passwords, compromised keys, or poor configuration can still make it vulnerable. |
| FTP | File Transfer Protocol | TCP 21 (control); TCP 20 traditionally for active-mode data | Transfers files between computers. | Insecure by default | Usernames, passwords, and data are typically transmitted in plaintext, allowing attackers to capture them if they can monitor the traffic. |
| SFTP | SSH File Transfer Protocol | TCP 22 by default | Securely transfers and manages files over an SSH connection. | Secure when configured properly | Encrypts data and uses SSH authentication. Weak credentials, compromised keys, or incorrect permissions can still create risks. |
| Telnet | Teletype Network | TCP 23 | Provides remote command-line access to another computer. | Insecure | Sends login credentials and session data in plaintext, making them vulnerable to interception. SSH is the preferred alternative. |
| SMTP | Simple Mail Transfer Protocol | TCP 25, 587, 465 | Sends email between mail clients and mail servers or between mail servers. | Depends on configuration | Without TLS, email credentials and message contents may be exposed in transit. SMTP does not inherently guarantee end-to-end encryption. |
| IMAP | Internet Message Access Protocol | TCP 143; TCP 993 for IMAP over TLS | Accesses and synchronizes emails stored on a mail server. | Depends on configuration | Without TLS, login credentials and email data may be intercepted. Use IMAP over TLS. |
| POP3 | Post Office Protocol version 3 | TCP 110; TCP 995 for POP3 over TLS | Retrieves emails from a mail server, traditionally downloading them to a client. | Depends on configuration | Without TLS, credentials and email contents may be exposed in transit. Use POP3 over TLS. |
| SMB | Server Message Block | TCP 445 commonly | Shares files, folders, printers, and other resources across a network. | Depends on version and configuration | Outdated SMB versions, weak access controls, or missing patches can expose files and enable attacks. SMBv1 is particularly risky. Use modern SMB with signing and encryption where appropriate. |
| RDP | Remote Desktop Protocol | TCP/UDP 3389 by default | Provides graphical remote access to a Windows computer or server. | Depends on configuration | Exposed RDP services can be targeted by brute-force attacks, stolen credentials, and unpatched vulnerabilities. Use Network Level Authentication (NLA), MFA, VPN or a secure gateway, and restrict access. |


-SSH vs Telnet
Both allow remote command-line access. SSH encrypts the session, whereas Telnet sends data, including credentials, without encryption by default.
Remember: SSH = secure remote shell; Telnet = plaintext remote shell.
- FTP vs SFTP
FTP transfers files without encryption by default. SFTP transfers files through SSH, protecting the connection with encryption.
Remember: SFTP is not simply FTP with an extra security setting; it is a different protocol
-- SMTP: Sends email.
- IMAP: Accesses and synchronizes email on the server.
- POP3: Retrieves email, often by downloading it to a client.
All three can use TLS to protect data in transit. TLS alone does not necessarily provide end-to-end email encryption.

Which protocols are insecure?
- The important distinction is that a protocol can be insecure by default, or it can be secure only when configured correctly.
- NOTE :FTPS is another secure file-transfer option. It is FTP protected by TLS, whereas SFTP operates over SSH.
## Which Protocols Are Insecure?

- A protocol can be insecure by design, or it can be secure only when configured correctly.
- **Note:** FTPS is another secure file-transfer option. It is FTP protected by TLS, whereas SFTP operates over SSH.

| Protocol | Main Security Concern | Safer Approach |
|---|---|---|
| FTP | Plaintext credentials and data | SFTP or FTPS |
| Telnet | Plaintext credentials and session data | SSH |
| SMTP without TLS | Email data and credentials may be intercepted | SMTP with properly configured TLS |
| IMAP without TLS | Mailbox data and credentials may be intercepted | IMAPS or IMAP with STARTTLS |
| POP3 without TLS | Downloaded messages and credentials may be intercepted | POP3S or POP3 with STARTTLS |
| ICMP | Can be abused for reconnaissance or attacks; no built-in encryption | Appropriate network filtering and monitoring |
| SMB | Risks from outdated versions, vulnerable configurations, and excessive permissions | Modern SMB, patches, restricted access, and appropriate signing/encryption |
| RDP | Exposed remote login service and credential attacks | NLA, MFA, restricted access, and a VPN or secure gateway |
| SSH / SFTP | Risks from weak credentials, compromised keys, or misconfiguration | Strong authentication, key protection, updates, and access controls |


Quick memory trick
- ICMP → Diagnostics and error messages
- SSH → Secure remote terminal
- FTP / SFTP → File transfer
- Telnet → Insecure remote terminal
- SMTP → Send email
- IMAP → Synchronize email
- POP3 → Retrieve email
- SMB → Share files and printers
- RDP → Remote graphical desktop



ATTACKS:

ARP Spoofing:( ON -PATH attach or Man-In-The-Middle attack)
- ARP used to resolve the IP addresses to MAC address
- for 1 device to communicate with anote device, they need the mac address of that device
- For a device to send a message to another device it needs its MAC address, but when it dosnt know, it will send a broadcast message, asking whats the mac address of the device with IP address as .....The corresponding device would respond to this broadcast using saying This is my MAC address. This is then stored in the client's ARP cache so that in the future if they have to communicate, it can use this line, instead of sending a braddcast and creating a new network
- SPOOFING: its when a device acts asif its the legitimate device inorder to intercept or steal data
- Now there would be a hacker who tries to intercept the network between the host and the server and instead of the router, the hacker would send the response for the broadcast sent by the hacker saying, m the one with IP address bla bla and this is my MAC, and when he does so, the client will receive it, and update its ARP cache to store this NEW MAC address for the corresponding IP address, and the hacker would also connect to the router the similar way. By this, he would act as a middle man between the client and the router and understand the communication that happens between them
<img width="415" height="165" alt="image" src="https://github.com/user-attachments/assets/8441b9d6-69aa-4c6c-94e3-e2af2b908354" />


MITM ( Man-In-The-Middle attack):
- Attacker can position himself btw ur device and the actual network, this is called MITM
- The attacker can intercept the communication happening between the 2 parties and oversee their connection, with both of them not knowing that there is an attacker present
- There r several types of MITM attacks that cybercriminals can sue to intercept and manipulate communication btw the 2 parties
    - IP spoofing
    - DNS spoofing
    - HTTPS spoofing
    - Wi-FI Eavesdropping
    - Email Hijacking
    - ARP poisoning
- ARP Poisoning:( ARP Spoofing)
    - most dangerous and most potential MITM attck
    - The request sent by the client may never get a response back or the entire communication can be seen by the hacker
- DNS Spoofing ( DNS Cache Poisoning):
    - the hacker redirects the user to another fake webiste or application by manipulating the DNS resolution process
    - when the client types in a domain name, the DNS resolver will send a request to the DNS server requesting for an IP address. The server will look into its cache if it has a corresponding IP address for the domain name and would send it to the client. The client would then use this IP address to connect to the website on the internet
    - But, there would be a situation when the client is sending the request to the DNS server to resolve the IP address, an attacker can intercept the connection and give its own IP address as the resolved IP address for the domain name. bcz of which the user would be redirected to the fake website and this would collect sensitive info like login credentials, financial info or also install malware on ur device

SYN flood attack:
- This is a volumetric attack at layer 4
- In a TCP model, first the client will send SYN, the server will send SYN-ACK and then the client will send an ACK
- In this attack, the client will send the syn, the server will send a syn-ack, but would never recieve a ack back..and at this moment of time, the connection between the client and the server is left open and the client would be sending mutiple SYN messages to the server making it overwhelmed by the volume
- the server is allocating the resources for the client request, but bcz theres no acknowledgement sent from the client side, it still remains open, and this happens to all the SYN requests sent bcz of which the server ends up exhausting its resources like CPU and bandwidth and they wouldnt be available for the actual devices
- Another way is that the client would send the SYN message and also spoof the IP address-> like sending the attacker's host IP instead of the legitimate client. In this case the Sever would send the SYN-ACK message to this attacker's host, rather than the legitimate one, this would let them be confused asto from where the attack is actually originating from

DoS( denial of service) and DDoS (distributed denial of service) attacks:
- DoS:
    - its overwhelming a website using illegitimate traffic making the server overwhelmed by the amt of traffic and it would be able to prove the services to the actual intended users
    - the attacker will send a large amt of requests so that it exhausts its resources like the CPU, memory and bandwidth
    - TCP SYN flood:( explained previously)
        - targets the handshake process of TCP
        - TCP is known for its reliability, ordered, sequence etc
        - TCP is used in web browsing, email, FTP and remote access(SSH)
    - UDP flood:( User datagram protocol)
        - It overwhelms the networks or servers with a flood of UDP packets
        - UDP is connectionless-> sent independently and dont require handshake to est. connection
        - no ack/verification-> so it wouldnt know if the traffic is from a legitimate source and would try to process each packet
        - difficult to mitigate UDP flooding attack bcz it makes use of the stateless process of the UDP to perform attacks making it difficult to differentiate between actual and fake traffic
    - HTTP flood:
        - overwhelms the websites with a flood of http requests
        - using botnet
        - targets specific URLs or web servers
        - GET floods, POST floods , mixed-method floods(combining both GET and POST requests)
- DDoS:
    - This is a process where a large number of compromised devices are combined together inorder to generate a large amt of traffic
    - These compromised devices are called Zombies/bots and the network of these is called a botnet, and the control of this botnet is with the attacker
    - Its very difficult to mitigate the DDoS than DoS bcz the traffic comes from multiple devices and its difficult to differentiate the legitimate and the fake traffic
 
- GitHub(2018)-> DDoS
- Sony Play station network(2011) - PSN
- ProtonMail ( 2015)-> DDoS-> ransom payment but proton mail refused
**Identifying these traffics**
  - Traffic analysis: observing abnormal spikes and patterns
  - wireshark, tcpdump and NetFlow: provide real time visibility into network traffic and help identify anomalies
  - Rate limiting mechanisms: limits the number of requests coming from a single source for a particular time-frame( eg, 1 source can send only 2 or 3 requests to the target in 1 second)-> Firewall, Load balancers and Intrusion Prevention systems often include this rate limiting features
  - Configuring Access Control Lists (ACLs) on routers, firewalls etc to filter incoming traffic based on source IP address, protocols and ports
  - Web Application Firewalls( WAFs): inspect and filter HTTP traffic blocking malicious users and known attack patterns
  - Content Delivery Networks(CDNs): distribute traffic to multiple networks to prevent DDoS attack by using caching and load balancing
  - Anomaly detection systems: monitor network behavior and alert the admin to deviation from normal patterns( IDS, IPS and SIEM use Anomaly detection systems)
  - DDoS Mitigation services: provides cloud based protection for large scale enterprises using advanced detection and leveraging techniques
  - Geolocation filtering: blocks traffic from specific geographical location thats known for creating malicious traffic
  - IP reputation lists: They contain non-malicious IP addresses associated with botnets, attackers and some devices, so blocking such ip addresses can reduce the DDoS attacks
  - Behavioural Analysis techniques: it analyses the normal patter between the communication fo teh client and the server and observes for any kind of diviation
  - Scalable infrastructure: with redundancy and failover capabilities by absorbing and mitigang the traffic by distributing it to multiple servers and data centers
  - Network segmentation: dividing the network into multiple segments, this will help prevent DoS and DDoS attacks from accessing critical resources
  - Emergency response plans: They help during the DDoS or DoS attacks
  - SYN Cookies: cryptographic technique used to mitigate TCP SYN Flood attack by eliminating the need to allocate the resources to incomplete connections, so here instead of generating a connection queue, it generates a SYN Cookie, which contain enough info to verify the client's request


Sniffing:
- Hacking( intercepting and capturing) all the data packets sent over a network- act of monitoring data packets
- Its a one of the DoS attack and hackers use software and hardware tools to sniff network traffic for sensitive info
- Types:
    - Passive Sniffing:
        - the attacker just watches the data packets passing through the network and dont do anything
        - This is done when the hacker just want to collect info like what kind of data is sent over the network or the info abt the target etc
    - Active Sniffing:
        - Here the attacker can actively look into whats happening and simultaneously perform DNS poisoning, MAC spoofing and MAC flooding attacks also
- Common sniffing tools:
    - wireshark
    - metacap : u can perform many types of MITM attacker
    - tcpdump : well known packet analyzer
- Detecting snififng attacks:
    - involves monitoring network traffic for anomalies
    - using IDS can help spot suspecious activities
    - regular audits and security checks are key in spotting sniffing attempts
 
       
