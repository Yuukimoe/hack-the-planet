# Script Kid's Paradise

## URL extraction

<table><thead><tr><th width="207">Name</th><th>Acquisition method</th></tr></thead><tbody><tr><td><a href="https://github.com/lc/gau">gau</a></td><td>Open Threat Exchange, Wayback Machine, Common Crawl, URLScan</td></tr></tbody></table>

## Passive Subdomain Enum

### Multi source

<table><thead><tr><th width="202">Name</th><th>Source</th></tr></thead><tbody><tr><td><a href="https://github.com/owasp-amass/amass">amass</a></td><td>APIs, Certificates, DNS, Routing, Scraping, Web Archives, WHOIS</td></tr><tr><td><a href="https://github.com/tomnomnom/assetfinder">assetfinder</a></td><td>crt.sh, certspotter, hackertarget, threatcrowd, wayback machine, dns.bufferover.run, facebook, virustotal, findsubdomains</td></tr><tr><td><a href="https://github.com/Findomain/Findomain/">Findomain</a></td><td>Certspotter, Crt.sh Database (favorite) or Crt.sh HTTP API, Virustotal, Sublist3r, Facebook, Spyse (CertDB), Bufferover, Threatcrowd, Virustotal with apikey, AnubisDB, Urlscan.io, SecurityTrails, Threatminer, C99, Archive.org, CTSearch</td></tr><tr><td><a href="https://github.com/shmilylty/OneForAll">OneForAll</a></td><td>证书透明度, 常规检查, 爬虫档案, DNS, 威胁情报, 搜索引擎</td></tr><tr><td><a href="https://github.com/projectdiscovery/subfinder">subfinder</a></td><td>BeVigil, BinaryEdge, BufferOver, C99, Censys, CertSpotter, Chaos, Chinaz, DnsDB, Fofa, FullHunt, GitHub, Intelx, PassiveTotal, quake, Robtex, SecurityTrails, Shodan, ThreatBook, VirusTotal, WhoisXML API, ZoomEye, ZoomEye API, dnsrepo, Hunter</td></tr></tbody></table>

### Single source

| Name                                                              | Description                                                                  |
| ----------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| [github-subdomains](https://github.com/gwen001/github-subdomains) | Find subdomains on GitHub.                                                   |
| [ctfr](https://github.com/UnaPibaGeek/ctfr)                       | Abusing Certificate Transparency logs for getting HTTPS websites subdomains. |
| [waybackurls](https://github.com/tomnomnom/waybackurls)           | Fetch all the URLs that the Wayback Machine knows about for a domain         |

### Permutations

* [dnsgen](https://github.com/ProjectAnte/dnsgen) 通过给定的域生成排列
* [goaltdns](https://github.com/subfinder/goaltdns) 通过给定的域生成排列
  * 您可以在[此处](https://github.com/subfinder/goaltdns/blob/master/words.txt)获取 goaltdns 排列词表
* [gotator](https://github.com/Josue87/gotator) 给定域和子域生成排列。如果没有指定排列文件，gotator 将使用它自己的排列文件
* [altdns](https://github.com/infosec-au/altdns) 除了生成子域排列外，它还可以尝试解析它们（但最好使用其他工具）。
  * 您可以在[此处](https://github.com/infosec-au/altdns/blob/master/words.txt)获取 altdns 排列词表。
* [dmut](https://github.com/bp0lr/dmut) 另一种执行子域排列、改变和更改的工具。此工具将暴力破解结果（它不支持 dns 通配符）
  * 您可以在此处获取 [dmut](https://raw.githubusercontent.com/bp0lr/dmut/main/words.txt) 排列词列表
* [alterx](https://github.com/projectdiscovery/alterx) 基于域, 它会根据指示的模式生成新的潜在子域名, 以尝试发现更多子域

## **DNS Resolve/Brute**

<table><thead><tr><th width="205">Name</th><th>Description</th></tr></thead><tbody><tr><td><a href="https://github.com/blechschmidt/massdns">massdns</a></td><td>用于批量查找和侦察 (子域枚举) 的高性能 DNS stub 解析器</td></tr><tr><td><a href="https://github.com/d3mondev/puredns/">puredns</a></td><td>基于 massdns 的域名爆破和解析工具</td></tr><tr><td><a href="https://github.com/projectdiscovery/shuffledns">shuffledns</a></td><td>基于 massdns 的子域暴力破解工具</td></tr><tr><td><a href="https://github.com/projectdiscovery/dnsx">dnsx</a></td><td>快速的、多功能的 DNS 工具包</td></tr></tbody></table>

## Web 服务发现

<table><thead><tr><th width="203">Name</th><th>Description</th></tr></thead><tbody><tr><td><a href="https://github.com/projectdiscovery/httpx">httpx</a></td><td>快速的、多功能的 HTTP 工具包</td></tr><tr><td><a href="https://github.com/tomnomnom/httprobe">httprobe</a></td><td>通过域名列表探测 HTTP 或 HTTPS 服务</td></tr><tr><td><a href="https://github.com/theblackturtle/fprobe">fprobe</a></td><td>获取域/子域的列表并探测的 HTTP/HTTPS 服务器</td></tr></tbody></table>

## Port Scan

* [https://github.com/projectdiscovery/naabu](https://github.com/projectdiscovery/naabu) 可以对域名进行端口扫描
* [https://github.com/RustScan/RustScan](https://github.com/RustScan/RustScan) 支持 IP, Host, CIDR, File

## **Wordlists**

```bash
# Subdomain Wordlists
https://github.com/danielmiessler/SecLists/blob/master/Discovery/DNS/
https://github.com/fuzzdb-project/fuzzdb/tree/master/discovery/dns
https://github.com/TheKingOfDuck/fuzzDicts/tree/master/subdomainDicts
https://wordlists-cdn.assetnote.io/data/manual/best-dns-wordlist.txt
https://localdomain.pw/subdomain-bruteforce-list/all.txt.zip
```

## Screenshot

* [https://github.com/sensepost/gowitness](https://github.com/sensepost/gowitness) 2.2k
* [https://github.com/FortyNorthSecurity/EyeWitness](https://github.com/FortyNorthSecurity/EyeWitness) 4.2k
* [https://github.com/breenmachine/httpscreenshot](https://github.com/breenmachine/httpscreenshot) 602
* [https://github.com/michenriksen/aquatone](https://github.com/michenriksen/aquatone) 5.2k Archived
* [https://github.com/maaaaz/webscreenshot](https://github.com/maaaaz/webscreenshot) 623
* [https://github.com/BishopFox/eyeballer](https://github.com/BishopFox/eyeballer) AI analyzing screenshot
* [https://shutter-project.org/](https://shutter-project.org/)

## 集成/自动化框架

<table><thead><tr><th width="202">Name</th><th>Description</th></tr></thead><tbody><tr><td><a href="https://github.com/yogeshojha/rengine">rengine</a></td><td>支持自定义扫描工具配置文件、Web 截屏、Nuclei POC 扫描、导入导出数据、CMS、To-do 等功能。</td></tr><tr><td><a href="https://github.com/pry0cc/axiom">axiom</a></td><td>Axiom dynamic infrastructure framework。可以为不同的工具分配不同的工作负载 (即工作量), 例如 ffu、masscan。</td></tr><tr><td><a href="https://github.com/TophantTechnology/ARL/">ARL</a></td><td>ARL 图形化侦查框架</td></tr><tr><td><a href="https://github.com/remonsec/SEF">SEF</a></td><td>SEF 子域枚举框架，涵盖被动、主动和置换枚举</td></tr></tbody></table>
