# Subdomain Enum

## Passive sources

<pre class="language-bash"><code class="lang-bash"><strong>## Multiple sources
</strong># https://github.com/OWASP/Amass
# https://github.com/OWASP/Amass/blob/master/examples/config.ini
amass enum -config ~/.config/amass/config.ini -d target.com -o subs/amass_subs.txt

# https://github.com/tomnomnom/assetfinder
assetfinder -subs-only target.com | tee subs/assetfinder_subs.txt

# https://github.com/shmilylty/OneForAll
# 修改部分配置 https://gist.github.com/moeuuki/cb6fbabe868ffab3c84f5886f3957326
python3 oneforall.py --target target.com --path subs/oneforall_subs.json run
jq -r '.[].subdomain' oneforall_subs.json > subs/oneforall_subs.txt

# https://github.com/projectdiscovery/subfinder
subfinder -all -silent -d subs/subfinder_subs.com

<strong>## GitHub source
</strong># https://github.com/gwen001/github-subdomains
github-subdomains -q -raw -t ~/.config/github-subdomains/github_token.txt -d target.com | tee subs/github-subdomain_subs.txt

<strong>## Certificate transparency
</strong># https://certificate.transparency.dev/
# https://crt.sh/
# https://github.com/UnaPibaGeek/ctfr
python3 ctfr.py -d domain.com -o subs/ctfr_subs.txt

<strong>## Wayback Machine
</strong># https://github.com/tomnomnom/waybackurls
# https://github.com/tomnomnom/unfurl
echo target.com | waybackurls | unfurl -u domains | tee subs/waybackurls_subs.tx
</code></pre>

## Active DNS resolution

<pre class="language-bash"><code class="lang-bash"><strong>## Generate resolvers lsits
</strong># https://public-dns.info/
# https://github.com/vortexau/dnsvalidator
dnsvalidator -tL https://public-dns.info/nameservers.txt -threads 200 -o lists/resolvers.txt

## or
# https://github.com/teknogeek/fresh.py
python3 fresh.py -o resolvers.txt

<strong>## NOERROR DNS record
</strong># https://github.com/projectdiscovery/dnsx
dnsx -r lists/resolvers.txt -l subs/* -rcode noerror -retry 3 -silent | cut -d' ' -f1 | tee subs/noerror_subs.txt

<strong>## Active DNS record
</strong># https://github.com/d3mondev/puredns
puredns resolve .subs.txt --resolvers lists/resolvers.txt -w subs/resolved_subs.txt
</code></pre>

## Permutation

```bash
# TBD
```

## BruteForce

```bash
## BruteForce
# wordlists
# https://github.com/danielmiessler/SecLists/blob/master/Discovery/DNS/
# https://github.com/fuzzdb-project/fuzzdb/tree/master/discovery/dns
# https://github.com/TheKingOfDuck/fuzzDicts/tree/master/subdomainDicts
```

## Other techniques

```bash
# https://github.com/lc/gau
# https://github.com/tomnomnom/unfurl
gau --subs example.com | unfurl -u domains
```
