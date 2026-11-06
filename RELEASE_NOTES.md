# PCL Unlocked v1.0.0 发布说明

基于官方 [Meloong-Git/PCL](https://github.com/Meloong-Git/PCL) 2.99.0.1 开源代码（2026-10-25）的第三方修改版。

## 本次修改

### 1. 恢复 MC 下载与整合包功能

官方于 2026-10-20 的 2.99.0.0 版本起，因被举报以"为遵守相关法律法规"为由，通过 `ModSecret.RestrictMcDownload` 常量移除了游戏本体下载与整合包安装入口（2.99.0.1 起为永久）。该封禁为硬编码开关，功能代码本身完整保留。

本版本将该常量恢复为 `False`，恢复内容包括：

- 下载页"安装 Minecraft"与全部子页面（正式版 / 快照版 / 远古版 / 愚人节版）
- 整合包搜索、详情页安装、本地整合包导入（CurseForge / Modrinth / MultiMC 格式）
- 版本列表右键"安装新版本"、版本修改页 MC 卡片、Mod 页下载按钮等全部入口
- Minecraft 更新提示弹窗中的"下载"按钮

### 2. 备用下载源优化

未配置 CurseForge API Key 时（即大多数自编译场景），社区资源请求直接使用 MCIM 镜像源，跳过对 `api.curseforge.com` 的无效 403 重试。已配置 Key 的构建行为与官方完全一致。

游戏本体下载的多源机制保持官方设计不变：Mojang 官方源 + BMCLAPI 镜像自动回退。

### 3. 品牌适配

- 窗口标题：Plain Craft Launcher Unlocked
- 程序集信息与关于页注明修改版身份；关于页首位保留原作者署名与赞助链接
- 更新日志中官方的移除条目改写为"官方版本历史"说明，并新增恢复条目

## 使用须知

- 首次启动会弹出"开源版本说明"，其中的限制项（正版登录 Client ID、CurseForge Key 等）与本版本一致，可通过仓库 Secrets 注入解决
- 修改版的设置与官方版相互隔离（注册表路径不同），可并存安装
- 无内置更新器：请通过 GitHub Releases 获取新版本，不要使用来路不明的"更新包"

## 构建方式

推送本仓库到 GitHub 后 Actions 自动编译；推送 `v*` 标签自动发布 Release。本地编译方法见 [README.md](README.md)。

## 合规与致谢

本项目遵循《PCL 分发有限许可》与《PCL 存储库合理使用指南》"重度使用"条款分发：标注第三方修改版身份、名称以 PCL 开头、关于页首位保留 [龙腾猫跃](https://meloong.com/afd/a/LTCat) 署名与赞助链接、源代码公开、保留正版购买劝导、主色相保持蓝色。

感谢龙腾猫跃七年来的免费开发，以及 BMCLAPI（bangbang93）、MCIM（z0z0r4）、MC 百科等社区服务的支持。有能力请支持官方正版：[PCL 官方下载](https://meloong.com/pcl) / [购买 Minecraft](https://www.minecraft.net/)。
