**ACL** concerne les routeurs.
(ACL need to be configured in the closest router to the target network)
acl standars:
access-list 1-99 prmit | deny network-ip geniric-masque
access-list 1-99 prmit | deny host "host-ip" | any
### Then move on to the interface
![[Pasted image 20240319142040.png]]
ip access-group 1-99 in/out

# ACL Etendue
