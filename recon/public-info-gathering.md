# Public info gathering

## OSINT websites

```bash
# Multipurpose
https://www.shodan.io/
https://fofa.info/
https://hunter.qianxin.com/

# Companies info
https://www.aiqicha.com/
https://www.xiaolanben.com/pc/

https://opencorporates.com/companies

# ICP
https://beian.miit.gov.cn/#/Integrated/index
https://www.beianx.cn/
https://icp.chinaz.com/
https://www.ggcx.com/main/record
http://www.chaicp.com/

# 公网备案
https://www.beian.gov.cn/portal/registerSystemInfo
https://icp.chinaz.com/psorgan

# APP
https://www.xiaolanben.com/pc
https://www.qimai.cn/
https://www.apple.com/app-store

# 小程序
https://tj.aldwx.com/

# Cloud drive
https://www.lingfengyun.com/
https://www.pansoso.com/
http://wp.soshoulu.com/
http://www.zhuzhupan.com/

# DNS zone transfer
https://hackertarget.com/zone-transfer/

# Ping tools
https://www.itdog.cn/batch_ping/
```

### Companie tools

```bash
# https://github.com/wgpsec/ENScan_GO
enscan -n company -invest 50 -email -is-merge -deep 2
enscan -f subcompany.txt -invest 50 -email -is-merge -deep 2
```

## Whois/Registrant

```bash
https://www.whoxy.com/
```

## Dorks

### Education

```bash
# education
filetype:xls site:xxx.edu.cn sfzh
filetype:xls site:xxx.edu.cn 身份证号
filetype:pdf site:xxx.edu.cn sfzh
filetype:pdf site:edu.cn 身份证号
inurl:edu inurl:PDF 机密等级 ABC
inurl:/backup intitle:index of backup intext:*sql site:edu.cn
inurl:/school/support site:edu.cn
```

### Google

```bash
https://gist.github.com/sundowndev/283efaddbcf896ab405488330d1bbc06
```
