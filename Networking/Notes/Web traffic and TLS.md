HTTP Methods:
- It consists of a client and a server which communicate with each other by request and response
- They have HTTP Request methods: get, post, patch, head, connect, put, options, delete, trace
- These 4 HTTP methods correspond to 4 CRUD operations : create-POST, read-GET, Update-PUT, Delete-DELETE
- Main ones are get, post, put and delete
i. HTTP GET request:
- RequestMethod=GET
- simple requests for info
- should only retrieve data
- shouldnt result in modification of data

ii. HTTP POST Request:
-RequestMethod=POST
-modify underlying data
-create new resource

iii. HTTP PUT Request:
- RequestMethod=POST
- modify underlying data
- update existing resources

iv. HTTP DELETE Request:
- RequestMethid=Delete
- remove existing resource


HTTP status codes:
1XX - Informational
- 100 Continue — the client can continue sending its request.
- 101 Switching Protocols — the server agrees to switch protocols.
  
2XX- success code
- 200- OK- request succeeded
- 201-
u succeeded and also created new resource( new user acc, DB entries, or new forum posts)-> the server will return the location with the header. The header will give the  exact location of what u just created
- 204- success with no response ( delete, patch or put)-no data is sent back to the client, only success message would be sent back

3XX - Redirection
- 301
-this resource has permanently moved, update ur bookmark-> The location is being updated(Very imp. for search engine optimization(SEO))
- This is the digital equivalent of submitting a permanent change of address form to the post office
- if ur moving pages, use 301 to save ur sites authority
- 302
- temporary change of URL(unlike 301 which is permanent)
- this normally happens during server maintenance or A/B testing
- Its like the website saying..use this page for now, but please do come back to my main page if u want anything in the future
- 304
- Not Modified
- when ur browser visits a page, it can ask the server if this page was modified since I last time I downloaded it. If not, the server will reply with 304-> not modified
- this increased the page loading speed and also save bandwidth for both the client and the server

4XX series- client error codes
-400- bad request
- the server understood the request but would not process it bcz of the malformed code
- This happens bcz of syntax errors, missing info , outdated cookie
- 401
- unauthorized indication status code
- Its like teh server is saying, I know who u r trying to be, but u havent given me proper credentials to prove it
- missing or invalid credentials
- Its all abt identity like, did u log in? is ur session token expired? is ur username or password wrong?
- Once u fix it, ur good to go
- 403-Forbidden
- I know who u r, but u r absolutely not allowed to access this
- U r authenticated but u lack the necessary permissions or roles for that specific resource
- 404-Not found
- what ur looking for dosnt exist in that server
- the page might be deleted, the website was restructured, or a typo in the url, link u clicked was broken
- 405-method not allowed
- This is for the developers dealing with APIs
- It means, the resource u requested exists, but the http method that u used for it not valid( eg: trying a post method in an API that allows only get)
- 429- too many requests
- this is done to prevent spams
- If u refresh the page very fast or u call the API too many times, ull be hit by 429
- This is not an error, its just a pause, the server might send u a retry message to try after a while

5XX series- server side problems
-500-Internal server error
- catch all error( something like..Something broke, and I dont know how to describe it better)
- Unhandled exceptions, DB failure, Misconfigured server
- 502- bad gateway
- The middleman server got a bad response from the server it relies on
- occurs commonly in load balancers and microservice architectures where the requests form a chain
- 503- service unavilable
- Either overwhelmed or under maintenance
- The server receives ur request but it has maxed out, so it woulnt reply to ur messages and throws this error message
- 504-Gateway Timeout-a gateway did not receive an upstream response in time.


Headers and Cookies:

HTTP Headers:
- the communication between the client and server happens using HTTP methods
- The info sent consists of 3 parts: start line, Headers and Body
<img width="438" height="234" alt="image" src="https://github.com/user-attachments/assets/327f7317-137f-498d-a314-c0b678efb5d9" />
-Header: its the meta info abt the body and the http parameters
- collection of key-value pairs, it can be strings or numbers
- Types: Authentication, cahcing, connection management, content negotiation, cookies, misc, CORS, request context, Response Context, Message Body Info, Data Transfer Encoding, Proxies, Security, Redirects, Custom etc

i. User-Agent: 
- This tells the server who the agent is
- The agent is the client
<img width="365" height="115" alt="image" src="https://github.com/user-attachments/assets/8f7130e4-40dd-4ebe-98b3-9f54ef88f008" />
<img width="770" height="32" alt="image" src="https://github.com/user-attachments/assets/2987cc3b-a050-423e-a256-56c3cb4b9b0b" />

ii. Content-type:
- the data that is sent between the client and the sever is in the form of bits
- This type tells the client and the server how to encode or decode the data 
<img width="367" height="134" alt="image" src="https://github.com/user-attachments/assets/f220c42e-d48b-493e-bc86-f5120279fbe8" />

iii.Authorization:
<img width="368" height="151" alt="image" src="https://github.com/user-attachments/assets/3e84decb-c157-47c6-a3cf-0f4aa2dd12af" />

iv. Content Length:
- gives the length of the content sent to the client
<img width="357" height="167" alt="image" src="https://github.com/user-attachments/assets/5d63047d-f5fd-4aef-b99e-654e222d067f" />


Cookies:
- Its a small part of the data of a specific website that will be stored in the users system while they r browsing the web
- track users browsing history( to give targetted info)
- remembering login details
- track site visitor count- if a user visits a website 2 to 3 times a day, it can be counted as just 1 and not 2 or 3- this allows website owners to collect accurate data abt their website traffic
- LOU MONTULLI-> Inventor of http cookie
- This can be useful or also a breach in privacy based on how the website decides to use this info

Working:
- when u open a website for the first time, a cookie gets installed in ur hard-drive
- This then keeps track of ur sessions( like how much time u spend on that particular website)
- This can also help keep in track of ur items in cart, ur coupon codes, stores the info even if u log out from the website
- A cookie of a particular website can only track ur activity of that particular website and not of anything else or if ur logged into a different website
- Third party cookie:
  In a website u might have a button to like or share on Facebook. ass soon as u press these, they will communicate with Facebook and Facebook will now add a session cookie in ur system and would send u targeted adds on Facebook
- Its bcz of such things Europe has brought abt GDPR (General data protection Regulation) where u can opt out of use of cookies
  

HTTPS, SSL, TLS:
- if u send the data over http, anyone could read ur credentials if they could break into it
- Https encrypts this data making it unreadable other than the send er and the reciever.
- Https info is secured by TLS ( Transport layer Security) so even if a hacker gets access, he could only see jumbled data

TLS Handshake:
Step 1 : TCP handshake
Step 2: Certificate check
- this is where TLS handshake begins
- The client sends a client hello to the server
- In this hello message, the browser tells the server the following things:
  i. which TLS Version it uses( TLS 1.2, TLS 1.3 etc)
  ii. which cyber suites it supports(encryption algo. used to encrypt the data)
-Based on the Client hello, the server chooses to use a cyber suite and a TLS version sent by the client
- As a response, the server will send " Server hello" to the client
- The server will send a certificate to the client, and it includes many things
  i.public key ( Asymmetric encryption)
- Server hello done- at this time the client ahs the server certificate and also the client and server have agreed on the TLS version and cyber suite
  
Step 3:Key exchange
- this is where the client and server will come up with a share encryption key used to encrypt the data and this is where asymmetric encryption comes into picture
- with this the data encrypted by the client b the public key from the server can only be decrypted by the public key of the server and thats how the client send an encryption key to the server over the wide open internet
- This is how client Key exchange is done, here RSA is taken as an example
- At the end of this step, the encrypted session key by the client using the public key is sent to the server where its decrypted by the server with the public key to finally have the resultant session key

Step 4:Data transmission
- by the end of step 3, both the sides hold the session key
- 
