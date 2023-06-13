# Subdomain Enum

## Passive

> _所有被动源的子域名枚举操作都建议在网络环境良好的情况下执行_

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

## Active

```bash
# Generate resolvers lsits
# https://github.com/vortexau/dnsvalidator
dnsvalidator -tL https://public-dns.info/nameservers.txt -threads 200 -o lists/resolvers.txt

## or
# https://github.com/teknogeek/fresh.py
python3 ~/tools/recon-tools/fresh.py/fresh.py --clean ~/tools/recon-tools/fresh.py/clean_regex.txt -o lists/resolvers.txt -j 200

# BF
# https://github.com/projectdiscovery/shuffledns
shuffledns -d target.com -r lists/resolvers.txt -w lists/subdict.txt -silent | anew subs.txt | wc -l
shuffledns -l roots.txt -r lists/resolvers.txt -w lists/subdict.txt -silent | anew subs.txt | wc -l

# Active DNS record
# https://github.com/d3mondev/puredns
puredns resolve subs.txt -r lists/resolvers.txt -w resolved.txt | wc -l
```

## Permutation

> 排列组合的操作费时 (又废内存), 在针对特定目标进行渗透测试时可以使用。

```bash
# https://github.com/Josue87/gotator
gotator -sub subs.txt -perm words.txt -depth 1 -numbers 10 -mindup -adv -md -silent

# https://github.com/infosec-au/altdns
altdns -i subs.txt -o out.txt -w words.txt -r -s results_output.txt
```

## DNS records

```bash
# https://github.com/projectdiscovery/dnsx
dnsx -l resolved.txt -json -o dns.json | wc -l

# get A record + IPs
cat dnsx.json | jq -r '.a?[]?' | anew ips.txt
```

## Wordlists

```bash
# General
https://github.com/danielmiessler/SecLists/blob/master/Discovery/DNS/subdomains-top1million-110000.txt
https://github.com/TophantTechnology/ARL/blob/master/app/dicts/domain_2w.txt

# Permutation
https://github.com/infosec-au/altdns/blob/master/words.txt
https://github.com/TophantTechnology/ARL/blob/master/app/dicts/altdnsdict.txt
https://github.com/moeuuki/Furry/tree/main/subdomain

# Deepth + Test Env + Intra Env
https://github.com/joinsec/BadDNS/blob/master/depthdict.txt
https://github.com/moeuuki/Furry/tree/main/subdomain
```

## Other techniques

```bash
# https://github.com/lc/gau
# https://github.com/tomnomnom/unfurl
gau --subs example.com | unfurl -u domains
```

