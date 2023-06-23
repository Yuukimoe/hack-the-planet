# Webs Recon

```bash
# Web 服务常用端口
80,81,300,443,591,593,832,981,1010,1311,1099,2082,2095,2096,2480,3000,3128,3333,4243,4567,4711,4712,4993,5000,5104,5108,5280,5281,5800,6543,7000,7396,7474,8000,8001,8008,8014,8042,8069,8080,8081,8083,8088,8090,8091,8118,8123,8172,8222,8243,8280,8281,8333,8337,8443,8500,8834,8880,8888,8983,9000,9043,9060,9080,9090,9091,9200,9443,9800,9981,10000,11371,12443,16080,18091,18092,20720,55672
```

## Resolution

```bash
# Top 3000 ports (非常非常非常非常非常非常的慢)
# https://github.com/projectdiscovery/dnsx
# https://github.com/projectdiscovery/httpx
# https://github.com/pry0cc/tew
dnsx -l resolved.txt -json -o dns.json | jq -r '.a?[]?'
nmap -T4 -vv -iL ips.txt --top-ports 3000 -n --open -oX nmap.xml
tew -x nmap.xml -dnsx dns.json —vhost | httpx -json -o http.json


# Gerneral
cat resolved.txt | httpx -fr -random-agent -sc -silent -retries 2 -title -web-server -tech-detect -location -no-color -json -o webs.json


# Top 1000 ports
# https://github.com/projectdiscovery/naabu
# https://github.com/projectdiscovery/httpx
# naabu ... 75.32s user 204.73s system 11% cpu 42:19.95 total (316 domains)
# httpx ... 6.55s user 2.40s system 0% cpu 43:19.48 total (316 domains)
cat resolved.txt | naabu -top-ports 1000 -silent \
| httpx -fr -retries 3 -json -o webs.json

# Filter URL (with status_code)
cat webs.json | jq -r '.url' | anew webs.txt
cat webs.json | jq -r '. | select(.status_code==200) | .url' | anew 200.txt
cat webs.json | jq -r '. | select(.status_code==403) | .url' | anew 403.txt
cat webs.json | jq -r '. | select(.status_code==404) | .url' | anew 404.txt

# jq usage
# a[] 数组中包含 1.1 的结果和 a[] 数组中存在 2.2.2.2 的结果
jq -r '. | select(.a[] | contains("1.1") or . == "2.2.2.2")'
cat webs.json | jq -r '. | select(.a[] | contains("8.8.8.") or . == "1.1.1.1")'
```

## CMS

```bash
# https://github.com/EdgeSecurityTeam/EHole
Ehole finger -l resolved.txt -o Ehole.xlsx

# https://github.com/Goqi/Banli

# https://github.com/Tuhinshubhra/CMSeeK

# https://github.com/TideSec/TideFinger

# https://github.com/0x727/ObserverWard_0x727

# https://github.com/urbanadventurer/WhatWeb

# https://github.com/zhzyker/dismap

# Online webtsites
http://www.yunsee.cn
```

## Scanning

```bash
# https://github.com/zan8in/afrog
# https://github.com/projectdiscovery/nuclei
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

## JavaScript

```bash
# JavaScript
https://github.com/rtcatc/Packer-Fuzzer
https://github.com/pingc0y/URLFinder
https://github.com/Threezh1/JSFinder

# Webpack and SourceMap
https://github.com/davidkevork/reverse-sourcemap
https://github.com/SunHuawei/SourceDetector
https://github.com/Lz1y/SourceDetector-dist

# 

```
