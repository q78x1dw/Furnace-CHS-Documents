# 常见术语的词汇

**2-op**, **3-op**, **4-op**...: 用于生成声音的FM运算器operators的数量。更多运算器operators可以产生更复杂的声音。FMthe number of FM operators used to generate a sound. more operators allow for more complex sounds.

**ADPCM**: 自适应差分PCM（PCM=pulse code modulation脉冲编码调制）。这是DPCM的一个变体，用更复杂的方式记录幅值的变化。adaptive differential pulse code modulation. this is a variety of DPCM with a more complex method of storing the amplitude differences.

**ADSR**: 起音，衰减，保持和释放。他们是组成一个基本包络的元素。attack, decay, sustain and release. these are elements that comprise a basic envelope.

**算法algorithm**: FM乐器中运算器operator相互组合连接的方式。the way in which the operators in an FM instrument interact.

- 当两个运算器连接到同一点，他们的声音输出被相加。when two operators connect to the same point, their sounds are added together.
- 当两个运算器中，左边的一个接到右边的另一个，左边的是调制器modulator，右面的是被调制的载波器carrier。when two operators are connected left to right, the left is the modulator and the right is the carrier sound that is modified.

**asset*不会翻译***: 一个乐器，波表或采样an instrument, wavetable or sample.

**位、比特bit**: 一个单独的二进制的开关值a single binary on-off value.

**bitbang*不会翻译***:为了实现PCM的效果，强行向一个非PCM通道快速发送音量指令的流。~~（译者瞎编的词：‘灌位’）~~ to achieve PCM sound by sending a rapid stream of volume commands to a non-PCM channel.

**位深bit depth**:在PCM流里面用于每个采样的bit的数量。一般认为16bit就是高音质了。位深更浅的话会引起更多噪音与失真，对于音量小的采样更是如此。 the number of bits used for each sample in a PCM stream. 16-bit is considered high quality; lower bit depths introduce more noise and distortion, especially for quieter samples.

- ‘1-bit DPCM’采样类型有7bit的值，但是每个采样点都只用1位记录它相比上一个采样点是上升一阶还是下降一阶。the "1-bit DPCM" sample type has 7-bit values, but each sample is represented by only 1 bit indicating whether its value differs from the previous sample by one step up or down.

**位掩码bitmask**:一组bit，它们代表独立的一bit一bit的开关，或者是更小的代表小数字的bit的组合。它们在 [十六进制知识](hex.md)讲到了。a set of bits which represent individual single-bit toggles or groups representing small numbers. these are explained fully in the [hexadecimal primer](hex.md).

**BRR**: 一种SNES使用的有损压缩采样格式。有一个固定的压缩比例。每32字节（16采样）被压缩成9字节。a lossy sample format used by the SNES. it has a fixed compression ratio; groups of 32 bytes (16 samples) are encoded in 9 bytes each.

- 一般以`.brr`文件存储。usually stored in `.brr` files.

**削波clipping**:当采样或回放流超越了最大或最小值。这会造成明显可听到的失真。 when a sample or playback stream exceeds the maximum or minimum values. this can cause audible distortion.

- 一般出现在一个采样被过度放大时this often occurs when a sample is amplified too much.
- 也可能出现在回放时过多声音被叠加到一起。有时可以使用混音器减小音量。这也没用的话，削波发生在芯片自己的混音器，只能把播放的音符的音量降低。it can also occur during playback if too much sound is being added together at once. in some cases the mixer can be used to reduce the volume. if this doesn't work, the clipping is caused within the chip's own mixing, and the only solution is to reduce the volumes of the notes being played.

**时钟速率clock rate**:芯片进行操作的时机。用每秒周期数（赫兹，Hz）表示。 the timing at which a chip operates, expressed as cycles per second (Hz).

- 改变它可能改变某些芯片工作的某些方面，最显著的就是音调。changing this may change aspects of how some chips work, most notably pitch.
- some chips cannot operate at anything other than their designed clock rate.

**光标cursor** (1): 输入焦点的标记。键盘输入的任何内容会发生在光标的位置。the marker of input focus. anything typed will happen at the cursor's location.

**光标cursor** (2): 由鼠标或类似指点设备控制的指针。当光标(2)处于可用区域时，点击会把光标(1)置于此处。the pointer controlled by a mouse or similar input. clicking when the cursor(2) is in a valid area will place the cursor(1) there.

**DAC**: 数字到模拟转换器。digital analog converter. 这把声音的数字信号表示转换成实际的输出。this converts a digital representation of sound into actual output.

**`.dmf`**: Deflemask 模组（Module）文件DefleMask Module File.

- _Furnace:_ 可以读取`.dmf`文件，这时会置位兼容性标记以让它们尽可能准确播放。但是仍可能有小问题。`.dmf` files may be read, and compatibility flags will be set to make them play as accurately as possible, but there may still be glitches.
- _Furnace:_ 可以保存`.dmf`文件但不能保证完全兼容，会丢失许多特性。除非走投无路，不建议使用。`.dmf` files may be saved, but full compatibility isn't guaranteed and many features will be missing. this isn't recommended unless absolutely necessary.

**`.dmp`**: Deflemask预设。一种乐器文件。DefleMask Preset. an instrument file.

**`.dmw`**:Deflemask波表。一种波表文件。 DefleMask Wavetable. a wavetable file.

**DPCM**: 差分/Δ（Delta）PCM.这是PCM的一种变体，保存每个幅值相对之前的幅值的不同。differential/delta pulse code modulation. this is a variety of PCM that stores each amplitude as its difference from the previous.

**占空比duty cycle**:一般也叫*脉冲宽度（脉宽）*。在方波里面，这是高位部分相比高位与低位的总和的占比。 usually called _pulse width._ in a pulse wave, this is the ratio of the high part to the high and low combined.

**反馈feedback**:在FM乐器中它把一个运算器的输出的一部分加回到它自己，用来创造复杂的泛音。 in FM instruments, this adds some of an operator's output into itself to create complex harmonics.

- in the algorithm view, an operator with a circle around it is capable of feedback.

**FM**: 频率调制。这是一种用一个运算器的振幅来调制另一个运算器的频率的产生声音的方法。frequency modulation. this is a method of generating sound that uses one operator's amplitude to modify another operator's frequency.

- 雅马哈的芯片的FM更准确来说是*相位调制Phase Modulation*，用另一种不同的计算方法达到相似的结果。the FM in Yamaha chips is more accurately called _phase modulation,_ which uses a different method of computation to achieve similar results.

**`.ftm`**: FamiTracker Module.

**`.fui`**: 一个Furnace乐器文件a Furnace instrument file.

**`.fur`**: 一个Furnace模组module文件。a Furnace module file.

**`.fuw`**: 一个Furnace波表文件。a Furnace wavetable file.

**硬声像hard-pan**: 声音的声像只能设为中间，100%左声道，100%右声道。这经常在乐器编辑器里的声像（panning）宏作为开关出现，分别控制左右声道sounds can only be panned to the center, 100% left, or 100% right. this often appears in the instrument editor's panning macro as on/off toggles for the left and right channels.

**Hz**: 赫兹，一个记录每秒的次数的单位。1Hz是每秒1次，100Hz是每秒100次。也有*kHz*（千赫兹，每秒1000次）和*MHz*（兆赫兹，每秒1000,000次）这两种单位。hertz. a unit representing divisions of one second. 1 Hz means once per second; 100 Hz means one hundred times per second. also, _kHz_ (kilohertz, one thousand per second) and _MHz_ (megahertz, one million per second).

**插值interpolate**:用中间值或平滑的斜坡填充两个值之间的区域。 to fill in the area between two values with a smooth ramp of values in between.

- 有的采样芯片可以插值，滤除不想要的泛音。some sample-based chips can interpolate, filtering out unwanted harmonics.

**`.it`**: Impulse Tracker 模组module.

**阶梯效应ladder effect**:一个不太准确但常见的术语，用于描述某些雅马哈FM芯片的DAC失真。 an inaccurate yet common term for the DAC distortion that affects some Yamaha FM chips.

**LFO**: 低频振荡器。一个有很慢的周期（一般低于人耳可听范围）的波，用于改变其他的声音。low frequency oscillator. a wave with a slow period (often below hearing range) used to alter other sounds.

**LFSR**: 线性反馈移位寄存器。一个能生成循环的伪随机噪声的方法。也叫‘周期性噪声’。在一个开关比特的序列里，它把位于特殊位置（叫做‘tap’）的位结合起来，然后向左位移整个序列，把作为结果的比特添加到序列最后，保证下一次流程时序列状态与上次不同。当tap的位置不同，生成的噪音周期也不同。当周期很短，这会改变它们的音调。linear-feedback shift register. a method to generate pseudo-random noise that loops, also known as "periodic noise". within a sequence of on-off bits, it does math to combine the bits at specified locations called "taps", then shifts the whole sequence and adds the resulting bit on the end, guaranteeing a different state for the next pass. depending on the locations of the taps, different lengths of noise loops are generated; for short loops, this will affect their tone.

**宏macro**: 一个音符播放时自动应用于音符的值的序列。a sequence of values automatically applied while a note plays.

**噪音贝斯noise bass**: 用PSG的周期性噪音发生器配合很短的周期来产生低频声音的技巧。the technique of using a PSG's periodic noise generator with a very short period to create low-frequency sounds.

**标准化normalize**:放大一个采样，使其音量大且恰好不削波。 to adjust the volume of a sample so it is as loud as possible without adding distortion from clipping.

**运算器/算子operator**: 在FM中一个能与其它振荡器配合产生声音的振荡器。in FM, a single oscillator that interacts with other oscillators to generate sound.

**振荡器oscillator**: 一个正弦波或其他基本的波形，用作声音或者是用于改变声音。a sine wave or other basic waveform used as sound or to alter sound.

**PCM**: 脉冲编码调制。一个数据流，它通过快速的振幅序列表示声音。pulse code modulation. a stream of data that represents sound as a rapid sequence of amplitudes.

**周期period**: 重复波形的长度。频率提高周期就变短。the length of a repeating waveform. as frequency rises, the period shortens.

**周期性噪音periodic noise**: an approximation of random noise generated algorithmically with an LFSR.

- 周期是算法重复它自己之前输出的值的数量。the period is the number of values generated until the algorithm repeats itself.

**相位重置phase reset**:回到一波形最开始的值重新启动它。 to restart a waveform at its initial value.

- 对FM乐器这也会重置音量包络。for FM instruments, this restarts the volume envelope also.

**PSG**:可编程声音发生器。任何音源芯片都是一个PSG，尽管这个词一般只指仅仅产生简单波形和噪音的芯片。 programmable sound generator. any sound chip is a PSG, though the term is often used to specifically refer to chips that produce only simple waveforms and noise.

**脉冲波pulse wave**:一种波形，周期内仅仅包含两个幅值，高和低。也叫**方波**（国内常用叫法）。 a waveform with a period consisting of only two amplitudes, high and low. also known as a rectangular wave.

**脉冲宽度（脉宽）pulse width**: 有时叫占空比。在方波里面，这是高位部分相比高位与低位的总和的占比。sometimes called _duty cycle._ in a pulse wave, this is the ratio of the high part to the high and low combined.

**释放release**: 音符不再保持之后的部分，或者是宏停止循环后的部分。通常在音符关之后启用。the part of a note that plays after it's no longer held, or the part of a macro the plays after it stops looping. usually applies at key off.

**重采样resample**:把一个采样转换到一个不同的回放采样率。 to convert a sample to a different playback rate.

- 这是个‘有损’的过程，一般牺牲一些音频质量。除非进一步损失音质，结果不能转换回原始的采样率。this is a "lossy" process; it usually loses some amount of audio quality. the results can't be converted back into the original rate without further loss of quality.
- 以更低采样率重采样减少所需内存的数量，但是损失声音里面的高频率。resampling to a lower rate reduces the amount of memory required, but strips away higher frequencies in the sound.
- 以更高采样率重采样不能恢复丢失的高频率，反而可能会带来不想要的泛音，还占用更多内存。resampling to a higher rate cannot recover missing frequencies and may add unwanted harmonics along with greater memory requirements.

**原始raw**:一个没有文件头的采样或波表文件。当加载这种文件，必须正确设置格式否则读出来的数据狗屁不通。 a sample or wavetable file without a header. when loading such a file, the format must be set properly or it will be a mess.

**寄存器register**: 一个音源芯片内部的内存位置。‘寄存器视图register view’会显示现在所用的所有芯片的相关内存。a memory location within a sound chip. "register view" shows all the relevant memory of all chips in use.

**`.s3m`**: ScreamTracker 3 模组Module.

**采样sample** (1):录制的数字音频。一般使用PCM的某种变体存储。 a digitally recorded sound. usually stored as some variant of PCM.

- 随长度与采样率不同，它们可能会占用很大空间，所以旧系统更多使用短而音质差的采样。these can take up a lot of room depending on length and sample rate, thus older systems tend to use short, lower quality samples.

**采样（点）sample** (2): 从录制的数字音频里面拿出的单独一个值。采样(1)由采样(2)（采样点）构成。a single value taken from a digitally recorded sound. a sample(1) is made up of samples(2).

**有符号signed**: 可能是正或负的数的数码（digital）表示。a digital representation of a number that may be negative or positive.

- 如果一个导入的raw（原始）采样听起来可以辨认但是严重失真，就可能是有符号采样被当成无符号导入，或者是相反的情况。if an imported raw sample sounds recognizable but heavily distorted, it's likely to be unsigned interpreted as signed or vice-versa.

**软件混音software mixing**: 把几个声音通道混合成一个单独的流，送到一个PCM通道。mixing multiple channels of sound down to a single stream to be sent to a PCM channel.

- 这对主机系统的CPU负载很大，很少在游戏里用。this puts a heavy load on the CPU of the host system, so it was rarely used in games.
- *Furnace*:这用于DualPCM和QuadTone。 this is used for DualPCM and QuadTone.

**正方波 *（姑且这么翻译）* square wave**: a wave consisting of only two values, high and low, with equal durations within the wave's period.

- 就是占空比为50%的方波this is equivalent to a pulse wave with a duty of 50%.

**supersaw**:由几列频率稍微不同的锯齿波叠加，以产生合唱效果的声音。 a sound made up of multiple saw waves at slightly different frequencies to achieve a chorusing effect.

**tap**:在LFSR里面一个特定的比特位置。 a specified bit location within an LFSR.

**tick速率tick rate**: 声音引擎向前移动的每秒次数。所有音符与效果都由这个速率量化。the number of times per second that the sound engine moves forward. all notes and effects are quantized to this rate.

- 这通常取决于系统使用的视频帧率，大概是NTSC是60，PAL是50.this usually corresponds to the frame rate the system uses for video, approximately 60 for NTSC and 50 for PAL.

**无符号unsigned**:一个仅能为正的数的数码（digital）表示。 a digital representation of a number that can only be positive.

- 如果一个导入的raw（原始）采样听起来可以辨认但是严重失真，就可能是无符号采样被当成有符号导入，或者是相反的情况。if an imported raw sample sounds recognizable but heavily distorted, it's likely to be signed interpreted as unsigned or vice-versa.

**`.vgm`**: Video Game Music. a file containing the log of data sent to a sound chip during sound playback.

- saving to a `.vgm` file may be compared to "converting text to outlines" or similar irreversible processes. the results cannot be loaded back into the tracker.
- different versions of the VGM format have different capabilities, with trade-offs. older versions may lack chips or features; newer versions may not be compatible with some software.
- samples are stored uncompressed. PCM streams (such as DualPCM) can quickly take up a huge amount of space.

**波形waveform**:一个很短周期的重复声音。 a very short period of repeating sound.

- 最基本的波形是正弦波。其他的波形包括三角波，方波，锯齿波之类的。the most basic waveform is a sine wave. others include triangle, pulse, saw, and the like.

**波表wavetable** (1):一个很短的循环的采样。 a very short looping sample.

**波表wavetable** (2): 一个在单一乐器内按序列使用的波表(1)的有序编组。an ordered group of wavetables(1) used in sequence within a single instrument.

**`.xm`**: e**X**tended Module. the file format of songs made with FastTracker 2.高级Module，用Fasttracker 2制作的音乐格式。

**`.zsm`**: ZSound Music.一种主要用于Commander X16电脑的像VGM的音乐文件。 a VGM-like file meant specifically for the Commander X16 computer.
