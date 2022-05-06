I Discuss here How You Can Get a List Of CIDRs For Comapny.

# Using Online Service
You can use this website https://bgp.he.net/
Add company name in search box and list of CIDRs and ASNs will appear.


# From Subdomains

```cat subdomains.txt | dnsx -a -resp-only -silent | sort -u | cut -d "." -f 1,2,3 | uniq -c | grep -v "[123] \.*"```

