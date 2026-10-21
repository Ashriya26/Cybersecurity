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
