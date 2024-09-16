
1. Check your `ip addres` 
```
ip a 
```
Check ip v4 and ip v6:
`v4`
```
ip -4 a
```
`v6`
```
ip -6 a
```
2. `traceroute`
Shows the path data takes from your computer to a destination, displaying each hop (router) along the way.

```
traceroute yahoo.com
```

3. `ping` 
Measures how long it takes to send data to a destination and get a response back.
```
ping <hostname> 
```

4. `netstat`-
 It displays information about different interface statistics, including open sockets, routing tables, and connection information. Further, it can be used to displays all the socket connections (including TCP, UDP) and active port on your system
```
netstat
```

display only TCP/UDP connection.
```
netstat -at
```

```
netstat -au
```

5 .  `ss`  
This command gives more information in comparison to the netstat. It is also faster than netstat as it gets all information from kernel userspace.
```
ss
```

 connected ports of TCP, UDP and Unix
```
ss -ta
ss -ua
ss -xa
```

6. `dig` 
dig helps you find out information about a domain name, like its IP address or mail server.
```
dig <domain_name>
```

7. `nslookup`
`nslookup` command is another tool for querying DNS (Domain Name System) to get information about domain names, similar to `dig`. It helps you find out details like IP addresses or mail servers associated with a domain.
```
nslookup <domain_name>
```

8. `route`
The route command is used to view and manage the routing table on a computer. The routing table is like a map that tells your computer how to send network traffic to different destinations.

- **Routing Table**: This is a list of rules that helps your computer decide where to send data packets. Think of it as a set of directions for your computer to follow when communicating over a network.
    
- **Route Command**: It lets you see these directions (routes) and can also be used to add or change them.
```
route -n
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.15.1    0.0.0.0         UG    100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
192.168.15.0    0.0.0.0         255.255.255.0   U     100    0        0 enp1s0

- **Destination**: The target network or IP address.
- **Gateway**: The next hop address used to reach the destination.
- **Genmask**: The subnet mask, which defines the network portion of the IP address.
- **Flags**: Indicators about the route (e.g., `U` means the route is up).
- **Metric**: The cost of the route; lower values are preferred.
- **Iface**: The network interface used for this route (e.g., `eth0` is a common name for a network interface).

9. `curl & wget`
These commands are used to download a file from the internet using CLI. With curl commands option O will be used while wget command will be used without any option. The file will be saved in the current directory
```
curl -O <fileLink>  
```

```
wget <fileLink>  
```

10. `mtr`
`mtr` continuously sends packets to a destination and displays:


