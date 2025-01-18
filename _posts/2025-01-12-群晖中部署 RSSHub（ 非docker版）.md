
# 为什么要用RSSHub
- 覆盖广，资源丰富
- 对不规则的网页内容会更容易实现。
# 为什么要用非docker版本
Docker版本涉及到跟主分支的版本关系管理，比较复杂。写了一个新路由后，要么合入主版本，最短也可能需要2天左右；要么自己编译docker镜像（个人编辑docker镜像的技术路线还没跑通），后期也涉及到版本管理的问题。
所以就直接在群晖NAS上部署了一个非docker版本的RSSHub，自用。
# 如何在群晖上部署非docker版RSSHub
1.  putty 连接到群晖
获取管理员权限
`sudo -i`
2. 创建文件夹
`cd /volume1/your_dir`
3. git 下载RSSHub
`git pull https://github.com/DIYgod/RSSHub`
4. 安装pnpm，因为群晖中Node.js 当前最新版为V20，所以pnpm 要装9.10.0版本的  
```
npm install -g pnpm@9.10.0
```
5. 跳转到RSSHub所在目录
```
cd /volume1/your_dir/RSSHub
```
6. 安装RSSHub 所需依赖项
   参考RSSHub官方教程[开始之前 | RSSHub](https://docs.rsshub.app/zh/joinus/new-rss/before-start) 
```pnpm i```


7. 访问`http://nas_ip:1200` 即可看到效果    
8. 参照IPV6 公网访问NAS（[外网访问群晖：IPV6+DDNS - 知乎](https://zhuanlan.zhihu.com/p/717555214)），在路由中设置内网路由转发  
9. 通过域名+代理端口(如 `https://you_synology_domain:1200`) 即可在外网访问部署的RSSHub
# 如何在群晖重启后同步启动RSSHub
可以在【控制面板】-》【任务计划】中添加一个开机启动RSSHub的任务。任务设置中的内容为
```
cd /Your_RSSHub_Path/
pnpm start
```

# 如何创建和部署自己的路由？
可以在本地电脑上调试好路由，然后将路由脚本上传到NAS_RSSHub_Dir 下面。重启RSSHub即可。
```
pnpm build
pnpm start
```
# 升级 `nodejs`
```
; https://www.cnblogs.com/visionsl/p/16824968.html
npm install -g n
n stable
```
# 报错解决
1. 文件被打开，
```
   Error: EMFILE: too many open files, open '/volume1/web/RSSHub-master/node_modules/.pnpm/tosource@2.0.0-alpha.3/node_modules/tosource/dist/index.js'
```
解决办法

```
; https://blog.csdn.net/weixin_44772835/article/details/128610490
ulimit n 65535
```
2. `pnpm i` 安装报错，多尝试几次，或者试试 `npm install`


