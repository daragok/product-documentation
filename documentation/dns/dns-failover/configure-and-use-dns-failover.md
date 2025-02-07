---
title: configure-and-use-dns-failover
displayName: Configure and use
published: true
order: 20
toc:
pageTitle: Configuring and usage of the DNS Health checks technology | Gcore
pageDescription: A comprehensive guide on how to configure and manage DNS Health checks.
---
# Configure and use DNS Health checks

1\. Go to the <a href="https://dns.gcore.com" target="_blank">DNS</a> service.

2\. Navigate to the DNS zone where you intend to set up Health checks. A new page will open.

<img src="https://assets.gcore.pro/docs/dns/dns-failover/configure-and-use-dns-failover/image-3571.png" alt="" width="70%">

3\. 3. Ensure that <a href="https://gcore.com/docs/dns/about-gcore-dns#interface-modes-non-advanced-and-advanced" target="_blank">Advanced interface mode</a> is enabled. In non-advanced mode, the Health checks feature will not appear.

4\. Click the name of the A, AAAA, or CNAME record. The “Records list/Edit record set” page will open.

<img src="https://assets.gcore.pro/docs/dns/dns-failover/configure-and-use-dns-failover/group-90994.png" alt="" width="80%">

5\. Enable the Health checks feature. To configure it, select a protocol (TCP, UDP, ICMP, or HTTP) that Health checks will use when sending requests to your web servers. Follow the instructions below:

<expandable-element title="TCP/UDP">

- **Port**: Specify the port to connect to; for example, 80 or 443
- **Check Frequency**: Choose the interval of checks from the list
- **Timeout**: Set the time within which your web servers should give the response before being considered down
- **Command (optional)**: Enter the text that will be sent to the host of the site as plain text, e.g., GET / HTTP/1.1\n\n

</expandable-element>

<expandable-element title="ICMP">

- **Check Frequency**: Choose the interval of checks from the list
- **Timeout**: Set the time within which your web servers should give the response before being considered down

</expandable-element>

<expandable-element title="HTTP">

- **Port**: Specify the port to connect to; for example, 80 or 443
- **Check Frequency**: Choose the interval of checks from the list
- **Timeout**: Set the time within which your web servers should give the response before being considered down
- **Requested URL**: Enter the URL that will be requested for checks.
- **Requested Method**: Choose the method for checking requests; e.g., GET
- **Using TLS**: Choose whether TLS should be used.
- **HTTP status code**: Put the expected HTTP response code or leave it blank if any response is ok.
- **Expected content regexp**: Enter a regular expression that would match the response body or leave it blank.

</expandable-element>

<img src="https://assets.gcore.pro/docs/dns/dns-failover/configure-and-use-dns-failover/image-checks-50.png" alt="" width="70%">

6\. (Optional) You can enable backup metadata for Health checks. In this case, records marked as backups will not participate in the response if at least one “healthy,” valid record exists. If all records not marked as backup are non-functional, the “healthy” backup records will appear in the response. 

To configure backup metadata, select which record will be used as a backup (Record 2 in the example,) choose “backup” from the dropdown list, and enable the toggle.

<img src="https://assets.gcore.pro/docs/dns/dns-failover/configure-and-use-dns-failover/image-checks-60.png" alt="" width="70%">

“Failover” is a read-only meta that appears on the records with the Health checks enabled (step no. 5).

7\. (Optional) You can configure logic that will be used to distribute requests among available servers when some of them are unavailable. By default, DNS Health checks use round-robin balancing. <a href="https://gcore.com/docs/dns/dns-records/configure-weight-balancing-and-geobalancing" target="_blank">Use our detailed guide</a> for more information. In the example, we set the weight balancing with DNS Health checks and backup metadata. 

<img src="https://assets.gcore.pro/docs/dns/dns-failover/configure-and-use-dns-failover/image-checks-70.png" alt="" width="70%">

8\. (Optional) You can add more records, specify content, and specify metadata (steps 7–8.)

9\. Save changes.

<img src="https://assets.gcore.pro/docs/dns/dns-failover/configure-and-use-dns-failover/image-checks-80.png" alt="">


The configuration is complete! Refresh your DNS cache renewal and Health checks will start to monitor your site’s availability.

You can also check for recent monitoring events in Health checks logs. Go to the page of the DNS zone for which your configured DNS Health checks. Select the needed record, click the three dots on the right, and click **Health checks logs**.

<img src="https://assets.gcore.pro/docs/dns/dns-failover/configure-and-use-dns-failover/image-3589.png" alt="" width="80%"> 