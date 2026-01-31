# Linux Commands

## whois
`whois` is a command that displays information about a domain owner.

```shell
$ whois google.com
  Domain Name: GOOGLE.COM
  Registry Domain ID: 2138514_DOMAIN_COM-VRSN
  Registrar WHOIS Server: whois.markmonitor.com
  Registrar URL: http://www.markmonitor.com
  Updated Date: 2019-09-09T15:39:04Z
  Creation Date: 1997-09-15T04:00:00Z
  Registry Expiry Date: 2028-09-14T04:00:00Z
  Registrar: MarkMonitor Inc.
  Registrar IANA ID: 292
  Registrar Abuse Contact Email: abusecomplaints@markmonitor.com
  Registrar Abuse Contact Phone: +1.2086851750
  Domain Status: clientDeleteProhibited https://icann.org/epp#clientDeleteProhibited
  Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited
  Domain Status: clientUpdateProhibited https://icann.org/epp#clientUpdateProhibited
  Domain Status: serverDeleteProhibited https://icann.org/epp#serverDeleteProhibited
  Domain Status: serverTransferProhibited https://icann.org/epp#serverTransferProhibited
  Domain Status: serverUpdateProhibited https://icann.org/epp#serverUpdateProhibited
  Name Server: NS1.GOOGLE.COM
  Name Server: NS2.GOOGLE.COM
  Name Server: NS3.GOOGLE.COM
  Name Server: NS4.GOOGLE.COM
  DNSSEC: unsigned
  URL of the ICANN Whois Inaccuracy Complaint Form: https://www.icann.org/wicf/
...  
```

## nslookup
`nslookup` is a command that displays DNS information about a domain.

```shell
$ nslookup ubc.com
Server:		192.168.65.7
Address:	192.168.65.7#53

Non-authoritative answer:
Name:	ubc.com
Address: 23.185.0.2
```

```shell
$ nslookup -type=NS ubc.com
Server:		192.168.65.7
Address:	192.168.65.7#53

Non-authoritative answer:
ubc.com	nameserver = ns2.ubc.com.
ubc.com	nameserver = ns1.ubc.com.

Authoritative answers can be found from:
```

## dig
`dig` is a command that displays DNS information about a domain.

```shell
$ dig ubc.com

; <<>> DiG 9.20.15-2-Debian <<>> ubc.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 63861
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ubc.com.			IN	A

;; ANSWER SECTION:
ubc.com.		752	IN	A	23.185.0.2

;; Query time: 115 msec
;; SERVER: 192.168.65.7#53(192.168.65.7) (UDP)
;; WHEN: Tue Jan 20 01:54:11 UTC 2026
;; MSG SIZE  rcvd: 48
```

```shell
$ dig mx ubc.com

; <<>> DiG 9.20.15-2-Debian <<>> mx ubc.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 3802
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ubc.com.			IN	MX

;; ANSWER SECTION:
ubc.com.		1127	IN	MX	10 ubc-com.mail.protection.outlook.com.

;; Query time: 91 msec
;; SERVER: 192.168.65.7#53(192.168.65.7) (UDP)
;; WHEN: Tue Jan 20 01:54:55 UTC 2026
;; MSG SIZE  rcvd: 83
```

## ping
`ping` is a command that sends ICMP echo requests to a host for checking if the host is reachable.

`-c` is the option to specify the number of packets to send.

```shell
$ ping -c 5 google.com
PING google.com (142.251.33.78) 56(84) bytes of data.
64 bytes from sea09s28-in-f14.1e100.net (142.251.33.78): icmp_seq=1 ttl=64 time=17.3 ms
64 bytes from sea09s28-in-f14.1e100.net (142.251.33.78): icmp_seq=2 ttl=64 time=20.0 ms
64 bytes from sea09s28-in-f14.1e100.net (142.251.33.78): icmp_seq=3 ttl=64 time=18.9 ms
64 bytes from sea09s28-in-f14.1e100.net (142.251.33.78): icmp_seq=4 ttl=64 time=20.8 ms
64 bytes from sea09s28-in-f14.1e100.net (142.251.33.78): icmp_seq=5 ttl=64 time=18.4 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4015ms
rtt min/avg/max/mdev = 17.308/19.079/20.768/1.216 ms
```

## traceroute
`traceroute` is a command that traces the route a packet takes to a host.

```shell
$ traceroute google.com
traceroute to google.com (142.251.33.78), 30 hops max, 60 byte packets
 1  * * 192.168.64.1 (192.168.64.1)  3.375 ms
 2  OpenWrt.lan (192.168.1.254)  11.750 ms  11.697 ms  11.660 ms
 3  s209-121-64-1.bc.hsia.telus.net (209.121.64.1)  13.596 ms  13.587 ms  13.579 ms
 4  * * *
 5  * * *
 6  * * *
 7  72.14.232.192 (72.14.232.192)  17.537 ms *  19.244 ms
 8  QUBCPQAJGR00.bb.telus.com (154.11.15.190)  19.191 ms 142.251.249.236 (142.251.249.236)  15.037 ms 142.251.50.243 (142.251.50.243)  19.165 ms
 9  108.170.255.133 (108.170.255.133)  25.161 ms 209.85.174.62 (209.85.174.62)  14.951 ms  16.727 ms
10  142.251.50.245 (142.251.50.245)  17.959 ms * *
11  142.251.55.202 (142.251.55.202)  13.915 ms sea09s28-in-f14.1e100.net (142.251.33.78)  15.468 ms  15.816 ms
```

## telnet
`telnet` is a command that connects to a TCP port on a host.

## netcat
`netcat` is a command that connects to a TCP or UDP port on a host or listens for incoming connections.

```shell
$ nc -sV 8000
```
