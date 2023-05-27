# Script Kiddie

**Subdomain Enum**

```bash
# Findomain 快速的生成大量子域列表, 同时包括屏幕截图、端口扫描、HTTP 检查等功能
# https://github.com/Findomain/Findomain/
findomain -t target.com -q

# waybackurls 获取所有 waybackuls 中包含的 url, 并过滤出子域
# https://github.com/tomnomnom/waybackurls
# https://github.com/tomnomnom/unfurl
echo target.com | waybackurls | unfurl -u domains
cat domains.txt | waybackurls | unfurl -u domains
```

**Integrated Framework**

```bash
# reNgine 支持自定义扫描工具配置文件、Web 截屏、Nuclei POC 扫描、导入导出数据、CMS、To-do 等功能。
# https://github.com/yogeshojha/rengine

# Axiom dynamic infrastructure framework。可以为不同的工具分配不同的工作负载 (即工作量), 例如 ffu、masscan。
# https://github.com/pry0cc/axiom

# ARL 图形化侦查框架
# https://github.com/TophantTechnology/ARL/

# SEF 子域枚举框架，涵盖被动、主动和置换枚举
# https://github.com/remonsec/SEF
```
