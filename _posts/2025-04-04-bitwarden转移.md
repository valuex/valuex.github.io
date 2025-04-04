# Vaultwarden 是什么
Vaultwarden 是一个用于本地搭建 Bitwarden 服务器的第三方 Docker 项目。仅在部署的时候使用 Vaultwarden 镜像，桌面端、移动端、浏览器扩展等客户端均使用官方 Bitwarden 客户端。

Vaultwarden 很轻量，对于不希望使用官方的占用大量资源的自托管部署而言，它是理想的选择。

# Vaultwarden 与 Bitwarden 的区别
除不支持 Bitwarden 官方企业版的部分功能（详情见这里）外，其他大部分功能均免费支持。并跟随官方版本保持及时更新。

Vaultwarden 比 Bitwarden 官方版更轻量。官方版使用 .Net 开发，使用 MSSQL 数据库，要求至少 2GB 内存；Vaultwarden 使用 Rust 编写，改用 SQLite 数据库（现在也支持 MySQL 和 PostgreSQL），运行时只需要 10M 内存，可以说对硬件基本没有要求。

# 安装
参见群晖安装，略。

# Chrome扩展/Android客户端登陆
在**自托管**中选择**服务器url**，填入对应的url后即可登陆
