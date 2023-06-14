# Webs Recon

```bash
# Web 服务常用端口
80,81,300,443,591,593,832,981,1010,1311,1099,2082,2095,2096,2480,3000,3128,3333,4243,4567,4711,4712,4993,5000,5104,5108,5280,5281,5800,6543,7000,7396,7474,8000,8001,8008,8014,8042,8069,8080,8081,8083,8088,8090,8091,8118,8123,8172,8222,8243,8280,8281,8333,8337,8443,8500,8834,8880,8888,8983,9000,9043,9060,9080,9090,9091,9200,9443,9800,9981,10000,11371,12443,16080,18091,18092,20720,55672
```

## Web Host Discovery

### PLAN 1 - nmap -> Services

扫描 nmap top 3000 端口, 但是速度慢

<pre class="language-bash"><code class="lang-bash"><strong># Get DNS records &#x26; IPs
</strong># https://github.com/projectdiscovery/dnsx
dnsx -l resolved.txt -json -o dns.json | jq -r '.a?[]?' | anew ips.txt | wc -l

<strong># Port Scan
</strong># https://github.com/nmap/nmap (316 ips ran about ***)
nmap -T4 -vv -iL ips.txt --top-ports 3000 -n --open -oX nmap.xml

<strong># Service Discovery
</strong># https://github.com/pry0cc/tew
# https://github.com/projectdiscovery/httpx
tew -x nmap.xml -dnsx dns.json —vhost | httpx -json -o http.json
</code></pre>

### PLAN 2 - httprobe ->  Services

httpx 和 httprobe 仅扫描 Web 服务器默认端口, 速度快, 但精度低

```bash
# https://github.com/tomnomnom/httprobe
# https://github.com/projectdiscovery/httpx
cat resolved.txt | httprobe -c 200 | tee httprobe.txt
cat resolved.txt | httpx -sc -fr -title -web-server -tech-detect -location -json -o httpx.json
cat httprobe.txt | anew webs.txt | wc -l
cat httpx.json | jq -r '.url' | anew webs.txt | wc -l

# Filter URL with status_code
cat httpx.json | jq -r '. | select(.status_code==200) | .url' > 200.txt
cat httpx.json | jq -r '. | select(.status_code==403) | .url' > 403.txt
cat httpx.json | jq -r '. | select(.status_code==404) | .url' > 404.txt
```

### PLAN 3 - naabu ->  Services

扫描 nmap 前 1000 个端口, httpx 与 naabu 一起使用

```bash
# https://github.com/projectdiscovery/naabu
# https://github.com/projectdiscovery/httpx
# cat resolved.txt | wc -l --- 316
# naabu ... 75.32s user 204.73s system 11% cpu 42:19.95 total
# httpx ... 6.55s user 2.40s system 0% cpu 43:19.48 total
naabu -list resolved.txt -top-ports 1000 -silent \
| httpx -sc -fr -title -web-server -tech-detect -location -json -o webs.json

# Filter URL with status_code
cat webs.json | jq -r '. | select(.status_code==200) | .url' > 200.txt
cat webs.json | jq -r '. | select(.status_code==403) | .url' > 403.txt
cat webs.json | jq -r '. | select(.status_code==404) | .url' > 404.txt
```

## Screenshot

```bash
# https://github.com/sensepost/gowitness/
# https://github.com/sensepost/gowitness/wiki/Usage
gowitness file -f 200.txt
gowitness server --address 127.0.0.1:9000


# Basic information & Screenshot (Not recommended)
cat webs/httprobe_webs.txt | httpx -sc -fr -title -web-server -tech-detect -location \
-json -o webs/httpx/httpx_webs.json -screenshot -srd webs/httpx_webs/
```

## Fingerprint

```bash
# https://github.com/urbanadventurer/WhatWeb

# https://github.com/zan8in/afrog

# https://github.com/EdgeSecurityTeam/EHole


```

