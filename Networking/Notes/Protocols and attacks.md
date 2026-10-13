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

