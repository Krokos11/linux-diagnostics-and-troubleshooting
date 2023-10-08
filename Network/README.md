# Troubleshooting Network Issues

## Ping command

Ping is using ICMP protocol, which means Internet Control Message Protocol.

When using ping, if it goes well, server gives proper output:

```
PING krokos-rpi.home (192.168.1.100) 56(84) bytes of data.
64 bytes from krokos-rpi.home (192.168.1.100): icmp_seq=1 ttl=64 time=0.950 ms
```
**ttl** means time ti live

### Specify interface
Using ping u can specify interface
```
ping -I eth0 krokos-rpi.home
```
(Something not work in that)

## Scanning Network Ports

Nmap tool

```
nmap krokos-rpi.home
Starting Nmap 7.93 ( https://nmap.org ) at 2023-10-07 14:15 UTC
Nmap scan report for krokos-rpi.home (192.168.1.100)
Host is up (0.0024s latency).
Other addresses for krokos-rpi.home (not scanned): 192.168.1.3
Not shown: 994 closed tcp ports (conn-refused)
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
3001/tcp open  nessus
8080/tcp open  http-proxy
8086/tcp open  d-s-n
9090/tcp open  zeus-admin

Nmap done: 1 IP address (1 host up) scanned in 0.25 seconds
```

It received open ports from host

### Scan subnet

```
nmap 192.168.1.1-20
```

### Scan route as well

```
nmap -A krokos-rpi.home
```

## Communicate with a remote service

Usually to check if service is running on another machine, there is using **telnet** command. To start communicate with that server, there is another command called **ncat**.

### Ncat

Ncat can use either TCP and UDP to communicate with a network service

## Network monitoring utility

One of tool it will be using is **iptraf-ng**. 

### Iptraf-ng
With this tool, you can monitor your inboud and outbound network traffic passing through interface.

```
iptraf-ng
fatal: This program requires a screen size of at least 80 columns by 24 lines
Please resize your window
```
It can display detail or summary counts about the network interfaces on your local system.

## Troubleshoot not working network interface

