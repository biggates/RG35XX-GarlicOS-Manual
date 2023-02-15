# 播放视频

在 GarlicOS 1.0.6 (2023-02-13) 中加入了播放视频的功能。

## 文件组织

视频文件需要放置在 `VIDEOS` 目录中。

TODO: 是否支持按更深的文件夹？

## 视频编码

目前已知需要使用 .x264 编码为 mkv 格式

```
ffmpeg -i input.mkv -vf scale=640x480 -vcodec libx264 -profile:v main -level 3.1 -preset medium -crf 23 -x264-params ref=4 -acodec libvorbis - - movflags +faststart output.mkv
```

## 播放 mp3

由 [reddit](https://www.reddit.com/r/RG35XX/comments/112ahwb/galicos_can_play_mp3_now_but_the_screen_its/), 可以播放 mp3 ，但屏幕会一直亮着 (黑的)。

