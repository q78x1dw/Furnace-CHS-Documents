# 效果列表effect list

有些效果的数字是从Protracker/Fasttracker2借鉴来的.some of the effect numbers are taken from ProTracker / FastTracker 2.

但是,效果都是连续作用的.这意味着,你只要输入这个效果一次,(他就会一直起作用,例如00CC),然后用效果值为00,或者没有设置效果值,的效果来停止它的作用(例如0000或00..).however, effects are continuous (unless specified), which means you only need to type it once and then stop it with an effect value of `00` or no effect value at all.

## 音量volume

- `0Axy`: **音量上滑/下滑Volume slide.**
  - 如果`x`是0那么每个tick音量下滑y.if `x` is 0 then this slides volume down by `y` each tick.
  - 如果`y`是0那么每个tick音量上升x.if `y` is 0 then this slides volume up by `x` each tick.
- `FAxy`: **快速的音量滑动Fast volume slide.** 同上,但是4倍速same as `0Axy` above but 4× faster.
- `F3xx`: **精确音量上滑Fine volume slide up.** same as `0Ax0` but 64× slower.同`0Ax0`,但是只有1/64倍速
- `F4xx`: **精确音量下滑Fine volume slide down.** same as `0A0x`0A but 64× slower.同`0A0x`,但是只有1/64倍速
- `F8xx`: **单tick音量上升Single tick volume up.** 从音量中加上`x`.adds `x` to volume.
- `F9xx`: **单tick音量下降Single tick volume down.** 从音量中减去`x`.subtracts `x` from volume.
  - ---
- `D3xx`: **音量滑动Volume portamento.** 将音量滑动到本行的音量列里面指定的值. `x`是滑动速度.slides the volume to the one specified in the volume column. `x` is the slide speed.
  - 必须同时提供一个音量,这个效果才起作用.a volume _must_ be present with this effect for it to work.
- `D4xx`: **快速音量滑动Volume portamento (fast).** 就像`D3xx`但是4倍速like `D3xx` but 4× faster.
  - ---
- `07xy`: **震音Tremolo.** changes volume to be "wavy" with a sine LFO. `x` is the speed. `y` is the depth.
  - tremolo is downward only.
  - 最大震音深度是-60音量.maximum tremolo depth is -60 volume steps.
  - ---
- `DCxx`: **延迟静音Delayed mute.** 在`xx`个tick之后将通道音量设为0.sets channel volume to 0 after `xx` ticks.

## 音高pitch

- `E5xx`: **设置音高Set pitch.** `00`是-1半音,`80`是基础音高,`FF`接近+1半音.`00` is -1 semitone, `80` is base pitch, `FF` is nearly +1 semitone.
- `01xx`: **音高上滑Pitch slide up.**
- `02xx`: **音高下滑Pitch slide down.**
- `F1xx`: **单个tick音高上滑Single tick pitch up.**
- `F2xx`: **单个tick音高下滑Single tick pitch down.**
  - ---
- `03xx`: **滑音Portamento.** 将当前播放的音高滑动到新的音高.`x`是滑音速度.slides the currently playing note's pitch toward the new note. `x` is the slide speed.
  - 必须同时提供一个音符,这个效果才起作用.a note _must_ be present with this effect for it to work.
  - 效果在滑到新的音符时候自动停止.the effect stops automatically when it reaches the new note.
- `E1xy`: **音符上滑Note slide up.** `x`是速度,`y`是要上滑多少半音`x` is the speed, while `y` is how many semitones to slide up.
- `E2xy`: **Note slide down.** 同上,`y`是要下滑多少半音`x` is the speed, while `y` is how many semitones to slide down.
  - ---
- `EAxx`: **切换连音Toggle legato.** 打开时,新的音符立即改变旧音符的音高,而不是重新开始音符.while on, new notes instantly change the pitch of the currently playing sound instead of starting it over.
- `E6xy`: **快速滑音(兼容性考虑)Quick legato (compatibility).** 在`x`个半音后将音符变调`y`个半音.transposes note by `y` semitones after `x` ticks.
  - 如果`x`在0和7间,那么上升if `x` is between 0 and 7, it transposes up.
  - 如果`x`在8和F间,那么下降.if `x` is between 8 and F, it transposes down.
- `E8xy`: **快速向上滑音Quick legato up**. transposes note up by `y` semitones after `x` ticks.
- `E9xy`: **快速向上滑音Quick legato down**. 将音符向下transposes note down by `y` semitones after `x` ticks.
- `00xy`: **琶音Arpeggio.** 这个效果产生目前音符,目前音符+x半音,目前音符+y半音之间的快速交替.this effect produces a rapid cycle between the current note, the note plus `x` semitones and the note plus `y` semitones.
  - 例如,我们考虑C-3,G-3,D#4组成的和弦,G#3与D#4分别比根音C-3高7,15个半音,对应的琶音效果是`007F`as an example, start with a chord of C-3, G-3, and D#4. the G-3 and D#4 are 7 and 15 semitones higher than the root note, so the corresponding effect is `007F`.
- `E0xx`: **设置琶音速度Set arpeggio speed.** 这设置琶音值之间的tick数.默认是1.this sets the number of ticks between arpeggio values. default is 1.
  - ---
- `04xy`: **颤音Vibrato.** 让音高振荡.`x`是速度,`y`是深度.makes the pitch oscillate. `x` is the speed, while `y` is the depth.
  - 最大颤音深度是±1半音.maximum vibrato depth is ±1 semitone.
- `E3xx`: **设置颤音波形.Set vibrato shape.** `xx`可以是如下的值`xx` may be one of the following:
  - `00`: 正弦波(默认)sine (default)
  - `01`: 正弦波(只有上半部)sine (upper portion only)
  - `02`: 正弦波(只有下半部)sine (lower portion only)
  - `03`: 三角波triangle
  - `04`: 锯齿波上升ramp up
  - `05`: 锯齿波下降ramp down
  - `06`: 方波square
  - `07`: 随机random
  - `08`: 方波(上)square (up)
  - `09`: 方波(下)square (down)
  - `0a`: 半边正弦波(上)half sine (up)
  - `0b`: 半边正弦波(下)half sine (down)
- `E4xx`: **设置颤音幅度Set vibrato range** 单位是1/16半音.in 1/16th of a semitone. 

## 声像panning

并不是所有芯片都支持这些效果.not all chips support these effects.

- `08xy`: **设置声像Set panning.** 分别设置双声道的音量.`x`是左声道,`y`是右声道.changes stereo volumes independently. `x` is the left channel and `y` is the right one.
- `88xy`: **设置后声道声像.Set rear panning.** 分别设置后部双通道的音量.`x`是后部左声道,`y`是后部右声道.changes rear channel volumes independently. `x` is the rear left channel and `y` is the rear right one.
- `81xx`: **设置左声道音量.Set volume of left channel** (从`00`到`ff`) (from `00` to `FF`).
- `82xx`: **设置右声道音量.Set volume of right channel** (from `00` to `FF`).
- `89xx`: **设置后部右声道音量Set volume of rear left channel** (from `00` to `FF`).
- `8Axx`: **设置后部右声道音量Set volume of rear right channel** (from `00` to `FF`).
  - ---
- `80xx`: **设置声像(线性)Set panning (linear).** 这个效果的行为更像其他的tracker.this effect behaves more like other trackers:
  - `00` is left.`00`是左.
  - `80` is center.`80`是正中.
  - `FF` is right.`FF`是右.
- ---
- `83xy`: **声像滑动Panning slide.**
  - 如果`y`是0那么每个tick声像向左滑动`x`.if `y` is 0 then this pans to the left by `x` each tick.
  - 如果`x`是0那么每个tick声像向右滑动`y`.xif `x` is 0 then this pans to the right by `y` each tick.
  - 注意:声像的宏会覆盖这个效果.be noted that panning macros override this effect.
- `84xy`: **声像振荡Panbrello.** 让声像振荡.`x`是速度,`y`是深度.makes panning oscillate. `x` is the speed, while `y` is the depth.
  - 注意:声像的宏会覆盖这个效果.be noted that panning macros override this effect.

## time

- `09xx`: **Set speed/groove.** if no grooves are defined, this sets speed. if alternating speeds are active, this sets the first speed.
- `0Fxx`: **Set speed 2.** during alternating speeds or a groove, this sets the second speed.
  - ---
- `Cxxx`: **设置tick速率.将tick速率设置为`xxx`Hz.(每秒tick数)Set tick rate.** changes tick rate to `xxx` Hz (ticks per second).
  - `xxx` 可以在`000`和`3ff`之间取值.may be from `000` to `3FF`.
- `F0xx`: **设置BPM.Set BPM.** 将tick速率设置为`xx`BPM.范围`01`到`ff`.changes tick rate according to beats per minute. range is `01` to `FF`.
  - ---
- `FDxx`: **设置虚拟拍速分子Set virtual tempo numerator.** 将效果值设置为虚拟拍速的分子.sets the virtual tempo's numerator to the effect value.
- `FExx`: **设置虚拟拍速的分母Set virtual tempo denominator.** 将效果值设置为虚拟拍速的分母.sets the virtual tempo's denominator to the effect value.
  - ---
- `0Bxx`: **跳到order.Jump to order.** `x`是目前的行播放完后要播放的order.`x` is the order to play after the current row.
  - 这标志着循环的结束(如果用order x 作为循环的开始)this marks the end of a loop with order `x` as the loop start.
- `0Dxx`: **跳到下一个patternJump to next pattern.** 跳过目前的行以及目前order的剩余部分.`x`是要从下一个pattern的那一行开始播放.skips the current row and remainder of current order. `x` is the row at which to start playing the next pattern.
  - 这可以缩短目前的order的长度,如果pattern太长了.this can be used to shorten the current order as though it had a different pattern length.
- `FFxx`: **停止曲目Stop song.** 停止播放,结束曲目.`x`被忽略.stops playback and ends the song. `x` is ignored.

## 音符note

- `0Cxx`: **重新触发Retrigger.** 每隔`xx`tick就触发一次目前的音符.repeats current note every `xx` ticks.
  - this effect is not continuous; it must be entered on every row.
- `ECxx`: **音符剪切Note cut.** 在FM/硬件包络芯片中触发'按键关',在其他地方就直接切断音符.triggers note off after `xx` ticks. this triggers key off in FM/hardware envelope chips, or cuts note otherwise.
- `EDxx`: **音符延迟Note delay.** 延迟音符`x`个tick.delays note by `x` ticks.
- `FCxx`: **音符释放Note release.** 在`xx`tick后释放目前的音符,这释放宏并且在FM/硬件包络芯片中触发'按键关'.releases current note after `xx` ticks. this releases macros and triggers key off in FM/hardware envelope chips.
- `E7xx`: **宏释放Macro release.** 在`xx`个tick之后释放宏.这并不会触发按键关.releases macros after `xx` ticks. this does not trigger key off.

## 采样偏移sample offset

这些效果让目前在本通道播放的采样跳到一个指定的位置.these effects make the current playing sample on the channel jump to a specific position.
只有某些芯片支持这个效果.only some chips support this effect.

采样偏置是一个24位(3字节)数字.sample offset is a 24-bit (3 byte) number.

- `90xx`: **Set sample offset (first byte).**
- `91xx`: **Set sample offset (second byte).**
- `92xx`: **Set sample offset (third byte).**

你可以在同一行里面使用这些效果.you may use these effects simultaneously in a row.

如果不设置字节,那么就采用上一个值.if you do not set a byte, its last value will be used.

在之前版本的Furnace中,`9xxx`效果将采样位置设置到`$xxx00`(`xxx`被乘256).但是他的效果现在映射到`920x 91xx`. in previous versions of Furnace a `9xxx` effect existed which set the sample position to `$xxx00` (`xxx` was effectively multiplied by 256). this maps to `920x 91xx` in current Furnace.

## 其他other

- `EBxx`: **设置旧式采样模式的库Set LEGACY sample mode bank.** 选择采样库,只用于兼容性.selects sample bank. used only for compatibility.
  - 对于Amiga不适用does not apply on Amiga.
- `EExx`: **发送外部指令Send external command.**
  - 这个效果目前不完善.this effect is currently incomplete.
- `F5xx`: **禁用宏Disable macro.**
- `F6xx`: **使能宏Enable macro.**
- `F7xx`: **重新启动宏Restart macro.**
  - see macro table at the end of this document for possible values.

另外,每个芯片都有它自己的宏.additionally, [each chip has its own effects](../7-systems/README.md).

## 宏表macro table

 | ID   | 宏macro                        |
 | ---- | ------------------------------ |
 | `00` | 音量volume                     |
 | `01` | 琶音arpeggio                   |
 | `02` | 占空比/噪声duty/noise          |
 | `03` | 波形waveform                   |
 | `04` | 音高pitch                      |
 | `05` | 附加1 extra 1                  |
 | `06` | 附加2 extra 2                  |
 | `07` | 附加3 extra 3                  |
 | `08` | 附加A(ALG)extra A (ALG)        |
 | `09` | 附加B(FM)extra B (FM)          |
 | `0A` | 附加C(FMS)extra C (FMS)        |
 | `0B` | 附加D(AMSextra D (AMS)         |
 | `0C` | 左声像panning left             |
 | `0D` | 右声像panning right            |
 | `0E` | 相位重置phase reset            |
 | `0F` | 附加4 extra 4                  |
 | `10` | 附加5 extra 5                  |
 | `11` | 附加6 extra 6                  |
 | `12` | 附加7 extra 7                  |
 | `13` | 附加8 extra 8                  |
 |      | **运算器1宏operator 1 macros** |
 | `20` | AM                             |
 | `21` | AR                             |
 | `22` | DR                             |
 | `23` | MULT                           |
 | `24` | RR                             |
 | `25` | SL                             |
 | `26` | TL                             |
 | `27` | DT2                            |
 | `28` | RS                             |
 | `29` | DT                             |
 | `2A` | D2R                            |
 | `2B` | SSG-EG                         |
 | `2C` | DAM                            |
 | `2D` | DVB                            |
 | `2E` | EGT                            |
 | `2F` | KSL                            |
 | `30` | SUS                            |
 | `31` | VIB                            |
 | `32` | WS                             |
 | `33` | KSR                            |
 | `40` | **运算器2宏operator 2 macros** |
 | `60` | **运算器3宏operator 3 macros** |
 | `80` | **运算器4宏operator 4 macros** |

对于占空比,波形和额外的宏的解释依赖于芯片/乐器类型.the interpretation of duty, wave and extra macros depends on chip/instrument type:

| ex  | FM               | OPM               | OPZ                | OPLL     | AY-3-8910  | AY8930     | Lynx     | C64                     |
| --- | ---------------- | ----------------- | ------------------ | -------- | ---------- | ---------- | -------- | ----------------------- |
| D   | NoiseF噪音频率   | NoiseFreq噪声频率 |                    |          | NoiseFreq  | NoiseFreq  | Duty/Int | Duty 占空比             |
| W   |                  | LFO Shape LFO波形 | LFO Shape          | Patch(?) | Waveform   | Waveform   |          | Waveform波形            |
| 1   |                  | AMD 振幅调制深度  | AMD                |          |            | Duty       |          | FilterMode滤波器模式    |
| 2   |                  | PMD  频率调制深度 | PMD                |          | Envelope   | Envelope   |          | Resonance共鸣           |
| 3   | LFOSpd LFO速度   | LFO Speed         | LFO Speed          |          | AutoEnvNum | AutoEnvNum |          | Filter Toggle滤波器开关 |
| A   | ALG算法          | ALG               | ALG                |          | AutoEnvDen | AutoEnvDen |          | Cutoff截止频率          |
| B   | FB反馈           | FB                | FB                 |          |            | Noise AND  |          |                         |
| C   | FMS频率调制速度  | FMS               | FMS                |          |            | Noise OR   |          |                         |
| D   | AMS振幅调制速度  | AMS               | AMS                |          |            |            |          |                         |
| 4   | OpMask运算器开关 | OpMask            |                    |          |            |            |          | Special特殊             |
| 5   |                  |                   | AMD2第二个LFO,同上 |          |            |            |          | Attack起音              |
| 6   |                  |                   | PMD2               |          |            |            |          | Decay衰减               |
| 7   |                  |                   | LFO2Speed          |          |            |            |          | Sustain保持             |
| 8   |                  |                   | LFO2Shape          |          |            |            |          | Release释放             |

| ex  | SAA1099      | X1-010          | Namco 163  | FDS       | Sound Unit | ES5506    | MSM6258  |
| --- | ------------ | --------------- | ---------- | --------- | ---------- | --------- | -------- |
| D   |              |                 | Wave Pos   |           | Duty       | Filt Mode | FreqDiv  |
| W   | Waveform波形 | Waveform波形    | Waveform   | Waveform  | Waveform   |           |          |
| 1   | Envelope包络 | EnvMode包络模式 | WaveLen    | Mod Depth | Cutoff     | Filter K1 | ClockDiv |
| 2   |              | Envelope包络    | WaveUpdate | Mod Speed | Resonance  | Filter K2 |          |
| 3   |              | AutoEnvNum      | WaveLoad W |           | Control    | Env Count |          |
| A   |              | AutoEnvDen      | WaveLoad P |           |            | Control   |          |
| B   |              |                 | WaveLoad L |           |            |           |          |
| C   |              |                 | WaveLoad T |           |            |           |          |
| D   |              |                 |            |           |            |           |          |
| 4   |              |                 |            |           | PResetTime | EnvRampL  |          |
| 5   |              |                 |            |           |            | EnvRampR  |          |
| 6   |              |                 |            |           |            | EnvRampK1 |          |
| 7   |              |                 |            |           |            | EnvRampK2 |          |
| 8   |              |                 |            |           |            | Env Mode  |          |

| ex  | QSound       | SNES      | MSM5232   | SID2          |
| --- | ------------ | --------- | --------- | ------------- |
| D   | Echo Level   | NoiseFreq | GroupCtrl | Duty          |
| W   |              | Waveform  |           | Waveform      |
| 1   | EchoFeedback | Special   | GroupAtk  | Filter mode   |
| 2   | Echo Length  | Gain      | GroupDec  | Resonance     |
| 3   |              |           | Noise     | Filter toggle |
| A   |              |           |           | Filter cutoff |
| B   |              |           |           |               |
| C   |              |           |           | Noise mode    |
| D   |              |           |           | Wave mix mode |
| 4   |              |           |           | Special       |
| 5   |              |           |           | Attack        |
| 6   |              |           |           | Decay         |
| 7   |              |           |           | Sustain       |
| 8   |              |           |           | Release       |


SID3乐器也使用主要宏表中的一些FM运算器的宏.SID3 instrument also uses some of the FM operators macros in main macros list:

| ex     | SID3                     |
| ------ | ------------------------ |
| D      | Duty                     |
| W      | Waveform                 |
| 1      | Special                  |
| 2      | Attack                   |
| 3      | Decay                    |
| A      | Special wave             |
| B      | Phase Mod source         |
| C      | Ring Mod source          |
| D      | Hard sync source         |
| 4      | Sustain                  |
| 5      | Sustain rate             |
| 6      | Release                  |
| 7      | LFSR feedback bits       |
| 8      | Wave mix mode            |
| OP1 AM | Key On/Off               |
| OP2 AM | Noise phase reset        |
| OP3 AM | Envelope reset           |
| OP4 AM | Noise Arpeggio           |
| OP1 AR | Noise Pitch              |
| OP2 AR | 1-bit noise/PCM mode     |
| OP3 AR | Channel signal inversion |
| OP4 AR | Feedback                 |

SID3乐器使用FM运算器宏作为滤波器宏.ID3 instrument uses FM operators macros for filters:

| ex  | SID3                      |
| --- | ------------------------- |
| D2R | Cutoff                    |
| DAM | Resonance                 |
| DR  | Filter toggle             |
| DT2 | Distortion level          |
| DT  | Output volume             |
| DVB | Connect to channel input  |
| EGT | Connect to channel output |
| KSL | Connection matrix row     |
| KSR | Filter mode               |
