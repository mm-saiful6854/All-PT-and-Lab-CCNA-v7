Switch boot steps:
Load POST (Power on self-test) program: 
stored in ROM
check the CPU subsystem, DRAM, flash file system.

Load Boot Loader:
stored in ROM
initialization: low-level CPU, CPU registers, flash file system, control physical memory, 

finally: locates and load default IOS image into physical memory and pass control of switch to IOS.


Important notes about Boot system command of cisco devices:

We can set BOOT environment variable using boot system commmand on cisco devices.
command: 
	(config)# boot system flash:/file-path on flash file system/IOS .bin image-file

If administrator doesn't set the BOOT environment variable, cisco devices will search for first executable file and will attempt to boot using that file.

Current content of boot environment variable:
command:
	# show boot
	
	
How to recover system from crash:
	The Boot-loader is the life-savier, when IOS image file is missing or can't be found for damaged file system.The Boot-loader has command line interface that helps to access flash file system.
	
	To enter into boot-loader cmd-line interface, administrator must follow this steps:
	
	Step 1. Connect a PC by console cable to the switch console port. Configure terminal emulation software to connect to the switch.
	
	Step 2. Unplug the switch power cord.
	Step 3. Reconnect the power cord to the switch and, within 15 seconds, press and hold down the Mode button while the System LED is still flashing green.
	
	Step 4. Continue pressing the Mode button until the System LED turns briefly amber and then solid green; then release the Mode button.
	
	Step 5. The boot loader switch: prompt appears in the terminal emulation software on the PC.
	
	Important command of boot-loader interface:
		
		switch: help or ?  => to view a list of available commands.
		switch: set	   	   => to view the path of the switch BOOT environment variable
		switch: flash_init => initialize the flash file system
		switch: dir flash: => After flash has finished initializing, to view the directories and files in flash
		
		switch: BOOT=flash:/path/bin file => set boot environment variable
		switch: boot => to load the new IOS.
		
	
	Overall, There are other boot loader commands that support initializing flash, formatting flash, installing a new IOS, changing the BOOT environment variable and recovery of lost or forgotten passwords.
	
	
	Note: (config)# sdm prefer dual-ipv4-and-ipv6 default
	then, reload the switch. These command help to be configured by ipv6 addressing.
	
	
	
Interface Duplex Communication and speed configuration:
	The methods of transferring data between sender and recevier is called duplex communication. There are two types of duplex system: Half duplex; Full duplex. In full deplex communication system, sender and recevier can send/receive data at a time simultaneously. But in half duplex system, it is not possible. One workstation operating in half duplex must have to send or receive data in seperate time slot. 
	
	Switch port configurations give scope to change this duplex system as well as speed. All ports can operate 10/100/1000 Mbps. If the port operates in 10 or 100 Mbps, then it can be set in half or full duplex. But the port operates in full duplex mode, when it is set to 1000 Mbps (1 Gbps). 
		command: 
			(config-if)# duplex full
				comment: it sets full duplex to this specific switch port.
			(config-if)# speed 100
				comment: here 100 means port speed will be 100 Mbps.
		
	Suppose two switches are connected by a crossover cable in f0/0 (s1) and f0/1(s2). If the configurations on both side port (f0/0 and f0/1) are mismatched, then there will be appeared a connection fault.
		
	In this situation, Autonegotiation is useful.
	
	
	
What is MDIX:
	MDIX stands for automatic medium-dependent interface crossover. There are two types of cables: straight-through and crossover. Same types devices(switch-switch/switch-hub) are connected by crossover and different types (server-switch) are connected by straight-through cable. Otherwise connection will be failed. 
	
	MDIX is a port feature that help to avoid this kinds of problem. 
	command:
		(config-if)# mdix auto
			comment: It sets the value of mdix is auto. So that any types of cable can use in this port.
	verify:
		# show controllers ethernet-controller fa0/1 phy 
		
		
		
		
Configure SSH on cisco devices:

(config)# show ip ssh
	comment: to display the current supported ssh config.
(config)# ip domain-name cisco.com
(config)# crypto key generate rsa                    
	comment: (config)# crypto key zeroize rsa // To delete the RSA key pair. After the RSA key pair is deleted, the SSH server is automatically disabled.
		
(config)# username admin secret ccna

(config-line)# transport input ssh

(config-line)# login local

(config)# ip ssh version 2



(config)# interface loopback number
	commnet: create loopback interface with indicated number.

# terminal history size 200
	comment: to increase history command size. this command is executable in privileged EXEC mode.

		
		
	
	








