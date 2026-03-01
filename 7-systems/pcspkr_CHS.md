# PC Speaker蜂鸣器

40年的单调的方波蜂鸣 - 并且还在继续! 单通道,没有音量控制... 40 years of one square beep - and still going! single channel, no volume control...

## 真实输出real output

目前这是furnace仅有的有真实硬件输出选项的设备.so far this is the only chip in Furnace which has a real hardware output option.
为了启用它,选择文件>配置芯片>PC蜂鸣器>使用系统蜂鸣器to enable it, select file > configure chip... > PC Speaker > Use system beeper.

注意这只在linux有效,因为Windows不提供用户空间直接操控PC蜂鸣器的API! be noted that this will only work on Linux as Windows does not provide any user-space APIs to address the PC speaker directly!

you may configure the output method by going in Settings > Emulation > PC Speaker strategy:

- `evdev SND_TONE`: uses input events to control the beeper.
  - requires write permission to `/dev/input/by-path/platform-pcspkr-event-spkr`.
  - is not 100% frequency-accurate as `SND_TONE` demands frequencies, but Furnace uses raw timer periods...
- `KIOCSOUND on /dev/tty1`: sends the `KIOCSOUND` ioctl to control the beeper.
  - may require running Furnace as root.
- `/dev/port`: writes to `/dev/port` to control the beeper.
  - requires read/write permission to `/dev/port`.
- `KIOCSOUND on standard output`: sends the `KIOCSOUND` ioctl to control the beeper.
  - requires running Furnace on a TTY.
- `outb()`: uses the low-level kernel port API to control the beeper.
  - requires running Furnace as root, or granting it `CAP_SYS_RAWIO` to the Furnace executable: `sudo setcap cap_sys_rawio=ep ./furnace`.

真正的硬件输出只在BIOS/UEFI(不是Mac)x86机器上可用! 在其他的设备上面使用这个**没有用** 甚至会让设备变砖(使用`/dev/port`或者`outb()`)! real hardware output only works on BIOS/UEFI (non-Mac) x86-based machines! attempting to do this under any other device **will not work**, or may even brick the device (if using `/dev/port` or `outb()`)!
oh, and of course you also need the beeper to be present in your machine. some laptops connect the beeper output to the built-in speakers (or the audio output jack), and some other don't do this at all.

## effects

哈哈! 效果吗...ha! effects...

## 信息info

这个芯片使用this chip uses the [Beeper](../4-instrument/beeper.md) 乐器编辑器instrument editor.

## ROM导出ROM export

有两个ROM导出选项two ROM export options exist:

- **iPod .tone 铃声alarm**: 当iPod在*磁盘模式*将导出的文件拖拽到`iPod_Control/Tones`文件夹.with the iPod _in disk mode,_ drag the export file into the `iPod_Control/Tones` folder.
- **GRUB_INIT_TUNE**: 与GRUB 启动管理器一同使用. use with the GRUB bootloader.
  - 在文件`/etc/default/grub`添加这样一行然后`text`替换为输出的文本:into the file `/etc/default/grub` add the following line with the text output copied and pasted where `text` is:\
    `GRUB_INIT_TUNE="text"`\
    then regenerate GRUB config.
  - **导出二进制文件export binary file**: 创建一个二进制文件而不是文本. 在GRUB shell 或者 GRUB config 文件里面使用 `play` 命令加上导出的文件名称. creates a binary file instead of text. in either the GRUB shell or the GRUB config file, use the `play` command followed by the exported file's name.

## 芯片配置chip config

下面的配置在芯片管理器中可用the following options are available in the Chip Manager window:

- **时钟速率Clock rate**: sets the rate at which the chip will run.
- **Speaker type**: select which speaker to use:
  - **Unfiltered**: raw square wave.
  - **锥体Cone**: 使用滤波器使得他听起来像圆锥形喇叭filter it to simulate the sound of a cone speaker.
  - **压电Piezo**: simulate the tiny speaker present in most PCs from the 2000s.
  - **使用Use system beeper**: 使用你的机器上的真正的蜂鸣器. 只在linux上面有用!use the actual PC speaker in your machine for output. only works on Linux!
- **频率变化时重置相位Reset phase on frequency change**: reset phase every time the frequency changes. 许多现代主板会这么做.many modern motherboards tend to do this.
