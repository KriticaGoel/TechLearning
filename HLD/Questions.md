1. How do Ipv4 and IPv6 differ?

Answer:
IPv4 and IPv6 are two versions of the Internet Protocol used for identifying devices on a network. 

The main differences are:
- **Address Format**: IPv4 uses a 32-bit address format, while IPv6 uses a 128-bit address format.
- **Address Space**: IPv4 has a total of approximately 4.3 billion addresses, whereas IPv6 has a vastly larger address space with about 3.4 x 10^38 addresses.
- **Notation**: IPv4 addresses are written in decimal format (e.g.), whereas IPv6 addresses are written in hexadecimal format (e.g.).
- **Exhaustion**: IPv4 addresses are limited and have been largely exhausted, leading to the development of IPv6 to address this issue.
- **NAT Usage**: IPv4 often relies on Network Address Translation (NAT) to extend its address space, while IPv6 is designed to eliminate the need for NAT due to its vast address space.

2. what role does NAT play in managing IP addresses?

Answer:
NAT (Network Address Translation) is a technique used to manage IP addresses by allowing multiple devices on a local network to share a single public IP address for accessing the internet.

The key roles of NAT include:
- **Address Conservation**: NAT helps conserve the limited number of public IPv4 addresses by enabling multiple devices to use private IP addresses within a local network.
- **Security**: NAT adds a layer of security by hiding the internal IP addresses of devices from external networks, making it more difficult for attackers to directly access them.
- **Flexibility**: NAT allows for the reuse of private IP addresses across different local networks, facilitating easier network management and scalability.
- **Cost-Effectiveness**: By using NAT, organizations can avoid the need to obtain multiple public IP addresses, reducing costs associated with IP address registration.

3. What are the differences between public and private IPs?

Answer:
Public and private IPs serve different purposes in network communication.

**Public Ips**
1. Assigned by ISPs
2. Unique across the internet
3. Used for external communication
4. Can be static or dynamic
5. Requires registration with a central authority (IANA/Regional Internet Registries)
6. Examples: Web servers, email servers

**Private Ips**
1. Used within private/local networks
2. Cannot be accessed directly from the internet
3. Ranges defined by RFC 1918
4. Benefits -
    * Security (if any one know private ip address still system is not assessable for direct use)
    * Scalability (reuse of IPs in different networks)
    * Cost-effective (no need to register with central authority for private IPs)- get one public address and create multiple private IPs using NAT


4. Can you explain the differences between static and dynamic IPs?

Answer: 

5. What is the function of ICANN in internet governance?

Answer:

6. why do we need private IPs in system design?

Answer:

7. How does DNS resolve IP addresses in large-scale systems?

Answer:

8. Explain how a load balancer distributes traffic using Ips? 
Answer: 