DNS: domain name system

computer -> DNS Resolver -> Root Resolver
			 -> TLD Server   -> Authoritative server -> website -> response

How does the data move in the internet?

OSI Model =>

WhatsApp -> application
	-> presentation
	-> session
	-> Transport
	-> Network    ->
	-> Data link
	-> physical     -> cables, router , switch
	

let's suppose form your laptop to a website you are trying to reach.

Physical Layer: laptop -> it is connected with either WIFI/router or LAN cables
here you have to understand at internet level address is IP address. and for local level mac(Media access control) address is there for each device.
2. Data Link layer: when device is  identified through mac address
3. Network layer:  packets forwarding with ip address
4. Transport layer:  where our data transport in two way TCP/UDP
5. session : connection established, authentication happens here
6. Presentation: here where data is encrypted
7. Application: where our day to application comes, WhatsApp

TCP/ip contains 4 layers
application  -> it includes application, presentation, session layer of osi
Transport layer -> transport layer of osi
internet layer -> Network
network access layer ->  datalink and physical layer


osi model contains 7 layer  - theory concept
TCP model contains 4 layers - practical

Transport layer is very important, it operates on client server model
in this 1. TCP
	2. UDP

client 						 server

sync	-------------------------------------->   2. Acknowledgement to synchronize request, server sends this acknowledgement message to client back
					|
3. Acknowledged	<------------------------


This is called 3 way handshake.



TCP -> HTTP protocol -> which is used to text transport

-------------------
security for the internet(VPC)

TLC
UFW allow

firewall -> ingresss
	-> egress

Protocol:ip: port

HTTPS: :443
ssh: :22
SMTP: :465


what is port??
=> ports are communication endpoints used to direct incoming and outgoing data to the correct application or service on a device

VPC (virtual private cloud)

public subnet                      			private subnet
	
internet gateway through		 	here almost sensitive data will be stored,
it connects the internet to			database, user data those things.
public subnet inside devices,
here we store thing which should be in 		it communicates, through pubic subnet via NAT gateway(Network address translation)
public, like website, applications such
 as youtube,
	
Internet → Internet Gateway → Public Subnet (Web Server) → Private Subnet (Database)

Private Subnet → NAT Gateway → Internet (for outbound traffic only)

🔄 Flow Example
Your app server in a private subnet wants to call an external API.

It sends the request to the NAT Gateway in the public subnet.

NAT Gateway translates the private IP → public IP and forwards it through the Internet Gateway.

The external server replies to the public IP.

NAT Gateway maps the response back to the original private IP and delivers it to the app server.
