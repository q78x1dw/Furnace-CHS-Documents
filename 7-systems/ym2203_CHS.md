# Yamaha YM2203 (OPN)

YM2151的廉价修改版. a cost-reduced version of the YM2151 (OPM).
只有3个FM通道而不是8个, 移除了立体声,it only has 3 FM channels instead of 8 and removes stereo, the LFO and DT2 (coarse detune).

但是他包含一个 AY/SSG 部分,有三个通道方波和噪声和包络.however it does contain an AY/SSG part which provides 3 channels of square wave with noise and envelope.

这个芯片在NEC PC-88/PC-98 系列, 富士通FM-7AV和一些街机基板中使用了, this chip was used in the NEC PC-88/PC-98 series of computers, the Fujitsu FM-7AV and in some arcade boards.

这个芯片的几个变体也发布了,有更多的特性. several variants of this chip were released as well, with more features.

## effects

- `11xx`: **设置通道的反馈set feedback of channel.**
- `12xx`: **设置运算器1的TL set operator 1 level.**
- `13xx`: **设置运算器2的TLset operator 2 level.**
- `14xx`: **设置运算器3的TLset operator 3 level.**
- `15xx`: **设置运算器4的TLset operator 4 level.**
- `16xy`: **设置运算器的倍频set multiplier of operator.**
  - `x` 是运算器1到4is the operator from 1 to 4.
  - `y` 是新的MULT值is the new MULT value..
- `18xx`: **切换拓展3通道模式toggle extended channel 3 mode.**
  - `0`禁用,`1`启用 `0` disables it and `1` enables it.
  - 只有在拓展通道3的芯片中.only in extended channel 3 chip.
- `19xx`: **设置所有运算器的起音set attack of all operators.**
- `1Axx`: **设置运算器1的起音 set attack of operator 1.**
- `1Bxx`: **设置运算器2的起音 set attack of operator 2.**
- `1Cxx`: **设置运算器3的起音 set attack of operator 3.**
- `1Dxx`: **设置运算器4的起音 set attack of operator 4.**
- `20xx`: **设置SSG通道模式set SSG channel mode.** `xx` 可以是如下的值 may be one of the following:
  - `0`: 矩形波square
  - `1`: 噪音noise
  - `2`: 矩形波和噪音square and noise
  - `3`: 什么都没有nothing (apparently)
  - `4`: 包络和方波envelope and square
  - `5`: 包络和噪声envelope and noise
  - `6`: 包络和方波和噪声 envelope and square and noise
  - `7`: 什么都没有nothing
- `21xx`: **设置噪声频率set noise frequency.** `xx` 是0到1f之间的值. is a value between 00 and 1F.
- `22xy`: **设置包络模式set envelope mode.**
  - `x` 设置包络形状,可以是如下的值sets the envelope shape, which may be one of the following:
    - `0`: `\___` decay衰减
    - `4`: `/___` attack once起音后静音
    - `8`: `\\\\` saw锯齿波
    - `9`: `\___` decay衰减
    - `A`: `\/\/` inverse obelisco翻转的三角波('方尖碑')
    - `B`: `\¯¯¯` decay once衰减后音量保持最大
    - `C`: `////` inverse saw翻转的锯齿波
    - `D`: `/¯¯¯` attack起音
    - `E`: `/\/\` obelisco三角波('方尖碑')
    - `F`: `/___` attack once起音后静音
  - 如果`y`是1那么包络会影响这个通道.if `y` is 1 then the envelope will affect this channel.
- `23xx`: **设置包络周期低字节set envelope period low byte.**
- `24xx`: **设置包络周期高字节set envelope period high byte.**
- `25xx`: **包络周期上滑slide envelope period up.**
- `26xx`: **包络周期下滑slide envelope period down.**
- `29xy`: **enable auto-envelope mode.启用自动包络模式.**
  - in this mode the envelope period is set to the channel's notes, multiplied by a fraction.这个模式下包络周期会设置为本通道的音高乘上一个系数
  - `x` is the numerator.x是分子
  - `y` is the denominator.y是分母
  - if `x` or `y` are 0 this will disable auto-envelope mode.x或者y为0则停用自动包络模式
- `30xx`: **设置包络硬件复位enable envelope hard reset.**
  - 这通过在新音符之前插入一个快速的释放和小的延迟this works by inserting a quick release and tiny delay before a new note.
- `50xy`: **设置运算器的AM set AM of operator.**
  - `x` 是运算器(1-4). 值0代表"所有运算器"is the operator (1-4). a value of 0 means "all operators".
  - `y` 决定AM是否开启determines whether AM is on.
- `51xy`: **set SL of operator.**
  - `x` 是运算器(1-4). 值0代表"所有运算器"is the operator (1-4). a value of 0 means "all operators".
  - `y` 是值is the value.
- `52xy`: **set RR of operator.**
  - `x` 是运算器(1-4). 值0代表"所有运算器"is the operator (1-4). a value of 0 means "all operators".
  - `y` 是值is the value.
- `53xy`: **set DT of operator.**
  - `x` 是运算器(1-4). 值0代表"所有运算器"is the operator (1-4). a value of 0 means "all operators".
  - `y` 是值is the value:
    - `0`: +0
    - `1`: +1
    - `2`: +2
    - `3`: +3
    - `4`: -0
    - `5`: -3
    - `6`: -2
    - `7`: -1
- `54xy`: **设置运算器的RS set RS of operator.**
  - `x` 是运算器(1-4). 值0代表"所有运算器"is the operator (1-4). a value of 0 means "all operators".
  - `y` 是值is the value.
- `55xy`: **设置运算器的SSG-EG set SSG-EG of operator.**
  - `x` 是运算器(1-4). 值0代表"所有运算器"is the operator (1-4). a value of 0 means "all operators".
  - `y` 是值is the value (0-8).
    - 0-7之间的值设置SSG-EGvalues between 0 and 7 set SSG-EG.
    - 值8禁用value 8 disables it.
- `56xx`: **设置所有运算器的DRset DR of all operators.**
- `57xx`: **set DR of operator 1.**
- `58xx`: **set DR of operator 2.**
- `59xx`: **set DR of operator 3.**
- `5Axx`: **set DR of operator 4.**
- `5Bxx`: **设置所有运算器的D2R/SRset D2R/SR of all operators.**
- `5Cxx`: **设置运算器1的D2R/SR set D2R/SR of operator 1.**
- `5Dxx`: **set D2R/SR of operator 2.**
- `5Exx`: **set D2R/SR of operator 3.**
- `5Fxx`: **set D2R/SR of operator 4.**
- `60xy`: **设置运算器掩码set operator mask.**
  - 启用或禁用运算器enables or disables operators.
  - 如果`x`是`0` ,`y` 从 `0` 到`f`变化,那么他就是一个位掩码, 所以`y`是活跃的运算器的位权之和:if `x` is `0`, `y` ranges from `0` to `F`. it is a bitfield, so `y` is the sum of the active operators' bits:
    - OP1 is +1, OP2 is +2, OP3 is +4, and OP4 is +8.
    - 例如只有OP2 和OP4 会是2+8=10 `xy`值就是 `0A` for example, having only OP2 and OP4 on would be 2 + 8 = 10, resulting in an `xy` value of `0A`.
  - 如果`x`是`1`到`4`, 效果就针对这个运算器:`y`开关这个运算器. `0`是关 `1`是开 if `x` is `1` to `4`, the effect targets that operator; `y` turns it off with a value of `0` and on with a value of `1`.
    - 例如`6031`启用OP3for example, the effect `6031` enables OP3.
- `61xx`: **设置算法set algorithm** (0 to 7).

## 信息info

这个芯片使用this chip uses the [FM (OPN)](../4-instrument/fm-opn.md) 和and [AY-3-8910/SSG](../4-instrument/ay8910.md) 乐器编辑器instrument editor.

## 拓展通道3extended channel 3

在拓展通道模式中, 通到3分裂为每个运算器一个, 反馈是共享的.每个运算器的频率都可以单独控制,通过音符和效果. 这可以创造更多复音或者更加复杂的声音.  in ExtCh mode, channel 3 is split into one column for each of its four operators and feedback are shared. the frequency of each operator may be controlled independently with notes and effects. this can be used for more polyphony or more complex sounds.

所有四个运算器仍然按照算法组合.all four operators are still combined according to the algorithm in use. 例如算法7作为4个独立的正弦波. for example, algorithm 7 acts as four independent sine waves. 算法4作为2个独立的2op声音. algorithm 4 acts as two independent 2op sounds. 甚至使用算法0时,在任意一个运算器触发一个音符都只触发这个运算器他自己. even with algorithm 0, placing a note in any operator triggers that operator alone.

## SSG-EG
(译者:我也不太了解这个)

这是SSG-EG is short for "软件Software-控制的controlled 声音Sound 发生器Generator – 包络Envelope 发生器Generator"的缩写. 他是把AY-3-8910/YM2149 包络发生器作用于每个运算器上面. it is the AY-3-8910/YM2149 envelope generator applied to each individual operator. 他让运算器的包络经历起音,衰减,保持和衰减2,直到他到达0振幅, 这时触发SSG包络. 按照SSG包络不同, 运算器的包络要么循环要么保持, 两种情况都可以设置为波形反转(起音减少, 衰减增加)it makes the operator's envelope play through attack, decay, sustain, and decay 2 until it reaches zero amplitude, at which time SSG triggers. according to the shape of the SSG envelope, the operator's envelope may then either loop or hold, and either of these can be set to invert the envelope (attack decreases and decay increases) when triggered.

一个针对SSG-EG的完全教程在这个文档之上. 想要更多信息,看这个视频: a full guide to SSG-EG is beyond the scope of this documentation. for more information, see this [简易的SSG-EG和CSM 视频教程brief SSG-EG and CSM video tutorial](https://www.youtube.com/watch?v=IKOR0TUlnWU), this [详细的技术解释detailed technical explanation](https://gendev.spritesmind.net/forum/viewtopic.php?t=386&start=106), 这个 and this [调音图示chart of tunings](https://docs.google.com/spreadsheets/d/1HGKQ08CnLGAjA1U0StJFldod3FkQ3uq86rYy1VBIuZc/).

## CSM

CSM, or "复合Composite 正弦波Sine 模式Mode", 采用了一个定时器设置为"CSM 定时器" 通道的频率. 在定时器每次触发, 他都生成按键开和按键关命令来重置通道3上面的所有运算器的相位, 然后迫使他们的包络重置为在释放点重新开始. involves a timer matching the frequency of the note in the "CSM Timer" channel. each time it triggers, it generates key-on and key-off commands to reset the phase of all operators on channel 3 and force their envelopes to restart at the release point. 这可以用于创造语音共振峰(语音合成!) 或者其他的复杂效果. 独立于这个芯片的实现, 这个技巧叫做"oscillator sync". this can be used to create vocal formants (speech synthesis!) or other complex effects. outside this chip's specific implementation, the technique is known as "oscillator sync".

working with CSM is beyond the scope of this documentation. for more information, see this [brief SSG-EG and CSM video tutorial](https://www.youtube.com/watch?v=IKOR0TUlnWU).

## 芯片配置chip config

以下选项在芯片管理器中可以使用.the following options are available in the Chip Manager window:

- **芯片速率Clock rate**: 设置芯片运行速率sets the rate at which the chip will run.
- **输出速率Output rate**: 设置芯片的"预分频器" 让你可以采取更加低的时钟频率. sets the "prescale" parameter of the chip. allows you to run at a lower clock rate.
- **SSG音量SSG Volume**: 设置SSG部分音量sets volume of SSG part.
- **FM音量FM Volume**: 设置FM部分音量sets volume of FM part.
