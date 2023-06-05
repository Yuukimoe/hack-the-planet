# Web Server resolution

## Purer Record

在使用工具枚举了大量的域名和子域名后, 通常会出现一些指向相同 IP 地址的不同域名, 如果正在进行手动测试, 可以通过建立 **IP 地址和域名的映射表,** 筛选重复项, 来缩小测试范围。

```bash
# https://github.com/projectdiscovery/dnsx
dnsx -l subs/subs.txt -r lists/resolvers.txt -resp -a -json | tee webs-2/dnsx.json
```

## Active Web Server resolution

```bash
# Web 服务常用端口
80,81,300,443,591,593,832,981,1010,1311,1099,2082,2095,2096,2480,3000,3128,3333,4243,4567,4711,4712,4993,5000,5104,5108,5280,5281,5800,6543,7000,7396,7474,8000,8001,8008,8014,8042,8069,8080,8081,8083,8088,8090,8091,8118,8123,8172,8222,8243,8280,8281,8333,8337,8443,8500,8834,8880,8888,8983,9000,9043,9060,9080,9090,9091,9200,9443,9800,9981,10000,11371,12443,16080,18091,18092,20720,55672
```

<pre class="language-bash"><code class="lang-bash"><strong>## Active Web resolution (5486 subdomains cost about 11 minutes)
</strong># https://github.com/tomnomnom/httprobe
cat subs/subs.txt | httprobe -c 50 -p 8080,8081,8089 | tee webs/httprobe_webs.txt

<strong>## Basic information Identify (7156 url cost about 6 minutes)
</strong># https://github.com/projectdiscovery/httpx
cat webs/httprobe_webs.txt | httpx -sc -fr -title -web-server -tech-detect -location \
-json -o webs/httpx_webs.json

<strong>## Filter URL with status_code=200
</strong>cat webs/httpx_webs.json | jq -r '. | select(.status_code==200) | .url' > webs/200.txt
cat webs/httpx_webs.json | jq -r '. | select(.status_code==403) | .url' > webs/403.txt
cat webs/httpx_webs.json | jq -r '. | select(.status_code==404) | .url' > webs/404.txt

<strong>## Basic information &#x26; Screenshot (Not recommended)
</strong>cat webs/httprobe_webs.txt | httpx -sc -fr -title -web-server -tech-detect -location \
-json -o webs/httpx/httpx_webs.json -screenshot -srd webs/httpx_webs/
</code></pre>

## Screenshot

```bash
# https://github.com/sensepost/gowitness/
# https://github.com/sensepost/gowitness/wiki/Usage
gowitness file -f 200.txt
gowitness server --address 127.0.0.1:9000
```

