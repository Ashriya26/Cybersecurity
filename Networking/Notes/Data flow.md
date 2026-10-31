**End-to-End Network Communication: From Entering a URL to Loading a Webpage**

# End-to-End Network Communication: From Entering a URL to Loading a Webpage

## 1. Connecting to the Wi-Fi Network

Before accessing the internet, the laptop must establish a connection with a wireless network.

1. **Wi-Fi Network Discovery:** The laptop scans for available wireless networks (SSIDs). SSID stands for Service Set Identifier, which is the name of a Wi-Fi network.
2. **Authentication:** If the network is secured using WPA2/WPA3, the user must provide the Wi-Fi password. The authentication and key exchange process establishes a secure wireless connection.
3. **Connection Established:** Once authentication and association are successful, the laptop is connected to the wireless network.

However, being connected to Wi-Fi does not automatically mean that the laptop has an IP address or internet access.

## 2. DHCP – Obtaining an IP Address

Once connected to Wi-Fi, the laptop needs an IP address to communicate with other devices over the network.

This is where **DHCP (Dynamic Host Configuration Protocol)** comes into the picture.

DHCP automatically assigns network configuration details to devices.

The DHCP process follows four steps, commonly known as DORA:

| Step | Description |
|---|---|
| Discover | The laptop broadcasts a DHCP Discover message to find an available DHCP server. |
| Offer | The DHCP server offers an available IP address to the laptop. |
| Request | The laptop requests the offered IP address. |
| Acknowledgement | The DHCP server confirms the assignment and provides the network configuration. |

The DHCP server typically provides:

- **IP Address:** Identifies the laptop within the network.
- **Subnet Mask (SM):** Determines which devices belong to the local network.
- **Default Gateway (DG):** The router's IP address, which allows the laptop to communicate with networks outside its local network.
- **DNS Server:** The server responsible for resolving domain names into IP addresses.

Now, the laptop has the necessary network configuration to communicate with other devices and access the internet.

## 3. DNS – Resolving the Domain Name

Suppose we open a browser and enter:

`www.example.com`

Computers communicate using IP addresses rather than human-readable domain names. Therefore, the domain name must first be resolved into an IP address.

This is where **DNS (Domain Name System)** comes into play.

1. The browser or operating system first checks whether the domain's IP address is already available in its cache.
2. If it is not cached, the laptop sends a DNS query to its configured DNS resolver.
3. The DNS resolver may be provided by the ISP or a third-party provider, such as Google DNS (8.8.8.8) or Cloudflare DNS (1.1.1.1).
4. If necessary, the DNS resolver queries other DNS servers to find the correct IP address.
5. The DNS resolver sends the resolved IP address back to the laptop.

**DNS Resolution:** Converts a domain name (www.example.com) into an IP address that the laptop can use to communicate with the destination server.

Note: DNS generally uses UDP port 53, although TCP port 53 is also used in certain situations. Encrypted DNS protocols are also available.

## 4. Data Encapsulation – Preparing the Request

Now that the laptop knows the destination server's IP address, it needs to send a request to retrieve the webpage.

Before sending the request, the data goes through the TCP/IP networking model, where each layer adds its own information. This process is called **encapsulation**.

### Application Layer

- The browser creates an HTTP or HTTPS request for the requested webpage.
- For example, it may send an HTTP GET request to retrieve the webpage.
- HTTPS uses TLS to encrypt the communication.

### Transport Layer

- The application data is passed to the transport layer.
- For traditional HTTPS connections, TCP is commonly used.
- TCP adds source and destination port numbers.
- It also provides reliable delivery through sequencing, acknowledgements and retransmissions.

Example:
- Source port: An ephemeral port selected by the laptop.
- Destination port: 443 (HTTPS).

The resulting data is called a TCP segment.

Note: HTTP/3 uses QUIC over UDP instead of TCP.

### Internet Layer

- The TCP segment is encapsulated inside an IP packet.
- The IP header contains:
  - Source IP address: The laptop's private IP address.
  - Destination IP address: The IP address of the destination web server.

The IP packet helps route the data across different networks.

### Network Access (Link) Layer

- The IP packet is encapsulated inside a Wi-Fi frame (or Ethernet frame for wired connections).
- The frame contains source and destination MAC addresses.
- These MAC addresses help deliver the frame across the local network.

**Important:** The destination MAC address at this stage is normally the MAC address of the default gateway (router), NOT the MAC address of the remote web server.

## 5. ARP – Finding the Router's MAC Address

The laptop knows the destination server's IP address, but it must first deliver the packet to its default gateway to reach an external network.

How does it find the router's MAC address?

This is where **ARP (Address Resolution Protocol)** comes into the picture.

1. The laptop checks its ARP cache to see whether the MAC address corresponding to the default gateway's IP address is already available.
2. If the entry is unavailable, the laptop broadcasts an ARP Request asking which device owns the default gateway's IP address.
3. The router responds with an ARP Reply containing its MAC address.
4. The laptop stores this IP-to-MAC mapping in its ARP cache for future communication.
5. The laptop can now send the Wi-Fi frame to the router using the router's MAC address.

Note: ARP is used for IPv4 networks. IPv6 uses Neighbor Discovery Protocol (NDP) instead.

## 6. Router – NAT and Forwarding

Once the router receives the frame, it processes the packet and determines where it needs to go.

### NAT (Network Address Translation)

In a typical home network, devices use private IP addresses that are not directly routable over the public internet.

The router uses NAT, commonly Port Address Translation (PAT), to allow multiple devices to share a single public IP address.

For example:

- Laptop private IP: 192.168.1.10
- Router public IP: 49.xxx.xxx.xxx

The router translates the laptop's private source IP address and source port into a public IP address and mapped port.

It also maintains a translation table so that returning traffic can be associated with the correct internal device.

### Packet Forwarding

- The router examines the destination IP address.
- It checks its routing table to determine the next hop.
- It forwards the packet towards the internet through the appropriate interface.

The router may also have a built-in firewall that filters traffic according to configured security rules.

## 7. Internet – Reaching the Destination Server

The packet travels through several intermediate network devices, such as routers, before reaching the destination network.

At each hop:

- The router examines the destination IP address.
- It determines the next hop using its routing table.
- It forwards the packet towards its destination.

The IP packet generally retains its source and destination IP addresses across the route, although NAT devices can modify them.

The link-layer MAC addresses are different at each network hop because MAC addresses are used for local network delivery.

## 8. Server-Side Firewall and Web Server

Before reaching the web server application, the incoming traffic may pass through network firewalls and security controls.

### Firewall

- The firewall examines incoming traffic based on configured security rules.
- It checks factors such as source/destination IP addresses, ports and protocols.
- Only traffic permitted by the firewall policies is allowed to proceed.

For example, a web server may allow:
- Port 80 – HTTP
- Port 443 – HTTPS

Other ports may be blocked depending on the security policy.

The server may also have its own host-based firewall.

### Web Server

Once the connection reaches the web server, software such as Apache or Microsoft IIS handles the incoming HTTP request.

- The web server processes the request.
- It may retrieve static files or forward the request to a backend application.
- The application processes the request and may retrieve information from a database.
- The server generates an appropriate HTTP response containing the requested webpage or other content.

For HTTPS, TLS is terminated at the appropriate endpoint, such as the web server or a reverse proxy, where the encrypted HTTP data is decrypted.

## 9. Returning the Response to the Laptop

Once the server generates the response, it sends the data back to the requesting laptop.

The response follows the reverse network path through the internet.

1. The server sends the response towards the laptop's public IP address.
2. Intermediate routers forward the packets towards the destination network.
3. The home router receives the returning packets.
4. The router checks its NAT translation table to identify the corresponding internal device.
5. NAT translates the destination public IP address and mapped port back into the laptop's private IP address and original port.
6. The router forwards the packets to the laptop using its MAC address on the local network.

**Important:** The router uses its NAT translation table to identify the laptop. The laptop does not need to send another ARP request for the remote server. ARP is used for local network address resolution, and the router handles the local delivery.

## 10. Laptop – Receiving and Displaying the Webpage

Finally, the response reaches the laptop.

- The laptop's network interface receives the frames.
- The operating system processes the incoming packets and passes the data through the networking layers.
- TCP reassembles the data and handles reliability (for TCP connections).
- TLS decrypts the HTTPS data at the appropriate endpoint, in this case the browser.
- The browser processes the HTTP response.
- It parses HTML, CSS and JavaScript and may request additional resources such as images, fonts and scripts.
- Finally, the browser renders and displays the webpage.

**The webpage is now successfully loaded!**

---

## Important Concepts to Remember

| Concept | Purpose |
|---|---|
| SSID | Identifies a wireless network by its name. |
| WPA2/WPA3 | Secures wireless network access. |
| DHCP | Automatically assigns IP and other network configuration details. |
| DNS | Resolves domain names into IP addresses. |
| TCP | Provides reliable, connection-oriented data delivery. |
| IP | Provides logical addressing and routing between networks. |
| MAC | Provides local network frame delivery. |
| ARP | Resolves IPv4 addresses into MAC addresses on a local network. |
| NAT | Translates private and public IP addresses. |
| Firewall | Filters network traffic based on security rules. |
| Web Server | Handles HTTP requests and serves web content. |
| TLS | Encrypts communication to provide confidentiality and integrity. |

## Complete Flow – Quick Revision

Wi-Fi Discovery → WPA2/WPA3 Authentication → Connection Established → DHCP (DORA) → IP Configuration → DNS Resolution → HTTP/HTTPS Request → TCP/UDP → IP Packet → Wi-Fi/Ethernet Frame → ARP (Default Gateway MAC) → Router → NAT → Internet → Destination Firewall → Web Server → HTTP Response → Internet → Router → NAT Translation → Laptop → TLS Decryption → Browser Rendering → Webpage Displayed.


<img width="830" height="441" alt="image" src="https://github.com/user-attachments/assets/4fdd7c78-cc82-4014-859a-3fa9c876ed91" />
