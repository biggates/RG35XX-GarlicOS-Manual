# Garlic OS 更新记录 (翻译)

原帖地址在 https://www.patreon.com/posts/76561333 。

## 2023-01-18

- 修正了 GarlicOS 主菜单的帧数限制
- 修正了 `dosbox_pure` 核心 (支持 DOS 游戏)
- 在游戏中按下菜单键将切换到 "最近的游戏" 页面 (注: 而不是切换到 GarlicOS 的主页面)
- 退出 RetroArch 屏幕时, 将记忆上一次 GarlicOS 选中的项目
- RetroArch 可以记忆音量设置了

## 2023-01-17

- 开启 `block_sram_overwrite` 使保存功能更稳定
- 修正了在快捷菜单中切换保存时崩溃的错误
- 修正了游戏中的透明效果
- GarlicOS 的主菜单现在使用双重缓冲以减少撕裂
- 重新编译了 `dosbox_pure` 核心，希望能够解决色彩空间的问题
- 增加了两个更低的屏幕亮度选项
- 主题可以关闭 "Main Menu" 文字，仅开启 logo

## 2023-01-16

- 固定使用核心 3 和 4 双线程进行临近插值缩放
- 固定使用核心 3 和 4 双线程进行半线性缩放 (Bresenham)
- 为了修正某些核心中出现的声音卡顿，关闭了声音同步

TODO: 其他翻译暂未完成，请参阅 [英文版](./changelog.en_US.md) 或原文。
