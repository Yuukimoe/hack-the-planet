# Script Kiddie

**Subdomain Enum**

```bash
# https://github.com/Findomain/Findomain/
# 快速的生成大量子域列表, 同时包括屏幕截图、端口扫描、HTTP 检查等功能
findomain -t target.com -q

# https://github.com/tomnomnom/waybackurls
# https://github.com/tomnomnom/unfurl
# 获取所有 waybackuls 中包含的 url, 并过滤出子域
echo target.com | waybackurls | unfurl -u domains
cat domains.txt | waybackurls | unfurl -u domains

# https://github.com/lc/gau
# https://github.com/tomnomnom/unfurl
# 包括从 Open Threat Exchange、Wayback Machine、Common Crawl 和 URLScan 获取已知的 URL
echo target.com | gau --subs | unfurl -u domains
cat domains.txt | gau --threads 5
```

**DNS Resolve**

```bash
# https://github.com/blechschmidt/massdns

# https://github.com/projectdiscovery/shuffledns
```

**Wordlists**

```bash
# Subdomain Wordlists
https://github.com/danielmiessler/SecLists/blob/master/Discovery/DNS/
https://github.com/fuzzdb-project/fuzzdb/tree/master/discovery/dns
https://github.com/TheKingOfDuck/fuzzDicts/tree/master/subdomainDicts
```

**Integrated Framework**

```bash
# https://github.com/yogeshojha/rengine
# 支持自定义扫描工具配置文件、Web 截屏、Nuclei POC 扫描、导入导出数据、CMS、To-do 等功能。

# https://github.com/pry0cc/axiom
# Axiom dynamic infrastructure framework。可以为不同的工具分配不同的工作负载 (即工作量), 例如 ffu、masscan。

# https://github.com/TophantTechnology/ARL/
# ARL 图形化侦查框架

# https://github.com/remonsec/SEF
# SEF 子域枚举框架，涵盖被动、主动和置换枚举
```
