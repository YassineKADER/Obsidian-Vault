**ACL** concerne les routeurs.
(ACL need to be configured in the closest router to the target network (destination))
acl standars:
access-list 1-99 prmit | deny network-ip geniric-masque
access-list 1-99 prmit | deny host "host-ip" | any
### Then move on to the interface
![[Pasted image 20240319142040.png]]
ip access-group 1-99 in/out

# ACL Etendue
![[Pasted image 20240319143817.png]]
Router (config) #access-list 101 deny tcp host 192.168.3.2 any eq 23 # block host 192.168.3.2 from using telnet telnet based on tcp and use port 23, http for example use tcp and port 80
Router (config) #access-list 101 permit ip host 192.168.3.2 any # permit other protocol to be used normaly
Router (config) #access-list 101 permit ip any any # permit other devices with using all the protocols
Router (config) #acees-group 101 out # affect the acl to interface
![[Pasted image 20240319144353.png]]
deny the 192.168.3.0 network from acccessing to http on the host 192.168.1.3
![[Pasted image 20240319145056.png]] 
deny ping from host 192.168.2.2 to 192.168.1.2