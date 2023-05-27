# Script Kiddie

**Subdomain Enum**

```
# https://github.com/Findomain/Findomain/
# 快速的生成大量子域列表, 同时包括屏幕截图、端口扫描、HTTP 检查等功能
findomain -t target.com -q

# https://github.com/tomnomnom/waybackurls
# https://github.com/tomnomnom/unfurl
# 获取所有 waybackuls 中包含的 url, 并过滤出子域
echo target.com | waybackurls | unfurl -u domains
cat domains.txt | waybackurls | unfurl -u domains
```

**集成化框架**

```bash
# reNgine https://github.com/yogeshojha/rengine
# 支持自定义扫描工具配置文件、Web 截屏、Nuclei POC 扫描、导入导出数据、CMS、To-do 等功能。
# Axiom https://github.com/pry0cc/axiom
# dynamic infrastructure framework。可以为不同的工具分配不同的工作负载 (即工作量), 例如 ffu、masscan。

# ARL https://github.com/TophantTechnology/ARL/
# 图形化侦查框架

# SEF https://github.com/remonsec/SEF
# 子域枚举框架，涵盖被动、主动和置换枚举
```
