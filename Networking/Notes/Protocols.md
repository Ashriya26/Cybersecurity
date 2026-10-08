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

     

   


