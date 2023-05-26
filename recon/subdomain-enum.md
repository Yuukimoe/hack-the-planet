# Subdomain Enum

```
# https://github.com/shmilylty/OneForAll
# https://github.com/tomnomnom/anew
# https://gist.github.com/moeuuki/cb6fbabe868ffab3c84f5886f3957326
python3 oneforall.py domain.com
jq -r '.[].subdomain' domain.com.json | anew subs.txt

# https://github.com/projectdiscovery/subfinder
subfinder -d domain.com -all -silent -o subs.txt
```
