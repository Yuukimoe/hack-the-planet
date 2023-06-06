# Subdomain Enum

## Passive sources

{% hint style="info" %}
<mark style="color:orange;">**所有被动源的子域名枚举操作都建议在网络环境良好的情况下执行**</mark>
{% endhint %}

<pre class="language-bash"><code class="lang-bash"><strong># Multiple sources
</strong># https://github.com/OWASP/Amass
amass enum -config ~/.config/amass/config.ini -d target.com | anew subs.txt | wc -l

# https://github.com/tomnomnom/assetfinder
# assetfinder 不配置 API 的情况下收集到的信息比较少
assetfinder -subs-only target.com | anew subs.txt | wc -l

# https://github.com/shmilylty/OneForAll
# 修改部分配置 https://gist.github.com/moeuuki/cb6fbabe868ffab3c84f5886f3957326
python3 ~/tools/recon-tools/OneForAll/oneforall.py --target target.com --path subs.json run
jq -r '.[].subdomain' subs.json | anew subs.txt | wc -l; rm subs.json

# https://github.com/projectdiscovery/subfinder
# subfinder 配置了所有的 API
subfinder -all -silent -d target.com | anew subs.txt | wc -l

<strong># GitHub source
</strong># https://github.com/gwen001/github-subdomains
github-subdomains -q -raw -t ~/.config/github-subdomains/github_token.txt -d target.com | anew subs.txt | wc -l

<strong># Certificate transparency
</strong># https://certificate.transparency.dev/
# https://crt.sh/
# https://github.com/UnaPibaGeek/ctfr
python3 ~/tools/recon-tools/ctfr/ctfr.py -d target.com | unfurl -u domains | anew subs.txt | wc -l

<strong># Wayback Machine
</strong># https://github.com/tomnomnom/waybackurls
# https://github.com/tomnomnom/unfurl
echo target.com | waybackurls | unfurl -u domains | anew subs.txt | wc -l
</code></pre>

## BruteForce

<pre class="language-bash"><code class="lang-bash"><strong># Subdomain wordlists
</strong># https://github.com/danielmiessler/SecLists/blob/master/Discovery/DNS/subdomains-top1million-110000.txt
# https://github.com/TophantTechnology/ARL/blob/master/app/dicts/domain_2w.txt
curl https://raw.githubusercontent.com/danielmiessler/SecLists/master/Discovery/DNS/subdomains-top1million-110000.txt https://raw.githubusercontent.com/TophantTechnology/ARL/master/app/dicts/domain_2w.txt | anew lists/subdict.txt | wc -l

<strong># Generate resolvers lsits
</strong># https://github.com/vortexau/dnsvalidator
dnsvalidator -tL https://public-dns.info/nameservers.txt -threads 200 -o lists/resolvers.txt

## or
# https://github.com/teknogeek/fresh.py
python3 ~/tools/recon-tools/fresh.py/fresh.py --clean ~/tools/recon-tools/fresh.py/clean_regex.txt -o lists/resolvers.txt -j 200

<strong># Brute-Force
</strong># https://github.com/projectdiscovery/shuffledns
shuffledns -d target.com -r lists/resolvers.txt -w lists/subdict.txt -silent | anew subs.txt | wc -l

<strong>## Active DNS record
</strong># https://github.com/d3mondev/puredns
puredns resolve subs.txt --resolvers lists/resolvers.txt -w subs/resolved.txt
</code></pre>

## Permutation

```bash
## wordlists
# https://github.com/infosec-au/altdns/blob/master/words.txt
# https://github.com/TophantTechnology/ARL/blob/master/app/dicts/altdnsdict.txt
curl https://raw.githubusercontent.com/infosec-au/altdns/master/words.txt | anew altdnsdict.txt
curl https://raw.githubusercontent.com/TophantTechnology/ARL/master/app/dicts/altdnsdict.txt | anew altdnsdict.txt

# https://github.com/Josue87/gotator
gotator -sub subdomains/subdomains.txt -perm permutations_list.txt -depth 1 -numbers 10 -mindup -adv -md
```

## Other techniques

```bash
# https://github.com/lc/gau
# https://github.com/tomnomnom/unfurl
gau --subs example.com | unfurl -u domains
```

