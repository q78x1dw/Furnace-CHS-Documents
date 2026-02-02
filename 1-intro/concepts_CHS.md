译者注：许多专有名词没有通行的中文，是作者自译，实际建议使用英文。专有名词一律附有对应英文。有的专有名词译者也不会译，只好保留原文。其实对于这些名词大家不要害怕，知道它对应什么东西即可，使用中就能学会，不像背英语单词那么困难。

# 基本概念与词汇

- a **song** (also called **module**) is a file for a tracker that contains at least one **subsong**.一首**乐曲song**（也叫**模组module**）是一个tracker的文件，它至少含有一首**子乐曲subsong**。<br>*举例说明：植物大战僵尸的BGM其实就是一个module文件，叫做mainmusic.xm(.xm是另一种tracker的格式)，这一个文件(也就是song）里面就包括了十多首音乐，例如grasswalk，zen garden，它们也就是subsong。*
- each Furnace song involves at least one **chip**, an emulation of a specific audio processor.每个furnace的song都使用至少一个**芯片**，这是对某个音源芯片的模拟。

## tracking（使用tracker编曲）

[pattern视图（pattern view）](../3-pattern/README.md) 就像一张包含以下内容的大表格：the **[pattern view](../3-pattern/README.md)** is similar to spreadsheet that displays the following:

- 每个带有标头的列表示一个**通道（channel）**，通道由当前使用的芯片提供each labeled column represents a **channel** of sound provided by the chips in use.
- **音符note**代表开始播放一个声音。在一个通道里同时只能有一个音符在播放。each **note** starts a sound playing. within a channel, only one note can play at a time.
- 每个音符都被分配了一个[乐器instrument](../4-instrument/README.md)，乐器描述这个音符听起来是什么样子。 each note is assigned an **[instrument](../4-instrument/README.md)** which describes what it will sound like.
- 一个**效果effect**是一个能改变播放过程的某些特性的指令。可能是音符的音高，音量（力度），时间和更多。**an **effect** is a command that changes some aspect of playback. it can alter note pitch, volume, timing, and more.
- 一个乐器**宏macro**是一个自动进行的效果序列，它会被用于使用那个乐器的所有音符。an instrument **macro** is an automated sequence of effects that applies to every note of that instrument.
- 在播放过程中，**播放头playhead**向下移动，在pattern视图中向下滚动，触发它遇到的每一个音符。during playback, the **playhead** moves down, scrolling through the pattern view, triggering the notes that it encounters.

## 结构

**order列表order list**是一个更小的表格，描述整首歌曲的结构。 the **order list** is a smaller spreadsheet showing the overall song structure.

- 乐曲由一个order的列表组成。a song is made up of a list of orders.
- **order**是若干个分别用于各个通道的、有编号的pattern的集合。an **order** is a set of numbered patterns used for each channel.
- 每个通道都有它独有的pattern列表each channel has its own unique list of patterns.<font color= #777777> 这一点不同于fasttracker，impulse tracker那些非chiptune的tracker</font>
- 每个**pattern**包含只能用于那个通道的音符与效果数据。each **pattern** contains note and effect data for that channel only.
- 一个pattern可以在order列表里面使用多次。改变一个order里面的一个pattern会同时改变用于其他order的同一个pattern。patterns may be used multiple times in the order list. changing a pattern's data in one order will affect the same pattern used in other orders.
- 每个pattern都由同样多的行（row）数，这个数量可以在tracker视图里面看到。each pattern is made of the same number of rows as seen in the tracker view.
- 在播放期间，**播放头playhead**如前所述地向下移动。如果它移动到pattern 视图的最底下，它就会跳转到下一个order的开始。during playback, the **playhead** moves down as described previously. when it reaches the end of the pattern view, it will go to the next order.
- 如果**播放头playhead**移动到最后一个order的pattern视图的最底端，它就会跳回乐曲的一开始。if the last order is reached and the playhead reaches the end of the pattern view, it will go back to the beginning of the song.

## 时间

- 在播放过程中，每一**行row**的时长都是n个tick，这个n由乐曲的**速度speed**值指定。during playback, each **row** lasts a number of ticks determined by the song's **speed** value(s).
- 一个**tick** *（大意是‘内部时钟周期’或‘滴答’）*是量化所有音符，效果，宏的最小时间单位。（a **tick** is the smallest measure of time to which all note, effect, and macro times are quantized.

## 声音

音源芯片有不同的本领。甚至在同一个芯片里，不同通道用不同的方式产生声音。sound chips have different capabilities. even within the same chip, each channel may have its own ways of making sound.

- 有些通道使用一个或多个波形**发生器**来产生声音。some channels use one or more waveform **generators** (sine, square, noise...) to build up a sound.
  - 特别的，**FM（频率调制）** 通道使用若干个发生器，它们互相合作可以产生很复杂的声音。 of special note are **FM (frequency modulation)** channels, which use a number of generators called **operators** that can interact to make very complex sounds.~~这是译者最喜欢的~~
- 有的通道使用[采样samples](../6-sample/README.md)，（通常）是录制的音频，它们通常定义有循环点loop points，这样能让一个音符保持sustain。some channels use **[samples](../6-sample/README.md)** which are (usually) recordings of sounds, often with defined loop points to allow a note to sustain.
- 有的通道使用波表，它们就是有固定长度的采样，并且总是自动循环。some channels use **[wavetables](../5-wave/README.md)**, which are very short samples of fixed length that automatically loop.
