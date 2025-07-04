---
title: LeviLamina 安装教程
sidebar_position: 1
---

# LeviLamina 安装教程

## 方法零：使用笨蛋脚本

首先下载[安装脚本](https://script.8aka.org/liteloaderbds-install)，下载完后右键**以管理员启动**即可

:::tip

你甚至不需要安装 VC 运行库，自动脚本会自行安装常用运行库，还会自动配置 Lip 镜像以加速下载

:::

## 方法一：使用 Lip 进行一键配置

### 准备工作 - 安装 Lip

首先，从 [GitHub](https://github.com/lippkg/lip/releases/latest) 下载 Lip 的最新版本的应用

然后，解压文件到你想要安装 Lip 的位置。

最后，将该位置添加到 PATH 环境变量中。

要检查是否成功安装 Lip，请在终端中运行 `lip --version`。你应该看到刚刚安装的 lip 的版本。

如果你使用的是 Windows 系统，你也可以在 GitHub 中下载 `.exe` 后缀的安装程序来安装。

### 安装

首先创建一个新的文件夹

然后运行命令

```shell
lip install github.com/LiteLDev/LeviLamina
```

Lip 会自动下载 BDS 并配置 LeviLamina 加载器

:::info

如果因网络问题无法下载 GO 模块或 LeviLamina 及其依赖，可以运行命令

```shell
lip config GoModuleProxyURL <url>
```

和

```shell
lip config GitHubMirrorURL <url>
```

来配置镜像，官方给的镜像

```shell
lip config GoModuleProxyURL https://goproxy.cn
lip config GitHubMirrorURL https://github.bibk.top
```

:::

:::info

如果因网络问题无法下载 BDS 服务端文件可以去其他地方寻找文件下载，并将压缩包放在 `your-folder\.cache\bdsdown`中

:::

现在，你已成功安装了 LeviLamina 了，要启动它，请运行命今

```shell
bedrock_server_mod.exe
```

## 方法二：手动安装 (不推荐)

只有想要调试新版本的开发人员才会手动安装，手动安装只会安装允许 LeviLamina 运行的基本部件，它缺少 CrashLogger、I18N 等组件。

### 下载必要的文件

1. ​**下载 LeviLamina**​：
   * 转到 [GitHub 上的 LeviLamina 发布页面](https://github.com/LiteLDev/LeviLamina/releases)。
   * 选择所需的版本。
   * 从所选版本 Release 中下载文件 `levilamina-windows-x64.zip`
2. ​**下载 BDS(Minecraft 服务器)**​：
   * 访问 [Minecraft 的服务器下载页面](https://www.minecraft.net/en-us/download/server/bedrock)。
   * 获取与你的 LeviLamina 版本相对应的 Bedrock 专用服务器 (BDS) 版本，名为
   `bedrock-server-<version>.zip`
3. ​**获取 PeEditor 和 PreLoader**​：
   * 前往他们各自的 GitHub 发布页面：[PeEditor Releases](https://github.com/LiteLDev/PeEditor/releases) 和 [PreLoader Releases](https://github.com/LiteLDev/PreLoader/releases)。
   * 下载最新的 `PeEditor.exe` ​`PreLoader.dll` 文件

:::warning

​**注意**​：通常，最新版本的 LeviLamina 与最新版本的 PeEditor 和 PreLoader 保持一致。确保它们与你的 BDS 版本兼容。

:::

### 安装步骤

1. ​**解压 BDS 文件**​：
   * 将从步骤 2 获取的文件 `bedrock-server-<version>.zip` 解压到一个新的空文件夹中
2. ​**放置 PeEditor 和 PreLoader**​：
   * 将 `PeEditor.exe` ​`PreLoader.dll`​ `bedrock_server.exe` 文件移动到解压后 BDS 文件的目录
3. ​**安装 LeviLamina**​：
   * 从步骤 1 中解压文件 `levilamina-windows-x64.zip`
   * 将文件夹放入 BDS 同一目录中
4. ​**运行 PeEditor**​：
   * 双击 `PeEditor.exe` 并等待配置完成
   * 然后，你可以在目录中找到一个名为 `bedrock_server_mod.exe` 的新文件，原始文件 `bedrock_server.exe` 将重命名为 `bedrock_server.exe.bak`

现在，你已成功安装了 LeviLamina 了，要启动它，请运行命今

```shell
bedrock_server_mod.exe
```
