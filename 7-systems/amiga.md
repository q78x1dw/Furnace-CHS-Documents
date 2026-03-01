# Commodore Amiga

1985年就有有桌面操作系统，逼真的图形和4通道PCM音频吗?这怎么可能啊!a computer with a desktop OS, lifelike graphics and 4 channels of PCM sound in 1985? no way!

就是在这个电脑上面,诞生了音乐tracker... in this very computer music trackers were born...

可以导入MOD文件到这个芯片上,然后A-4会调整为436.imported MOD files use this chip, and will set A-4 tuning to 436.

## 振幅/相位调制amplitude/period modulation

Amiga有(相对原始的)振幅与相位(频率)调制.Amiga has support for (rather primitive) amplitude and period (frequency) modulation.
但是,没有人用过这个功能,因为它相对没有用,资料不多,而且工作方式复杂.however, nobody has used this feature as it is rather useless, not well-documented and works in a complicated way.

Amiga的采样播放由两个芯片完成:Paula(你可能知道)和Agnus(它给Paula提供采样)Amiga sample playback is done by two chips: Paula (the one that you probably know) and Agnus (the one that actually feeds Paula with samples).
Agnus有几个DMA(直接内存访问)通道,可以独立于CPU读取内存.其中4个通道用于采样.Agnus has several DMA (direct memory access) units which read from chip memory independent of the CPU. four of these DMA units are used for samples.

当DMA开启,Paula向Agnus请求采样数据,然后播放.when DMA is enabled, Paula requests sample data from Agnus, and then plays these samples back.
这里暗藏玄机,数据总线是16位的,所以Paula一次获取**2个**8位采样!这就解释了为什么there's a catch though. since the data bus is 16-bit, Paula requests **two** 8-bit samples at once! this explains why:
- 采样长度寄存器是以字而不是以字节为单位(这样采样总长可以达到131070)the sample length registers are in words rather than bytes (thereby allowing samples up to 131070 in length)
- 最大播放速率(31250Hz PAL;~31469Hz NTSC)是HBlank速率(Agnus以HBlank速率获取采样,PAL ~15625Hz,NTSC ~15734Hz)的二倍!the maximum playback rate (31250Hz PAL; ~31469Hz NTSC) is two times the HBlank rate (Agnus fetches samples on HBlank, around 15625Hz on PAL or ~15734Hz on NTSC)

正常播放期间,第一个采样输出后第二个输出,之后更多采样就会获取到,以此类推during normal sample playback, the first sample is output and then the second. afterwards, two more samples are fetched, and so on.

现在,如果振幅或相位调制启用,工作原理就不一样了.now, when amplitude or period modulation are enabled, things work differently.
这个通道被静音,两个八位采样被**当成大端序十六位数字**,然后被写到下一个通道的音量或者相位.the channel is silenced, and the two 8-bit samples are **treated as a big-endian 16-bit number**, which is then written to the next channel's volume or period.

在振幅调制的情况下,只有第二个采样占数值,因为音量寄存器使用7位(表示0到64,65到127被当成64),其他的位都被忽略了.in the case of amplitude modulation, only the second sample is significant because the volume register uses 7 bits (to represent 0 to 64 (65 to 127 are treated as 64)) and the other bits are ignored.

在相位调制的情况下,两个采样都占数值.第一个采样是高字节,第二个采样是低字节.in the case of period modulation, both samples are significant. the first sample is the upper byte, and the second is the lower byte.

## 效果effects

- `10xx`: **开关低通滤波器toggle low-pass filter.** `0` turns it off and `1` turns it on.
- `11xx`: **开关对于下一个通道的振幅调制toggle amplitude modulation with the next channel.**
  - 对于最后一个通道无效does not work on the last channel.
- `12xx`: **开关对于下一个通道的相位(频率)调制toggle period (frequency) modulation with the next channel.**
  - 对于最后一个通道无效does not work on the last channel.
- `13xx`: **更换波形change wave.**
  - 只有乐器中'模式'设置为'波表'时候才有用.only works when "Mode" is set to "Wavetable" in the instrument.

## 有关信息info

这个芯片使用this chip uses the [Generic Sample](../4-instrument/sample.md) 乐器编辑器instrument editor.

- 采样最大播放速率理论上是31469Hz但是高于28867Hz的在硬件上会有破音.the maximum rate for sample playback is technically 31469Hz but anything higher than 28867Hz will sound glitchy on hardware.
- 采样长度与循环位置总是一个偶数.sample lengths and loop will be set to an even number.
- 采样不可以长于131070.samples can't be longer than 131070.

## 芯片设置chip config

如下选项在芯片管理器窗口中可用.the following options are available in the Chip Manager window:

- **左右声道分离Stereo separation**: 设置左右声道的分离程度sets the amount of left/right separation.
- **型号Model**: allows you to change the chipset.
  - Amiga 500 (OCS): 在用户可选的滤波器之上还有一个低通滤波器has a low-pass filter on top of the user-selectable filter.
  - Amiga 1200 (AGA): 没有上述的低通滤波器doesn't have the aforementioned low-pass filter.
- **芯片内存Chip memory**: 更多芯片内存意味着有更多空间放采样.more chip memory means more space for samples.
- **PAL**: 让芯片跑在PAL时钟而不是NTSC时钟.run the chip at PAL clock (3.54MHz) instead of NTSC (3.58MHz).
- **旁路频率限制Bypass frequency limits**: 打开后,~31KHz频率限制被取消,可以播放更高的音.when enabled, the ~31KHz frequency limit is disabled, allowing you to play higher notes.
