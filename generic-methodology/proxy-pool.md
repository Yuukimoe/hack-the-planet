# Proxy Pool

```bash
# https://github.com/jhao104/proxy_pool
python3 proxyPool.py schedule # 获取代理地址
python3 proxyPool.py server   # https://ip/5010 接口
curl http://127.0.0.1:5010/all/ | jq -r '.[].proxy' | sed 's|^|http://|' | tee proxies.txt # # 在 json 数据中筛选出所有免费代理并在开头添加 http://

# https://github.com/kitabisa/mubeng
mubeng -f proxies.txt --check --output live.txt      # 检测所有存活代理
mubeng -a localhost:8089 -f live.txt -r 10 -m random # 开启代理端口
```
