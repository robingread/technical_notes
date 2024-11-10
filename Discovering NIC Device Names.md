tags: #linux 

Each *Network Interface Card* ([NIC](https://en.wikipedia.org/wiki/Network_interface_controller)) has it's own unique ID, and we sometimes need to know what this is. This is often the case when we need to create a docker network that uses the interface.

The first step is to unplug the device that you want to know the ID of. Then run the `lshw` command to list the network devices/classes (`-c network`).
```bash
sudo lshw -short -c network
```
Output:
```console
H/W path                       Device           Class          Description
==========================================================================
/0/100/14.3                    wlp0s20f3        network        Wi-Fi 6 AX201
/3                             veth46b14d8      network        Ethernet interface
/4                             veth2030653      network        Ethernet interface
/5                             veth7e5a980      network        Ethernet interface
/6                             enxc025a535f451  network        Ethernet interface
```

Then plug in the NIC device and run the command again, you should see a new divice listed:
```bash
sudo lshw -short -c network
```
Output:
```console
H/W path                       Device           Class          Description
==========================================================================
/0/100/14.3                    wlp0s20f3        network        Wi-Fi 6 AX201
/3                             veth46b14d8      network        Ethernet interface
/4                             veth2030653      network        Ethernet interface
/5                             veth7e5a980      network        Ethernet interface
/6                             enxc025a535f451  network        Ethernet interface
/7                             enx00e04c6c0424  network        Ethernet interface
```

From the output we can see that the device of interest is `enx00e04c6c0424`.