# Garlic OS

GarlicOS 是基于 RetroArch 在 RG35XX 上的一个系统。可以类比 Miyoo Mini 的 [Onion OS](https://github.com/OnionUI/Onion) 。

GarlicOS 的文件内容可以从 [Black-Seraph 的 Patreon 页面](https://www.patreon.com/posts/76561333) 下载（需要注册账号）。

文件内容：

- `CopyPasteOnTopOfStock.7z` 中的 `misc`, `ROMS`, `BIOS` 等文件夹直接复制到官方镜像的对应分区中，用于升级。
- `MicroSDCardImage.7z` 是整个 TF 卡的镜像 (`garlic.img`), 建议使用 [balenaEtcher](https://www.balena.io/etcher/) 还原到 TF 卡。

建议将 ROM 和存档 (TODO) 放在 TF2 中，这样换机和维护都比较方便。

本 repo 的风格:

- 主要包含在 Windows 平台中的操作步骤、一些常见问题等
- 可能包含 Black-Seraph 原帖中的一些翻译内容
- 不会存放 Garlic OS 的文件内容
- 不负责解答问题

## 目录

### 使用手册

- [如何安装和更新 GarlicOS (Windows) (中文)](./installation.windows.zh_CN.md)
- [GarlicOS 快捷键一览 (中文)](./hotkeys.zh_CN.md)
- 以下内容尚不完全：
  - [显示游戏图片](./thumbnails.zh_CN.md) (目前仍在施工中)
  - [游戏遮罩](./bezels.zh_CN.md) (尚未完成编写)
  - [常用配置信息](./configuration.zh_CN.md) (尚未开始编写)
  - [金手指](./cheats.zh_CN.md) (尚未开始编写)

### 技术资料

- [GarlicOS 更新记录 (中文)](./changelog.zh_CN.md)
  - [GarlicOS 更新记录 (原文转载)](./changelog.en_US.md)
- [分区信息](./partitions.zh_CN.md)
- [已知问题](./known_issues.zh_CN.md)

## 其他资源

- [一些 RG35XX 资源下载 (百度网盘)](https://pan.baidu.com/s/1jHsoRIHnCFNSarL5DOmkJA?pwd=35xx#list/path=%2F)

## 参考资料

- [RG35XX Starter Guide by Retro Game Corps](https://retrogamecorps.com/2023/01/03/anbernic-rg35xx-starter-guide/)
