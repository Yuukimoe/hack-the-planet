# Subdomain Enum

## Passive

> _所有被动源的子域名枚举操作都建议在网络环境良好的情况下执行_

```bash
## Multiple sources
# https://github.com/OWASP/Amass
amass enum -d target.com -config ~/.config/amass/config.ini
amass enum -df roots.txt -config ~/.config/amass/config.ini

# https://github.com/shmilylty/OneForAll
# 修改部分配置 https://gist.github.com/moeuuki/cb6fbabe868ffab3c84f5886f3957326
python3 ~/Tools/ReconTools/OneForAlloneforall.py --target target.com --fmt json --path ./ run

python3 ~/Tools/ReconTools/OneForAll/oneforall.py --targets roots.txt --fmt json --path ./ run
cat all_subdomain_*.json | jq -r '.[].subdomain' | anew subs.txt | wc -l
# rm all_subdomain_*.txt *.json

# https://github.com/projectdiscovery/subfinder
# subfinder 配置了所有的 API
subfinder -d target.com -all -silent | anew subs.txt | wc -l
subfinder -dL subs.txt -all -silent | anew subs.txt | wc -l

# https://github.com/tomnomnom/assetfinder
# assetfinder 不配置 API 的情况下收集到的信息比较少
assetfinder -subs-only example.com
cat roots.txt| assetfinder -subs-only

# https://github.com/lc/gau
# https://github.com/tomnomnom/unfurl
echo example.com | gau --subs | unfurl -u domains

## GitHub source
# https://github.com/gwen001/github-subdomains
github-subdomains -d target.com -q -raw -t ~/.config/github-subdomains/github_token.txt | anew subs.txt | wc -l

## Certificate transparency
# https://certificate.transparency.dev/
# https://crt.sh/
# https://github.com/UnaPibaGeek/ctfr
python3 ctfr.py -d target.com | unfurl -u domains | anew subs.txt | wc -l

## Wayback Machine
# https://github.com/tomnomnom/waybackurls
# https://github.com/tomnomnom/unfurl
echo target.com | waybackurls | unfurl -u domains | anew subs.txt | wc -l
cat roots.txt | waybackurls | unfurl -u domains
```

## Active

```bash
# Generate resolvers lsits
# https://github.com/vortexau/dnsvalidator
dnsvalidator -tL https://public-dns.info/nameservers.txt -threads 200 -o resolvers.txt

## or
# https://github.com/teknogeek/fresh.py
python3 fresh.py -o resolvers.txt -j 200

# Active DNS record
# https://github.com/d3mondev/puredns
puredns resolve subs.txt -r resolvers.txt -w resolved.txt

# BF
# https://github.com/projectdiscovery/shuffledns
shuffledns -d target.com -r resolvers.txt -w subdict.txt -silent
cat roots.txt | shuffledns -r resolvers.txt -w subdict.txt -silent

```

## Permutation

> 排列组合的操作费时 (又废内存), 在针对特定目标进行渗透测试时可以使用。

```bash
# https://github.com/Josue87/gotator
gotator -sub subs.txt -perm words.txt -depth 1 -numbers 10 -mindup -adv -md -silent

# https://github.com/infosec-au/altdns
altdns -i subs.txt -o out.txt -w words.txt -r -s results_output.txt
```

## DNS/IP

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

