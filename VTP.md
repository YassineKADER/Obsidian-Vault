
## VTP Configure Server:
```
Switch(config)# vtp mode server
Switch(config)# vtp domain mydomain
Switch(config)# vtp password mypassword
```
## VTP Client:
```
Switch(config)# vtp mode client
Switch(config)# vtp domain mydomain
Switch(config)# vtp password mypassword
```
## VTP Transparent
```
Switch(config)# vtp mode transparent
Switch(config)# vtp domain mydomain
```
