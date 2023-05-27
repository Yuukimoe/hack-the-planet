# Subdomain Enum

## Passive sources

### Multiple sources

```bash
# https://github.com/OWASP/Amass
# https://github.com/OWASP/Amass/blob/master/examples/config.ini
amass enum -config ~/.config/amass/config.ini -d target.com -o subs/amass_subs.txt

# https://github.com/tomnomnom/assetfinder
assetfinder -subs-only target.com > subs/assetfinder_subs.txt

# https://github.com/shmilylty/OneForAll
# 修改部分配置 https://gist.github.com/moeuuki/cb6fbabe868ffab3c84f5886f3957326
python3 oneforall.py --target target.com --path subs/oneforall_subs.json run
jq -r '.[].subdomain' oneforall_subs.json > subs/oneforall_subs.txt

# https://github.com/projectdiscovery/subfinder
subfinder -all -silent -d subs/subfinder_subs.com
```

### GitHub source

```bash
# https://github.com/gwen001/github-subdomains
github-subdomains -q -raw -t ~/.config/github-subdomains/github_token.txt -d target.com > subs/github-subdomain_subs.txt
```

### Certificate transparency

```bash
# https://certificate.transparency.dev/
# https://crt.sh/
# https://github.com/UnaPibaGeek/ctfr
python3 ctfr.py -d domain.com -o subs/ctfr_subs.txt
```

### Wayback Machine

```bash
# https://github.com/tomnomnom/waybackurls
# https://github.com/tomnomnom/unfurl
echo target.com | waybackurls | unfurl -u domains > subs/waybackurls_subs.tx
```

## Active DNS resolution

```bash
## Generate resolvers lsits
# https://public-dns.info/
# https://github.com/vortexau/dnsvalidator
dnsvalidator -tL https://public-dns.info/nameservers.txt -threads 200 -o subs/.resolvers.txt

```

### Active DNS record

```bash
# https://github.com/d3mondev/puredns
puredns resolve .subs.txt --resolvers .resolvers.txt -w subs/.resolved_subs.txt
```

### NOERROR DNS record

```bash
# https://github.com/projectdiscovery/dnsx
dnsx -r .resolvers.txt -l subs/* -rcode noerror -retry 3 -silent | cut -d' ' -f1 > subs/.noerror_subs.txt
```

## Summary

```bash
tree -a
.
└── subs
    ├── .noerror_subs.txt
    ├── .resolved_subs.txt
    ├── .resolvers.txt
    ├── amass_subs.txt
    ├── assetfinder_subs.txt
    ├── ctfr_subs.txt
    ├── github-subdomain_subs.txt
    ├── oneforall_subs.txt
    ├── subfinder_subs.txt
    ├── subs.txt
    └── waybackurls_subs.txt

2 directories, 11 files
```



References

* [https://www.hahwul.com/2020/09/23/amass-go-deep-in-the-sea-with-free-apis/](https://www.hahwul.com/2020/09/23/amass-go-deep-in-the-sea-with-free-apis/)
* [https://blog.projectdiscovery.io/building-one-shot-recon/](https://blog.projectdiscovery.io/building-one-shot-recon/)
* [https://0xpatrik.com/subdomain-enumeration-2019/](https://0xpatrik.com/subdomain-enumeration-2019/)

