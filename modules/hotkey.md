<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [cheetsheets](#cheetsheets)
- [Mac](#mac)
- [alfred](#alfred)
- [intelliJ IDEA](#intellij-idea)
- [Terminal](#terminal)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# cheetsheets

[cheetsheets including languages, tools, libraries](https://github.com/skywind3000/awesome-cheatsheets)

# Mac

[Resource](https://support.apple.com/zh-cn/HT201236)

- `Fn`+`delete` 向前删除

- `command + shift + g` Finder进入指定文件夹

- `command + shift + .`开/关隐藏文件 

- `command + option + v` 剪切

- `sqlite3 $(sudo find /private/var/folders -name com.apple.dock.launchpad)/db/db "DELETE FROM apps WHERE title='LaunchPadIconName';" && killall Dock` 

  删除多余的图标, 把LauchPadIconName改成图标的名字

- `Command + shift + 5` 截屏

- `⌥` + `⇧` + `音量/亮度` 1/4格调节

- `⌘ + ⌃ + space` emoji

  ![The OS X emoji interaction](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-17-213953.gif) 

# alfred

- usage
  - general

      - `ej` eject volumes; `eja` eject all volumes
      - append selected text: hold `⌘` and double tap `c` twice
    - search for Medium.com freely in Twitter: `twitter {query}`  
  
- snippets
  
  - `s {query}`
  
  - collection: Mac symbols, currency, emoji, dynamic placeholder
  
    - [emoji](http://joelcalifa.com/blog/alfred-emoji-snippet-pack/)
  
      `s :{query}` browse emoji
  
    - [dynamic placeholder](https://www.alfredapp.com/help/workflows/advanced/placeholders/)
  
      `::date` May 17, 2020
  
      `::time` 16:10:55 
  
- workflow
  
  > 合集: 
  >
  > [1](https://github.com/learn-anything/alfred-workflows)
  >
  > [2](http://www.packal.org/)
  >
  > [3](https://github.com/alfred-workflows/awesome-alfred-workflows)
  >
  > [官网](https://links.jianshu.com/go?to=https%3A%2F%2Fwww.alfredforum.com%2Fforum%2F3-share-your-workflows)
  
  - [变量命名](https://github.com/xudaolong/CodeVar)
  
      - update：[替换为自己的有道 key](https://github.com/xudaolong/CodeVar/issues/35#issuecomment-1707950484)
  
  - [有道](https://github.com/wensonsmith/YoudaoTranslate)
  
    - 使用方法 `yd {query}`
    - 按住`cmd` +`return` 即可发音,这样不会关闭窗口。在音标上直接回车也可以播放发音并会关闭窗口。
    - 在选项上`return`可以复制翻译结果
    - 翻译结果上按 `Shift` 可以直接预览有道网页
    - 输入 `yd *` 可以查询最近的查询记录
  
  - ~~Stack Overflow~~
  
    1. `so {query}`
    2. `so {query} .{tag}`
  
  - [GitHub](https://github.com/gharlan/alfred-github-workflow)
  
    - Key Combinations
    | Key Combination        | Action                        |
    | ---------------------- | ----------------------------- |
    | `enter`                | Open entry in default browser |
    | `cmd` + `c`            | Copy URL of the entry         |
    | `cmd` + `enter`        | Paste URL to front most app   |
    | `shift` or `cmd` + `y` | Open URL in QuickLook         |
  
      - Search commands
        - `gh s repo`
        - `gh s @user`
      - Repo commands
        - `gh user/repo`
        - `gh user/repo @branch`
      - User commands
        - `gh @user`
        - `gh @user overview`
      - "My" commands
        - `gh my dashboard`
        - `gh my notifications`
        - `gh my profile`
        - `gh my issues`
      - Workflow commands
        - `gh > logout`
        - `gh > delete cache`
        - `gh > delete database`
        - `gh > update`
        - `gh > activate autoupdate`
        - `gh > deactivate autoupdate`
        - `gh > help`
        - `gh > changelog`
      - Commands
        - To search through your GitHub Enterprise instance replace `gh` by `ghe`.

# intelliJ IDEA

> [refer](https://www.jetbrains.com/help/rider/Reference_Keymap_Rider_OSX.html?keymap=mac_os_x_10.5)

- 常用

  | Command                                                      | Shortcut    |
  | ------------------------------------------------------------ | ----------- |
  | [Open Solution or Project](https://www.jetbrains.com/help/rider/Creating_and_Opening_Projects_and_Solutions.html?keymap=mac_os_x_10.5#open_existing_project) | ⌃+⇧+O       |
  | [Show Action List](https://www.jetbrains.com/help/rider/Actions_List.html?keymap=mac_os_x_10.5) | ⌥+Enter     |
  | [Search Everywhere](https://www.jetbrains.com/help/rider/Searching_Everywhere.html?keymap=mac_os_x_10.5) | Double-⇧    |
  | [Navigate To…](https://www.jetbrains.com/help/rider/Navigation_and_Search__Navigate_from_Here.html?keymap=mac_os_x_10.5) | ⌃+⇧+N       |
  | [Find Usages](https://www.jetbrains.com/help/rider/Navigation_and_Search__Finding_Usages__Finding_Usages_of_a_Symbol.html?keymap=mac_os_x_10.5) | ⌥+F7        |
  | [Select In...](https://www.jetbrains.com/help/rider/Navigation_and_Search__Context_Dependent_Navigation.html?keymap=mac_os_x_10.5#locating-current-item-in-other-views) | ⌥+F1        |
  | [Settings...](https://www.jetbrains.com/help/rider/Rider_Settings.html?keymap=mac_os_x_10.5) | ⌘+,         |
  | [Find Action...](https://www.jetbrains.com/help/rider/Navigating_to_Action.html?keymap=mac_os_x_10.5) | ⌘+⇧+A       |
  | [Generate...](https://www.jetbrains.com/help/rider/Generating_Type_Members.html?keymap=mac_os_x_10.5) | ⌘+N ⌃+Enter |
  | [Build Solution](https://www.jetbrains.com/help/rider/Building_Projects.html?keymap=mac_os_x_10.5) | ⌘+F9        |
  | [Debug...](https://www.jetbrains.com/help/rider/Starting_Debugging.html?keymap=mac_os_x_10.5) | ⌃+⌥+D       |
  | [View Breakpoints...](https://www.jetbrains.com/help/rider/Using_Breakpoints.html?keymap=mac_os_x_10.5) | ⌘+⇧+F8      |
  | [Attach to Process...](https://www.jetbrains.com/help/rider/Starting_Debugging.html?keymap=mac_os_x_10.5) | ⌥+⇧+F5      |
  | [VCS Operations Popup...](https://www.jetbrains.com/help/rider/Version_Control_Integration.html?keymap=mac_os_x_10.5) | ⌃+V         |
  | [Refactor This...](https://www.jetbrains.com/help/rider/Refactor_This.html?keymap=mac_os_x_10.5) | ⌃+T         |
  | [Inspect This...](https://www.jetbrains.com/help/rider/Code_Analysis__Inspect_This.html?keymap=mac_os_x_10.5) | ⌘+⌥+⇧+A     |
  | 移动光标到上一次/下一次位置                                  | ⌘+[ or ⌘+]  |

  - `⇧ + enter `光标移到新建的下一行

- Editing（编辑）

  - `⌘ + ⇧ + 上/下` 上下移动当前行代码. 若光标在方法前, 则移动整个方法

  - `⌘ + 左/右` 定位到行首/行末

    `⌥ + 左/右` 定位到前一个单词

  - `Control + Space` 基本的代码补全（补全任何类、方法、变量）

  - `Control + Shift + Space` 智能代码补全（过滤器方法列表和变量的预期类型）
    
  - `Command + Shift + Enter` 自动结束代码，行末自动添加分号

  - `F1` 查看文档, 参数信息

  - `Command + 鼠标放在代码上` 显示代码简要信息

  - `Command + F1` 在错误或警告处显示具体描述信息
    
  - `Command + N, Control + Enter, Control + N` 生成代码（getter、setter、构造函数、hashCode/equals,toString）

  - `Control + O` 覆盖方法（重写父类方法）
    
  - `Control + I` 实现方法（实现接口中的方法）

  - `Command + Option + T` 包围代码（使用if..else, try..catch, for, synchronized等包围选中的代码）

  - `Option + 方向键上` 连续选中代码块
    
  - `Option + 方向键下` 减少当前选中的代码块

  - `Control + Shift + Q` 显示上下文信息
    
  - `Option + Enter` 显示意向动作和快速修复代码

  - `Command + Option + L` 格式化代码

  - `Control + Option + O` 优化import

  - `Control + Option + I` 自动缩进线
    
  - `Tab / Shift + Tab` 缩进代码 / 反缩进代码

  - `Command + D` 复制当前行或选定的块
    
  - `Command + Delete` 删除当前行或选定的块的行

  - `Control + Shift + J` 智能的将代码拼接成一行

    `Command + Enter` 智能的拆分拼接的行

  - `Command + Shift + ] / Command + Shift + [` 选择直到代码块结束/开始

  - `Option + Fn + Delete` 删除到单词的末尾

    `Option + Delete` 删除到单词的开头

  - `Command + 加号 / Command + 减号` 展开 / 折叠代码块

    `Command + Shift + 加号` 展开所有代码块

    `Command + Shift + 减号` 折叠所有代码块

- Search/Replace（查询/替换）
  - `Double Shift` 查询任何东西
  - `Command + F` 文件内查找
  - `Command + G` 查找模式下，向下查找
  - `Command + Shift + G` 查找模式下，向上查找
  - `Command + R` 文件内替换
  - `Command + Shift + F` 全局查找（根据路径）
  - `Command + Shift + R` 全局替换（根据路径）
  - `Command + Shift + S` 查询结构（Ultimate Edition 版专用，需要在Keymap中设置）
  - `Command + Shift + M` 替换结构（Ultimate Edition 版专用，需要在Keymap中设置）

- Usage Search（使用查询）
  - `Option + F7 / Command + F7` 在文件中查找用法 / 在类中查找用法
  - `Command + Shift + F7` 在文件中突出显示的用法
  - `Command + Option + F7` 显示用法

- Compile and Run（编译和运行）
  - `Command + F9` 编译Project
  - `Command + Shift + F9` 编译选择的文件、包或模块
  - `Control + Option + R` 弹出 Run 的可选择菜单
  - `Control + Option + D` 弹出 Debug 的可选择菜单
  - `Control + R` 运行
  - `Control + D` 调试
  - `Control + Shift + R, Control + Shift + D` 从编辑器运行上下文环境配置

- Debugging（调试）
  - `F8` 进入下一步，如果当前行断点是一个方法，则不进入当前方法体内
  - `F7` 进入下一步，如果当前行断点是一个方法，则进入当前方法体内，如果该方法体还有方法，则不会进入该内嵌的方法中
  - `Shift + F7` 智能步入，断点所在行上有多个方法调用，会弹出进入哪个方法
  - `Shift + F8` 跳出
  - `Option + F9` 运行到光标处，如果光标前有其他断点会进入到该断点
  - `Option + F8` 计算表达式（可以更改变量值使其生效）
  - `Command + Option + R` 恢复程序运行，如果该断点下面代码还有断点则停在下一个断点上
  - `Command + F8` 切换断点（若光标当前行有断点则取消断点，没有则加上断点）
  - `Command + Shift + F8` 查看断点信息

- Navigation（导航）
  - `Command + O` 查找类文件
  - `Command + Shift + O` 查找所有类型文件、打开文件、打开目录，打开目录需要在输入的内容前面或后面加一个反斜杠`/`
  - `Command + Option + O` 前往指定的变量 / 方法
  - `Control + 方向键左 / Control + 方向键右` 左右切换打开的编辑tab页
  - `F12` 返回到前一个工具窗口
  - `Esc` 从工具窗口进入代码文件窗口
  - `Shift + Esc` 隐藏当前或最后一个活动的窗口，且光标进入代码文件窗口
  - `Command + Shift + F4` 关闭活动run/messages/find/... tab
  - `Command + L` 在当前文件跳转到某一行的指定处
  - `Command + E` 显示最近打开的文件记录列表
  - `Option + 方向键左 / Option + 方向键右` 光标跳转到当前单词 / 中文句的左 / 右侧开头位置
  - `Command + Option + 方向键左 / Command + Option + 方向键右` 退回 / 前进到上一个操作的地方
  - `Command + Shift + Delete` 跳转到最后一个编辑的地方
  - `Option + F1` 显示当前文件选择目标弹出层，弹出层中有很多目标可以进行选择(如在代码编辑窗口可以选择显示该文件的Finder)
  - `Command + B / Command + 鼠标点击` 进入光标所在的方法/变量的接口或是定义处
  - `Command + Option + B` 跳转到实现处，在某个调用的方法名上使用会跳到具体的实现处，可以跳过接口
  - `Option + Space, Command + Y` 快速打开光标所在方法、类的定义
  - `Control + Shift + B` 跳转到类型声明处
  - `Command + U` 前往当前光标所在方法的父类的方法 / 接口定义
  - `Control + 方向键下 / Control + 方向键上` 当前光标跳转到当前文件的前一个/后一个方法名位置
  - `Command + F12` 弹出当前文件结构层，可以在弹出的层上直接输入进行筛选（可用于搜索类中的方法）
  - `Control + H` 显示当前类的层次结构
  - `Command + Shift + H` 显示方法层次结构
  - `Control + Option + H` 显示调用层次结构
  - `F2 / Shift + F2` 跳转到下一个/上一个突出错误或警告的位置
  - `F4 / Command + 方向键下` 编辑/查看代码源
  - `Option + Home` 显示到当前文件的导航条
  - `F3`选中文件/文件夹/代码行，添加/取消书签
  - `Option + F3` 选中文件/文件夹/代码行，使用助记符添加/取消书签
  - `Control + 0...Control + 9` 定位到对应数值的书签位置
  - `Command + F3` 显示所有书签
  
- Refactoring（重构）
  - `F5` 复制文件到指定目录
  - `F6` 移动文件到指定目录
  - `Command + Delete` 在文件上为安全删除文件，弹出确认框
  - `Shift + F6` 重命名文件
  - `Command + F6` 更改签名
  - `Command + Option + N` 一致性
  - `Command + Option + M` 将选中的代码提取为方法
  - `Command + Option + V` 提取变量
  - `Command + Option + F` 提取字段
  - `Command + Option + C` 提取常量
  - `Command + Option + P` 提取参数

- VCS/Local History（版本控制/本地历史记录）
  - `Command + K` 提交代码到版本控制器
  - `Command + T` 从版本控制器更新代码
  - `Option + Shift + C` 查看最近的变更记录
  - `Control + C` 快速弹出版本控制器操作面板

- Live Templates（动态代码模板）
  - `Command + Option + J` 弹出模板选择窗口，将选定的代码使用动态模板包住
  - `Command + J` 插入自定义动态代码模板

- General（通用）
  - `Command + 1...Command + 9` 打开相应编号的工具窗口

  - `Command + Option + Y` 同步、刷新

  - `Control + Command + F` 切换全屏模式

  - `Command + Shift + F12` 切换最大化编辑器

  - `Option + Shift + F` 添加到收藏夹

  - `Option + Shift + I` 检查当前文件与当前的配置文件

  - `Control + ` 快速切换当前的scheme（切换主题、代码样式等）

  - `Command + ;` 打开项目结构对话框

  - `Shift + Command + A` 查找动作（可设置相关选项）

  - `Control + Shift + Tab` 编辑窗口标签和工具窗口之间切换（如果在切换的过程加按上delete，则是关闭对应选中的窗口）

  - `Command + Shift +8` 竖编辑模式

    

# Terminal

[Cheatsheet](https://github.com/0nn0/terminal-mac-cheatsheet)

