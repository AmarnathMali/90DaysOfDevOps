IP Address:
3.33.251.168 -> United States Washington Seattle Amazon Technologies Inc.


244.5.0.25 -> india Maharashtra pune

240.1.12.6
240.1.8.13
240.1.8.25

traceroute:

Router: A router is a networking device that connects different networks together and decides the best path (or route) for data packets to travel.	

Traceroute is a network diagnostic tool that shows the exact path your data packets take across the internet, listing each router (hop) along the way and measuring the delay at each step. It’s used to troubleshoot slow connections, packet loss, or routing problems.

these data centers gives the data, if data is static/Static data means unchanging information that stays the same unless explicitly modified. 
examples: Country codes → The ISO list of country codes (IN for India, US for United States). These don’t change often, so they’re stored as static reference data.

CDN -> these static data comes from one server which is named as CDN (content delivery network)

What an Edge Location Means?
An edge location is a small data center in the AWS global network that sits close to end users, designed to deliver content faster and more securely. For you in India, AWS has edge locations in major cities like Mumbai, Chennai, and Hyderabad, which help speed up access to services like CloudFront, Route 53, and Global Accelerator.

Purpose: It caches and delivers content (like images, videos, or API responses) closer to users, reducing latency.

Region:
such as N.Verginia, ohio, Mumbai, Hyderbad these location where data centers are there (AWS)

 a region is a specific geographic area where a provider (AWS, Azure, GCP) has one or more data centers.

availability zones/Local Zones: A local zone is a type of cloud infrastructure that extends a provider’s region closer to end users in specific cities, so applications can run with ultra-low latency without needing a full region nearby.
Smaller data centers placed in metro areas, directly connected to an AWS Region.
Purpose: Run workloads that need single-digit millisecond latency (like gaming, video rendering, or real-time analytics).

Example: AWS has local zones in Delhi, Kolkata, Bengaluru, and Chennai, connected to the Mumbai region.

AWS has 39 Geographic Regions	

this is how physical internet looks,

now new chapter:

## 2) Addressing for internet

from one address to  other address to connect share we need unique address, thats where interent protocol comes which defines set of rule how to connect uniquely to that particular address. 
that address called as IPv4 -> 4.3 billion unique address

so they got know that this much will not enough for the entire world they came with new address IPv6

IPv4 is defined like this: 0-255.0-255.0-255.0-255 (4 octet)

IPv6 is defined like this:- 0000–FFFF:0000–FFFF:0000–FFFF:0000–FFFF:0000–FFFF:0000–FFFF:0000–FFFF:0000–FFFF       ~340 undecillion (virtually unlimited)

0000–FFFF = 0–65,535 in decimal, as its 128 bit complex address, again preferred to IPv4

why IPv4 is still widely preferred?
Compatibility → Works with almost all existing devices, apps, and networks.

Simplicity → Easier to read, configure, and troubleshoot.

Infrastructure cost → Upgrading to IPv6 requires hardware, software, and training investments.

Dual-stack preference → Systems run both IPv4 and IPv6, but IPv4 is chosen by default for reliability.

Global support → IPv4 works everywhere — even where IPv6 isn’t deployed yet.

NAT usage → Allows many devices to share one public IP, delaying exhaustion.

In short: IPv4 remains dominant because it’s simple, universal, and still “good enough” thanks to NAT and dual-stack setups.
