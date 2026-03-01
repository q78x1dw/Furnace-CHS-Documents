# VERA

这是commander x16 的视频和声音生成器,commander x16 是一个现代的8-bit电脑,由8-Bit Guy制作.this is a video and sound generator chip used in the Commander X16, a modern 8-bit computer created by the 8-Bit Guy.
它有16个方波/三角波/锯齿波/噪音通道和一个立体声PCM通道.it has 16 channels of pulse/triangle/saw/noise and one stereo PCM channel.

目前Furnace并不支持这个PCM通道的立体声模式(但是可以设置声像)currently Furnace does not support the PCM channel's stereo mode, though (except for panning).

## 效果effects

- `20xx`:设置波形 **set waveform.**
  - `0`: 方波pulse
  - `1`锯齿波 saw
  - `2`:三角波 triangle
  - `3`:噪音 noise
- `22xx`: **设置占空比set duty cycle.**
  - 范围是`0`到`3f` range is `0` to `3F`.
- `EExx`: **ZSM同步事件ZSM synchronization event.**
  - `xx`是事件载荷(?不会译)这对于Furnace里面播放的音乐没有影响,但是Commander X16的ZSMKit库会解释ZSM文件里面的这些事件,可以触发一个可选的回调例程.这可以用于,例如,让游戏逻辑对音乐节拍或者音乐中某个节点做出反应`xx` is the event payload. this has no effect in how the music is played in Furnace, but the ZSMKit library for the Commander X16 interprets these events inside ZSM files and optionally triggers a callback routine. this can be used, for instance, to cause game code to respond to beats or at certain points in the music.

## 信息info

这个芯片使用[VERA](../4-instrument/vera.md)和[通用采样](../4-instrument/sample.md)乐器编辑器this chip uses the [VERA](../4-instrument/vera.md) and [Generic Sample](../4-instrument/sample.md) instrument editors.

## 芯片配置chip config

以下选项在Chip Manager芯片设置窗口里面可用the following options are available in the Chip Manager window:

- **芯片版本Chip revision**:选择使用芯片的哪个版本 sets which revision of the chip to use.
  - V 47.0.0引入了一个稍微不一样的音量表 introduces a slightly different volume table.
