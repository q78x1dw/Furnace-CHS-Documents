# MOS Technology TED

也叫7360/8360. TED表示Text Editing Device. 这是COmmodore的廉价型电脑的兼用的音频和视频芯片,就像 Plus/4 和 16. also called 7360/8360, TED stands for Text Editing Device. it's both a video and audio chip of Commodore budget computers, like Plus/4 and 16. 

他的音频方面比较贫乏 - 只有2通道, 一个可以输出方波,另一个可以输出方波或者噪音. its audio portion is pretty barren - only 2 channels. one can output square wave and other may be either square or noise.
音调范围也比较有限, 与SN76489的相似, 音量的控制也是全局的. pitch range is limited as well, akin to that of SN76489, and volume control is global.

## 效果effects

目前没有
none so far.

## 信息info

这个芯片使用 this chip uses the [TED](../4-instrument/ted.md) 乐器编辑器instrument editor.

## 芯片配置chip config

以下选项在芯片管理器中可用.the following options are available in the Chip Manager window:

- **时钟速率Clock rate**: sets the rate at which the chip will run.
- **全局参数优先级Global parameter priority**: 改变控制全局参数的宏的优先级,例如音量. change the priority of macros which control global parameters, such as volume.
  - 从左到右Left to right: 从通道1到3处理. 最后一个运行宏的通道会生效. process channels from 1 to 3. the last one to run macros will take effect.
  - 最后一个使用的通道Last used channel: 从最旧到最新(自上个音符以来) 处理通道. 最后一个有音符的通道会有效果. process channels from oldest to newest (since last note). the one which had the latest note on will take a effect.
