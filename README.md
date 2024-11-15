## Get CIDR from subdomains
```cat subdomains.txt | dnsx -a -resp-only -silent | sort -u | cut -d "." -f 1,2,3 | uniq -c | grep -v "[123] \.*"```

## Brute-Force for virtual hosts
```ffuf -w urls:URL -w hosts:HOST -u URL -H "Host: HOST" -ac -c -of csv  -o vhost.csv```

## Content Discovery
1- ```ffuf -w urls.txt:URL -w fuzz.txt:FUZZ -u URL/FUZZ -ac -c -of json -o fuzz.json```

Output : url     status        length

2- ```cat fuzz.json | jq -r '.results[].url +" "+ (.results[].status|tostring) + " " + (.results[].length|tostring)```

## BruteForce Basic Auth
Add this function to your ~/.profile
```
generate_basicauth () {
    for user in `cat $1`; do for pass in `cat $2`; do echo -n "$user:$pass"| base64 ; done; done
}
```

Use ffuf
```
generate_basicauth users.txt passes.txt https://target.com/protected
```
