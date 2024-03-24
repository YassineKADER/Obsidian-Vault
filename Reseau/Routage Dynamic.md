### RIPv2 Configuration Example:

```shell
router rip
 version 2
 network 10.0.0.0
 network 192.168.1.0
```

In this example:
    router rip: Enters RIP configuration mode.
    version 2: Enables RIPv2, which supports CIDR and VLSM.
    network 10.0.0.0: Advertises the network 10.0.0.0 with its subnet mask into the RIP domain.
    network 192.168.1.0: Advertises the network 192.168.1.0 with its subnet mask into the RIP domain.

### OSPF Configuration Example:

```bash
router ospf 1
 network 10.0.0.0 0.255.255.255 area 0
 network 192.168.1.0 0.0.0.255 area 0
```

In this example:

    router ospf 1: Enters OSPF configuration mode with process ID 1.
    network 10.0.0.0 0.255.255.255 area 0: Advertises the network 10.0.0.0/8 into OSPF Area 0.
    network 192.168.1.0 0.0.0.255 area 0: Advertises the network 192.168.1.0/24 into OSPF Area 0.

### EIGRP Configuration Example:

```bash
router eigrp 1
 network 10.0.0.0 0.255.255.255
 network 192.168.1.0 0.0.0.255
```
In this example:

    router eigrp 1: Enters EIGRP configuration mode with AS number 1.
    network 10.0.0.0: Advertises the network 10.0.0.0 with its subnet mask into the EIGRP domain.
    network 192.168.1.0: Advertises the network 192.168.1.0 with its subnet mask into the EIGRP domain.

Additional Notes:

    Replace the network addresses (10.0.0.0, 192.168.1.0, etc.) with your actual network addresses.
    For OSPF, the area 0 parameter specifies the OSPF area. Adjust it according to your network's OSPF area design.
    For EIGRP, the AS number (1 in the example) should match on all routers in the same EIGRP autonomous system.

Remember to configure the corresponding routing protocols on all routers in your network to ensure proper routing and communication between them. Adjust the configurations as per your network topology and requirements.