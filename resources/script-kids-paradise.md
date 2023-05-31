# Script Kid's Paradise

## URL extraction

<table><thead><tr><th width="207">Name</th><th>Acquisition method</th></tr></thead><tbody><tr><td><a href="https://github.com/lc/gau">gau</a></td><td>Open Threat Exchange, Wayback Machine, Common Crawl, URLScan</td></tr></tbody></table>

## Subdomain Enum

### Multiple Sources

<table><thead><tr><th width="202">Name</th><th>Source</th></tr></thead><tbody><tr><td><a href="https://github.com/owasp-amass/amass">amass</a></td><td>APIs, Certificates, DNS, Routing, Scraping, Web Archives, WHOIS</td></tr><tr><td><a href="https://github.com/tomnomnom/assetfinder">assetfinder</a></td><td>crt.sh, certspotter, hackertarget, threatcrowd, wayback machine, dns.bufferover.run, facebook, virustotal, findsubdomains</td></tr><tr><td><a href="https://github.com/Findomain/Findomain/">Findomain</a></td><td>Certspotter, Crt.sh Database (favorite) or Crt.sh HTTP API, Virustotal, Sublist3r, Facebook, Spyse (CertDB), Bufferover, Threatcrowd, Virustotal with apikey, AnubisDB, Urlscan.io, SecurityTrails, Threatminer, C99, Archive.org, CTSearch</td></tr><tr><td><a href="https://github.com/shmilylty/OneForAll">OneForAll</a></td><td>证书透明度, 常规检查, 爬虫档案, DNS, 威胁情报, 搜索引擎</td></tr><tr><td><a href="https://github.com/projectdiscovery/subfinder">subfinder</a></td><td>BeVigil, BinaryEdge, BufferOver, C99, Censys, CertSpotter, Chaos, Chinaz, DnsDB, Fofa, FullHunt, GitHub, Intelx, PassiveTotal, quake, Robtex, SecurityTrails, Shodan, ThreatBook, VirusTotal, WhoisXML API, ZoomEye, ZoomEye API, dnsrepo, Hunter</td></tr></tbody></table>



### Single Sources

<table><thead><tr><th width="203">Name</th><th>Description</th></tr></thead><tbody><tr><td><a href="https://github.com/gwen001/github-subdomains">github-subdomains</a></td><td>Find subdomains on GitHub.</td></tr><tr><td><a href="https://github.com/UnaPibaGeek/ctfr">ctfr</a></td><td>Abusing Certificate Transparency logs for getting HTTPS websites subdomains.</td></tr><tr><td><a href="https://github.com/tomnomnom/waybackurls">waybackurls</a></td><td>Fetch all the URLs that the Wayback Machine knows about for a domain</td></tr></tbody></table>

## **DNS** resolution

<table><thead><tr><th width="205">Name</th><th>Description</th></tr></thead><tbody><tr><td><a href="https://github.com/blechschmidt/massdns">massdns</a></td><td>用于批量查找和侦察 (子域枚举) 的高性能 DNS stub 解析器</td></tr><tr><td><a href="https://github.com/d3mondev/puredns/">puredns</a></td><td>基于 massdns 的域名爆破和解析工具</td></tr><tr><td><a href="https://github.com/projectdiscovery/shuffledns">shuffledns</a></td><td>基于 massdns 的子域暴力破解工具</td></tr><tr><td><a href="https://github.com/projectdiscovery/dnsx">dnsx</a></td><td>快速的、多功能的 DNS 工具包</td></tr></tbody></table>

## Server Discovery

### Web Server

<table><thead><tr><th width="203">Name</th><th>Description</th></tr></thead><tbody><tr><td><a href="https://github.com/projectdiscovery/httpx">httpx</a></td><td>快速的、多功能的 HTTP 工具包</td></tr><tr><td><a href="https://github.com/tomnomnom/httprobe">httprobe</a></td><td>通过域名列表探测 HTTP 或 HTTPS 服务</td></tr><tr><td><a href="https://github.com/theblackturtle/fprobe">fprobe</a></td><td>获取域/子域的列表并探测的 HTTP/HTTPS 服务器</td></tr></tbody></table>

## **Wordlists**

```bash
# Subdomain Wordlists
https://github.com/danielmiessler/SecLists/blob/master/Discovery/DNS/
https://github.com/fuzzdb-project/fuzzdb/tree/master/discovery/dns
https://github.com/TheKingOfDuck/fuzzDicts/tree/master/subdomainDicts
```

## **Integrated Framework**

<table><thead><tr><th width="202">Name</th><th>Description</th></tr></thead><tbody><tr><td><a href="https://github.com/yogeshojha/rengine">rengine</a></td><td>支持自定义扫描工具配置文件、Web 截屏、Nuclei POC 扫描、导入导出数据、CMS、To-do 等功能。</td></tr><tr><td><a href="https://github.com/pry0cc/axiom">axiom</a></td><td>Axiom dynamic infrastructure framework。可以为不同的工具分配不同的工作负载 (即工作量), 例如 ffu、masscan。</td></tr><tr><td><a href="https://github.com/TophantTechnology/ARL/">ARL</a></td><td>ARL 图形化侦查框架</td></tr><tr><td><a href="https://github.com/remonsec/SEF">SEF</a></td><td>SEF 子域枚举框架，涵盖被动、主动和置换枚举</td></tr></tbody></table>
