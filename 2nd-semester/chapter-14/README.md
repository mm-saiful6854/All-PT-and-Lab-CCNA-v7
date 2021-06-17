## Step 1: Configure the PC interfaces.

## Step 2: Configure the router.
enable
configure terminal
hostname R2
enable secret c1sco1234
ip domain-name ccna-lab.com
no ip domain lookup
service password-encryption
username SSHadmin secret 55Hadm!n
crypto key generate rsa
1024

line console 0
password cisco
logging synchronous
exec-timeout 6 0
login

line vty 0 4
password cisco
exec-timeout 6 0
transport input ssh
login local

banner motd $ WARNING Authorized Users Only! $
ipv6 unicast-routing

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

end
copy running-config startup-config