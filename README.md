# Get CIDR from subdomains
```cat subdomains.txt | dnsx -a -resp-only -silent | sort -u | cut -d "." -f 1,2,3 | uniq -c | grep -v "[123] \.*"```

# Brute-Force for virtual hosts
```ffuf -w urls:URL -w hosts:HOST -u URL -H "Host: HOST" -ac -c -of csv  -o vhost.csv```
