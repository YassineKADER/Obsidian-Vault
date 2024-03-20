## EIRGP
router eigrp 1
 network 172.10.0.0
 redistribute rip metric 50000 0 100 1 1500 
 redistribute ospf 1 metric 50000 100 100 1 1500 
## OSPF
router ospf 1
 network 13.0.0.0 0.255.255.255 area 0
 redistribute rip subnets 
 redistribute eigrp 1 subnets 
## RIP
router rip
 version 2
 network 173.10.0.0
 redistribute eigrp 1 metric 1 
 redistribute ospf 1 metric 1 
