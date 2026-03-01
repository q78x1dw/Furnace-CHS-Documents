# Yamaha YMU759

这是个2000s初期给手机设计的声音芯片.the Yamaha YMU759 is a sound chip designed for feature phones during the early 2000s.
也叫MA-2it is also known as MA-2.

不幸的是Yamaha并不十分关心这些芯片,寄存器布局完全未知,这意味着YMU759完全不受支持,没有模拟,除了Yamaha的官方模拟器(用于集成在MidRadio中) sadly Yamaha didn't care about these chips too much, and the register specs were completely unavailable, which means the YMU759 is totally unsupported and unemulated besides Yamaha's official emulator for it built into MidRadio.

Furnace可以加载针对这个系统创作的Deflemask模组,但是他不支持任何效果,而且是通过OPL核心模拟的. Furnace is able to load DefleMask modules written for this system; however, it doesn't support any of its effects and is simulated using the OPL core.

## 效果effects

因为芯片被弃用,所以没有任何的支持since this chip is so abandoned, there isn't any support for it.

甚至Deflemask在0.11版本都放弃了支持, 这说明这个芯片被Yamaha自己和社区都是相当冷淡的对待. even DefleMask dropped support for the chip in version 0.11, which just shows how poorly the chip has been treated, both by Yamaha themselves and the community.


嘿, 至少他是引起DefleMask这一想法的火种之一. hey, at least it was the spark that ignited the idea of DefleMask.

## info

这个芯片使用this chip uses the [FM (OPL)](../4-instrument/fm-opl.md) and [通用采样Generic Sample](../4-instrument/sample.md) 乐器编辑器instrument editors.
