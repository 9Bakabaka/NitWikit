---
title: 手机直装模板
---

# 手机直装模板

在手机上装 PojavLauncher/FCL 还是太吃操作了，这时候我们就需要客户端安装包了

[GitHub 地址](https://github.com/MrXiaoM/FoldCraftLauncher)

## 设置

### 与 FCL 原版共存

已经与原版共存的了，避免与本仓库主的服务器客户端冲突，建议修改

(应用包名)  
文件：`FCL/build.gradle`  
位置：`applicationId`

(文件提供器)  
文件：`FCLLibrary/src/main/res/values/strings.xml`  
位置：`file_browser_provider`, `file_browser_document_provider`

(默认 FCL 客户端公共目录)  
文件：`FCLauncher/src/main/java/com/tungsten/fclauncher/utils/FCLPath.java`  
位置：`STORAGE_DIR`

### 应用版本号

(实际版本号)  
文件：`FCL/build.gradle`  
位置：`versionCode` 和 `versionName`

(显示版本号)  
文件：`FCL/src/main/res/values/strings.xml`  
位置：`app_version`

### 应用图标

文件：`FCL/src/main/res/drawable/ic_launcher` + (`.png`|`_round.png`)  
文件：`FCL/src/main/res/drawable/img_app.png`

### 首次启动的 EULA 页面

文件：`FCL/src/main/assets/eula.txt`

### 默认主题颜色

文件：`FCLLibrary/src/main/java/com/tungsten/fcllibrary/component/theme/ThemeEngine.java`  
位置：`getDefaultColor`

### 删除多余的 Java

路径：`FCL/src/main/assets/app_runtime/java/`  
不需要哪个就删哪个，只留自己客户端需要的那个即可

### 背景图

文件：`FCLLibrary/src/main/res/drawable/background_` + (`dark.jpg`|`light.jpg`)

### 游戏启动加载页面背景图

文件：`FCLLibrary/src/main/res/drawable/background_loading_` + (`dark.jpg`|`light.jpg`)

### 主页面皮肤

文件：`FCL/src/main/res/layout/ui_main.xml`

删掉 `android:visibility="gone"` 即可在主页面显示 FCL 的皮肤展示

在该文件中还可以给主页面加任意组件，如果需要加点击事件  
文件：`FCL/src/main/java/com/tungsten/fcl/ui/main/MainUI.java`

### 创建账户页面

(离线登录，离线账户用户名的规则)  
文件：`FCL/src/main/java/com/tungsten/fcl/ui/account/CreateAccountDialog.java`  
位置：`USERNAME_CHECKER_PATTERN`

默认的规则是，允许中文、英文、数字、下划线

(如果玩家输入的用户名规则，将会显示的警告内容)
文件：`FCL/src/main/res/values-zh/strings.xml`
位置：`account_methods_offline_name_invalid`

(离线登录，离线账户用户名上面的红字提示)

### 游戏界面右下角小字

文件：`FCL/src/main/res/layout/view_game_menu.xml`
位置：开头往下翻一点

### 客户端自动解压释放

路径：`FCL/src/main/assets/minecraft`

将客户端的 `.minecraft` 文件夹复制至此，注意不要删除 `version` 文件，每次更新客户端都应该将 `version`
文件的数字加一，这样下次玩家更新客户端 apk 后就会提示更新客户端文件了。

更新策略是，删除原有的所有文件，再释放安装包内文件。

为了避免**安装包太大**，建议打包的客户端删除 libraries 和 assets，否则过大的安装包，会导致储存空间占用翻倍、增加使用门槛，且让玩家失去下载安装包的耐心。

### 显示公告

文件：`FCL/src/main/java/com/tungsten/fcl/ui/main/MainUI.java`
位置：`enableAnnouncement`

默认关闭

### 隐藏皮肤模型预览

文件：`FCLLibrary/src/main/java/com/tungsten/fcllibrary/component/theme/Theme.java`
位置：搜索 `sharedPreferences.getBoolean("close_skin_model", false);`，后面的即为默认值

默认不隐藏

## 构建

首先你需要安装 Android Studio，使用 git 命令克隆仓库

```shell
git clone https://github.com/MrXiaoM/FoldCraftLauncher
```

将项目导入到 Android Studio 中，修改项目根目录下的『local.properties』
在『local.properties』文件中增加以下键值对：

* key-store-password
* oauth-api-key
* curse-api-key

找到『Build』 —> 『Generate Signed App Bundle / APK…』选项，并编译该项目即可

