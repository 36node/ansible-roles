# Alidns

这里采用阿里云的 DNS 解析，实现域名到 ip 的分配

## 准备

需要在控制机准备这两个命令行工具

- aliyun-cli
- jq

并且授权 aliyun

```
aliyun configure set \
  --profile akProfile \
  --mode AK \
  --region cn-beijing \
  --access-key-id ${ALI_KEY} \
  --access-key-secret ${ALI_SECRET}
```
