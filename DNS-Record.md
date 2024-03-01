## What are the most common types of DNS record?

|S.No.| Record Type | Descritption|
|-----|------------|-------------|
|1.|**A record** | The record that holds the `IP address of a domain`.|
|2.|**AAAA record**|The record that contains the `IPv6 address for a domain` (as opposed to A records, which list the IPv4 address). |
|3.|**CNAME record**|Forwards one domain or subdomain to `another domain, does NOT provide an IP address`. |
|4.|**MX record**| Directs mail to an `email server`.|
|5.|**TXT record**| Lets an admin store text notes in the record. These records are often used for `email security`.|
|6.|**NS record**|Stores the name server for a `DNS entry`. |
|7.|**SOA record**|Stores `admin information about a domain`.|
|8.|**SRV record** |Specifies a `port for specific services`.|
|9.|**PTR record** |Provides a domain name in `reverse-lookups`.|

Note:
-----
Reference - https://www.cloudflare.com/en-gb/learning/dns/dns-records/
