*This project has been created as part of the 42 curriculum by ykonka*.

## <font color="red">Description</font>

* The project introduces us to the networking fundamentals. following concepts are required to study before start working with training simulation
	+ What are network components
		- Router
		- Switch
	+ IP addressing
	+ Subnet Masks
	+ Default gateway
	+ Network Protocol Model
		- TCP/IP
	+ Network Reference Model
		- OSI model

### <font color="green">Network Components:</font>
+ Transmission medium: Copper, Fiber, Air
+ End devices: any electronic device which has NetworkInterfaceCard(NIC)
+ Router: a router is used to manage and plan ip addresses for correct packet transmission to its corresponding destination device
+ Switch: a switch is used to manage the local data transfer among local hosts connected to it
+ Router & Switch: switch and router functionalities are completely different and one can not be exchanged with other
+ Internet: web of network wires or configurations

### <font color="green">IP Addressing:</font>
+ This is one of the Layer in OSI and TCP/IP Models
+ Which does the naming to network devices and processing to deliver via best possible path
+ IP addressing is very important step in the network communicaiton model
#### <font color="yellow">What it is?</font>
A process of assigning name to an network device, so that it can participate in data transfer process via group of networks connected together
#### <font color="yellow">Who does this?</font>
ISP provider will do this job for your home router for an global communication
local IT Adminstrator will assign the ip addresses to local devices which are participates in your LocalAreadNetwork(LAN)
#### <font color="yellow">How the IP address is processed for data transfer?</font>
##### IP address structure
- an IPv4 has `4` octets, each octet has `8` bits
	- `00000000.00000000.00000000.00000000`
	- `________.________.________.________`
- each octet can be assigned from `0` to `255(2**8)`
- E.g: `127.0.0.1` is allocated for loop back ip address within the same local host
##### Subnet Mask
a subnet maks has same structure like ip address with 4 octets each has 255 value possibilities
E.g: `255.255.255.0`  which is also written in `Classless Inter-Domain Routing (CIDR)` form `/24`
##### How the IP address is processed
during data transmission steps are followed as below
1. atleast 2 hosts are needed for data transmission, one is sender(source) and the other is reciever(destination)
2. a sender checking a destination ip address whether it is within its own network or needs to be routed to default Gateway(a router, interface to the outside world[internet])
3. to validate this it does following calculations
	1. bitwise `AND` between IP address of source and source subnet mask, after this the IP address is segmented into `Network ID` and `Host ID`
	2. bitwise `AND` between IP address of destination and source subnet mask, after this we get `Network ID` and `Host ID`
	3. if the both souce and destination `Network ID`s are same then they are in local network
	4. once this confirmed source device send the packet to its destination device
4. if an destination IP address fall outside of the Local Network, then this is forwarded to Default Gateway(which next hop, a Routing Interface). From here on group of Router will do the job of delivering Packet to its Correct Destination Address.
5. above explanation is very abstract for more concrete explanation of a data is transfered via network, I recommend one should study about TCP/IP and OSI models

### <font color="green">Network Models and Protocols</font>
- In simple words
	- `A OSI model says `**what**` needs to be done at each layer`
	- `A Protocol defines `**how**` it should be done at each layer`
	- `A Program(implementation) & Hardware `**does**` it`

#### <font color="yellow">TCP/IP</font>
-  TCP/IP is a suite of protocols organized in layers to define how data is communicated over a network.
-  TCP/IP has 4 layers:
	- Application: HTTP, DNS, SMTP
	- Transport: TCP, UDP
	- Internet: IPv4, IPv6, ICMP
	- Network Access: Ethernet, Wi-Fi

#### <font color="yellow">OSI Model</font>
- The OSI model is a reference model that provides a conceptual framework for network communication.
- it is created in Open System Interconnet Project at ISO
- It is used to achieve three main objectives:
	+ Provide a common framework for network design.
	+ Standardize network functions and communication between different systems.
	+ Help identify and troubleshoot network problems layer by layer.
- it has 7 layers
	+ Application - (Provides network services and protocols for applications to communicate with each other)
	+ Presentation - (Converts data into a common format for transfer, and can handle encryption, compression, and character encoding)
	+ Session - (Establishes, manages, and ends sessions between applications)
	+ Transport - (Breaks application data into segments, transfers them end to end, and reassembles them at the destination)
	+ Network - (Provides logical addressing, routing, and forwarding of packets between networks)
	+ Data Link - (Packages data into frames for delivery across the local network, using MAC addresses; routers remove and create new frames at each hop)
	+ Physical - (Transmits raw bits over a physical medium, such as copper cable, fiber, or radio waves)

#### <font color="yellow">Layerwise Data Representation</font>
| Unit          | Layer       |
| ------------- | ----------- |
| Bits          | Physical    |
| Frames        | Data Link   |
| Packets       | Network     |
| Segments      | Transport   |
| Data/messages | Application |

## <font color="red">Instructions</font>
* a simulation interface is provided by the 42

### <font color="green">Training</font>
- To get started following steps will be helpful
- run.sh is an shell script which gives clear instructions on how to start the server

```bash
# to start simulation
$ ./run.sh
```
- then open the local server of simulation in your `web browser`
- after that select `training`
- enter your intra name `ykonka`
- start
- solve total 10 network config problems
- save the config files per level in the json format
- submit them to evaluate

### <font color="green">Evaluation</font>
```bash
# to start simulation
$ ./run.sh
```
- select the practice
- enter your intra name `ykonka`
- start

## <font color="red">Training Levels Solving Details</font>
### <font color="green">Level-1:</font>
- connection between 2 local devices
### <font color="green">Level-2:</font>
- 127.0.0.0 are not allowed to communicate between two hosts
- while these ip addresses are reserved for loop back communication

### <font color="green">Level-3:</font>
- 255.255.255.128
- `|octet-1|octet-2|octet-3|octet-4|`
- each octet has 8 bits reserved
- during calculation they are processed seperately

above subnet mask divides a network into 2 subnets or groups
- each subnet gets 128 total ip addresses and 126 are assignable
- 0 & 127 are assigned as *network_ID* & *broadcasting*
- that means, 1-126 host ID s are possible in abov 4th octet of the ip address
- 255.255.255.[1-126]

### <font color="green">Level-4:</font>
ip address: 95.74.114.129
subnet:     255.255.255.240

according to given subnet mask
the network on router interface R1 is divided into 16 groups

however for host A1 the interface config is locked
based on this config we have only 14 out of 16 ip addresses are possible
both config files are set so the edge values are assigned to
	- Router Interface
	- Host B1 Interface
accordingly so that in the future it would be easy to understand how many ip addresses can be used for configuration
	+ 95.74.114.[129-142]
	+ 128[network ID]
	+ 143[broadcasting address]


### <font color="green">Level-5:</font>
- In this network we have Router, which has 2 interfaces connected to their corresponding hosts
- How the two host interfaces or router-host interfaces transmit packets
	- device calculate the network ID of both its own and reciever host using its own subnet mask
	- if both matches then the device decides the other device is on-link, else it is a remote connection
	- for local communication a device sends the ARP request with an Ethernet frame, then starts communicating with it
- A default gateway of any local host is the ip address of the nearest router it has been connected to
- default ip address of any host is set as [0.0.0.0/0]

#### <font color="yellow">Router Interface R1 - to - Host A</font>
- In this connection link, we have vast number of possibilites for A
- the subnet mask of A can be from 0.0.0.0 to 255.255.255.[0-252], however one has to configure the ip addresses accordingly. which means both R1 and A interface ip address fall under same network using for forward communication with *A subnet mask* and for reverse communication with *R1 subnet mask*
- `**one play around to set the different ranges of the ip addresses and subnet masks**`

| Interface   | Subnet Mask           | IP Address          |
| ----------- | --------------------- | ------------------- |
| R1          | 255.255.255.128       | 48.209.85.126       | fixed
| A           | /18                   | 48.209.85.125       |
#### <font color="yellow">A route table [From Routes To]</font>
| Interface   | IP Address From       | IP Address To       |
| ----------- | --------------------- | ------------------- |
| A-default   | 0.0.0.0/0             | 48.209.85.126       |

#### <font color="yellow">Router Interface R2 - to - Host B</font>
- Based on its subnet mask we have 4 possible groups/subnets in 3rd octet
	+ 130.55.[0-63].[0-255]
	+ 130.55.[64-127].[0-255]
	+ 130.55.[127-191].[0-255]
	+ 130.55.[192-255].[0-255]
- Accordingly, we can assign any ip address, which fall under these groups to B corresponding to R2
- R2 is fixed, so we must set B ip address which fall under this group. which is
	+ 130.55.[192-255].[0-255]

| Interface   | Subnet Mask           | IP Address                    |
| ----------- | --------------------- | ----------------------------- |
| R2          | 255.255.192.0         | 130.55.228.254                | fixed
| B           | /18                   | 130.55.[192-255].[0-255]      |
#### <font color="yellow">B route table [From Routes To]</font>
| Interface   | IP Address From       | IP Address To       |
| ----------- | --------------------- | ------------------- |
| B-default   | 0.0.0.0/0             | 130.55.228.254      |

### <font color="green">Level-6:</font>
- In this network, the only interesting part is routing table
- it could be set to vast possible hosts or contrain it to only desired ip addresses
	- 43.159.41.0/24
	- 43.159.41.128/25

- here they are restricted to above ip address while the subnet mask of router and ip address of the host are fixed
### <font color="green">Level-7:</font>
- to set a default to a ip address for routing, would mostly be its next hop(router)
- so when the router encounters remote ip address it will forward them to outside

### <font color="green">Level-8:</font>
- private address ranges can not set to an host for remote communication
### <font color="green">Level-9:</font>
-  in this network simulation, the Router-1 is connected to 3 main interfaces which have their own subnetworks locally
#### <font color="yellow">Interface R11 - connection from switch(neutron) to router-1</font>
- here 2 hosts could be any ip address which is with in the range of public addresses
- do not forget to set the default of both hosts to router interface ip address
#### <font color="yellow">Interface R12 - connection from router-2 to router-1</font>
- this is straight forward while the subnet mask of router-2 is fixed, so only 2 ip addresses are allowed and must be serialised
#### <font color="yellow">Interface R13 - connection from internet to router-1</font>
- here routerR13 interface is already fixed by simulation provider, so the only part is filling routing table.
- to set communication between internet and switch, we should enter the allowed range of ip addresses of switch
- to set communication between internet and router-2, we should enter the allowed range of ip addresses of router-2
#### <font color="yellow">Routing table of the Router-1</font>
- here either we can use default ip to route to router-2 interface
	+ if Router-2, R21 interface ip address is `200.200.200.253`
	+ Router table

| IP Address From       | IP Address To       |
| --------------------- | ------------------- |
| 0.0.0.0/0             | 200.200.200.253     |
- or, we can enter the each individual ip addresses range of the Router-2 2 subnetwork interfaces seperately
	+ if Router-2, R21 interface ip address is `200.200.200.253`, subnet-mask: `255.255.255.252`
	+ if Router-2, subnetwork-1 interface(R23 to gluon) ip address is `114.188.114.160`, subnet-mask: `255.255.192.0`
	+ if Router-2, subnetwork-2 interface(R22 to cation) ip address is `3.3.3.1`, subnet-mask: `255.255.192.0`
	+ Router table

| IP Address From       | IP Address To       |
| --------------------- | ------------------- |
| 3.3.0.0/16            | 200.200.200.253     |
| 114.188.0.0/16        | 200.200.200.253     |
### <font color="green">Level-10:</font>
- this simulation is same as level-9

## <font color="red">Glossary</font>
#### <font color="yellow">default gateway</font>
- which is 0.0.0.0./0
- it tells your router to forward any ip address to the IP address the default assigned to in the routing table
#### <font color="yellow">routing table</font>
- it is an list of ip addresses that are not connected directly to router interface and added in the table
- so that any incoming or outcoming ip address fall into this ip address, the router can forward the data from this ip address range to assigned ip address
#### <font color="yellow">subnet mask</font>
- it is used to calculate the 2 components from ip address, which are `Network ID` and `Host ID` to support ip forwarding

## <font color="red">Resources</font>
- `AI usage`: AI is used for research
- [Networking Basics](https://www.geeksforgeeks.org/computer-networks/basics-computer-networking/)
- [Networking Basics Course](https://www.netacad.com/courses/networking-basics?courseLang=en-US)
- [Routing](https://www.youtube.com/watch?v=CGmTvukObOw&pp=ygURaG93IHJvdXRpbmcgd29ya3M%3D)
- [Subnetmask](https://www.youtube.com/watch?v=s_Ntt6eTn94&pp=ygULc3VibmV0IG1hc2s%3D)
- [OSI model](https://www.youtube.com/watch?v=0y6FtKsg6J4&pp=ygUJb3NpIG1vZGVs)
- [IP addressing](https://www.youtube.com/watch?v=po8ZFG0Xc4Q&pp=ygUNaXAgYWRkcmVzc2luZw%3D%3D)
