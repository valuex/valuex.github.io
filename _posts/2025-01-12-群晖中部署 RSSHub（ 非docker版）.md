
# 为什么要用RSSHub
- 覆盖广，资源丰富
- 对不规则的网页内容会更容易实现。
# 为什么要用非docker版本
Docker版本涉及到跟主分支的版本关系管理，比较复杂。写了一个新路由后，要么合入主版本，最短也可能需要2天左右；要么自己编译docker镜像（个人编辑docker镜像的技术路线还没跑通），后期也涉及到版本管理的问题。
所以就直接在群晖NAS上部署了一个非docker版本的RSSHub，自用。
# 如何在群晖上部署非docker版RSSHub
1. 下载源码（直接在Github上下载源码的zip包）  
[GitHub - DIYgod/RSSHub: 🧡 Everything is RSSible](https://github.com/DIYgod/RSSHub)
2. 将Zip包上传到NAS，并解压
3. 通过putty 登录NAS，并跳转到RSSHub所在目录
4. 参照这个网页，运行`pnpm i`和 `pnpm dev` 即可, 参考RSSHub官方教程[开始之前 | RSSHub](https://docs.rsshub.app/zh/joinus/new-rss/before-start)  
5. 访问`http://nas_ip:1200` 即可看到效果  
6.参照IPV6 公网访问NAS（[外网访问群晖：IPV6+DDNS - 知乎](https://zhuanlan.zhihu.com/p/717555214)），在路由中设置内网路由转发
7. 通过域名+代理端口(如 `https://you_synology_domain:1200`) 即可在外网访问部署的RSSHub
# 如何在群晖重启后同步启动RSSHub
可以在【控制面板】-》【任务计划】中添加一个开机启动RSSHub的任务。任务设置中的内容为
```
cd /Your_RSSHub_Path/
pnpm start
```

# 如何创建和部署自己的路由？
可以在本地电脑上调试好路由，然后将路由脚本上传到NAS_RSSHub_Dir 下面。重启RSSHub即可。

