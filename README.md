*This project has been created as part of the 42 curriculum by ykonka*.

## Description

* The project introduces us to the networking fundamentals. following concepts are required to study before start working with training simulation
	+ What are network components
		- Router
		- Switch
	+ IP addressing
	+ Subnet Masks
	+ Default gateway
	+ Network Protocol Model
		- TCP/IP
	+ Communicaiton Reference Model
		- OSI model

### Network Components:
+ Router: a router is used to manage and plan ip addresses for correct packet transmission to its corresponding destination device
+ Switch: a switch is used to manage the local data transfer among local hosts connected to it
+ Router & Switch: switch and router functionalities are completely different and one can not be exchanged with other

### IP Addressing:
IP addressing is very important step in the network communicaiton model
#### What it is?
A process of assigning name to an network device, so that it can participate in data transfer process via group of networks connected together
#### Who does this?
ISP provider will do this job for your home router for global communication
local IT Adminstrator will assign the ip addresses to local devices which are participates in your LocalAreadNetwork(LAN)
#### How the IP address is processed for data transfer?
##### IP address structure
an IPv4 has `4` octets, each octet has `8` bits
________.________.________.________
each octet can be assigned from `0` to `255(2**8)`
E.g: `127.0.0.1` is allocated for loop back ip address within the same local host
##### Subnet Mask
a subnet maks has same structure like ip address as 4 octets each has 255 value possibilities
E.g: `255.255.255.0`  which is also written in `Classless Inter-Domain Routing (CIDR)` form `/24` 
##### How the IP address is processed
during data transmission steps are followed as below
1. atleast 2 hosts are needed for data transmission, they are sender(source) and reciever(destination)
2. a sender checking a destination ip address is within its own network or needed to be routed to default Gateway(a router)
3. to validate this it does following calculations
	1. bitwise `AND` between IP address of source and source subnet mask, after this the IP address is segmented into `Network ID` and `Host ID`
	2. bitwise `AND` between IP address of destination and source subnet mask, after this we get `Network ID` and `Host ID`
	3. if the both souce and destination `Network ID`s are same then they are in local network
	4. once this confirmed source device send the packet to its destination device
4. if an destination IP address fall outside of the Local Network, then this is forwarded to Default Gateway(which next hop, a Routing Interface). From here on group of Router will do the job of delivering Packet to its Correct Destination Address.
5. above explanation is very abstract for more concrete explanation of a data is transfered via network, I recommend one should study about TCP/IP and OSI models

### TCP/IP
-  a TCP/IP is an suite of protocols layered together to make sure the communication is done reliablely.
-  it has 4 layers
	+ Application Layer - HTTP Protocol
	+ TCP - Transport Communication Protocol
	+ Internet - IP protocol
	+ Network Access - Ethernet Protocol
- this model is used to defined set of functionalities done at each layer so that the data is transfered seamlessly.
							   TCP/IP
					   		   ------
							Application
								|
							TCP
								|
							Internet
								|
							Network Access

### OSI Model
- A OSI model is an reference model used to support the any networking configuration
- it is created in Open Source Interconnet Project at ISO
- it delivers 3 objectives:
	+ data network design
	+ operational specification
	+ troublshooting
- Why it is necessary if TCP/IP is there?
	+ TCP/IP provides rules for each layer functionalities
	+ while OSI provides rules for between layeres functionalities and whole networking capabilities in detail
- TCP/IP and OSI model layers have 2 layers which have similar functions among them
								OSI
								---
							Application
								|
							Presentation
								|
							  Session
								|
							   TCP
								|
							  Network
								|
							 Data Link
								|
							 Physical
	
* a simulation interface is provided by the 42

## Instructions

### Training
- To get started following steps will be helpful
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

### Evaluation
```bash
# to start simulation
$ ./run.sh
```
- select the practice
- enter your intra name `ykonka`
- start

## Resources
- `AI usage`: AI is used for research
- [Networking Basics](https://www.geeksforgeeks.org/computer-networks/basics-computer-networking/)
- [Networking Basics Course](https://www.netacad.com/courses/networking-basics?courseLang=en-US)
- [Routing](https://www.youtube.com/watch?v=CGmTvukObOw&pp=ygURaG93IHJvdXRpbmcgd29ya3M%3D)
- [Subnetmask](https://www.youtube.com/watch?v=s_Ntt6eTn94&pp=ygULc3VibmV0IG1hc2s%3D)
- [OSI model](https://www.youtube.com/watch?v=0y6FtKsg6J4&pp=ygUJb3NpIG1vZGVs)
- [IP addressing](https://www.youtube.com/watch?v=po8ZFG0Xc4Q&pp=ygUNaXAgYWRkcmVzc2luZw%3D%3D)
