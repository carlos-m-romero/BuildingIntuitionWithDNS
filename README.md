<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png" alt="osTicket logo"/>
</p>

# Building Intuition for DNS
In this tutorial, let's simplify things and make it easy to understand DNS. We'll explore DNS A-Records on a server, creating and deleting records. We'll also dive into concepts like CNAME records and Root hints.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Command Line
- Microsoft Active Directory

## Operating Systems Used

- Windows 10 (21H2)

## List of Prerequisites

- Active Directory Virtual Machine
- Client Machine joined to your domain
- Microsoft Azure with two pre-configured VMs: Client-1 and DC-1
- Microsoft Active Directory installed on DC-1 and promoted to a domain controller

## Lab Steps

**A-Record Exercise**

First, let's take a look at DNS A-Records on the server. A-Records are mappings from hostnames to IP addresses. Follow these steps:

1. Log in to DC-1 as your domain admin account (mydomain.com\jane_admin).
2. Log in to Client-1 as an admin (mydomain\jane_admin).
3. From Client-1, try to ping "mainframe." You'll notice that it fails.
4. Use nslookup to check "mainframe" and observe that there is no DNS record.
5. Create a DNS A-record on DC-1 for "mainframe" and point it to DC-1's private IP address.
6. Go back to Client-1 and try to ping "mainframe." You'll see that it works now.

![16](https://github.com/carlos-m-romero/BuildingIntuitionWithDNS/assets/148396073/a6fade3a-1f9d-45ba-9223-25bdc4155d9a)



**Local DNS Cache Exercise**

1. Go back to DC-1 and change the record address of "mainframe" to 8.8.8.8.
2. Return to Client-1 and ping "mainframe" again. Notice that it still pings the old address.
3. Check the local DNS cache using the command `ipconfig /displaydns`.
4. Flush the DNS cache using the command `ipconfig /flushdns`. Observe that the cache is now empty.
5. Try to ping "mainframe" again. You'll see that the new record address is now shown.

![17](https://github.com/carlos-m-romero/BuildingIntuitionWithDNS/assets/148396073/43dc53bb-1cb0-4cb4-be43-b16d90af8cb7)

![18](https://github.com/carlos-m-romero/BuildingIntuitionWithDNS/assets/148396073/8d3bf535-3fb1-44b0-b4ff-5dbc339ea65b)


**CNAME Record Exercise**

1. Go back to DC-1 and create a CNAME record that points the host "search" to "www.google.com."
2. Return to Client-1 and attempt to ping "search." Observe the results of the CNAME record.


![19](https://github.com/carlos-m-romero/BuildingIntuitionWithDNS/assets/148396073/a26e025d-eaed-4f29-a7af-f697527735b5)


3. On Client-1, use `nslookup` to query "search" and observe the results of the CNAME record.

By following these steps, you'll develop a better understanding of DNS, A-Records, DNS caching, and CNAME records.
