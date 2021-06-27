
## Essential commands for Packet tracer lab 

### Configure the router. 
#### Configure router basic details
    > enable 
    # configure terminal
    (config)# hostname R2
    (config)# enable secret c1sco1234
    (config)# ip domain-name ccna-lab.com
    (config)# no ip domain lookup
    (config)# service password-encryption
    (config)# username SSHadmin secret 55Hadm!n
    (config)# crypto key generate rsa 1024
    (config)# banner motd $ WARNING Authorized Users Only! $
    (config)# ipv6 unicast-routing
    
- - - - - - - - - - 
#### router line console setting      

    line console 0
    password cisco
    logging synchronous
    exec-timeout 6 0
    login
- - - - - - - - - - 
#### router virtual teletype setting

    line vty 0 4
    password cisco
    exec-timeout 6 0
    transport input ssh
    login local

- - - - - - - - - - 
#### router physical interface setting

    interface g0/0/0
    description Connection to S3
    ip address 10.0.4.1 255.255.255.0
    ipv6 address fe80::2:a link-local
    ipv6 address 2001:db8:acad:4::1/64
    no shutdown

    interface g0/0/1
    description Connection to S4
    ip address 10.0.5.1 255.255.255.0
    ipv6 address fe80::2:b link-local
    ipv6 address 2001:db8:acad:5::1/64
    no shutdown

    interface s0/1/0
    description Link to R1
    ip address 10.0.3.2 255.255.255.0
    ipv6 address fe80::1:c link-local
    ipv6 address 2001:db8:acad:3::2/64
    no shutdown

    interface s0/1/1
    description Link to Internet
    ip address 209.165.200.225 255.255.255.252
    ipv6 address fe80::1:d link-local
    ipv6 address 2001:db8:feed:224::1/64
    no shutdown
__return to the previllige EXEC mode___
 
    end
    copy running-config startup-config
