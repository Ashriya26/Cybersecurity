# Day 1 — How Data Travels Across a Network

## Objective

Understand how network communication is organised into layers and gain hands-on experience capturing and analysing network traffic using Wireshark.

## Tools Used

- Wireshark
- Npcap
- Windows
- Google Chrome

## Lab 1: Capturing Network Traffic

### Procedure

1. Installed Wireshark and Npcap on Windows.
2. Selected the active Wi-Fi network interface.
3. Started a packet capture.
4. Visited YouTube to generate network traffic.
5. Applied display filters to investigate specific protocols.

### Observations

Wireshark displayed captured packets with source and destination addresses, protocol names, packet lengths and packet information.

<img width="1282" height="1020" alt="image" src="https://github.com/user-attachments/assets/bfca7d6e-0a01-43f8-93ff-4c93f0214c34" />


## Lab 2: Analysing a TLS Client Hello

### Filter Used

```text
tls.handshake.extensions_server_name contains "youtube"
```

### Observed Packet

- TLS message: Client Hello
- TLS version indicated by Wireshark: TLS 1.3
- SNI hostname: `accounts.youtube.com`
- Source IP: `192.168.1.44`
- Destination IP: `192.178.173.139`
- Transport protocol: TCP
- Source port: `34342`
- Destination port: `443`

### What I Learned

The TLS Client Hello is part of establishing a secure connection. The Server Name Indication (SNI) extension can indicate which hostname the client wants to reach.

TCP port 443 is commonly used for HTTPS traffic. The hostname and destination IP address provide different information: the hostname identifies the requested service, while the IP address identifies the network destination.

<img width="1282" height="1020" alt="image" src="https://github.com/user-attachments/assets/f701e892-f397-47b7-a765-8dd9bed272d9" />
<img width="1282" height="1020" alt="image" src="https://github.com/user-attachments/assets/8121607c-65a1-4032-99c0-bb99b2ee3122" />


## Lab 3: Investigating DNS Queries

### Filter Used

```text
dns.qry.name contains "youtube"
```

### Observations

I applied the Wireshark display filter `dns.qry.name contains "youtube"` to identify DNS queries and responses related to YouTube.

I observed DNS queries from my computer (`192.168.1.44`) to the DNS resolver (`8.8.8.8`) for `www.youtube.com` and `accounts.youtube.com`.

Packet 982 contained a DNS response for the A record of `www.youtube.com`, returning multiple IPv4 addresses, including `142.251.152.4`.

Packet 2456 contained a DNS response for `accounts.youtube.com`, showing a CNAME pointing to `www3.l.google.com`, along with IPv4 addresses.

### What I Learned

- DNS translates domain names into information used to locate network services.
- An A record maps a hostname to an IPv4 address.
- A CNAME record provides an alias from one domain name to another.
- DNS queries travel from a client to a resolver, and DNS responses return the requested information when available.
- Wireshark allows DNS queries and responses to be inspected at the packet level.

<img width="1282" height="1020" alt="image" src="https://github.com/user-attachments/assets/e412984c-e3bd-426e-818f-129471d7c9ca" />
<img width="1282" height="1020" alt="image" src="https://github.com/user-attachments/assets/8d49f16e-14d0-4ea5-b37e-4a32d9311414" />


## OSI and TCP/IP Model Mapping

| TCP/IP layer | Related OSI layers | Examples |
|---|---|---|
| Application | Application, Presentation, Session | HTTP, DNS, TLS-related functions |
| Transport | Transport | TCP, UDP |
| Internet | Network | IPv4, IPv6 |
| Network Access | Data Link, Physical | Ethernet, Wi-Fi |

This is a simplified mapping between the two models.

## Key Learnings

- Wireshark captures and decodes network packets visible on a selected interface.
- IP addresses and transport ports provide different information about network communication.
- DNS helps investigate domain name resolution.
- TLS Client Hello messages can expose an SNI hostname when the extension is visible.
- HTTPS protects application data through encryption, although some connection metadata may remain observable.

## Conclusion

This lab provided practical experience capturing network traffic, using Wireshark display filters, inspecting a TLS handshake and investigating the relationship between network layers and application communication.
