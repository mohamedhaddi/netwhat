# NETWHAT?

Let's figure it out!

## OSI MODEL

In order for network communication to take place, there needs to be a set of standards, and that's why the **OSI (Open Systems Interconnect) model** was developed.

The OSI model describes how information from a software, in one computer, moves through a network, to reach software in another computer. And it does this by breaking down this huge task of data communication, into 7 different layers. Giving control of a data being sent from one layer to another, and these layers are numbered from 1 to 7 starting from the bottom:

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Layer&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Function |
| :---: | --- |
| 7. Application | Manages communications between applications; supports application protocols such as email, HTTP, and FTP; at this layer, **data** still resembles something that people can read. |
| 6. Presentation | Converts **data** into a form that can be sent over a network; data is compressed or decompressed, and encrypted or decrypted; sometimes referred to as the translation layer. |
| 5. Session | Controls the dialog during communications; establishes, manages and terminates the connections between the local and remote applications; also known as the "traffic cop" because it directs network traffic. |
| 4. Transport | Provides the transfer of **data segments** between end users; responsible for resending any packets that do not receive an acknowledgement from the destination; guarantees that packets are received. |
| 3. Network | Responsible for routing the **data packet** based on its logical IP address; it **fragments** and **reassembles** the **packets**; instructs data on how to find its ultimate destination. |
| 2. Data Link | Responsible for sending **data frames** to the physical layer; data packets are encoded and decoded into bits; handles flow control and frame synchronization; divided into **2 sub-layers**: the Media Access Control (**MAC**) layer and the Logical Link Control (**LLC**) layer. |
| 1. Physical | Defines the network standards and physical characteristics of a network. Such as connectors, media types, cables, voltages, etc.; defines the topology of a network. |

## IP Address

- An IP (Internet Protocol) address is a numeric address.
- It's an identifier for a computer or device on a network.
- Every device on a network needs to have an IP address to communicate.
- Consists of two parts:  A network address and a host address.
- There are 2 types of IP addresses: **IPv4** (the most common one) and IPv6.

### IPv4

- IPv4 is the current version of IP addresses.
- It's a **32-bit** numeric address written as four numbers separated by periods.
- Each one of these numbers is called an **octet**. *e.g.:* `66.94.234.13`
- The number range in each octet, is 0 --- 225.
- This address version can produce **4,294,967,296** possible unique addresses.

### <a id="binary" style="text-decoration: none;">IPv4: BINARY LESSON</a>

***8 Bit Octet Chart:***
| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
| --- | --- | --- | --- | --- | --- | --- | --- |

Let's take for example: `66.94.29.13`
First octet is 66, how do we get a binary number from 66? First we look at the Octet Chart, and we would put 1 under the numbers that would add up to the total of 66, so: 64 and 2.

66 = 64 + 2 = `0.1.0.0.0.0.1.0`
94 = 64 + 16 + 8 + 4 + 2 = `0.1.0.1.1.1.1.0`
etc.

`66.94.29.13` is: `01000010.01011110.00011101.00001101`

### IPv6

- IPv6 is the next generation of IP addresses.
- It's a 128-bit hexadecimal address. *e.g.:* `76DC:4F59:34CF:71CD:9DC6:89CD:45D6:67A2`
- Capable of producing over **340 undecillion** addresses.

## SUBNET MASK

An IP address consists of 2 parts: A **network** address and a **host** address.
`173.16.0.0`
To tell which part is which, we need the subnet mask:
`255.255.0.0`
A subnet mask reveals how many bits of the IP address are used for the network by masking the network portion of the IP address.

The way to tell which portion of this IP address is the network portion, is when the subnet mask's binary digit is one, it will indicate the position of the IP address that defines the network:
`173.16.0.0` is: `10101101.00010000.00000000.00000000`
`255.255.0.0` is: `11111111.11111111.00000000.00000000`
So we'll cross out all the digits in the IP address that line up with ones in the subnet mask:
`173.16` is the network portion, and the remaining `0.0` is the host portion.

## CLASSES AND RANGES

IP addresses are assigned to different organizations and blocks, and these blocks are divided into 5 classes, and you can tell by the number in the first octet which class an IP address belongs to.

| Class | First Octet Address &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Default Subnet Mask | Number of Networks | Number of Hosts | More Information |
| :---: | :---: | :---: | :---: | :---: | --- |
| A | 1 --- 126 | 255.0.0.0 | 125 | 16,777,214 | Mainly given to large organizations, because of the tremendous amounts of IP addresses it can give out |
| B | 128 --- 191 | 255.255.0.0 | 16,382 | 65,534 | Given to medium-sized organizations |
| C | 192 --- 223 | 255.255.255.0 | 2,097,150 | 254 | Given to small organizations |
| D | 224 --- 239 | | | | Multicast Addresses
| E | 240 --- 254 | | | | Restricted/Experimental
*127 is reserved for loopback testing*

## PRIVATE IP

Unlike public IP addresses, private IP addresses do not have direct access to the internet (Since they're not publicly registered from the ISP).
Let's say we run a small business and we need 10 IP addresses to be connected to the internet, instead of registering 10 IP addresses from our ISP, we can have just 1 publicly registered IP address, and set 10 private IP addresses that will be all translated into the one public IP, so they can also have access to the internet.

This not only save money, but it also helps prevent having a shortage of public IP addresses.

Private IPs are typically used on local networks, like homes, schools and businesses.

### Ranges

Private IP ranges have three classes:
| Class | IP Range | Default Subnet Mask |
| :---: | :---: | :---: |
| A | 10.0.0.0 --- 10.255.255.255 | 255.0.0.0 |
| B | 172.16.0.0 --- 172.31.255.255 | 255.255.0.0 |
| C | 192.168.0.0 --- 192.168.255.255 | 255.255.255.0 |

## SUBNETTING

The word "subnet" stands for "sub-network", meaning a smaller network within a larger one.
Subnetting is basically breaking down a large network into smaller networks, or subnets. It's mainly done to make your network more manageable.

*e.g.:*

Let's say we have a company with 3000 employees, and our ISP assigned us with a class B IP address `173.16.0.0` with a default subnet mask (`255.255.0.0`).
As we already know, a class B IP address will allow us approximately 65,000 IP for all our computers.
But to avoid various traffic issues, or if the computers are on multiple separate physical networks, we'll need to breakdown the network to subnets.

Subnetting is basically done by changing the default subnet mask (`255.255.0.0`) by borrowing some of the bits that were designated for host, and using them to create subnets.
Let's say we want to break down this network into 3 smaller ones, the formula we would use is `2^n - 2`, where `n` equals the number of bits we need to borrow from the host portion of the subnet mask. So we need to make a custom subnet mask that is equal to **at least** 3 subnets or larger.

Let's try `n = 2`: `2^2 - 2 = 2`
The resulting 2 is not going to work because we need at least `3` subnets.

Let's try `n = 3`: `8 - 2 = 6`
This means we need to borrow `n = 3` bits from the host portion, which will give us `6` subnets, which is fine because all we need is 3 subnets.

So let's borrow those 3 bits:
 1. 255.255.0.0
 2. **11111111.11111111. ~~000~~** 00000.00000000
 3. **11111111.11111111. 111** 00000.00000000
 4. 255.255.224.0

Then our new custom subnet mask is `255.255.224.0`, which will allow us to have 6 subnets and set a 1000 host per subnet.

## ADDRESSING METHOD

There are two ways that a computer can be assigned an IP address, it can be done either by using a dynamic IP, or a static IP.

- ### Dynamic IP:
A dynamic IP is when a computer gets an IP address automatically from a *DHCP (Dynamic Host Configuration Protocol)* server.

A DHCP server automatically assigns a computer with an IP address, and in addition to an IP address, it can also assign a subnet mask, default gateway and a DNS server.
When this option is chosen, the computer sends out a request for an IP address, then the DHCP server will assign an IP address from its pool and deliver it to the computer.

Dynamic IP addressing is the best choice because it makes managing a network a lot easier.

- ### Static IP:

A static IP is when a user manually assigns a computer with an IP address, so there is no need for a DHCP server.
This kind of IP addressing is also known as permanent, because unlike dynamic addressing, where the IP address can change automatically, a static IP only changes if the user decides to.

- ### Self-assigned:

If a computer can't reach a DHCP server, for instance, if the DHCP server goes down, or if the connection to it is lost, then the computer itself will assign its own IP address. This IP address will be in the 169.254.0.0 network, and this type of self-assigned addressing is called *APIPA (Automatic Private IP Address Assignment)*. Computers (running Windows 98 or later) do this to be still able to communicate with other computers on the same network that also have self-assigned IP addresses.
If a DHCP server later becomes available, the computer changes its IP address to one that's obtained from a DHCP server.

## TCP/IP PROTOCOL SUITES

### TCP/IP Model

The **TCP** (Transmission Control Protocol)/**IP** (Internet Protocol) model is a concise version of the **OSI** (Open Systems Interconnect) model. It contains **four** layers, unlike **seven** layers in the OSI model. It should be noted that this model was not intended to be a rigid reference model into which new protocols have to fit in order to be accepted as a standard.

The TCP/IP model layers are:

| | |
| --- | --- 
4. |  Process/Application Layer
3. | Host-to-Host/Transport Layer
2. | Internet Layer
1. | Network Access/Link Layer

### TCP (Transmission Control Protocol):

- TCP is one of the main protocols used in a TCP/IP network.
- It's a **connection oriented protocol**, which basically means it must first **acknowledge a session** between two computers that are communicating before they start delivering data, and it does this by using a **three-way handshake**.
- TCP guarantees the delivery of data. If data was missing, then TCP **will** resend it.
- TCP doesn't not support broadcast.

### UDP (User Datagram Protocol):

UDP is very similar to TCP, it is also for sending and receiving data, but the main difference is:
- UDP is a **connectionless oriented protocol**, which means that it **does not establish a session**.
- UDP **does not guarantee data delivery** (fire-and-forget).
- Because of the less overhead that's involved, of not guaranteeing data delivery, **UDP is faster than TCP**.
- UDP supports broadcast.

### Other protocols

**FTP** (File Transfer Protocol) --- **TFTP** (Trivial File Transfer Protocol) --- **SFTP** (SSH File Transfer Protocol) --- **SMTP** (Simple Mail Transfer Protocol) --- **POP3** (Post Office Protocol) --- **IMAP4** (Internet Message Access Protocol) --- **HTTP** (Hypertext Transfer Protocol) --- **HTTPS** (Secure Hypertext Transfer Protocol) --- **Telnet** --- **SSH** (Secure Shell) --- **ARP** (Address Resolution Protocol) --- **RARP** (Reverse Address Resolution Protocol) --- **NTP** (Network Time Protocol) --- **SCP** (Secure Copy) --- **SNMP** (Simple Network Management Protocol)

## PORTS

When data is sent over the internet to your computer, it needs to know how to accept it, and you computer accepts this data using ports.

- A port is a logical connection that is used by programs to exchange information.
- These ports are categorized by 2 protocols: TCP and UDP.
- Ports are identified by a **unique** number.
- A port number ranges between 0 and 65535.

| Port Number | Service | Port Number | Service |
| :---: | :---: | :---: | :---: |
| 80 | HTTP | 20,21 | FTP |
| 443 | HTTPS | 161 | SNMP |
| 137-139 | NetBIOS | 22 | SSH |
| 110 | POP | 23 | TELNET |
| 143 | IMAP | 53 | DNS |
| 25 | SMTP | 67,68 | DHCP |
| 5060/5061 | SIP | 69 | TFTP |
| 2427/2727 | MGCP | 445 | SMB |
| 1720 | H.323 | 5004/5005 | RTP |

## NETWORKING SERVICES

### DNS (Domain Name System)

DNS resolves domain names to IP addresses. In the world of networking, computers don't go by names, like humans do, they go by numbers. So if you type in a web address in your web browser, DNS will transform the name to an IP address.

*e.g.:*

When you type in `www.google.com` in your web browser, the DNS server will search through its database to find a matching IP address for that domain name, and when it finds it, it will transform that domain name to the IP address of the Google web server. So DNS basically works like a phone book.


| **Domain Name** | **IP Address** |
| --- | --- |
| `www.yahoo.com` | 68.142.226.32 |
| **`www.google.com`** | **64.233.179.99** |
| `www.cnn.com` | 64.236.16.20 |
| ... | ... |

### Other services

**WINS** (Windows Internet Name Service) --- **NAT** (Network Address Translation) --- **PAT** (Port Address Translation) --- **SNAT** ( Static Network Address Translation) --- **Proxy** --- **RDP** (Remote Desktop Protocol) --- **CSMA/CD** (Carrier Sense Multiple Access with Collision Detection) --- **CSMA/CA** (Carrier Sense Multiple Access with Collision Avoidance) --- **Broadcast** --- **Multicast**  --- **Unicast**

## ROUTING PROTOCOLS

If you were traveling to a certain destination anywhere in the world, most likely you'll need directions or a map on how to get there. Well, in the world of networking, it works the same way. In order for data to travel across a network, and reach its destination, it needs a map to determine the best path to take, and the way it does this is by using routing protocols.

Routing protocols collect information about the current network status and map out the best path for data packets to take to their specific destination.

### Routing Table

A routing table is a **file** that contains a **set of rules** that shows information on **what path a data packet takes to its destination**.

For example, a router uses a routing table, so as a **data packet** arrives at a router, the router looks at its routing table to find out where **to forward** the data packet along the **best path** to its destination.

So a basic routing table contains:

- **A network destination**: The IP address of the final destination.
- **A subnet mask**: Determines which part of the IP address is the host or the network portion.
- **Gateway**: Tells the router which IP address a data packet should be forwarded to.
- **Interface**: Which is the outgoing IP address of the device that's sending the data.
- **Next hop**: The IP address to which the IP address is forwarded to.
- **Metric**: Determines the best route among multiple destinations.

### Types of routing protocols

- **Distance Vector**: Factors in distance the destination based on how many hops (routers). (RIP --- RIPv2 --- BGP)
- **Link State**: Each node independently map out the best path on a network. (OSPF --- IS-IS)
- **Hybrid**: A combination of distance vector and link state protocols. (EIGRP)

### Loopback Interface

- A fake or virtual interface that is created on a router.
- Assigned an IP address.
- Used for testing and administration purposes.

### SIP (Session Initiation Protocol)

- SIP establishes communication sessions over the internet.
*e.g.*: **VoIP** (Voice over the Internet Protocol) --- Instant Messaging --- Conferencing
- SIP operates at the **application layer** of the **OSI model**.

### RTP (Real-Time Transport Protocol)

- The internet standard for transporting real-time data such as streaming audio and video.
- It's often used over UDP, so it doesn't guarantee data delivery.
- It's also used with RTCP (Real-time Transport Control Protocol), which enables you to monitor the quality of the data being delivered.
- It can be used to send data in both unicast and multicast.

## CALCULATIONS

[Online calculator.](http://jodies.de/ipcalc)

### Calculating the subnet mask Length (also called a prefix; CIDR notation)

Let's say we have the subnet mask `255.255.248.0`.
Convert the dotted-decimal representation of the subnet mask to binary (see [***IPv4: BINARY LESSON***](#binary)). Then, count the number of contiguous 1 bits, starting at the most significant bit in the first octet (i.e. the left-hand-side of the binary number).

```
255.255.248.0   in binary: 11111111 11111111 11111000 00000000
                           -----------------------------------
                           I counted twenty-one 1s             -------> /21

```

The prefix of `128.42.5.4` with a `255.255.248.0 ` subnet mask is `/21`.

(And vice versa!)

### Network Address

Let's say we have this IP address: `172.16.5.130/26`
To calculate the network address, we take the last remaining bits out of result of `32 (total number of bits in an IPv4 address) - 26 (the CIDR prefix)` and turn them all into `0`s.

So we have:
172(**128**+**32**+**8**+**4**).16(**16**).5(**4**+**1**).130(**128**+**2**) = **1**0**1**0**11**00.000**1**0000.00000**1**0**1**.**1**00000**1**0

Turning all the last `32 - 26 = 6` bits into zeros, we get:
10101100.00010000.00000101.10**000000**
which is the network address: `127.16.5.128`.

### Broadcast Address

For this, it's the exact opposite, instead of turning those bits into `0`, we turn them into `1`s.
Let's take that same IP address: `172.16.5.130/26` = `10101100.00010000.00000101.10000010`.

After changing the last `6` bits to `1` this time, we'll get:
`10101100.00010000.00000101.10111111`, which is the broadcast address:  `172.16.5.191`.

### Maximum Number of Hosts

Let's take the same example above (`172.16.5.130/26`).
To find the maximum number of hosts we'll, again, subtract the subnet mask length from `32`. This gives us the number of host bits in the address, which is `6`. At that point...

***Maximum number of hosts*** = 2^(32 - **subnet mask length**) - 2

The reason we subtract `2` above is because the all-ones and all-zeros host numbers are reserved. The all-zeros host number is the **network address**; the all-ones host number is the **broadcast address**.

Using the example subnet of `172.16.5.130/26` above, the number of hosts is...

***Maximum Number of hosts***  = `2^(32 - 26) - 2`
= `2^6 - 2`
= `64 - 2`
= `62`

## References

- [CompTIA Network+ Certification Video Course](https://www.youtube.com/watch?v=vrh0epPAC5w)
- [Calculate Network, Broadcast and host addresses](https://www.youtube.com/watch?v=hb2yTNT2rBU)
- [How do you calculate the prefix, network, subnet, and host numbers?](https://networkengineering.stackexchange.com/questions/7106/how-do-you-calculate-the-prefix-network-subnet-and-host-numbers)

67414141414142655a62562d564a6d564f4759564c50364a68796d585768536b6d484f5473745a433348707a48446d76546d676c705a704b5675314a2d5868726b7537414a397146714e6f394f6c486a4b554b574156484e59496f39764d6d77365561717943504d6e3433683674745849525841424661504e4138423232743262715331764d5a7a61715f44475f69745764695741697a4537386a33676152467370514a7a676d524456487042585a6c44644e4d736a712d497a5f36337630306d356c5366393269654b6b4e7a79614d4f712d57544536696a79524e3737393338395375585637434e6e5a4a4a75396156396a5453524a3866702d69536d384e367a43494a4f5448425468737842304c4c4c4d744e687a753452674b3455795963546f5754793452647a4a79766853467369574c38375254375f696e6b634b68634f394147545a6139745a43584b46754d534b47564941445657636d754c46374d4c43334b384d767a7953723858447848414a493766684c62794b5656315a5049642d394d435042306b6d7071573954436b625a4d6a62504a702d4e664c6841434246336254336f6d335f4f4d793352696d385164305f7233726c615657324a417644376e5931494b5276742d63756c4c4e523559517a3741576847526f4d667a773d3d
