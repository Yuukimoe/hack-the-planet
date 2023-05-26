# Subdomain Enum

{% code title="OSINT" %}
```bash
# https://github.com/shmilylty/OneForAll
# https://github.com/tomnomnom/anew
# https://gist.github.com/moeuuki/cb6fbabe868ffab3c84f5886f3957326
python3 oneforall.py --target domain.com --path . run
jq -r '.[].subdomain' domain.com.json

# https://github.com/projectdiscovery/subfinder
subfinder -d domain.com -all -silent
subfinder -dL roots.txt -all -silent

# https://github.com/gwen001/github-subdomains
github-subdomains -q -raw -t ~/.config/github-subdomains/github-token.txt -d example.com

# https://github.com/OWASP/Amass
# https://github.com/OWASP/Amass/blob/master/examples/config.ini
amass enum -d domain.com -config ~/.config/amass/config.ini
```
{% endcode %}



