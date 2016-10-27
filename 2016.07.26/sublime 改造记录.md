# sublime 改造记录
## 安装插件管理工具
复制以下代码

```
import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

打开sublime text 3，按`control` + `~`或者菜单`View` > `Show Console`打开命令窗口，粘贴以上代码并回车即可。

## 配置和快捷键修改

打开右上角的Sublime Text,然后选中Perferences,可以看到几个选项.
* Settings - Default : 系统设置
* Settings - Use : 用户设置
* Key Bindings - Default : 系统快捷键设置
* Key Bindings - User : 用户快捷键设置

PS : 虽然都可以修改,但是最好不要动系统的设置,在用户设置里面修改,方便同步备份.

## 插件安装

安装插件很简单,`Command` + `Shift` + `P` 召唤出命令面板,输入 `install` ,选择 Package Control : Install Package` ,然后会联网加载插件库,输入插件名称即可.

## 插件选择

插件的选择,够用就好.

* SideBarEnhancement
侧边栏增强插件.

* SideBarFolders
项目列表插件.
如果需要打开多个项目文件夹，切经常在多个项目之间切换工作空间，可以安装 `SideBarFolders` 插件，该插件在在菜单栏多出一个 `Folders` 选项，点击可查看所有项目文件夹.

* AllAutocomplete 
代码自动补全插件.

* BracketHignlighter
高亮配对的括号插件.

* ConvertToUTF8
转码插件.打开GBK文件必备.

* DocBlockr
自动生成注释.

* CTags
一个用于从程序源代码树产生索引文件(或tag文件),从而便于文本编辑器来实现快速定位的实用工具.

* PHP Codebeautifier
php代码美化工具.

* SublimeTmpl
快速生成代码模板插件.

* phpfmt
php代码格式化插件.需要自行配置php路径.

* Seti_UI 
做工精良的主题插件.
启用 `Seti_UI` 主题:
在 `Settings - User` 配置文件中,加入一句话.

```
"theme": "Seti.sublime-theme"
```

* SideBarGit 
在侧边栏显示文件的git状态的插件.

* SublimeLinter
错误提示插件.

* SublimeLinter-php (依赖于上面的插件)
PHP错误提示插件.

* Color Highlighter
css颜色高亮插件,将鼠标放在css颜色的值上时,会自动显示对应的颜色.

* ColorPicker
css取色器,将光标置于想要输入颜色的位置,打开sublime的控制台,输入color picker召唤出取色器，选择你想要的颜色,点击pick(也可以设置快捷键).

## 其他配置
显示所有已打开的文件:

`View` > `Side Bar` > `Show Open Files`

修改配置文件,加入如下代码:

```
"auto_find_in_selection": true,
"bold_folder_labels": true,
"color_scheme": "Packages/User/SublimeLinter/Seti Monokai (SL).tmTheme",
"disable_tab_abbreviations": true,
"draw_minimap_border": true,
"draw_white_space": "all",
"fade_fold_buttons": false,
"font_face": "mononoki-Regular",
"font_size": 14,
"highlight_line": true,
"highlight_modified_tabs": true,
"ignored_packages":
[
	"Vintage"
],
"line_padding_bottom": 1,
"line_padding_top": 1,
"margin": 4,
"save_on_focus_lost": true,
"show_full_path": true,
"tab_size": 4,
"theme": "Seti.sublime-theme",
"translate_tabs_to_spaces": true
```

