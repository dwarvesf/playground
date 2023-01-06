---
tags: engineering, DNS, network, A record, CNAME record
author: Tran Hoang Nam
github_id: namtrhg
date: 2022-06-01
---
 **A record** and **CNAME** are one of the most common types of records when you want to deploy your `domain` or `subdomain` on the internet.

## Use-cases and restrictions

### A record

`A` record is an abbreviation for "Address". The address you type when you go to a website, send an email or connect to Twitter or Facebook.
You can do a lot with `A` records, including using multiple `A` records for the same domain in order to provide redundancy and fallbacks. Additionally, multiple names could point to the same address, in which case each would have its own `A` record pointing to that same IP address.
![A record config picture](https://www.elegantthemes.com/blog/wp-content/uploads/2020/09/a-record-example.jpg)

#### Use-cases

- Use an  `A`  record if you manage which IP addresses are assigned to a particular machine, or if the IP are fixed (this is the most common case).

### CNAME record

A canonical name `CNAME` is a type of database record in the Domain Name System (DNS) that shows that one domain name is a nickname or alias for another domain name. The `CNAME`, which is also called the "true name," is especially important when more than one service runs from the same IP address.
![CNAME record config picture](https://www.elegantthemes.com/blog/wp-content/uploads/2020/09/cname-example-1024x305.jpg)

#### Use-cases

- To direct people to the main website from many websites owned by the same individual or organization.
- To assign a unique hostname to each network service, such as File Transfer Protocol (FTP) or email, and point it to the root domain.
- To assign a `subdomain` to each customer on the domain of a single service provider and use `CNAME` to point the `subdomain` to the customer's `root domain`.
- To register the same domain in many countries and direct each country's version to the main domain.

#### Restrictions

- A `CNAME` record should always link to another domain name rather than an IP address.
- A `CNAME` record cannot exist alongside another record with the same name. It is not feasible for `www.example.com` to have both a 'CNAME' and a 'TXT' record.
- A `CNAME` can point to another CNAME. However, this is not normally advised for performance reasons. To prevent needless performance overheads, the `CNAME` should point as nearly as feasible to the destination name when relevant.

## References

- <https://support.dnsimple.com/articles/differences-between-a-cname-alias-url/>
- <https://support.dnsimple.com/categories/dns/>
- <https://www.elegantthemes.com/blog/wordpress/what-is-an-a-record-and-how-is-it-different-from-cname-and-mx>
- <https://www.cloudflare.com/learning/dns/dns-records/#:~:text=What%20is%20a%20DNS%20record,handle%20requests%20for%20that%20domain>.
