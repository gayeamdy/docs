---
title: 'Configuring the vRack on your dedicated servers'
slug: configuring-vrack-on-dedicated-servers
excerpt: 'Find out how to configure the vRack on two or more dedicated servers'
section: 'vRack'
order: 01
---

**Last updated 19th October 2021**

## Objective

The OVHcloud vRack (virtual rack) allows multiple servers to be grouped together (regardless of number and physical location in our data centres) and connects them to a virtual switch within the same private network. Your servers can communicate privately and securely between each other, within a dedicated VLAN.

**This guide explains how to configure the vRack on two or more dedicated servers.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZA7IsbDdAmc?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## Requirements

- A [vRack](https://www.ovh.ie/solutions/vrack/) service activated in your account
- Two or more [dedicated servers](https://www.ovhcloud.com/en-ie/bare-metal/) (compatible with vRack)
- Administrative access (root) to the server via SSH or RDP
- Access to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie)
- A private IP address range of your choice


## Instructions

### Step 1: Adding your servers to the vRack

Once the vRack is activated in your account, go to the `Bare Metal Cloud`{.action} section of your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie) and open the `vRack`{.action} menu in the left-hand sidebar.

Select your vRack from the list to display the list of eligible services. Click on each server you want to add to the vRack and then click the `Add`{.action} button.

![vRack selection](images/vrack_selection.png){.thumbnail}

### Step 2: Configuring your network interfaces

The following sections contain the configurations for the most commonly used recent distributions/operating systems. The first step is always to [log in to your server](../getting-started-dedicated-server/) via SSH or a RDP session (for Windows). The examples below presume you are logged in as a user with elevated permissions (Administrator/sudo).

> [!primary]
>
Concerning different distribution releases, please note that the proper procedure to configure your network interface as well as the file names may have been subject to change. We recommend to consult the manuals and knowledge resources of the respective OS versions if you experience any issues.
> 
For example purposes, the configuration details below will have the IP address range `192.168.0.0/16` (**Subnet mask**: `255.255.0.0`).
> 
You can use any private IP range of your choice and any address within that range.
> 

#### GNU/Linux configurations

The network interface names of your servers are not always the same. Whenever used in the following examples, replace NETWORK_INTERFACE with the appropriate interface name.

The sure way to verify the correct interface for the vRack is to check the tab `Network interfaces`{.action} of your server in the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie). In the table at the bottom, take note of the MAC address which is also the **Name** of the **Private** interface.

![vRack interface](images/private_interface.png){.thumbnail}

Once connected to your server via SSH, you can list your network interfaces with the following command:

```bash
ip a
```

In the line that begins with ```link ether```, you can verify that this interface matches the **Private** interface listed in your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie). Use this interface name to replace `NETWORK_INTERFACE` in the configurations below (example: `eno2`).

```console
link ether f0:00:00:ef:0e:f0
```

##### **Debian**

Using a text editor of your choice, open the network configuration file located in `/etc/network/interfaces.d` for editing. Here the file is called `50-cloud-init`.

```bash
editor /etc/network/interfaces.d/50-cloud-init
```

Add the following lines:

```console
auto NETWORK_INTERFACE
iface NETWORK_INTERFACE inet static
address 192.168.0.1
netmask 255.255.0.0
```

Save your changes to the config file and exit the editor.

Restart the networking service to apply the configuration:

```bash
systemctl restart networking
```

Repeat this process for your other server(s) and assign an unused IP address from your private range. Once you have done this, your servers will be able to communicate with each other on the private network.

##### **Ubuntu**

Using a text editor of your choice, open the network configuration file located in `/etc/netplan/` for editing. Here the file is called `50-cloud-init.yaml`.

```bash
editor /etc/netplan/50-cloud-init.yaml
```

Add the IP configuration to the existing one after the line `ethernets`:

```yaml
    ethernets:
        NETWORK_INTERFACE:
            dhcp4: no
            addresses:
              - 192.168.0.1/16
```

> [!warning]
>
> It is important to respect the alignment of each element in `yaml` files as represented in the example above. Do not use the tab key to create your spacing. Only the space key is needed. 
>

Save your changes to the config file and exit the editor.

Apply the configuration:

```bash
netplan apply
```

Repeat this process for your other server(s) and assign an unused IP address from your private range. Once you have done this, your servers will be able to communicate with each other on the private network.

##### **CentOS**

Using a text editor of your choice, open the file `/etc/sysconfig/network-scripts/ifcfg-NETWORK_INTERFACE`.

```bash
editor /etc/sysconfig/network-scripts/ifcfg-NETWORK_INTERFACE
```

Add these lines:

```console
DEVICE=NETWORK_INTERFACE
BOOTPROTO=static
IPADDR=192.168.0.1
NETMASK=255.255.0.0
ONBOOT=yes
TYPE=Ethernet
```

Save your changes to the config file and exit the editor.

Restart the networking service to apply the changes:

```bash
systemctl restart networking
```

On **CentOS 8** use this command:

```bash
systemctl restart NetworkManager.service
```

Repeat this process for your other server(s) and assign an unused IP address from your private range. Once you have done this, your servers will be able to communicate with each other on the private network.


#### Windows configuration 

For example purposes, the following configurations will use the IP address range of `192.168.0.0/16` (**Subnet mask**: `255.255.0.0`).

Log on to your Windows server via remote desktop and go to the **Control Panel**.

![Windows Control Panel](images/windows_control_panel.png){.thumbnail}

Click on `Network and Internet`{.action}.

![Network and Internet](images/windows_network_and_internet.png){.thumbnail}

Open `Network and Sharing Center`{.action}.

![Network and Sharing Centre](images/windows_network_and_sharing_centre.png){.thumbnail}

Click on `Change Adapter Settings`{.action}.

![Change Adapter Settings](images/windows_change_adapter_settings.png){.thumbnail}

Right-click the secondary network interface and then click `Properties`{.action}.

![Windows Properties](images/windows_properties_button.png){.thumbnail}

Double-click `Internet Protocol Version 4 (TCP/IPv4)`{.action}.

![Internet Protocol Version 4](images/windows_ipv4.png){.thumbnail}

Click on **Use the following IP address**. Enter any **IP address** from your private range and the appropriate **Subnet mask** (`255.255.0.0` in this example) into the corresponding fields.

![Use the following IP address](images/windows_use_following_ip_address.png){.thumbnail}

Click on `OK`{.action} to save the changes and reboot your server to apply them.

Repeat this process for your other server(s) and assign an unused IP address from your private range. Once you have done this, your servers will be able to communicate with each other on the private network.

## Go further

Join our community of users on <https://community.ovh.com/en/>.
