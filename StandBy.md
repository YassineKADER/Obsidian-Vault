Configuring HSRP (Hot Standby Router Protocol) for two routers involves setting up redundancy for network connectivity. In this example, I'll show you how to configure HSRP for two routers with IP addresses 192.168.1.1 (primary router) and 192.168.1.2 (standby router) on the same subnet.

Here's how you can configure HSRP on both routers:

Router 1 Configuration:

```bash
Router1(config)# interface GigabitEthernet0/0
Router1(config-if)# ip address 192.168.1.1 255.255.255.0
Router1(config-if)# standby 1 ip 192.168.1.254
Router1(config-if)# standby 1 priority 110
Router1(config-if)# standby 1 preempt
```

Explanation:

    interface GigabitEthernet0/0: Enter the interface connected to the LAN.
    ip address 192.168.1.1 255.255.255.0: Configure the IP address and subnet mask for the interface.
    standby 1 ip 192.168.1.254: Set the virtual IP address that clients will use as their default gateway.
    standby 1 priority 110: Set the priority of this router. Higher priority means it will be the active router (default priority is 100).
    standby 1 preempt: Allow this router to become the active router if its priority is higher than the current active router.

Router 2 Configuration:

```bash
Router2(config)# interface GigabitEthernet0/0
Router2(config-if)# ip address 192.168.1.2 255.255.255.0
Router2(config-if)# standby 1 ip 192.168.1.254
Router2(config-if)# standby 1 priority 100
Router2(config-if)# standby 1 preempt
```

Explanation:

    interface GigabitEthernet0/0: Enter the interface connected to the LAN.
    ip address 192.168.1.2 255.255.255.0: Configure the IP address and subnet mask for the interface.
    standby 1 ip 192.168.1.254: Set the virtual IP address that clients will use as their default gateway (same as Router 1).
    standby 1 priority 100: Set the priority of this router. Lower priority means it will be the standby router (default priority is 100).
    standby 1 preempt: Allow this router to become the active router if its priority is higher than the current active router.

After configuring HSRP on both routers, they will exchange HSRP messages to determine the active and standby roles. The virtual IP address 192.168.1.254 will be used as the default gateway for devices on the LAN, and traffic will be forwarded through the active router. If the active router fails, the standby router will take over seamlessly due to preemptive mode. Adjust the priority values as needed based on your network requirements.