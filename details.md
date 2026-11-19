## Resources
- [intro to computer networking](https://www.geeksforgeeks.org/computer-networks/basics-computer-networking/)
- []()

## Glossar
#### default gateway
- which is 0.0.0.0./0
- it tells your router to forward any ip address to the IP address the default assigned to in the routing table
#### routing table
- it is an list of ip addresses that are not connected directly to router interface but pass though
- so that the router can forward the data from this ip address to assigned ip address
#### subnet mask
- it is used to calculate the 2 components from ip address, which are `Network ID` and `Host ID`
## Training Levels
### 1:

### 2:
- 127.0.0.0 are not allowed to communicate between two hosts
- while these ip addresses are reserved for loop back communication

### 3:
255.255.255.128
|octet-1|octet-2|octet-3|octet-4|
- each octet has 8 bits reserved
- during calculation they are processed seperately

above subnet mask divides a network into 2 subnets or groups
- each subnet gets 128 total ip addresses and 126 are assignable
- 0 & 127 are assigned as *network_ID* & *broadcasting*
- that means, 1-126 host ID s are possible in abov 4th octet of the ip address
- 255.255.255.[1-126]

### 4:
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


### 5:
In this network we have Router, which has 2 interfaces connected to their corresponding hosts
How the two host interfaces or router-host interfaces transmit packets
	- device calculate the network ID of both its own and reciever host using its own subnet mask
	- if both matches then the device decides the other device is on-link, else it is a remote connection
	- for local communication a device sends the ARP request with an Ethernet frame, then starts communicating with it
- A default gateway of any local host is the ip address of the nearest router it has been connected to
- default ip address of any host is set as [0.0.0.0/0]

#### Router Interface R1 - to - Host A
- In this connection link, we have vast number of possibilites for A
- the subnet mask of A can be from 0.0.0.0 to 255.255.255.[0-252], however one has to configure the ip addresses accordingly. which means both R1 and A interface ip address fall under same network using for forward communication with *A subnet mask* and for reverse communication with *R1 subnet mask*
- `**one play around to set the different ranges of the ip addresses and subnet masks**`
| Interface   | Subnet Mask           | IP Address          |
| ----------- | --------------------- | ------------------- |
| R1          | 255.255.255.128       | 48.209.85.126       | fixed
| A           | /18                   | 48.209.85.125       |
#### A route table [From Routes To]
| Interface   | IP Address From       | IP Address To       |
| ----------- | --------------------- | ------------------- |
| A-default   | 0.0.0.0/0             | 48.209.85.126       |

#### Router Interface R2 - to - Host B
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
#### B route table [From Routes To]
| Interface   | IP Address From       | IP Address To       |
| ----------- | --------------------- | ------------------- |
| B-default   | 0.0.0.0/0             | 130.55.228.254      |

### 6:
In this network, the only interesting part is routing table
it could be set to vast possible hosts or contrain it to only desired ip addresses
- 43.159.41.0/24
- 43.159.41.128/25

here they are restricted to above ip address while the subnet mask of router and ip address of the host are fixed
### 7:
- to set a default to a ip address for routing, would mostly be its next hop(router)
- so when the router encounters remote ip address it will forward them to outside

### 8:
- private address ranges can not set to an host for remote communication
### 9:
-  in this network simulation, the Router-1 is connected to 3 main interfaces which have their own subnetworks locally
#### Interface R11 - connection from switch(neutron) to router-1
- here 2 hosts could be any ip address which is with in the range of public addresses
- do not forget to set the default of both hosts to router interface ip address
#### Interface R12 - connection from router-2 to router-1
- this is straight forward while the subnet mask of router-2 is fixed, so only 2 ip addresses are allowed and must be serialised
#### Interface R13 - connection from internet to router-1
- here routerR13 interface is already fixed by simulation provider, so the only part is filling routing table.
- to set communication between internet and switch, we should enter the allowed range of ip addresses of switch
- to set communication between internet and router-2, we should enter the allowed range of ip addresses of router-2
#### Routing table of the Router-1
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
### 10:
- this simulation is same as level-9
