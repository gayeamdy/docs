---
title: 'Configuring IPv6 on dedicated servers'
slug: network-ipv6
excerpt: 'Find out how to configure IPv6 addresses on our infrastructure'
section: 'Network Management'
---

**Last updated 1st December 2021**

## Objective

Internet Protocol version 6 (IPv6) is the latest version of the Internet Protocol (IP). It is designed to address the long-anticipated address exhaustion of its predecessor, IPv4, by using 128-bit addresses instead of 32-bit addresses. Every OVHcloud dedicated server comes with a /64 IPv6 block. This represents over 18 quintillion IP addresses that you can use at your convenience.

**This guide explains how to configure IPv6 addresses on your server using various examples.**

> [!warning]
>OVHcloud is providing you with services for which you are responsible, with regard to their configuration and management. You are therefore responsible for ensuring they function correctly.
>
>This guide is designed to assist you in common tasks as much as possible. Nevertheless, we recommend that you contact a specialist service provider and/or discuss the issue with [our community](https://community.ovh.com/en/) if you face difficulties or doubts concerning the administration, usage or implementation of services on a server.
>

## Requirements

- A [dedicated server](https://www.ovhcloud.com/en-ie/bare-metal/) in your OVHcloud account
- All your IPv6 information (prefix, gateway etc.)
- Basic knowledge of [SSH](../ssh-introduction/) and networking

## Instructions

If you are using an OVHcloud-provided Linux OS template to install your server, you will see that you already have the first (main) IPv6 configured out of the box.


> [!primary]
>
> The default gateway for your IPv6 block (IPv6_GATEWAY) is usually xxxx.xxxx.xxxx.xxFF:FF:FF:FF:FF. 
>
> For example:
> 
> - The IPv6 address of the server is 2607:5300:60:62ac::/64. The IPv6_GATEWAY will therefore be 2607:5300:60:62FF:FF:FF:FF:FF.
> - The IPv6 address of the server is 2001:41D0:1:46e::/64. The IPv6_GATEWAY will therefore be 2001:41D0:1:4FF:FF:FF:FF:FF.
>
> The safe way to retrieve the networking information for your server is to [use the OVHcloud API](https://docs.ovh.com/ie/en/api/first-steps-with-ovh-api/). Execute the following API call, indicating the internal server name (example: `ns3956771.ip-169-254-10.eu`):
>

> [!api]
>
> @api {GET} /dedicated/server/{serviceName}/specifications/network
>


### Debian and Debian-based operating systems

> [!warning]
>
> Before following the steps below, we strongly suggest that you disable IPv6 autoconf and router advertising to prevent known issues. You can do so by adding the following lines to your `sysctl.conf` file, which is located in /etc/sysctl.conf:
> 
> `net.ipv6.conf.all.autoconf=0`
> 
> `net.ipv6.conf.all.accept_ra=0`
> 
> Once this has been done, you can apply those rules by executing the following command: `sh sysctl -p`.
> 

#### Step 1: Use SSH to connect to your server

Find more information in [this guide](../getting-started-dedicated-server/#logging-on-to-your-server).

#### Step 2: Open your server's network configuration file

Your server's network configuration file is located in `/etc/network/interfaces`. Use the command line to locate the file and open it for editing. Also consider creating a backup first.

#### Step 3: Amend the network configuration file

Amend the file so that it looks like the example below. In this example, the network interface is called `eth0`. The interface on your server may differ.

```console
iface eth0 inet6 static 
    address YOUR_IPv6 
    netmask 128

post-up /sbin/ip -f inet6 route add IPv6_GATEWAY dev eth0 
post-up /sbin/ip -f inet6 route add default via IPv6_GATEWAY 
pre-down /sbin/ip -f inet6 route del IPv6_GATEWAY dev eth0
pre-down /sbin/ip -f inet6 route del default via IPv6_GATEWAY
```

Additional IPv6 addresses can be added by `up /sbin/ifconfig eth0 inet6 add YOUR_2nd_IPv6/64` lines in the file.

#### Step 4: Save the file and apply the changes

Save your changes to the file and then restart the network or reboot your server to apply the changes.

#### Step 5: Test the IPv6 connectivity

You can test the IPv6 connectivity by running the commands shown below:

```bash
ping6 -c 4 2001:4860:4860::8888

>>> PING 2001:4860:4860::8888(2001:4860:4860::8888) 56 data bytes
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=1 ttl=55 time=23.6 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=2 ttl=55 time=23.8 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=3 ttl=55 time=23.9 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=4 ttl=55 time=23.8 ms

>>> --- 2001:4860:4860::8888 ping statistics ---
>>> 1 packets transmitted, 1 received, 0% packet loss, time 0ms
>>> rtt min/avg/max/mdev = 23.670/23.670/23.670/0.000 ms
```


If you are not able to ping this IPv6 address, check your configuration and try again. Also ensure that the machine you are testing from is connected with IPv6. If it still does not work, please test your configuration in [Rescue mode](../rescue_mode/).

### Fedora 26 and above

> [!warning]
>
> This example has been made with CentOS 7.0. Results may vary when using other Redhat derivatives.
>

#### Step 1: Use SSH to connect to your server

Find more information in [this guide](../getting-started-dedicated-server/#logging-on-to-your-server).


#### Step 2: Open your server's network configuration file

Your server's network configuration file is located in /etc/sysconfig/network-scripts/ifcfg-eth0. Use the command line to locate this file and open it for editing.

#### Step 3: Amend the network configuration file

Amend the file so that it looks like the example below. In this example, the network interface is called eth0. The interface on your server may differ. Also, we have omitted the IPv4 Failover configuration to avoid confusion, but the IPv6 configuration is made in the same configuration file.

```console
IPV6INIT=yes
IPV6_AUTOCONF=no
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6ADDR=YOUR_IPv6/64
IPV6ADDR_SECONDARIES=YOUR_2nd_IPv6/64 YOUR_3rd_IPv6/64
IPV6_DEFAULTGW=IPv6_GATEWAY
```
If you need more IPv6 addresses on the machine, add them in the `IPV6ADDR_SECONDARIES` line, separated by whitespace.

#### Step 4: Save the file and apply the changes

Save your changes to the file and then restart the network or reboot your server to apply the changes.

#### Step 5: Test the IPv6 connectivity

You can test the IPv6 connectivity by running the commands shown below:

```bash
ping6 -c 4 2001:4860:4860::8888

>>> PING 2001:4860:4860::8888(2001:4860:4860::8888) 56 data bytes
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=1 ttl=55 time=23.6 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=2 ttl=55 time=23.8 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=3 ttl=55 time=23.9 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=4 ttl=55 time=23.8 ms

>>> --- 2001:4860:4860::8888 ping statistics ---
>>> 1 packets transmitted, 1 received, 0% packet loss, time 0ms
>>> rtt min/avg/max/mdev = 23.670/23.670/23.670/0.000 ms
```

If you are not able to ping this IPv6 address, check your configuration and try again. Also ensure that the machine you are testing from is connected with IPv6. If it still does not work, please test your configuration in [Rescue mode](../rescue_mode/).

### FreeBSD

#### Step 1: Use SSH to connect to your server

Find more information in [this guide](../getting-started-dedicated-server/#logging-on-to-your-server).


#### Step 2: Open your server's network configuration file

Your server's network configuration file is located in `/etc/rc.conf`. Use the command line to locate this file and open it for editing.

#### Step 3: Amend the network configuration file

Amend the file so that it looks like the example below. In this example, the network interface is called em0. The interface on your server may differ.

```bash
IPv6_activate_all_interfaces="YES" 
IPv6_defaultrouter="IPv6_GATEWAY" 
ifconfig_em0_IPv6="inet6 IPv6_Address prefixlen 64"
ifconfig_em0_alias0="inet6 IPv6_Address_2 prefixlen 64"
ifconfig_em0_alias1="inet6 IPv6_Address_3 prefixlen 64"
```

#### Step 4: Save the file and reboot the server

Save your changes to the file and then restart the network or reboot your server to apply the changes.

#### Step 5: Test the IPv6 connectivity

You can test the IPv6 connectivity by running the commands shown below:

```bash
ping6 -c 4 2001:4860:4860::8888

>>> PING 2001:4860:4860::8888(2001:4860:4860::8888) 56 data bytes
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=1 ttl=55 time=23.6 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=2 ttl=55 time=23.8 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=3 ttl=55 time=23.9 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=4 ttl=55 time=23.8 ms

>>> --- 2001:4860:4860::8888 ping statistics ---
>>> 1 packets transmitted, 1 received, 0% packet loss, time 0ms
>>> rtt min/avg/max/mdev = 23.670/23.670/23.670/0.000 ms
```

If you are not able to ping this IPv6 address, check your configuration and try again. Also ensure that the machine you are testing from is connected with IPv6. If it still does not work, please test your configuration in [Rescue mode](../rescue_mode/).

### Ubuntu 18.04

#### Step 1: Use SSH to connect to your server

Find more information in [this guide](../getting-started-dedicated-server/#logging-on-to-your-server).

#### Step 2: Open your server's network configuration file

Open the network configuration file located in /etc/systemd/network. For demonstration purposes, our file is called 50-default.network.

#### Step 3: Amend the network configuration file

Using a text editor, amend the file by adding the following lines to the relevant sections as shown in the example below:

```console
[Network]
Destination=Gateway_Address

[Address]
Address=IPv6_Address/64

[Route]
Destination=Gateway_Address
Scope=link
```
To add multiple IPv6 addresses, add multiple [Address] sections

```console
[Address]
Address=IPv6_Address_2/64

[Address]
Address=IPv6_Address_3/64
```
#### Step 4: Save the file and reboot the server

Save your changes to the file and then restart the network or reboot your server to apply the changes.

#### Step 5: Test the IPv6 connectivity

You can test the IPv6 connectivity by running the commands shown below:

```bash
ping6 -c 4 2001:4860:4860::8888

PING 2001:4860:4860::8888(2001:4860:4860::8888) 56 data bytes
64 bytes from 2001:4860:4860::8888: icmp_seq=1 ttl=57 time=4.07 ms
64 bytes from 2001:4860:4860::8888: icmp_seq=2 ttl=57 time=4.08 ms
64 bytes from 2001:4860:4860::8888: icmp_seq=3 ttl=57 time=4.08 ms
64 bytes from 2001:4860:4860::8888: icmp_seq=4 ttl=57 time=4.07 ms

--- 2001:4860:4860::8888 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 4.075/4.079/4.083/0.045 ms
```

### Windows Server 2012

#### Step 1: Use RDP to connect to your server

Find more information in [this guide](../getting-started-dedicated-server/#logging-on-to-your-server).


#### Step 2: Open your server's network configuration

First, right-click on the network icon in the notification area to go to the `Network and Sharing Center`{.action}.

![Network and Sharing Center](images/ipv6_network_sharing_center.png){.thumbnail}

Click `Change adapter settings`{.action}.

![Change adapter settings](images/ipv6_change_adapter_settings.png){.thumbnail}

Right-click your network adapter, then click `Properties`{.action}.

![Network Adapter Properties](images/ipv6_network_adapter_properties.png){.thumbnail}

Select `Internet Protocol Version 6`{.action}, then click `Properties`{.action}.

![Properties](images/ipv6_properties.png){.thumbnail}

#### Step 3: Amend the network configuration 

Enter your IPv6 configuration (`IPv6 address` and `Default Gateway`) and click `OK`{.action}.

![Properties](images/ipv6_configuration.png){.thumbnail}

### Troubleshooting

If after testing your connection you are still experiencing problems, please create a support request to review your configurations. It is necessary to provide:

- The operating system name and version you are using on your server.
- The name and directory of the network configuration file.
- The content of that file.


## Go further

Join our community of users on <https://community.ovh.com/en/>.
