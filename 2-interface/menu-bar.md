# 菜单栏menu bar

菜单栏让你从五个菜单选择一个: 文件 编辑 设置 窗口 帮助. the menu bar allows you to select from five menus: file, edit, settings, window and help.

## 文件file

- **新建new...**: 打开新建乐曲对话框,选择一个系统. opens the new song dialog to choose a system.
  - 点击一个系统的名称,然后用它创建一个新歌曲click a system name to create a new song with it.
  - 有的系统有几个变体,这些都出现在同一个组. some systems have several variants, which are inside a group.
- **打开open...**: 打开文件选择器opens the file picker, 让你选择一个要打开的乐曲allowing you to select a song to open.
  - see 见[文件格式file formats](formats.md) furnace可以打开的文件格式的列表. for a list of formats Furnace is able to open.
- **打开最近的open recent**: 包含你之前打开的歌曲的列表contains a list of the songs you've opened before.
  - **清除历史clear history**: 清除文件历史erases the file history.
- **保存save**: 保存目前的歌曲saves the current song.
  - 如果这是一个新建的歌曲或者是一个备份就打开文件选择器.opens the file picker if this is a new song, or a backup.
- **保存为save as...**: 打开文件选择器, 让你以不同的名字保存这个歌曲opens the file picker, allowing you to save the song under a different name.
- **导出export...**: 让你导出歌曲为其他的格式,例如音频文件,VGM和其他. allows you to export your song into other formats, such as audio files, VGM and more. see the [导出export](export.md) 页有更多信息page for more information.
- **管理芯片manage chips**: 打开opens the [芯片管理器Chip Manager](../8-advanced/chip-manager.md) 对话框dialog.
- **恢复备份restore backup**: 恢复一个以前保存的备份restores a previously saved backup.
  - Furnace 保留一首乐曲的最多5个备份.keeps up to 5 backups of a song.
  - 备份目录在the backup directory is located in:
    - Windows: `%USERPROFILE%\AppData\Roaming\furnace\backups`
    - macOS: `~/Library/Application Support/Furnace/backups`
    - Linux/其他other: `~/.config/furnace/backups`
  - 随着你使用furnace这个目录会膨胀this directory grows in size as you use Furnace. 记着周期性删除旧备份来节约空间!remember to delete old backups periodically to save space.
  - **不要把备份系统当作自动保存!do NOT rely on the backup system as auto-save!** 你应该把恢复的备份保存, 因为furnace不保存备份的备份 you should save a restored backup because Furnace will not save backups of backups.
- **退出exit**: 关闭furnacecloses Furnace.

## 编辑edit
*这部分可以在pattern视图点击鼠标右键得到相同的菜单. --译者注*

- **...**: 防止意外点击之后的菜单栏选项, 如果菜单太高了而不能塞进程序窗口,除此之外什么也不做does nothing except prevent accidental clicks on later menu items if the menu is too tall to fit on the program window.
- **撤销undo**: 撤销上一个操作2reverts the last action.
- **重做redo**: 重复你之前撤销的操作repeats what you undid previously.
- **剪切cut**: 把pattern视图目前的选区移动到剪贴板moves the current selection in the pattern view to clipboard.
- **复制copy**: 把pattern视图目前的选区拷贝到剪贴板copies the current selection in the pattern view to clipboard.
- **粘贴paste**: 在光标处插入剪贴板内容inserts the clipboard's contents in the cursor position.
  - 你也可以从OpenMPT粘帖you may be able to paste from OpenMPT as well.
- **特殊粘帖paste special...**: 粘贴特性的变体variants of the paste feature.
  - **粘贴混合paste mix**: 在光标处插入剪贴板内容,但是不擦除占用的空间. inserts the clipboard's contents in the cursor position, but does not erase the occupied region.
  - **粘贴混合paste mix (背景background)**: 同'粘贴混合'但是也不改变已经在那里的内容does the same thing as paste mix, but doesn't alter content which is already there.
  - **随乐器粘帖paste with ins (前景foreground)**: 同粘贴混合但是改变乐器same thing as paste mix, but changes the instrument.
  - **随乐器粘帖paste with ins (背景background)**: 同粘贴混合(背景)但是改变乐器same thing as paste mix (background), but changes the instrument.
  - **重复粘帖paste flood**: 在光标处插入剪贴板内容inserts the clipboard's contents in the cursor position, 并且重复直到遇到pattern的末尾and repeats until it hits the end of a pattern.
  - **溢出粘帖paste overflow**: 粘帖paste, 但是即使粘帖到下一个pattern也不停止.but it will keep pasting even if it runs over another pattern.
- **删除delete**: 清除选区内容clears the contents in the selection.
- **选中所有select all**: 改变选区,使得他覆盖更广的区域changes the selection so it covers a larger area.
  - 如果选区宽,他会选中一行里面所有列if the selection is wide, it will select the rows in a column.
  - 如果选区高,他会选中行.if the selection is tall, it will select the entire column.
  - 如果一行已经被选中了,他会选中整个通道if a column is already selected, it will select the entire channel.
  - 如果一个通道已经被选中,他会选中整个patternif a channel is already selected, it will select the entire pattern.
- **操作掩码operation mask**: 列出哪些列会被列出的操作影响toggles which columns will be affected by the listed operations. [这里有更多信息more information here.](../8-advanced/opmask.md)
- **输入所存input latch**: 决定哪些数据随同音符防止determines which data are placed along with a note. [这里有详情more information here.](../8-advanced/inputlatch.md)
- **音符note/八度octave 上升up/下降down**: 对于目前的选区的音符转调transposes notes in the current selection.
- **values up/down**: changes values in the current selection by ±1 or ±16.
- **transpose**: transpose notes or change values by a specific amount.
- **interpolate**: fills in gaps in the selection by interpolation between values.
- **change instrument...**: changes the instrument number in a selection.
- **gradient/fade...**: replace the selection with a "gradient" that goes from the beginning of the selection to the end.
  - does not affect the note column.
  - **Nibble mode**: when enabled, the fade will be per-nibble (0 to F) rather than per-value (00 to FF).
    - use for effects like `04xy` (vibrato).
- **scale...**: scales values in the selection by a specific amount.
  - use to change volume in a selection for example.
- **randomize**: replaces the selection with random values.
  - does not affect the note column.
  - **Nibble mode**: when enabled, the randomization will be per-nibble (0 to F) rather than per-value (00 to FF).
  - **Set effect:**: only appears when the selection includes an effect column. if enabled, an input box will appear. instead of being randomized, all effect types in the selection will be changed to the value entered.
- **invert values**: `00` becomes `FF`, `01` becomes `FE`, `02` becomes `FD` and so on.
- **flip selection**: flips the selection so it is backwards.
- **collapse/expand amount**: allows you to specify how much to collapse/expand in the next two menu items.
- **collapse**: shrinks the selected contents.
- **expand**: expands the selected contents.
- **collapse pattern**: same as collapse, but affects the entire pattern.
- **expand pattern**: same as expand, but affects the entire pattern.
- **collapse song**: same as collapse, but affects the entire song.
  - it also changes speeds and pattern length to compensate.
- **expand song**: same as expand, but affects the entire song.
  - it also changes speeds and pattern length to compensate.
- **find/replace**: shows [the Find/Replace window](../8-advanced/find-replace.md).
- **clear...**: opens a window that allows you to mass-delete things like songs, unused instruments, and the like.

## 设置settings

- **全屏full screen**: expands the Furnace window so it covers your screen.
- **锁定布局lock layout**: 防止你拖拽/改变停靠窗口的大小, 或者停靠更多窗口. prevents you from dragging/resizing docked windows, or docking more.
- **pattern视觉效果pattern visualizer**: 切换歌曲播放时的pattern视图的粒子特效. toggles pattern view particle effects when the song plays.
- **重置布局reset layout**: 将工作区域恢复默认resets the workspace to its defaults.
- **用户系统user systems...**: 显示用户系统窗口shows the User Systems window. 这在this is detailed in [用户系统文档the User Systems documentation](../8-advanced/user-systems.md)有更多细节.
- **设置settings...**: 显示设置窗口.shows the Settings window. 它们在these are detailed in [设置文档the Settings documentation](settings.md)详细说明了.

## window

所有这些菜单项都打开/隐藏对应的窗口all these menu items show or hide their associated windows.

- 乐曲song
  - **[乐曲注释song comments](../8-advanced/comments.md)**
  - **[乐曲信息song information](song-info.md)**
  - **[子乐曲subsongs](song-info.md)**
  - **[通道channels](../8-advanced/channels.md)**
  - **[芯片管理器chip manager](../8-advanced/chip-manager.md)**
  - **[顺序orders](order-list.md)**
  - **[样式pattern](../3-pattern/README.md)**
  - **[样式pattern 管理器manager](../8-advanced/pat-manager.md)**
  - **[混音器mixer](../8-advanced/mixer.md)**
  - **[兼容性标志compatibility flags](../8-advanced/compat-flags.md)**
- 资产assets
  - **[乐器instruments](../4-instrument/README.md)**
  - **[采样samples](../6-sample/README.md)**
  - **[波表wavetables](../5-wave/README.md)**
  - **[乐器编辑器instrument editor](../4-instrument/README.md)**
  - **[采样编辑器sample editor](../6-sample/README.md)**
  - **[波表编辑器wavetable editor](../5-wave/README.md)**
- 视觉效果visualizers
  - **[示波器oscilloscope](../8-advanced/osc.md)**
  - **[示波器oscilloscope (分通道per-channel)](../8-advanced/chanosc.md)**
  - **[oscilloscope (X-Y)](../8-advanced/xyosc.md)**
  - volume meter
- 拍速tempo
  - **[时钟clock](../8-advanced/clock.md)**
  - **[律动grooves](../8-advanced/grooves.md)**
  - **[速度speed](song-info.md)**
- 调试debug
  - **[日志查看器log viewer](../8-advanced/log-viewer.md)**
  - **[寄存器视图register view](../8-advanced/regview.md)**
  - **[统计数据statistics](../8-advanced/stats.md)**
  - **[内存组成memory composition](../8-advanced/memory-composition.md)**
- **[效果列表effect list](../3-pattern/effects.md)**
- **[播放/编辑控制play/edit controls](play-edit-controls.md)**
- **[钢琴/输入面板piano/input pad](../8-advanced/piano.md)**

## 帮助help

- **effect list**: displays the effect list.
- **debug menu**: this menu contains various debug utilities.
  - unless you are working with the Furnace codebase, it's not useful.
- **inspector**: this option shows the Dear ImGui Metrics/Debugger window.
  - unless you are working with the Furnace codebase, it's not useful.
- **panic**: this resets all chips while the song is playing, effectively silencing everything.
- **about...**: displays the About screen.

at the end of the menu bar, more information may be shown:
- during editing, information about the data under the cursor will be shown here:
  - note or note modifier.
  - instrument number and name.
  - volume in decimal, hex, and percentage.
  - effect type and description.
- during playback, these values will be displayed:
  - `speed/groove @ tick rate (BPM) | order | row | elapsed time`
- if any changes or edits have been made but not yet saved, "modified" will appear.
