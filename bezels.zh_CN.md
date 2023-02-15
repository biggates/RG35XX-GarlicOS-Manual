# 遮罩

例如 GBA 游戏，在启用了整数缩放 Integer Scaling 之后，图像会变成中间小小的一块。使用遮罩可以填充外面的黑色区域。

## 实现

遮罩由至少一张 `.png` 图片和一个 `.cfg` 配置文件组成。

- `.cfg` 文件的名称需要和第一张图片的名称相同
- 文件名中不能包含空格
- 存放在 `overlay` 文件夹中

## 参考

- [Input Overlays](https://docs.libretro.com/guides/libretro-overlays/)
- [RetroArch Overlays @ libretro 论坛](https://forums.libretro.com/c/retroarch-additions/retroarch-overlays)
- [libretro/overlay-borders @ GitHub](https://github.com/libretro/overlay-borders)
