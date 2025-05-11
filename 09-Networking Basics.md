# Common Networking Terms and Definitions
## Domain Name System (DNS)
- Global network of servers that translates between hostnames and IP addresses.
- *Internet phonebook*.

## Dynamic Host Configuration Protocol (DHCP)
- A way for computers on a network to be able to obtain configuration information from another computer on the network.

## Ethernet 
- Wired network hardware used by most computers today.

## Hostname
- The name of a computer that is easier to read and remember.

## Internet
- Globe-spanning network of interconnected computers that we use TCP-IP to communicate over.

## IP (Internet Protocol) Address
- A number assigned to computer for network addressing purposes.
- *Phone number* for a computer.
- Types: **IPv4**, **IPv6**.

## Network Mask (Netmask)
- Distinguishes between the network and the machine portions of an IP address.

## Router 
- A device that connects two or more networks together.
- Serves as a gateway between these two networks.

## Transmission Control Protocol - Internet Protocol (TCP/IP)
- A set of standards that underly most modern network connections at the software level.
- Backbone of the Internet.

## Wi-Fi
- Common name for wireless networking IEEE 802.11 standard.

# Four Things Needed for a Valid Internet Connection
- IP Address
- Netmask
- Router’s IP Address
- DNS Server’s IP Address

---

# Configuring a Network Connection
- **Automatic configuration is handled via DHCP.**
- **Types of DHCP**:
    1. **Fixed DHCP**: Each computer receives the exact same IP address every time it boots up.
    2. **Dynamic DHCP**: A computer receives possibly different IP addresses from the DHCP server every time it connects.
- **Establishing a Wi-Fi connection is easiest using the GUI method.**
- **Wireless Configuration Tools**:
    1. <code>iwlist</code>: Can identify nearby wireless networks.
    2. <code>iwconfig</code>: Can connect to and disconnect from specific wireless networks.
- **Wired Configuration Tools**:
    1. <code>ifconfig</code>: Brings up or shut down a specific network connection and associate a netmask to a particular piece of network hardware such as a network adapter.
    2. <code>route</code>: Adjusts the computer’s routing table.
    3. <code>/etc/resolv.conf</code>: Configuration file that contains the IP addresses of up to 3 DNS servers.
    4. **DHCP client**: Can configure a network connection automatically. Example: dhclient, dhcpcd
    5. There are also some distribution-specific Network scripts available which can be directly used to configure a network connection.

---

# Network Testing
- **Routing table**
- **PING**
    `If you can ping your local systems but not your remote systems, you must be having a router problem.
    `If you can ping the IP address but not the name of the device, you must be having a DNS problem.
    `If you cannot ping at all, you must be having a fundamental configuration problem.
- **Traceroute**: Tests the connectivity for breaks.
- **Domain Name Servers (DNS)**: <code>host</code>, <code>dig</code>, <code>nslookup</code>
- **Netstat**:'Swiss army knif' of networking tools.

---

# Network Protection (Basic Tips)
- Basic Tips
- Shut down unused servers
- Enable a firewall
- Use good passwords
- Be suspicious
- Keep your software up-to-date
