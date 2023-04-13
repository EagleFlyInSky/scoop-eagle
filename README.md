# scoop-eagle

## 仓库特性

- 使用Scoop代替正常安装
- 完全静默方式安装
- 仓库自动更新 -> 使用Github Actions自动更新
- 优先使用绿色软件、便携软件，同时也会支持安装包软件
- 收录的软件没有弹窗绑定主页的流氓行为

## 软件列表

- BaiduNetdisk-Portable
- bandicam
- nTrun
- wolai
- WestWorldVPN



##  参数

需要做的就是将其中的各项替换。现对各个项目做一下介绍，加*的是必填项：

*homepage：主页链接；
license：软件发布遵循的协议；
*version：软件的版本；
*url：软件下载链接；
*hash：软件的校验码；
*bin：安装完毕后的可执行文件（.exe 等）的相对路径；
shortcuts：开始菜单里的快捷方式，上下分别为文件名、文件夹名；
checkver：版本校对；
autoupdate：自动升级，涉及持续集成

## hash

脚本开始构建的时候，需要到官网，把软件下载下来，然后本机查看 hash，默认为 sha256 码，也有 md5 和 sha1 形式的，命令如下：

```bash
certutil -hashfile [file] sha256
certutil -hashfile [file] md5
certutil -hashfile [file] sha1
```

## url

url是比较难处理的。简单说，开源软件最方便，很多可以开箱即用，而非开源的不少就特别繁琐，有的甚至处理不了，如 QQ。这个叙述起来都特别麻烦，需要具体情况具体分析，这里只简述一般情况，后面慢慢补充。

.msi类：往往不需要变更；
.zip类：往往不需要变更，部分需要在下载链接末尾添加#/dl.7z；
.exe类：

大部分都需要在下载链接末尾添加#/dl.7z（Scoop 默认使用 7zip 进行解压安装）；
不能直接解压的，如果内置有innosetup，需要在脚本里添加，"innosetup": true；
