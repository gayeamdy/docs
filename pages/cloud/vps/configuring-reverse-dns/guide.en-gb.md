---
title: Configuring the reverse DNS of a VPS
excerpt: Find out how to set up the reverse DNS resolution
slug: configure-reverse-dns-vps
routes:
    canonical: 'https://docs.ovh.com/gb/en/public-cloud/configure-reverse-dns-instance/'
section: Network management
order: 3
---

**Last updated 14th November 2021**

## Objective

Reverse DNS is the complement to "forward" DNS resolution which resolves domain names into IP addresses. With reverse DNS resolution, an IP address can resolve into the domain name (or host name) it is mapped to. This means that DNS queries of the associated IP address will return this domain name.

Configuring the reverse DNS resolution for a VPS is especially useful when sending emails. A mail server's validation by spam protection systems will improve if a DNS lookup of the IP address resolves properly.

**This guide explains how to configure the reverse DNS path for the IP address(es) of your VPS.**

## Requirements

- A [Virtual Private Server](https://www.ovhcloud.com/en-gb/vps/) in your OVHcloud account
- A domain name with its `A` record pointing to the VPS
- Access to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB)

## Instructions

Log in to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB), switch to the `Bare Metal Cloud`{.action} section and click on `IP`{.action} in the left-hand menu.

In the table on this page, your eligible services will be listed. You can filter for your VPS using the drop-down menu under **Services**.

![Reverse DNS](images/reversecp01.png){.thumbnail}

Click on `...`{.action} in the row of the IP address concerned and select `Modify the reverse path`{.action}.

![Reverse DNS](images/reversecp02.png){.thumbnail}

In the new window, enter your reverse path and click on `Confirm`{.action}.

You can also edit the reverse path directly via the icon in the **Reverse DNS** column of the table.

> [!primary]
>
If the modification does not work as expected, verify that the `A` record is correctly configured in the DNS zone of your domain name. Bear in mind that it might take up to 24 hours for DNS zone changes to be effective, in case you have only recently edited the `A` record.
>
If the domain name is managed by OVHcloud as its registrar and it uses OVHcloud DNS servers, you can refer to [this guide](https://docs.ovh.com/gb/en/domains/web_hosting_how_to_edit_my_dns_zone/).
>

## Go further <a name="gofurther"></a>

[Getting started with a VPS](../getting-started-vps/)

[Editing an OVHcloud DNS zone](https://docs.ovh.com/gb/en/domains/web_hosting_how_to_edit_my_dns_zone/)

Join our community of users on <https://community.ovh.com/en/>.
