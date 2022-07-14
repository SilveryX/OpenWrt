<div align="center">
<img width="768" src="https://cdn.jsdelivr.net/gh/haiibo/OpenWrt/image/openwrt.png"/>
<h1>OpenWrt — 多设备固件云编译</h1>


[![](https://img.shields.io/badge/-目录:-696969.svg)](#readme) [![](https://img.shields.io/badge/-项目说明-FFFFFF.svg)](#项目说明-) [![](https://img.shields.io/badge/-固件下载-FFFFFF.svg)](#固件下载-) [![](https://img.shields.io/badge/-近期更新-FFFFFF.svg)](#近期更新-) [![](https://img.shields.io/badge/-插件预览-FFFFFF.svg)](#插件预览-) [![](https://img.shields.io/badge/-编译教程-FFFFFF.svg)](#编译教程-) [![](https://img.shields.io/badge/-特别提示-FFFFFF.svg)](#特别提示-) [![](https://img.shields.io/badge/-捐助项目-FFFFFF.svg)](#捐助项目-) [![](https://img.shields.io/badge/-鸣谢-FFFFFF.svg)](#鸣谢-)
</div>


## 项目说明 [![](https://img.shields.io/badge/-项目基本介绍-FFFFFF.svg)](#项目说明-)
- 固件来源：[![Lean](https://img.shields.io/badge/Lede-Lean-red.svg?style=flat&logo=appveyor)](https://github.com/coolsnowwolf/lede) [![P3TERX](https://img.shields.io/badge/OpenWrt-P3TERX-blueviolet.svg?style=flat&logo=appveyor)](https://github.com/P3TERX/Actions-OpenWrt) [![Sirpdboy](https://img.shields.io/badge/Package-Sirpdboy-orange.svg?style=flat&logo=appveyor)](https://github.com/sirpdboy/sirpdboy-package) [![Haiibo](https://img.shields.io/badge/Build-Haiibo-success.svg?style=flat&logo=appveyor)](https://github.com/haiibo/OpenWrt)
- 项目使用 Github Actions 拉取 [Lean](https://github.com/coolsnowwolf/lede) 的 `Openwrt` 源码仓库进行云编译
- 固件默认 IP 地址：`192.168.1.1` 默认密码：`password`
- 适配的软路由设备有：`Wyse3040`



## 编译教程 [![](https://img.shields.io/badge/-项目基本编译教程-FFFFFF.svg)](#编译教程-)
1. 点击右上角 `Fork`，Fork 本项目到你自己的仓库

2. 创建个人访问令牌，如果已创建请跳过第三步（固件发布会调用，否则无法发布）

3. 点击右上角自己头像 → `Settings` → `Developer settings` → `Personal access tokens` → `Generate new token` Note 名字随便写一个，勾选 `repo` 和 `workflow` 点击最下方绿色按钮 `Generate token` 完成创建

4. 编辑对应文件夹下 `.config` 文件，`luci-app-xxx` 为插件名，结尾 `=y` 为选择，`is not set` 为不选择

5. 插件对应名称及功能请参考恩山网友帖子：[OpenWrt 编译 LuCI -> Applications 添加插件应用说明-L大](https://www.right.com.cn/forum/thread-3682029-1-1.html)

6. 如果需要修改默认 IP、添加或删除插件源以及一些其他自定义设置请在 `diy-part2.sh` 文件中进行修改

7. 点击 `Actions` → `要编译的workflow` → `Run workflow` → `Run workflow` 一次编译大概需要3~5小时

8. 编译完成后在仓库主页 `Releases` 对应 Tag 标签中查看以及下载固件

<details>
<summary><b>&nbsp;如果你觉得修改 .config 文件麻烦，那么你可以点击此处尝试本地提取</b></summary>

1. 首先安装好 Ubuntu 64bit，推荐 Ubuntu 20.04 LTS x64

2. 命令行输入 `sudo apt-get update`，然后输入
`sudo apt-get -y install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch python3 python2.7 unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint device-tree-compiler g++-multilib antlr3 gperf wget curl swig rsync`

3. 使用 `git clone https://github.com/coolsnowwolf/lede` 命令下载好源代码，然后 `cd lede` 进入目录

4. 复制 diy-part2.sh 文件内所有内容到命令行，添加自定义插件和自定义设置

5. ```bash
   ./scripts/feeds update -a
   ./scripts/feeds install -a
   make menuconfig
   ```

6. 选好插件后输入以下命令导出差异部分

   ```bash
   make defconfig
   ./scripts/diffconfig.sh > seed.config
   ```

7. 这样配置的差异部分就写入 seed.config 这个文件了
   
   在命令行输入 `cat seed.config` 查看这个文件，也可以用文本编辑器打开

8. 复制 seed.config 文件内所有内容到对应 .config 文件中覆盖就可以了

   **如果不懂编译界面可以参考 YouTube 视频：[软路由固件 OpenWrt 编译界面设置](https://www.youtube.com/watch?v=jEE_J6-4E3Y&list=WL&index=7)**
</details>


## 特别提示 [![](https://img.shields.io/badge/-个人免责声明-FFFFFF.svg)](#特别提示-)

- **因精力有限不提供任何技术支持和教程等相关问题解答，不保证完全无 BUG！**

- **本人不对任何人因使用本固件所遭受的任何理论或实际的损失承担责任！**

- **本人保证固件没加入任何后门，保护干净安全的网络环境从我做起！**




## 鸣谢 [![](https://img.shields.io/badge/-跪谢各大佬-FFFFFF.svg)](#鸣谢-)
| [ImmortalWrt](https://github.com/immortalwrt) | [coolsnowwolf](https://github.com/coolsnowwolf) | [P3TERX](https://github.com/P3TERX) | [Flippy](https://github.com/unifreq) |
| :-------------: | :-------------: | :-------------: | :-------------: |
| <img width="100" src="https://avatars.githubusercontent.com/u/53193414"/> | <img width="100" src="https://avatars.githubusercontent.com/u/31687149"/> | <img width="100" src="https://avatars.githubusercontent.com/u/25927179"/> | <img width="100" src="https://avatars.githubusercontent.com/u/39355261"/> |
| [Ophub](https://github.com/ophub) | [Breakings](https://github.com/breakings) | [QiuSimons](https://github.com/QiuSimons) | [IvanSolis1989](https://github.com/IvanSolis1989) |
| <img width="100" src="https://avatars.githubusercontent.com/u/68696949"/> | <img width="100" src="https://avatars.githubusercontent.com/u/25475074"/> | <img width="100" src="https://avatars.githubusercontent.com/u/45143996"/> | <img width="100" src="https://avatars.githubusercontent.com/u/44228691"/> |


<a href="#readme">
<img src="https://img.shields.io/badge/-返回顶部-FFFFFF.svg" title="返回顶部" align="right"/>
</a>
