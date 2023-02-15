# 存档管理

TODO: 完善该文档

## 存档的位置

在 2023-01-11 的版本中，存档和 Roms 放在一起。

例如在单卡环境中，存档存放在 Roms 分区中:

(TODO)

```
/
```

例如在双卡环境中，存档存放在 TF2 中:

(TODO)

```
/
```

## 存档的内容

```
CurrentProfile/
    lists/
        content_history.lpl
    saves/
        Gambatte/
            xxx.srm
        gpSP/
            xxx.sav
    states/
        Gambatte/
            xxx.state.auto
            xxx.state.auto.png
        gpSP/
            xxx.state1
            xxx.state1.png
```

### 游戏历史记录

`lists/content_history.lpl` 实际上是一个 json 文件

```json
{
  "version": "1.5",
  "default_core_path": "",
  "default_core_name": "",
  "label_display_mode": 0,
  "right_thumbnail_mode": 0,
  "left_thumbnail_mode": 0,
  "sort_mode": 2,
  "items": [
    {
      "path": "/mnt/SDCARD/GBA/Densetsu no Stafy 2 (Japan).zip",
      "label": "",
      "core_path": "/mnt/mmc/CFW/retroarch/.retroarch/cores/gpsp_libretro.so",
      "core_name": "Nintendo - Game Boy Advance (gpSP)",
      "crc32": "",
      "db_name": ""
    },
    {
      "path": "/mnt/SDCARD/GBC/Tetris DX (World) (SGB Enhanced) (GB Compatible).zip",
      "label": "",
      "core_path": "/mnt/mmc/CFW/retroarch/.retroarch/cores/gambatte_libretro.so",
      "core_name": "Nintendo - Game Boy / Color (Gambatte)",
      "crc32": "",
      "db_name": ""
    }
  ]
}
```

### 存档

存放在 `saves/核心名/` 目录下，每个游戏一个文件。

### 状态 savestate

存放在 `states/核心名/` 目录下。

默认状态的后缀名为 `.state.auto` 。

手动设置的状态后缀名为 `.state1`, `.state2`, 等。

配有同名的 `.png` 的截图。
