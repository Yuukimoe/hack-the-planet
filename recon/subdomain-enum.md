# Subdomain Enum

## DNS Enumeration

```bash
# DNS record/Zone Transfer
python3 dnsrecon.py -d target.com
```

## Passive sources

<pre class="language-bash"><code class="lang-bash"># https://github.com/shmilylty/OneForAll
# https://github.com/tomnomnom/anew
# https://gist.github.com/moeuuki/cb6fbabe868ffab3c84f5886f3957326
python3 oneforall.py --target target.com --path . run
jq -r '.[].subdomain' target.com.json

# https://github.com/projectdiscovery/subfinder
subfinder -d target.com -all -silent
subfinder -dL domains.txt -all -silent

# https://github.com/OWASP/Amass
# https://github.com/OWASP/Amass/blob/master/examples/config.ini
amass enum -d target.com -config ~/.config/amass/config.ini

# https://github.com/tomnomnom/assetfinder
<strong>assetfinder -subs-only target.com
</strong>
# https://github.com/gwen001/github-subdomains
github-subdomains -q -raw -t ~/.config/github-subdomains/github_token.txt -d example.com

# https://github.com/lc/gau
# https://github.com/tomnomnom/unfurl
echo target.com | gau --subs | unfurl -u domains
cat domains.txt | gau --threads 5
</code></pre>

## Active DNS resolution

```bash
# Subdomain Wordlists
https://github.com/danielmiessler/SecLists/blob/master/Discovery/DNS/
https://github.com/fuzzdb-project/fuzzdb/tree/master/discovery/dns
https://github.com/TheKingOfDuck/fuzzDicts/tree/master/subdomainDicts

# Resolvers
# https://public-dns.info/
# https://github.com/vortexau/dnsvalidator
dnsvalidator -tL https://public-dns.info/nameservers.txt -threads 100 -o resolvers.txt

# Resolution
# https://github.com/d3mondev/puredns
# https://github.com/projectdiscovery/dnsx

# BruteForce

```





References

* [https://www.hahwul.com/2020/09/23/amass-go-deep-in-the-sea-with-free-apis/](https://www.hahwul.com/2020/09/23/amass-go-deep-in-the-sea-with-free-apis/)
* [https://blog.projectdiscovery.io/building-one-shot-recon/](https://blog.projectdiscovery.io/building-one-shot-recon/)
* [https://0xpatrik.com/subdomain-enumeration-2019/](https://0xpatrik.com/subdomain-enumeration-2019/)

