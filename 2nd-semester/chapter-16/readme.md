## Troubleshooting static and default routes

1. **Problem:** 
PC1 can't reach remote network like LAN2 and LAN3. R1 is misconfigured to set default static route. The preferred default static route command is: 
			For ipv4 addressing:
				(config)# ip route 0.0.0.0 0.0.0.0 {next-hop-ip | exit-intf}
			For ipv6 addressing:
				(config)# ipv6 route ::/0 {next-hop-ipv6-address | exit-intf}
			
			But It is recommanded to use next-hop-ip/ipv6 address instead of exit-intf.
**Solution:**
		R1(config)# ip route 0.0.0.0 0.0.0.0 172.31.1.193
		Similarly configure static route correctly in R2 and R3. 


2. **Problem:** PC1 can't access server using ipv6 address. 
**Solution:** 
		In R2, verify 
			R2# show ipv6 route
		there has misconfiguration on ipv6 static route. 
		