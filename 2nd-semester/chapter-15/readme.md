
# Chapter 15

## 15.6.1 Packet Tracer - Configure IPv4 and IPv6 Static and Default Routes

![15.6.1 Network-Structure](./2nd-semester/chapter-15/img/network-structure.PNG?raw=true "Title")



## Part 1: Configure IPv4 Static and Floating Static Default Routes

### Step 1: Configure an IPv4 static default route.

	Edge_Router(config)# ip route 0.0.0.0 0.0.0.0 s0/0/0
### Step 2: Configure an IPv4 floating static default route.

	Edge_Router(config)#ip route 0.0.0.0 0.0.0.0 s0/0/1 5
	
## Part 2: Configure IPv6 Static and Floating Static Default Routes

### Step 1: Configure an IPv6 static default route.

	Edge_Router(config)#ipv6 route ::/0 2001:db8:a:1::1
	
### Step 2: Configure an IPv6 floating static default route.

	Edge_Router(config)#ipv6 route ::/0 2001:db8:a:2::1
	
	
## Part 3: Configure IPv4 Static and Floating Static Routes to the Internal LANs

### Step 1: Configure IPv4 static routes to the internal LANs.
		a. 
		ISP1(config)#ip route 192.168.10.16 255.255.255.240 10.10.10.2
		b.
		ISP1(config)#ip route 192.168.11.32 255.255.255.224 10.10.10.2

### Step 2: Configure IPv4 floating static routes to the internal LANs.
		a. ISP1(config)#ip route 192.168.10.16 255.255.255.240 g0/0 5
		b. ISP1(config)#ip route 192.168.11.32 255.255.255.224 g0/0 5



## Part 4: Configure IPv6 Static and Floating Static Routes to the Internal LANs.

### Step 1: Configure IPv6 static routes to the internal LANs.
		**a** ISP1(config)#ipv6 route 2001:db8:1:10::/64 2001:db8:a:1::2
		**b** ISP1(config)#ipv6 route 2001:db8:1:11::/64 2001:db8:a:1::2
		
		
### Step 2: Configure IPv6 floating static routes to the internal LANs.
		a.ISP1(config)#ipv6 route 2001:db8:1:10::/64 2001:db8:f:f::2 5
		b. ISP1(config)#ipv6 route 2001:db8:1:11::/64 2001:db8:f:f::2 5


## Part 5: Configure Host Routes

###Step 1: Configure IPv4 host routes.
		a. Edge_Router(config)#ip route 198.0.0.10 255.255.255.255 s0/0/0
		b. Edge_Router(config)#ip route 198.0.0.10 255.255.255.255 s0/0/1


### Step 2: Configure IPv6 host routes.
		a. Edge_Router(config)#ipv6 route 2001:db8:f:f::10/128 2001:db8:a:1::1
		b. Edge_Router(config)#ipv6 route 2001:db8:f:f::10/128 2001:db8:a:2::1 5




