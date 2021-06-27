## Troubleshooting static and default routes

1. **Problem:** 
PC1 can't reach remote network like LAN2 and LAN3. R1 is misconfigured to set default static route.    

The preferred default static route commands are: 
___For ipv4 addressing:___    

	(config)# ip route 0.0.0.0 0.0.0.0 {next-hop-ip | exit-intf}
___For ipv6 addressing:___

	(config)# ipv6 route ::/0 {next-hop-ipv6-address | exit-intf}
			
___But It is recommanded to use next-hop-ip/ipv6 address instead of exit-intf.___

**Solution:**

	R1(config)# ip route 0.0.0.0 0.0.0.0 172.31.1.193
___Similarly configure static route correctly in R2 and R3.___ 

- - - - - - - - 
2. **Problem:** PC1 can't access server using ipv6 address. 
**Solution:** 
In R2, verify 

	R2# show ipv6 route
	
there has misconfiguration on ipv6 static route. 
		
