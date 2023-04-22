# ports 移植游戏

## DevilutionX (Diablo)

暗黑破坏神

https://github.com/JoeStaff/devilutionX/releases

需从 Diablo 游戏中获取 *.mpq 文件放到 `Roms/PORTS/Diablo/` 下。

参考：

- https://www.reddit.com/r/RG35XX/comments/111tahx/devilutionx_diablo_1_for_rg35xxgarlicos_initial/
- https://github.com/JoeStaff/devilutionX


## Super Mario 64 port

按 https://retrogamecorps.com/2023/01/03/anbernic-rg35xx-starter-guide/ 的内容摘录如下:

* `sm64` 文件夹不要改名
* 确认 `sm64` 文件夹中有 `baserom.us.z64` 文件 (md5 值为 `20b854b239203baf6c961b850a4a51a2`)
* 没有自动存档功能
* 建议使用 "++" 频率运行，并且还有一些卡顿现象

## Jazz Jackrabbit port

从 https://github.com/JoeStaff/openjazz/releases 下载

把 GOG 版本中的游戏文件覆盖到 : `ROMS/PORTS/Jazz Jackrabbit/game/` 目录下

操作：

- 方向键 移动
- B 跳
- A 射击 / 进入
- Y 更换武器
- X 向上游泳
- L1 暂停
- R1 选项 / 后退
- 音量键 控制音量

## 参考资料

- https://www.rg35xx.com/en/bios-roms/ports/
