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
dnsvalidator -tL https://public-dns.info/nameservers.txt -threads 200 -o subs/.resolvers.txt

<strong>## Active DNS record
</strong># https://github.com/d3mondev/puredns
puredns resolve .subs.txt --resolvers .resolvers.txt -w subs/.resolved_subs.txt

<strong>## NOERROR DNS record
</strong># https://github.com/projectdiscovery/dnsx
dnsx -r .resolvers.txt -l subs/* -rcode noerror -retry 3 -silent | cut -d' ' -f1 | tee subs/.noerror_subs.txt

<strong>## Permutation
</strong>TBD

<strong>## BruteForce
</strong>TBD
</code></pre>

## Web Server resolution

<pre class="language-bash"><code class="lang-bash"><strong>## Active Web resolution (5486 subdomains cost about 11 minutes)
</strong># https://github.com/tomnomnom/httprobe
cat subs/.subs.txt | httprobe -c 50 -p 8080,8081,8089 | tee webs/httprobe_webs.txt

<strong>## Basic information Identify (7156 url cost about 6 minutes)
</strong># https://github.com/projectdiscovery/httpx
cat webs/httprobe_webs.txt | httpx -sc -fr -title -web-server -tech-detect -location \
-json -o webs/httpx_webs.json

<strong>## 根据 200 状态码筛选 URL
</strong>cat webs/httpx_webs.json | jq -r '. | select(.status_code==200) | .url' > webs/200.txt

<strong>## Basic information &#x26; Screenshot (Not recommended)
</strong>cat webs/httprobe_webs.txt | httpx -sc -fr -title -web-server -tech-detect -location \
-json -o webs/httpx/httpx_webs.json -screenshot -srd webs/httpx_webs/
</code></pre>

## Screenshot

```bash
# https://github.com/sensepost/gowitness/
gowitness 
```

