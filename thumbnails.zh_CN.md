# 缩略图

在 RGUI 中支持 playlist 的缩略图。

## playlist

RetroArch 的 playlist 是以 `.lpl` 为后缀名的 JSON 文件。

## 缩略图

缩略图的根目录是 TF1 卡中的 `ROMS` 分区下的 `/CFW/retroarch/.retroarch/thumbnails/` 目录。应当存放在和 playlist 同名的目录下。

例如，有一个 playlist 名为 `Atari - 2600.lpl`，那么对应的缩略图应放在 `Atari - 26000` 目录下，如下所示：

```
/CFW/retroarch/.retroarch/thumbnails/
    Atari - 2600/
        Named_Boxarts/
            Q_bert's Qubes.png
        Named_Snaps/
            Q_bert's Qubes.png
        Named_Titles/
            Q_bert's Qubes.png
```

缩略图的文件名应和 playlist 中的 `label` 完全一致，但 `label` 中的 <code>$*/:\`<>?\|</code> 这几个字符应当被替换为 `_`。

## 参考

- [RGUI Interface](https://docs.libretro.com/guides/rgui/)
- [Playlists and Thumbnails](https://docs.libretro.com/guides/roms-playlists-thumbnails/)
- [libretro-thumbnails @ GitHub](https://github.com/libretro-thumbnails/libretro-thumbnails)