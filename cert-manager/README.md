# cert-manager

安装 cert-manager，用于生成 https 证书

## cert-manager 调试错误的流程

https://cert-manager.io/docs/faq/troubleshooting/

## 两种域名验证方式

发 tls 证书时，服务机构要验证服务器 ip 的归属，会采用两种方式:

1. 给定一个 path，放一个 .well-known/xxxx.txt 文件
2. 域名添加 cname

具体体现在 letsencrypt.yaml 文件的 solvers 一节

注意：**alidns 默认是关闭的**，需要使用的话请打开，否则当外部使用 `cert_issuer: "letsencrypt-alidns"` 时，是不起作用的
