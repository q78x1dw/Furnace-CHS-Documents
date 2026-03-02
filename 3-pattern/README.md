# pattern

pattern视图让你编辑歌曲的pattern。the pattern view allows you to edit the song's patterns.

![pattern view](pattern.png)

一个pattern包括许多列('通道')和带有行号的行.a pattern consists of columns ("channels") and numbered rows.
每个列都有如下排列的几个子列each column has several subcolumns in this order:

1. 音符note
2. 乐器instrument
3. 音量volume
4. 效果,分为效果类型和效果值.effects, split into effect type and effect value

所有列都用十六进制表示,除了音符列.all columns are represented in hexadecimal, except for the note column.

行的高亮显示拍与小节.row highlights show beats and measures, and are configured in the [the Speed window](../2-interface/song-info.md).



## 光标与选择cursor and selection

你可以通过点击pattern上面的任何位置来改变光标位置you may change the cursor position by clicking anywhere on the pattern.

要想选中区域,就长按鼠标左键不动,然后拖动鼠标到结束的地方再放开左键,完成选择.to select an area, press and hold the left mouse button. then drag the mouse and release the button to finish selection.

在pattern视图里面右键会弹出一个菜单,里面有[edit menu](../2-interface/menu-bar.md)里面的大部分选项.right-clicking within the pattern view brings up a pop-up menu with most options from the [edit menu](../2-interface/menu-bar.md).



## 通道 条channel bar

使用通道条,你可以调整通道显示的几个方面using the channel bar, you may adjust several aspects of the channel display.

![channel bar](channelbar.png)

点击通道名称就会静音这个通道. clicking on a channel name mutes that channel.

双击或者右键就会启用独奏模式, 这时只有这个通道有声音.double-clicking or right-clicking it enables solo mode, in which only that channel will be audible.

点击左上的 `++`就会弹出一个小菜单,可以设置显示模式: clicking the `++` at the top left corner of the pattern view pops up a small menu to set view modes:
- **效果列/收起Effect columns/collapse**: 显示收起通道和增加/减少效果列的附加选项displays extra options for collapsing channels and adding/removing effect columns:
  - **-**: 收起可见的列.当所有列都隐藏后,它变为 **+** ;点击一下以拓展他们.collapse visible columns. changes to **+** when columns are hidden; click to expand them.
  - **<**: 禁用最后一个效果列并且隐藏它. 效果并没有删除disables the last effect column and hides it. effects are not deleted...
  - **>**: 增加一个效果列. 如果已经存在一个效果列,他的内容会被保留.adds an effect column. if one previously existed, its contents will be preserved.
- **Pattern名称Pattern names**: 显示pattern名称(按每个通道).当鼠标停留在order列表中的一个pattern上,pattern名称也显示出来. displays pattern names (per channel). pattern names are also visible when hovering over a pattern in the order list.
- **通道结组提示Channel group hints**: 当通道被以某种形式结合,就显示指示标志.(例如OPL3 4-op模式) display indicators when channels are paired in some way (e.g. OPL3 4-op mode).
- **视觉效果Visualizer**: 在播放过程中在pattern视图显示视觉效果. during playback, show visual effects in the pattern view.
  - 可以通过在`++`按钮上面右键开关also can be toggled by right-clicking on the `++` button.
- **通道状态Channel status**: 显示 指示通道活动状态的图标. displays icons that indicate activity in the channel. 看下文的"通道状态"段落. see the "channel status" section below.

想要重命名 和/或者 隐藏通道,通过窗口菜单打开to rename and/or hide channels, open [通道窗口the Channels window](../8-advanced/channels.md) via the window menu.

### 通道状态channel status

- 音符状态note status:
  - ![note off](status-note-off.png) 音符关note off
  - ![note on](status-note-on.png) 音符开note on
  - ![macro released](status-note-on-rel.png) 音符开但是宏释放note on but macro released (`REL`)
  - ![note released](status-note-off-rel.png) 音符释放note released (`===`)
- 音高变化pitch alteration:
  - ![no effect](status-pitch-none.png) 无效果nothing
  - ![pitch up](status-pitch-up.png) 上滑音pitch slide up
  - ![pitch down](status-pitch-down.png) 下滑音pitch slide down
  - ![portamento](status-pitch-porta.png) 滑音(到某个音符)portamento
  - ![arpeggio](status-pitch-arpeg.png) 琶音arpeggio
- 音量变化volume alteration:
  - ![no effect](status-volume-none.png) 无效果nothing
  - ![volume up](status-volume-up.png) 音量增加volume slide up
  - ![volume down](status-volume-down.png) 音量下降volume slide down
  - ![tremolo](status-volume-tremolo.png) 震音tremolo (音量周期性增减)
- 根据所用的芯片可能显示其他的图标other icons may be present depending on the used chips.


## 输入input

### 音符输入note input

![键盘keyboard](keyboard.png)

- 按下任何一个对应音符的按键就会在光标处插入一个音符,然后移动到下一行pressing any of the respective keys will insert a note at the cursor's location, then advance to the next row (或者根据编辑步长移动or otherwise according to the Edit Step.)
- **音符关note off** (`OFF`) 关闭这个通道里最后一个播放的音符turns off the last played note in that channel (FM/硬件包络中的按键关, 其他芯片中的音符剪切)key off for FM/hardware envelope; note cut otherwise).
- **音符释放note release** (`===`) 触发宏释放triggers macro release (在FM/硬件包络通道他也触发按键关 and in FM/hardware envelope channels it also triggers key off).
- **宏释放macro release** (`REL`) 同上,但是在FM/硬件包络通道他不触发按键关does the same as above, but does not trigger key off in FM/hardware envelope channels.
- **切换编辑toggle edit** 启用或禁用编辑.当编辑被启用,光标行有红色阴影enables and disables editing. when editing is enabled, the cursor's row will be shaded red.

### 乐器/音量输入instrument/volume input

输入任何十六进制type any hexadecimal number (0-9 and A-F). 光标会按照编辑步长移动 当输入了一个合适的值the cursor will move by the Edit Step when a suitable value is entered.

### 效果输入effect input

就像乐器/音量输入works like the instrument/volume input.

每个效果列都有两个子列: 效果 和 效果值.each effect column has two subcolumns: effect and effect value.
如果效果值不存在,他被当成`00`if the effect value is not present, it is treated as `00`.

大部分效果都一直运行 直到被一个有同样类型且值为`00` 的效果终止, 这有几个例外.most effects run until canceled using an effect of the same type with effect value `00`, with some exceptions.

这里是here's [效果类型的列表a list of effect types](effects.md).



## 快捷键keyboard shortcuts

这些是默认的键盘快捷键.所有快捷键都在设置窗口里面可以设置.these are the default key functions. all keys are configurable in the Keyboard tab of the Settings window.

key         | action
------------|-----------------------------------------------------------------
Up/Down     | 向上/向下移动一行或者一个Edit Step.move cursor up/down by one row or the Edit Step (configurable)
Left/Right  | 向左或向右移动光标move cursor left/right
PageUp      | 向上移动16行move cursor up by 16 rows
PageDown    | 向下移动16行move cursor down by 16 rows
Home        | 移动到pattern的开始move cursor to beginning of pattern
End         | 移动到pattern的结尾move cursor to end of pattern
Shift-Home  | 向上移动一行,与Edit Step无关.move cursor up by exactly one row, overriding Edit Step
Shift-End   | 向下移动一行,与Edit Step无关.move cursor down by exactly one row, overriding Edit Step
Shift-Up    | 向上扩展选区expand selection upwards
Shift-Down  | 向下扩展选区expand selection downwards
Shift-Left  | 向左扩展选区expand selection to the left
Shift-Right | 向右扩展选区expand selection to the right
Alt-Up      | 选区向上移动一行move selection up by one
Alt-Down    | 选区向下移动一行move selection down by one
Alt-Left    | 将选区移动到左边通道move selection to previous channel
Alt-Right   | 将选区移动到右边通道move selection to next channel
Backspace   | 删除光标下的音符并将之后的pattern部分上移delete note at cursor and/or pull pattern upwards (configurable)
Delete      | 删除选区delete selection
Insert      | 创建空白行并把pattern的之后部分下移.create blank row at cursor position and push pattern
Ctrl-A      | 自动扩展选区(选中所有)auto-expand selection (select all)
Ctrl-X      | 剪切选区cut selection
Ctrl-C      | 复制选区copy selection
Ctrl-V      | 粘贴选区paste selection
Ctrl-Z      | 撤销undo
Ctrl-Y      | 重做redo
Ctrl-F1     | 选区变调(+1半音)transpose selection (-1 semitone)
Ctrl-F2     | 选区变调(-1半音)transpose selection (+1 semitone)
Ctrl-F3     | 选区变调(-1八度)transpose selection (-1 octave)
Ctrl-F4     | 选区变调(+1八度)transpose selection (+1 octave)
Space       | 开关音符输入(编辑)toggle note input (edit)
