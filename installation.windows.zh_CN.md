# 如何安装 (Windows)

以下内容以 Windows 11 为例介绍如何安装 Garlic OS 。

## 准备工作

### 硬件

### 软件

- 7-zip, 建议可以安装。
- DiskGenius, 如本文使用的是 `DGEngSetup5461441.exe` ，需要安装。
- Balena Etcher, 如本文使用的是 `balenaEtcher-Portable-1.13.1.exe` 不需要安装。如果下载了安装版则需要安装。

### Garlic OS

## 安装 Garlic OS

### 1. 准备镜像文件

1. 将 `RG35XX-Garlic-MicroSDCardImage.7z` 解压，得到 `garlic.img`

### 2. 烧录 SD 卡

1. 打开 BalenaEtcher , 选择 "从文件烧录", 选择刚刚解压出来的 `garlic.img` 文件

  ![](./images/balena_etcher_step_1.png)

2. 把 SD 卡插入读卡器, 或插入电脑。
3. 在 BalenaEtcher 中点击 "选择目标磁盘" , 选择要安装 Garlic OS 的 SD 卡 (注意别选错了!)

  ![](./images/balena_etcher_step_2.png)

4. 在 BalenaEtcher 中确认好信息之后，点击 "现在烧录!"。在这一过程中会触发 UAC 提示，确认即可。

  ![](./images/balena_etcher_step_3.png)

5. 耐心等待 BalenaEtcher 烧录完成。

  注: 在烧录过程中显示的广告可能会有所不同，这不影响烧录的结果。

  ![](./images/balena_etcher_step_4.png)

  ![](./images/balena_etcher_step_5.png)

  注: 烧录完成后，Windows 可能会提示 XX 分区需要格式化。请务必忽略这些提示。
  注: 如果烧录失败，可以重来一次。

  烧录成功之后就可以关闭 BalenaEtcher 了。

### 3. 调整分区表

1. 打开 DiskGenius, 可以看到新烧录的 SD 卡中的分区信息如下所示:

  ![](./images/diskgenius_garlicos_partition.png)

2. 在 DiskGenius 中，选中 FAT32 分区，在右键菜单中点击 "Resize Partition"

  ![](./images/diskgenius_resize_partition_step_1.png)

3. 在 "Resize Partition" 窗口中，将蓝色分区右边拖动到最后，或者手动输入 `Space of Rear Part` 的值为 `0` ，使分区占据所有剩余的空间。

  调整前: 这个分区只有 3.16 GB

  ![](./images/diskgenius_resize_partition_step_2.png)

  调整后: 分区大小变为 57.67 GB

  ![](./images/diskgenius_resize_partition_step_3.png)

4. 确认无误后，点击 "Start"，并确认。

  ![](./images/diskgenius_resize_partition_step_4.png)

  ![](./images/diskgenius_resize_partition_step_5.png)

### 4. 准备 ROMS SD 卡

注: 这一节描述的内容仅适用于新卡。如果你已经准备好了 ROMS ，那么就不需要按此节进行操作。


1. 将需要操作的 SD2 插入电脑
2. 以管理员身份打开 FAT32 Format 程序，选中正确的 SD 卡后，将 `Volume label` 设置为 `ROMS`，选择 "Start" 并确认。

  ![](./images/FAT32Format_step_1.png)

  注: 在这一步中如果反复出现文件被占用的操作，可以先用 Windows 把 SD2 格式化一遍，格式化成 NTFS 或者 exFAT 都无所谓。

3. 格式化完成

  ![](./images/FAT32Format_step_2.png)

4. 把 Roms 中的全部文件夹复制进 SD2 中。

  ![](./images/ROMS_folders.png)

## 升级 Garlic OS

