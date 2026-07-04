# Sibelius Practice Track Exporter / Sibelius 练习音轨导出器

Batch-export rehearsal and practice tracks from a Sibelius score. It is designed for a cappella preparation workflows where you need one track per staff, optional percussion/VP grouping, and a full mix.

用于从 Sibelius 乐谱批量导出排练/练习音轨，适合阿卡贝拉资料准备：每个 staff 一条练习音轨，可选打击乐/VP 编组，并可额外导出 FullMix。

## Plugins / 插件

- `ExportDimPracticeTracks.plg`: GUI version. Recommended for most users.
- `ExportDimPracticeTracksNoGUI.plg`: stable no-GUI version. Settings are edited at the top of the plugin code.

- `ExportDimPracticeTracks.plg`：图形界面版，推荐大多数用户使用。
- `ExportDimPracticeTracksNoGUI.plg`：稳定无界面版，通过修改插件代码顶部变量来配置。

## Features / 功能

- Export one audio file per staff.
- Export MP3 by default, or WAV if selected.
- Keep the current target staff at `NotMuted`.
- Set other staves to `HalfMuted` or `Muted`.
- Detect percussion staves by Sibelius instrument type, not by staff name.
- Create up to three custom groups from detected staff names.
- Optionally skip individual exports for grouped staves.
- Export an optional `FullMix`.
- Export into a subfolder such as `Practice Tracks`.
- Skip existing files or auto-number existing filenames.

- 按 staff 逐条导出音频。
- 默认导出 MP3，也可选择 WAV。
- 当前目标 staff 保持 `NotMuted`。
- 其他 staff 可设为 `HalfMuted` 或 `Muted`。
- 通过 Sibelius 乐器类型识别打击乐 staff，而不是依赖 staff 名字。
- 可从识别到的 staff 名称中创建最多 3 个自定义编组。
- 可选择“编组后不单独导出组内 staff”。
- 可额外导出 `FullMix`。
- 可导出到 `Practice Tracks` 等子文件夹。
- 可跳过已有文件或自动加编号。

## Installation / 安装

1. Download the latest release ZIP, or clone this repository.
2. Copy the `.plg` files from `plugins/` into your Sibelius user plugin folder.
3. Restart Sibelius.
4. Open the plugin from the Sibelius Plug-ins menu.

macOS user plugin folder:

```text
/Users/<your-user-name>/Library/Application Support/Avid/Sibelius/Plugins
```

Recommended category folder:

```text
/Users/<your-user-name>/Library/Application Support/Avid/Sibelius/Plugins/Batch Processing
```

If you use a localized Sibelius category name, you may also place the files in a category folder such as `批处理`.

1. 下载最新版 release ZIP，或克隆本仓库。
2. 将 `plugins/` 里的 `.plg` 文件复制到 Sibelius 用户插件目录。
3. 重启 Sibelius。
4. 在 Sibelius 插件菜单中运行。

macOS 用户插件目录：

```text
/Users/<你的用户名>/Library/Application Support/Avid/Sibelius/Plugins
```

推荐放入批处理分类目录：

```text
/Users/<你的用户名>/Library/Application Support/Avid/Sibelius/Plugins/批处理
```

如果你的 Sibelius 使用英文界面，也可以放入 `Batch Processing` 等分类文件夹。

## How To Use The GUI Version / GUI 版使用方法

1. Open a saved `.sib` score.
2. Run `导出练习音轨（GUI）`.
3. Check the output folder and file prefix.
4. Choose MP3 or WAV.
5. Choose whether other staves should be `HalfMuted` or fully muted.
6. Review groups. Percussion staves are automatically selected in the default `Percussion` group when Sibelius reports them as percussion instruments.
7. Click a staff in a group list and press `加入/移除选中音轨` to include or remove it.
8. Click `导出`.

1. 打开并保存一个 `.sib` 乐谱。
2. 运行 `导出练习音轨（GUI）`。
3. 检查导出目录和文件名前缀。
4. 选择 MP3 或 WAV。
5. 选择其他声部使用 `HalfMuted` 还是全静音。
6. 检查编组。若 Sibelius 将某些 staff 识别为打击乐，它们会默认出现在 `Percussion` 编组中。
7. 在编组列表中选中 staff，点击 `加入/移除选中音轨` 来加入或移除。
8. 点击 `导出`。

## How To Use The No-GUI Version / 无 GUI 版使用方法

Open `ExportDimPracticeTracksNoGUI.plg` in Sibelius's plugin editor or a text editor, then edit the variables near the top of `Run()`:

打开 `ExportDimPracticeTracksNoGUI.plg`，在 Sibelius 插件编辑器或文本编辑器中修改 `Run()` 顶部附近的变量：

```javascript
outputFormat = 'MP3';
otherTracksMode = 'HALF';
vpAlwaysFull = True;
exportFullMix = True;
useScoreFileLocation = True;
manualOutputFolder = '/Users/your-name/Downloads';
manualBaseScoreName = 'Score';
```

The no-GUI version is useful when you want a fixed one-click workflow.

无 GUI 版适合固定流程的一键导出。

## Notes / 注意事项

- Sibelius may cache loaded plugins. If the menu or dialog does not update, fully quit and reopen Sibelius.
- MP3 export uses `SaveAsCompressedAudio`; WAV export uses `SaveAsAudio`.
- Audio export depends on Sibelius playback configuration. If export fails, check that playback uses suitable virtual instruments/audio devices.
- The plugin does not currently control the Sibelius metronome/click. Turn it off manually before exporting if needed.

- Sibelius 可能缓存已加载的插件。如果菜单或窗口没有更新，请完全退出并重新打开 Sibelius。
- MP3 导出使用 `SaveAsCompressedAudio`；WAV 导出使用 `SaveAsAudio`。
- 音频导出依赖 Sibelius 回放配置。如果导出失败，请检查回放配置是否使用合适的虚拟乐器/音频设备。
- 插件目前不控制 Sibelius 节拍器/click。如需关闭节拍器，请在导出前手动关闭。

## Version / 版本

Current version: `0.1.0`

当前版本：`0.1.0`

