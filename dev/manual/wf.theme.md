主题样式
===============
系统支持多个主题，管理员可在系统后台选择确定使用哪个主题。


## 样式选择
所有主题样式存放在./theme文件夹中，每个主题放在一个文件夹。默认主题是./theme/default/。

## 主题目录结构：
```
-+ theme
 |- default                # 默认主题
     |- pc                 # PC版样式
     |  |- images          # PC版样式使用的图片
     |  |- preview.jpg     # PC版样式首页截图缩略图
     |  |- screenshot.jpg  # PC版样式首页截图
     |  |- style.css       # PC版样式表
     |- mobile             # 手机版版样式
     |  |- images          # 手机版样式使用的图片
     |  |- preview.jpg     # 手机版样式首页截图缩略图
     |  |- screenshot.jpg  # 手机版样式首页截图
     |  |- style.css       # 手机版样式表
     |- style.ini          # 主题参数设置
```

## 主题配置信息
主题配置信息目的是在后台选择主题时显示主题信息。
主题配置信息放在主题文件夹中的style.ini文件。如默认主题配置为./theme/default/style.ini。

主题参数：
```
name     = 默认主题
version  = 1.0
author   = Windwork
desc     = 官方提供默认主题
```

