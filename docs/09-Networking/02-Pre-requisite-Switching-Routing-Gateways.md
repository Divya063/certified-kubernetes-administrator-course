# Pre-requisite Switching Routing Gateways

  - Take me to [Lecture](https://kodekloud.com/courses/539883/lectures/9817246)

In this section, we will take a look at **Switching, Routing and Gateways**
- How to connect two systems, we add a switch and the switch creates network containing the two systems. To connect host to switch we need an interface, on each host, physical or virtual depending on host. A router helps in connecting two networks.  If network is a room, gateway is a door to the outside world , to other networks.  ip route add command to add a gateway

## Switching

- To see the interface on the host system

```
$ ip link
```
- To see the IP Address interfaces.

```
$ ip addr
```

![net-14](../../images/net14.PNG)

## Routing

- To see the existing routing table on the host system.

```
$ route
```
```
$ ip route show
or
$ ip route list
```

- To add entries into the routing table.

```
$ ip route add 192.168.1.0/24 via 192.168.2.1
```

![net-15](../../images/net15.PNG)

## Gateways

- To add a default route.
```
$ ip route add default via 192.168.2.1
```

Whether a packet can be forwarded from one interface to another it is governed by `/proc/sys/net/ipv4/ip_forward`

- To check the IP forwarding is enabled on the host.
```
$ cat /proc/sys/net/ipv4/ip_forward
0

$ echo 1 > /proc/sys/net/ipv4/ip_forward
```

- Enable packet forwarding for IPv4.
```
$ cat /etc/sysctl.conf # if you want to persist those changes. 

# Uncomment the line
net.ipv4.ip_forward=1
```

- To view the sysctl variables.
```
$ sysctl -a 
```

- To reload the sysctl configuration.
```
$ sysctl --system
```





