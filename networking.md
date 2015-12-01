#Networking
Now you know some common tools for viewing and controlling your computers
local state, it is time to teach you something (more) about the linux tools
that check and configure your network.

I would like to point out, at this point, the complexity of the Linux
Networking Stack\*.

\*) Stack: a set of tools built on top of each other, collaborating to
accomplish some common goal (in this case a networking capable Linux
kernel, along with the user space utilities that configure and extend
such functionality - these are the applications trained in this article).

An incomplete list of applications, you could look up (most of them are
likely to be already installed on your system):
* <span width="25px">`ip`</span>: An immensely useful tool for controlling
your network settings
* <span width="15px">`netstat`</span>: This tool can do way more than show
**NET** work **STAT** istics
* <span width="15px">`nslookup`</span>: ns is in networking a `nameserver`
* <span width="15px">`tcpdump`</span>: Can monitor local network traffic
* <span width="15px">`arp`</span>: Show the ARP-table for the network
* <span width="15px">`nmap`</span>: Can tell almost anything about your
network - if you know how to ask
* <span width="15px">`nettop`</span>: A top-like program for monitoring net
traffic
* <span width="15px">`iptables`</span>: Most common cli frontend to the Linux
kernel firewall.
* <span width="15px">`nftables`</span>: From the same dev as above, meant to
replace iptables.
* <span width="15px">`shitload of others`</span>... for masking dns queries,
running various servers (web,mail,"clouds"), and for accessing the internet,
etc., etc. - the linux community love their CLIs and also networks, but
I shall keep this article about the lower-level stuff, and refer you to
[this article](networking.usage.md), if you wish to know about the more
userland-oriented software.
<!---
* <span width="15px">`tracepath`</span>: Analgous to the Windows Command Line tool tracert
--->

#IPTABLES!
1. Install and configure iptables as per
   [the Arch Wiki](https://wiki.archlinux.org/index.php/Iptables)
