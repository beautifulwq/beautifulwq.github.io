---
title : "一次sshPubKey连接问题"
date : 2024-03-17
draft : false
taxonomies:
    categories:
        - "tech"
extra:
   lang : "zh"
   toc : false
   comment : true
   copy : true
   math : false
   mermaid : false
   outdate_alert : false
   outdate_alert_days : 120
   display_tags : true
   truncate_summary : false # 摘要
   featured : false
---


之前一直是用 root 登录云服务器，想用普通用户 wqq 登录发现 ssh 免密码登录上不去，反复排查终于找到了，原来是 `/home/wqq` 这个文件夹的属性出了问题，others 不应该有 w 权限，其他的像是生成密钥等都写在 techbook->linux 页面。

这次花费2h总结得出：
1. chatgpt在查命令这方面好用太多了
2. 用正确的和错误的比对有可能有收获
3. 打日志，像 `ssh -vvv` `/var/log/auth.log`