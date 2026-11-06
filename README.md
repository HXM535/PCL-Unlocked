# Plain Craft Launcher Unlocked (PCL Unlocked)

基于 [Meloong-Git/PCL](https://github.com/Meloong-Git/PCL) 官方开源代码（2.99.0.1）的第三方非官方修改版。

> 本项目与 PCL 官方（龙腾猫跃 / Meloong）无关。免费使用官方正式版请前往[爱发电主页](https://meloong.com/afd/a/LTCat)下载。

## 修改内容

| 提交 | 说明 |
| --- | --- |
| 解锁 MC 下载与整合包功能 | 官方自 2.99.0.0 起通过 `ModSecret.RestrictMcDownload` 常量屏蔽了游戏本体下载与整合包安装（功能代码本身保留）。本版本将该常量恢复为 `False`，行为与官方 2.14.0.0 一致 |
| 备用下载源 | 未配置 CurseForge API Key 时，社区资源请求直接使用 MCIM 镜像（mod.mcimirror.top），避免对官方 API 的无效 403 重试；已配置 Key 时行为不变 |
| 品牌适配 | 窗口标题、程序集信息与关于页"修改版说明"卡片注明修改版身份，关于页首位保留原作者署名 |
| 构建流水线 | GitHub Actions 推送自动编译，打 `v*` 标签自动发布 Release |

其余功能与官方开源版完全一致，包括：BMCLAPI / MCIM / Mojang 多源下载、启动前的正版购买劝导（`McLaunchPrecheck`）、默认蓝色主色相。

## 已知限制（继承自官方开源分支）

- 微软正版登录需要 Azure Client ID：在仓库 Secrets 配置 `CLIENT_ID`，或按启动时的"开源版本说明"自行填写
- CurseForge 官方 API 需要 API Key：在仓库 Secrets 配置 `CURSEFORGE_API_KEY`（不配置则自动走 MCIM 镜像）
- 无内置更新器（更新功能在开源分支已桩化），版本更新通过 GitHub Releases 发布
- 官方的纪念主题、百宝箱等未公开功能不在开源分支中

## 构建

### GitHub Actions（推荐）

1. 将本仓库推送到你的 GitHub 账号（Fork 或新建仓库均可）
2. 推送后 Actions 自动构建 Debug / Release 两个配置，在对应 Run 的 Artifacts 中下载 exe
3. 推送 `v1.0.0` 之类的标签即可自动创建 GitHub Release 并附上 exe
4. 可选：仓库 Settings → Secrets and variables → Actions 中配置 `CLIENT_ID` 与 `CURSEFORGE_API_KEY`

### 本地编译（Windows）

1. 安装 Visual Studio 2022（".NET 桌面开发"工作负载）
2. `git clone --recursive <本仓库地址>`（MeloongCore 子模块必须一并拉取）
3. `dotnet restore PCLCS\PCLCS.csproj`
4. 编译 `Plain Craft Launcher 2\Plain Craft Launcher 2.vbproj`（Release 配置，MSBuild 或 VS 均可）
5. 产物位于 `Plain Craft Launcher 2\obj\Release\Plain Craft Launcher 2.exe`

## 许可协议与合规声明

本仓库依据 PCL 官方的《PCL 分发有限许可》与《PCL 存储库合理使用指南》（见 [LICENCE](LICENCE)）以"重度使用"条款分发：

1. 明确标识为第三方基于 PCL 独立二次创作的产物，与官方无关
2. 名称以 Plain Craft Launcher (PCL) 开头，附加表现第三方修改的后缀（Unlocked）
3. 关于页面首位保留龙腾猫跃的署名及[赞助链接](https://meloong.com/afd/a/LTCat)；源代码公开；继续沿用原 LICENCE 文件
4. 实现与官方一致的 Minecraft 正版购买劝导与赞助劝导（`McLaunchPrecheck`，未做任何削弱）
5. 界面默认主色相保持蓝色，未实现任何与赞助解锁类似的功能

## 免责声明

- 本修改版按"现状"提供，不附带任何担保；使用产生的后果由使用者自行承担
- 启动器内下载的 Minecraft 本体文件来自 Mojang 官方源与 BMCLAPI、MCIM 等社区镜像；请自行确认在你的所在地区使用相关功能的合规性
- 有能力的话请购买正版 Minecraft 支持开发者：https://www.minecraft.net/
