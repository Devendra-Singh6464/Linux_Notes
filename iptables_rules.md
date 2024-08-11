# IP TABLES RULES ----

## Blocak all types of access to 'firewall' from 149.154.161.221 network 
```
iptables -t filter -A INPUT -s 149.154.161.221 -j DROP
```

## Check all rules 
```
iptables -L -n
```

## flusse/delete all rules---
```
iptables -F 
```

## Delete the specific rule -
```
iptables -t filter -D INPUT -s 149.154.161.221 -j DROP 
```

## Block all types of access to 'filewall' from any ip. 
```
iptables -t filter -A INPUT -j DROP 
```

# Block Ports ---
### (input direction, telnet/ssh/web services)

## block web access on 'firewall', we are not able to access 'web server on 'firewall'.
```
iptables -t filter -A INPUT -m tcp/udp -p tcp/udp -a 172.24.0.11 --drop 80 -j DROP
```

## we want to block 'telnet'(23) and 'ssh'(22). we could write 2 rules for blocking 2 ports as we did in case of web server but here we will be using 'multiport' module for specifying multiple ports in single rule.
```
iptables -t filter -A INPUT  -m multiport -p tcp/upd -s 172.24.0.11 --dports 22,23 -j DROP 
```
### block 'ssh' and 'telnet'. if we have written incourect rule syntax,'iptables' will show the error
 
