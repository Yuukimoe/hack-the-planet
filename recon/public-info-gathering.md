# Public info gathering

## 工商信息

工商信息收集基本流程

1. 企业官网寻找备案号 -> 通过备案号获取公司名称
2. 工具/站点查询公司名称 -> 获取子公司、法人/股东信息、非 Web 资产 (APP/小程序/公众号)
3. 对子公司重复执行第 2 步骤操作

```bash
# 企业基本信息
https://www.aiqicha.com/
https://www.tianyancha.com/
https://www.qcc.com/
https://www.xiaolanben.com/pc/
https://www.qixin.com/

# APP 信息收集
https://www.qimai.cn/
https://tj.aldwx.com/

# 小程序信息收集
https://tj.aldwx.com/

# ICP 备案查询
https://beian.miit.gov.cn/#/Integrated/index
https://www.beianx.cn/
https://aiqicha.baidu.com/
https://icp.chinaz.com/

# 公安备案查询
https://www.beian.gov.cn/portal/registerSystemInfo
https://icp.chinaz.com/psorgan
```

## 域名收集

```bash
# Reverse ICP
https://beian.miit.gov.cn/#/Integrated/index
https://www.beianx.cn/
https://www.aiqicha.com/

# Whois
https://whois.chinaz.com/
https://www.whoxy.com/

# DNS zone transfer
https://hackertarget.com/zone-transfer/
```

## 自动化工具

```bash
# 企业信息收集
# https://github.com/wgpsec/ENScan_GO
enscan -n company -invest 50
```
