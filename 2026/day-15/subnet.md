Subnet:

from big internet divided into smaller logical network or internet

CIDR (Classless Inter-Domain Routing) :

=> how to addrees assign?
     
2^(32-n) = ip address

if cidr notation is 1
n= 1 , 2^(32-1) = 2^31 = 2147483648

n=2, 2^(32-8)= 2^24 = 16,777,216

n=16, 2^(32-16) = 2^16 = 65,536

n = 24, 2^(32-24) = 2^8 = 256

n = 32, 2^(32-32) = 2^0 = 1

in this first address goes to : Network address
last one goes to : broadcast address


Subnetting → Divides a big network into smaller logical subnets to avoid IP waste, reduce broadcast traffic, and improve routing efficiency.

CIDR notation → Uses IP/prefix_length (e.g., /24) to define how many bits are for the network vs hosts. Formula: 
2
(
32
−
𝑛
)
 total addresses, minus 2 for usable hosts.

Private vs Public IP → Your laptop gets a private IP from the router; the router has a public IP from the ISP. Private IPs are not visible on the internet.

NAT → Network Address Translation lets multiple devices in a subnet share one public IP. It maps private IPs to the router’s public IP.

Routing flow → Laptop → Wi‑Fi Router (NAT) → ISP → Internet backbone → Web Server → Response back through the same path.

Web server → A computer in a data center that hosts websites. It has a public IP, and your domain name maps to it via DNS.

Shared hosting → Many websites can share the same public IP. The server uses the domain name (Host header) to serve the right site.

IPv6 → Provides an enormous address pool, ensuring IP exhaustion isn’t a problem in the future.






🚀 Day 19 of #90DaysOfDevOps

Today, I learned how networks are divided, how IP addresses are allocated, and how devices communicate with the Internet using subnetting, CIDR, NAT, and routing concepts.

🌐 **What is a Subnet?**

A subnet (sub-network) is a smaller logical network created by dividing a larger network into smaller segments.

Benefits of subnetting:

✅ Efficient IP address utilization
✅ Reduced broadcast traffic
✅ Better network performance
✅ Improved routing and security

📏 **CIDR (Classless Inter-Domain Routing)**

CIDR is a method used to allocate IP addresses more efficiently.

Format:

`IP Address/Prefix Length`

Example:

`192.168.1.0/24`

The number after `/` represents the network bits.

Formula:

`2^(32 - n)`

Where **n** is the CIDR prefix length.

Examples:

🔹 `/8` → 16,777,216 addresses

🔹 `/16` → 65,536 addresses

🔹 `/24` → 256 addresses

🔹 `/32` → 1 address

Important:

• First IP → Network Address

• Last IP → Broadcast Address

• Remaining IPs → Usable Host Addresses

🏠 **Private vs Public IP Addresses**

Private IP:

* Used inside local networks
* Assigned by routers
* Not directly accessible from the Internet

Public IP:

* Assigned by the ISP
* Visible on the Internet
* Used for external communication

Example:

Laptop → Private IP (192.168.x.x)

Router → Public IP assigned by ISP

🔄 **NAT (Network Address Translation)**

NAT allows multiple devices in a private subnet to share a single public IP address.

Without NAT, every device would require its own public IP.

Benefits:

✅ Conserves IPv4 addresses
✅ Improves security
✅ Enables Internet access for private networks

🛣️ **How a Request Travels Across the Internet**

1️⃣ Laptop sends request

2️⃣ Router performs NAT

3️⃣ ISP forwards traffic

4️⃣ Internet backbone routes packets

5️⃣ Request reaches Web Server

6️⃣ Response travels back through the same path

🌍 **Web Servers & Hosting**

A web server is a computer that hosts websites and applications.

Each server has a public IP address, and DNS maps domain names to those IPs.

Example:

google.com → Public IP Address

🏢 **Shared Hosting**

Multiple websites can share the same public IP address.

The server identifies which website to serve using the domain name (Host Header) in the HTTP request.

🚀 **IPv6**

IPv6 was introduced to solve IPv4 address exhaustion.

Example:

`2001:0db8:85a3:0000:0000:8a2e:0370:7334`

Benefits:

✅ Massive address space

✅ Better scalability

✅ Future-proof Internet connectivity

💡 Key Takeaway

Today's learning helped me understand how IP addresses are allocated, how subnetting improves network efficiency, how NAT enables Internet access, and how requests travel from my device to web servers across the Internet.

These networking concepts form the foundation for cloud networking, VPCs, subnets, route tables, and security groups in AWS.

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham #DevOps #Networking #Subnetting #CIDR #NAT #IPv4 #IPv6 #AWS #CloudComputing #Linux #NetworkEngineering #LearningInPublic









